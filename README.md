# Sichere Implementierungen auf Microcontrollern (WS 2023/2024)

## Installation and Setup

### Prerequisites

- VSCode
- VSCode Extensions: Python, Jupyter
- Git
- Python >=3.9

### Installation of ChipWhisperer

#### Windows

1. Download latest version of ChipWhisperer Setup from
   [https://github.com/newaetech/chipwhisperer/releases](https://github.com/newaetech/chipwhisperer/releases).
2. Install. Recommended Installation folder: `C:\cw`.

#### Unix like OS

1. Clone ChipWhisperer repository somewhere
   (In the following we will assume that the location is `~/work/chipwhisperer`):

   ```sh
   cd ~/work/
   git clone --branch 5.7.0 https://github.com/newaetech/chipwhisperer.git
   ```

2. Install required packages. Here as example for a Debian based OS:

   ```sh
   sudo apt install libusb-dev make avr-libc gcc-avr gcc-arm-none-eabi
   ```

3. Adjust udev rules and allow user to access serial interfaces:

   ```sh
   sudo cp ~/work/chipwhisperer/hardware/50-newae.rules /etc/udev/rules.d/50-newae.rules
   sudo udevadm control --reload-rules
   sudo usermod -aG dialout $USER
   sudo usermod -aG plugdev $USER
   ```

### Installation of required Python packages

1. Clone this repository somewhere
   (In the following we will assume that the location is `~/work/ws2324/securecoding_ws2324`):

   ```sh
   cd ~/work/ws2324
   git clone https://github.com/hackenbergstefan/securecoding_ws2324.git
   ```

2. Create virtual environment and activate it:

   ```sh
   cd ~/work/ws2324/securecoding_ws2324
   python -m venv .venv
   # On Unix like:
   . .venv/bin/activate
   # On Windows:
   .venv/Scripts/activate
   ```

3. Install requirements:

   ```sh
   (.venv)$ pip install -r requirements.lock
   ```

### Adjust environment variables

Create a file `.env` inside the repository with the following content:

Windows:

```env
# C:\work\ws2324\securecoding_ws2324\.env
PATH=C:\cw\cw\usr\bin;C:\cw\cw\home\portable\armgcc\bin;C:\cw\cw\home\portable\avrgcc\bin;$env["PATH"]
CWFIRMWAREPATH=C:\cw\cw\home\portable\chipwhisperer\hardware\victims\firmware
```

Unix like (Assume your username is `stefan`):

```env
# /home/stefan/work/ws2324/securecoding_ws2324/.env
CWFIRMWAREPATH=/home/stefan/work/chipwhisperer/hardware/victims/firmware
```

Reload VSCode (`Ctrl+Shift+P -> "Developer: Reload Window"`)

### Test setup

1. Open repository folder with VSCode
   VSCode should have recognized your virtual environment
2. Inside VSCode open [./lecture_0/test_setup.ipynb](./lecture_0/test_setup.ipynb)
3. Select kernel from virtual environment
4. Run cells step by step
