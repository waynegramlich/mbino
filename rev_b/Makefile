# zip together files starting with robus as the root.  This
# allows the search path inside of KiCAD to find all the
# appropriate .mod and .lib files:

# The project base:
BASE := busduino

# Root directory:
ROOT_DIR := ../../..

# The library driectory from $(ROOT_DIR):
LIBRARY_DIR := robus
LIBRARY_MODULE_FILES := \
    $(LIBRARY_DIR)/extra-nominal.mod \
    $(LIBRARY_DIR)/IPC7351-Nominal.mod \
    $(LIBRARY_DIR)/robus.mod \
    $(LIBRARY_DIR)/ipc7351_extra.mod \
    $(LIBRARY_DIR)/robus.lib

# The base directory from $(ROOT_DIR):
BASE_DIR := $(LIBRARY_DIR)/$(BASE)/rev_b
BASE_PREFIX := $(BASE_DIR)/$(BASE)
BASE_FILES := \
    $(BASE_PREFIX).brd \
    $(BASE_PREFIX)-cache.lib \
    $(BASE_PREFIX).cmp \
    $(BASE_PREFIX).net \
    $(BASE_PREFIX).pdf \
    $(BASE_PREFIX).pro \
    $(BASE_PREFIX).sch \
    $(BASE_PREFIX)$$savepcb.brd \
    $(BASE_DIR)/notes.txt

ARCHIVE_FILES := \
    ${LIBRARY_MODULE_FILES} \
    ${BASE_FILES}

ZIP_FILES := \
    $(BASE_PREFIX).zip

ARDUINO_DIR := $(ROOT_DIR)/arduino/arduino-1.0.1
BOOTLOADER_DIR := $(ARDUINO_DIR)/hardware/MDuino/bootloaders/optiboot
BOOTLOADER_FILES := \
    optiboot.c \
    avrdude_interactive.sh \
    burn_flash.sh \
    burn_fuses.sh \
    Makefile



all: ${ZIP_FILES}

$(BASE_PREFIX).zip:
	cd $(ROOT_DIR) ; zip $@ ${ARCHIVE_FILES}

bootloader.zip:
	rm -f $@
	cp 