---
title: "Programming ATMEL AVR fails to open interface ports"
date: 2011-07-29
forum: Programming Talk
---

### Post by arvevans on 2011-07-29
Has anybody been able to make AVRDude or PonyProg work directly in Debian Linux?  I seem to be unable to open the I/O ports so my programmer dongles will see the chip to be programmed (Tiny 2313 and/or Mega8A).  My preference would be to use the parallel port with AVRDude and a DAPA cable, but at this point I would be satisfied with almost any method and hardware that actually works.

[INDENT]avrdude -p t2313 -c dapa -P lpt1 -n -v[/INDENT]

complains about not being able to see the AVR device being programmed.

---

### Post by ve4cib on 2011-07-29
I've been using this makefile to build and download programs to the AVR Butterfly controller for the last several years.  It seems to work well.

(Despite having a lot of win-avr lines in it, I use it on Ubuntu with avr-gcc and avrdude without any issues.)

```
# WinAVR Sample makefile written by Eric B. Weddington, Jörg Wunsch, et al.

# Released to the Public Domain
# Please read the make user manual!
#
# Additional material for this makefile was submitted by:
#  Tim Henigan
#  Peter Fleury
#  Reiner Patommel
#  Sander Pool
#  Frederik Rouleau
#  Markus Pfaff
#

# On command line:
#
# make all = Make software.
#
# make clean = Clean out built project files.
#

# make coff = Convert ELF to AVR COFF (for use with AVR Studio 3.x or VMLAB).
#
# make extcoff = Convert ELF to AVR Extended COFF (for use with AVR Studio
#                4.07 or greater).
#
# make program = Download the hex file to the device, using avrdude.  Please
#                customize the avrdude settings below first!
#
# make filename.s = Just compile filename.c into the assembler code only
#
# To rebuild project do "make clean" then "make all".
#

# MCU name
MCU = atmega169



# Output format. (can be srec, ihex, binary)
FORMAT = ihex

# Target file name (without extension).
TARGET = main



# Optimization level, can be [0, 1, 2, 3, s]. 0 turns off optimization.
# (Note: 3 is not always the best optimization level. See avr-libc FAQ.)
#OPT = s
OPT=s
#OPT = 0

# List C source files here. (C dependencies are automatically generated.)
SRC = $(TARGET).c 

# If there is more than one source file, append them above, or modify and
# uncomment the following:

# the file test.c can be omitted (remove #inc test.h and test() in main.c)
SRC += bcd.c \
lcd_functions.c \
lcd_driver.c \
speaker.c \
songs.c \
button.c \
timer.c \
#bcd.c \
#main.c \
#vcard.c \
#usart.c \
#timer0.c \
#test.c \
#sound.c \
#RTC.c \
#eeprom.c \
#dataflash.c \
#button.c \
#ADC.c \

# You can also wrap lines by appending a backslash to the end of the line:
#SRC += baz.c \
#xyzzy.c


# List Assembler source files here.
# Make them always end in a capital .S.  Files ending in a lowercase .s
# will not be considered source files but generated files (assembler
# output from the compiler), and will be deleted upon "make clean"!
# Even though the DOS/Win* filesystem matches both .s and .S the same,
# it will preserve the spelling of the filenames, and gcc itself does
# care about how the name is spelled on its command-line.
ASRC = 


# List any extra directories to look for include files here.
#     Each directory must be seperated by a space.
EXTRAINCDIRS = 


# Optional compiler flags.
#  -g:        generate debugging information (for GDB, or for COFF conversion)
#  -O*:       optimization level
#  -f...:     tuning, see gcc manual and avr-libc documentation
#  -Wall...:  warning level
#  -Wa,...:   tell GCC to pass this to the assembler.
#    -ahlms:  create assembler listing
CFLAGS = -g -O$(OPT) \
-funsigned-char -funsigned-bitfields -fpack-struct -fshort-enums \
-Wall -Wstrict-prototypes \
-Wa,-adhlns=$(<:.c=.lst) \
$(patsubst %,-I%,$(EXTRAINCDIRS))


# Set a "language standard" compiler flag.
#   Unremark just one line below to set the language standard to use.
#   gnu99 = C99 + GNU extensions. See GCC manual for more information.
#CFLAGS += -std=c89
#CFLAGS += -std=gnu89
#CFLAGS += -std=c99
CFLAGS += -std=gnu99


# Optional assembler flags.
#  -Wa,...:   tell GCC to pass this to the assembler.
#  -ahlms:    create listing
#  -gstabs:   have the assembler create line number information; note that
#             for use in COFF files, additional information about filenames
#             and function names needs to be present in the assembler source
#             files -- see avr-libc docs [FIXME: not yet described there]
ASFLAGS = -Wa,-adhlns=$(<:.S=.lst),-gstabs 


# Optional linker flags.
#  -Wl,...:   tell GCC to pass this to linker.
#  -Map:      create map file
#  --cref:    add cross reference to  map file
LDFLAGS = -Wl,-Map=$(TARGET).map,--cref


# Additional libraries


# Minimalistic printf version
#LDFLAGS += -Wl,-u,vfprintf -lprintf_min

# Floating point printf version (requires -lm below)
#LDFLAGS += -Wl,-u,vfprintf -lprintf_flt

# -lm = math library
LDFLAGS += -lm


# Programming support using avrdude. Settings and variables.


# Programming hardware: alf avr910 avrisp bascom bsd 
# dt006 pavr picoweb pony-stk200 sp12 stk200 stk500
#
# Type: avrdude -c ?
# to get a full listing.
#
AVRDUDE_PROGRAMMER = butterfly
AVRDUDE_PORT = /dev/ttyUSB0	   # programmer connected to serial device
#AVRDUDE_PORT = lpt1	# programmer connected to parallel port
AVRDUDE_WRITE_FLASH = -U flash:w:$(TARGET).hex
#AVRDUDE_WRITE_EEPROM = -U eeprom:w:$(TARGET).eep
AVRDUDE_FLAGS = -p $(MCU) -P $(AVRDUDE_PORT) -c $(AVRDUDE_PROGRAMMER)


# Uncomment the following if you want avrdude's erase cycle counter.
# Note that this counter needs to be initialized first using -Yn,
# see avrdude manual.
#AVRDUDE_ERASE += -y

# Uncomment the following if you do /not/ wish a verification to be
# performed after programming the device.
#AVRDUDE_FLAGS += -V


# Increase verbosity level.  Please use this when submitting bug
# reports about avrdude. See <http://savannah.nongnu.org/projects/avrdude> 
# to submit bug reports.
#AVRDUDE_FLAGS += -v -v


# ---------------------------------------------------------------------------

# Define directories, if needed.
DIRAVR = c:/winavr
DIRAVRBIN = $(DIRAVR)/bin
DIRAVRUTILS = $(DIRAVR)/utils/bin
DIRINC = .
DIRLIB = $(DIRAVR)/avr/lib


# Define programs and commands.
SHELL = sh
CC = avr-gcc
OBJCOPY = avr-objcopy
OBJDUMP = avr-objdump
SIZE = avr-size


# Programming support using avrdude.
AVRDUDE = avrdude

REMOVE = rm -f
COPY = cp
HEXSIZE = $(SIZE) --target=$(FORMAT) $(TARGET).hex

#mt - use hexadezimal output-fromat // org:  ELFSIZE = $(SIZE) -A $(TARGET).elf
ELFSIZE = $(SIZE) -x -A $(TARGET).elf


# Define Messages
# English
MSG_ERRORS_NONE = Errors: none
MSG_BEGIN = -------- begin --------
MSG_END = --------  end  --------
MSG_SIZE_BEFORE = Size before: 
MSG_SIZE_AFTER = Size after:
MSG_COFF = Converting to AVR COFF:
MSG_EXTENDED_COFF = Converting to AVR Extended COFF:
MSG_FLASH = Creating load file for Flash:
MSG_EEPROM = Creating load file for EEPROM:
MSG_EXTENDED_LISTING = Creating Extended Listing:
MSG_SYMBOL_TABLE = Creating Symbol Table:
MSG_LINKING = Linking:
MSG_COMPILING = Compiling:
MSG_ASSEMBLING = Assembling:
MSG_CLEANING = Cleaning project:


# Define all object files.
OBJ = $(SRC:.c=.o) $(ASRC:.S=.o) 

# Define all listing files.
LST = $(ASRC:.S=.lst) $(SRC:.c=.lst)


# Combine all necessary flags and optional flags.
# Add target processor to flags.
ALL_CFLAGS = -mmcu=$(MCU) -I. $(CFLAGS)
ALL_ASFLAGS = -mmcu=$(MCU) -I. -x assembler-with-cpp $(ASFLAGS)


# Default target.
all: begin gccversion sizebefore $(TARGET).elf $(TARGET).hex $(TARGET).eep \
	$(TARGET).lss $(TARGET).sym sizeafter finished end


# Eye candy.
# AVR Studio 3.x does not check make's exit code but relies on
# the following magic strings to be generated by the compile job.
begin:
	@echo
	@echo $(MSG_BEGIN)


finished:
	@echo $(MSG_ERRORS_NONE)

end:
	@echo $(MSG_END)
	@echo


# Display size of file.
sizebefore:
	@if [ -f $(TARGET).elf ]; then echo; echo $(MSG_SIZE_BEFORE); $(ELFSIZE); echo; fi


sizeafter:
	@if [ -f $(TARGET).elf ]; then echo; echo $(MSG_SIZE_AFTER); $(ELFSIZE); echo; fi


# Display compiler version information.
gccversion : 
	@$(CC) --version


# Convert ELF to COFF for use in debugging / simulating in
# AVR Studio or VMLAB.
COFFCONVERT=$(OBJCOPY) --debugging \
	--change-section-address .data-0x800000 \
	--change-section-address .bss-0x800000 \
	--change-section-address .noinit-0x800000 \
	--change-section-address .eeprom-0x810000 


coff: $(TARGET).elf
	@echo
	@echo $(MSG_COFF) $(TARGET).cof
	$(COFFCONVERT) -O coff-avr $< $(TARGET).cof


extcoff: $(TARGET).elf
	@echo
	@echo $(MSG_EXTENDED_COFF) $(TARGET).cof
	$(COFFCONVERT) -O coff-ext-avr $< $(TARGET).cof


# Program the device.  
program: $(TARGET).hex $(TARGET).eep
	$(AVRDUDE) $(AVRDUDE_FLAGS) $(AVRDUDE_WRITE_FLASH) $(AVRDUDE_WRITE_EEPROM)



# Create final output files (.hex, .eep) from ELF output file.
%.hex: %.elf
	@echo
	@echo $(MSG_FLASH) $@
	$(OBJCOPY) -O $(FORMAT) -R .eeprom $< $@

%.eep: %.elf
	@echo
	@echo $(MSG_EEPROM) $@
	-$(OBJCOPY) -j .eeprom --set-section-flags=.eeprom="alloc,load" \

	--change-section-lma .eeprom=0 -O $(FORMAT) $< $@


# Create extended listing file from ELF output file.
%.lss: %.elf
	@echo
	@echo $(MSG_EXTENDED_LISTING) $@
	$(OBJDUMP) -h -S $< > $@


# Create a symbol table from ELF output file.
%.sym: %.elf
	@echo
	@echo $(MSG_SYMBOL_TABLE) $@
	avr-nm -n $< > $@


# Link: create ELF output file from object files.
.SECONDARY : $(TARGET).elf
.PRECIOUS : $(OBJ)
%.elf: $(OBJ)
	@echo
	@echo $(MSG_LINKING) $@
	$(CC) $(ALL_CFLAGS) $(OBJ) --output $@ $(LDFLAGS)


# Compile: create object files from C source files.
%.o : %.c
	@echo
	@echo $(MSG_COMPILING) $<
	$(CC) -c $(ALL_CFLAGS) $< -o $@


# Compile: create assembler files from C source files.
%.s : %.c
	$(CC) -S $(ALL_CFLAGS) $< -o $@


# Assemble: create object files from assembler source files.
%.o : %.S
	@echo
	@echo $(MSG_ASSEMBLING) $<
	$(CC) -c $(ALL_ASFLAGS) $< -o $@


# Target: clean project.
clean: begin clean_list finished end

clean_list :
	@echo
	@echo $(MSG_CLEANING)
	$(REMOVE) $(TARGET).hex
	$(REMOVE) $(TARGET).eep
	$(REMOVE) $(TARGET).obj
	$(REMOVE) $(TARGET).cof
	$(REMOVE) $(TARGET).elf
	$(REMOVE) $(TARGET).map
	$(REMOVE) $(TARGET).obj
	$(REMOVE) $(TARGET).a90
	$(REMOVE) $(TARGET).sym
	$(REMOVE) $(TARGET).lnk
	$(REMOVE) $(TARGET).lss
	$(REMOVE) $(OBJ)
	$(REMOVE) $(LST)
	$(REMOVE) $(SRC:.c=.s)
	$(REMOVE) $(SRC:.c=.d)


# Automatically generate C source code dependencies. 
# (Code originally taken from the GNU make user manual and modified 
# (See README.txt Credits).)
#
# Note that this will work with sh (bash) and sed that is shipped with WinAVR
# (see the SHELL variable defined above).
# This may not work with other shells or other seds.
#
%.d: %.c
	set -e; $(CC) -MM $(ALL_CFLAGS) $< \
	| sed 's,\(.*\)\.o[ :]*,\1.o \1.d : ,g' > $@; \
	[ -s $@ ] || rm -f $@


# Remove the '-' if you want to see the dependency files generated.
-include $(SRC:.c=.d)


# Listing of phony targets.
.PHONY : all begin finish end sizebefore sizeafter gccversion coff extcoff \
	clean clean_list program

```

Obviously my setup is a little different than yours; I've got the device connected to a USB-to-serial adaptor (/dev/ttyUSB0), not a parallel port.  Have you tried that kind of a setup?

---

### Post by cguy on 2011-07-29
You need to add yourself to those groups which have the permissions to access the desired ports.
eg: uucp for the serial port


However, I've had a nightmareish experience with serial/parallel programmers for AVRs and I've wasted a lot of precious time in trying to get them to work correctly 100% of the time (I'm not sure it was Linux's fault)

I suggest you buy a cheap, USB-based programmer. It will save you nerves, time and you will grow up loving programming uC, not dreading it.


If you already have experience on Windows using these kinds of programmers, then ignore my ramble from above. :)

---

### Post by blitzit on 2011-09-01
Hi! If you are okay with using any hardware, I would suggest:
[LIST=1]
[*]PonyProg: Very simplistic hardware that will connect to the Serial Port. Does not require preprogrammed MicroController for operation. [http://www.lancos.com/pplinux.html](http://www.lancos.com/pplinux.html)
[*]USBasp: Slightly better sophistication. Requires a preprogrammed MicroController for operation. [http://www.fischl.de/usbasp/](http://www.fischl.de/usbasp/)
[/LIST]

To setup my working environment (4 years back), I first built up a ponyprog circuit and used ponyprog to dump the firmware .hex for usbasp. I then shifted to usbasp and avrdude as I found it to be more convenient and sophisticated. Since then I have been distributing programmed chips to friends and colleagues, makes the task pretty simple.

Also, if avrdude fails to open interface ports, the most common problem generally is the user not having permissions. A solution that works for me is running avrdude as a super user like this:
```
sudo avrdude . . .
```

e.g.```
sudo avrdude -c usbasp -p m8 -U flash:w:file.hex
```

---

