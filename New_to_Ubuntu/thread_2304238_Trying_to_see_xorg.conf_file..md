---
title: "Trying to see xorg.conf file."
date: 2015-11-25
forum: New to Ubuntu
---

### Post by Netuzist on 2015-11-25
Hi folks I'm trying to see the contents of the xorg.config file so that I can edit it to cure my installed distro of the dreaded xfce bug which causes my hdtv monitor to lose it's signal to my modified chromebox every time I power cycle my hdtv off than on.  My modified chromebox also loses it's connection to my hdtv whenever I switch the hdmi output from the chromebox to my cable box then switch back to my chromebox and that's when I lose the signal very annoying.  I installed get-edid and read-edid on my system and this was the output:

This is read-edid version 3.0.1. Prepare for some fun.
Attempting to use i2c interface
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface
mmap /dev/zero: Operation not permitted
error initialising realmode interface
do you have full superuser (root) permissions?
I'm sorry nothing was successful. Maybe try some other arguments
if you played with them, or send an email to Matthew Kern <pyrophobicman@gmail.com>.
Partial Read... Try again
el-junior@eljunior-Panther:~$ sudo get-edid | parse-edid 
[sudo] password for el-junior: 
This is read-edid version 3.0.1. Prepare for some fun.
Attempting to use i2c interface
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0xc9a24 "Intel(R) HSW Mobile/Desktop Graphics Chipset Accelerated VGA BIOS"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call successful

EDID claims 1 more blocks left


*********** Something special has happened!
This happens a lot with TV's, and other devices
with extension blocks. If you have a TV, don't bother.
Otherwise, please contact the author, Matthew Kern
E-mail: [email]pyrophobicman@gmail.com[/email]
Please include full output from this program (especially that to stderr)



Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call successful

EDID claims 1 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
Looks like VBE was successful. Have a good day.
Checksum Correct

Section "Monitor"
    Identifier "LG TV"
    ModelName "LG TV"
    VendorName "GSM"
    # Monitor Manufactured week 1 of 2011
    # EDID version 1.3
    # Digital Display
    DisplaySize 160 90
    Gamma 2.20
    Option "DPMS" "false"
    Horizsync 31-82
    VertRefresh 57-63
    # Maximum pixel clock is 160MHz
    #Not giving standard mode: 1280x1024, 60Hz
    #Not giving standard mode: 1024x768, 60Hz
    #Not giving standard mode: 800x600, 60Hz
    #Not giving standard mode: 640x480, 60Hz

    #Extension block found. Parsing...
I only know about extension blocks of type 02h. PLEASE email me!
Something strange happened. Please contact the author,
Matthew Kern at <pyrophobicman@gmail.com>

So as you can see the output at the beginning reads "Looks like no busses have an EDID. Sorry!" but then towards the end of it it retrieved some information about my hdtv.  So what does this all mean does my system have an edid file which I think is supposed to be part of the xconfig file or is the xconfig hidden and thus protected.  Please help me out here because if I accidently erased my xconfig file trying to clean my system then I'll have to recreate it by following [Alexander Malakhov]("http://askubuntu.com/users/144929/alexander-malakhov")'s advice in this thread : [http://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file](http://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file)

---

