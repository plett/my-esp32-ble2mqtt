# Installing dependencies

You should clone this repo with `git clone --recursive path_to_repo`. If you
didn't do this and already have a checked out copy, `git submodule update --init
--recursive` will do it

## ESP-IDF dependencies
This bit following https://docs.espressif.com/projects/esp-idf/en/stable/get-started/linux-setup.html

Download https://dl.espressif.com/dl/xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0.tar.gz
```
mkdir esp
cd esp
tar xvf xtensa-esp32-elf-linux64-1.22.0-80-g6c4433a-5.2.0.tar.gz
```

sudo apt-get install gcc git wget make libncurses-dev flex bison gperf
virtualenv -p python2 esp-venv
. esp-venv/bin/activate
pip install -r esp-idf/requirements.txt

# Building

```
export PATH="/full/path/to/xtensa-esp32-elf/bin:$PATH"
cd esp32-ble2mqtt
export IDF_PATH=../esp-idf
make```
First run with do `make menuconfig` in esp-idf. Set `Serial flasher config` to
/dev/ttyUSB0 or wherever your ESP32 is connected and Save.

You might get errors about `__bswap16()` not being a function. Change it to
`__bswap_16()` if you do.

## Installing
make flash
