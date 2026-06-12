---
title: "creating a &quot;Makefile&quot;"
date: 2012-02-04
forum: Packaging and Compiling Programs
---

### Post by b.karthi-k-yan on 2012-02-04
hi,

i'v tries a lot to create a makefile, and also searched in the same forum. but still creating one throughs me different errors like "no target" & "stopped" etc,..

im trying to use gcc to compile a program for AVR microcontroller
    [PHP]$ avr-gcc -g -Os -mmcu=atmega16 -c filename.c[/PHP]

the previous command gives an output file with the same name as default, something like filename.o, now i have to convert this file into an .elf format
    [PHP]$ avr-gcc -g -Os -mmcu=atmega16 -o filename.elf filename.o[/PHP]

then i have to create a list file which will be helpfull in producing the actual code
    [PHP]$ avr-objdump -h -S filename.elf > filename.lst[/PHP]

after this command i need some information regarding the memory space occupied by the code & etc
    [PHP]$ avr-gcc -g -mmcu=atmega8 -Wl,-Map,filename.map -o filename.elf filename.o[/PHP]

since microcontroller can only accept code in hexa file format**(Uploading the code to the microcontroller)** the next command goes like
    [PHP]$ avr-objcopy -j .text -j .data -O ihex filename.elf filename.hex[/PHP]

These are the codes im using from compilation to upload a code into controller.During all these stages there are some file which i dont need later except 1 or 2 files. iv got the commands which i'v wrote above from another site [***_link_***]("http://www.nongnu.org/avr-libc/user-manual/group__demo__project.html"), at the very end they have even given the code to write make file,.. but even then its not working for me,.. and there are certain commands which im not using from their list

can some one please help me in creating a make file,..!!:(

---

### Post by howefield on 2012-02-04
Thread isn't a Tutorial or Tip so moved to "*[I]Packaging and Compiling Programs*[/I]"

---

### Post by b.karthi-k-yan on 2012-02-04
> **howefield said:**
> Thread isn't a Tutorial or Tip so moved to "*[I]Packaging and Compiling Programs*[/I]"
Im extremely sorry,.. i wasnt aware of it,..

---

