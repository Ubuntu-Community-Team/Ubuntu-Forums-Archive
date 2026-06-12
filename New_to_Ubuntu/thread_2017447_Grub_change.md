---
title: "Grub change"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by KoosD on 2012-07-05
I installed ubuntu. With the start up i need to change the graphic settings to nomodset. Changedthis with the editor and saved succesfully. But the updat grub does not work i get no reaction and no change from the system. Changing the config file leaves me with no rights to change. 

Any sugestions please?

Koos

---

### Post by Quackers on 2012-07-05
The changes needed are explained in the section headed
"How to permanently set kernel boot options on an installed OS (not wubi)"
in this thread
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
You could first check your changes.

It may also be possible to install an extra video card driver by running Additional Drivers. This might mean that the nomodeset option is no longer needed. Have you tried that?

---

### Post by KoosD on 2012-07-05
Thanks for the reply, but i have tried al the possibilities decribed in the forums but no result. The problem is I am on a yacht and have no cable and wireless is not working. So loading any drivers is at this moment not an option. May be my HP Pavilion dv7 is to new? I can see the changes in the file I but the update doesnt work.

---

### Post by drs305 on 2012-07-05
A few questions:

Are you trying to add the "nomodeset" option to the "linux" line of a Grub menuentry?

Are you editing /boot/grub/grub.cfg (the menu) or the settings file (/etc/default/grub)? If you edit the grub menu itself and then run "update-grub" it is going to remove the changes you made.

At the GRUB menu, until you get this resolved, you can highlight the menu item you wish, press 'e' to edit it, and cursor to the end on the 'linux' line. Backspace to remove 'quiet splash' and the 'vt...' entry and add *nomodeset*. Then ctrl-x or F10 to boot. Perhaps that is what you are already doing.

---

### Post by KoosD on 2012-07-05
I have changed this file /etc/default/grub and I can see the changes after saving and opening again. Then I run the sudo update-grub and nothing happens. At the start up I edit the start command with adding nomodeset to the line otherwise my screen does not work. ( as you already expected). I need the pc for running my navigation program. My old pc died two weeks ago. I a am not yet planning to go home.

---

### Post by Quackers on 2012-07-05
Did you save the file after edit?
Can you post the contents of the /etc/default/grub file here please?
Preferably in code tags (in New Reply click the # symbol and paste in between the two).

---

### Post by KoosD on 2012-07-05
Yes I saved the file and when opening again I can see the changes but they dont show in the opening screen at start up. I am working in windows now because i can not communicate in ubuntu yet so I cannot copy anything from there. sorry!

---

### Post by KoosD on 2012-07-05
I found a way to work around. hope this is what you want?
 
```

# If you change this file, run 'update-grub' afterwards to update 
# /boot/grub/grub.cfg. 
# For full documentation of the options in this file, see: 
# info -f grub -n 'Simple configuration' 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]GRUB_DEFAULT=0 
#GRUB_HIDDEN_TIMEOUT=0 
GRUB_HIDDEN_TIMEOUT_QUIET=true 
GRUB_TIMEOUT=10 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" 
GRUB_CMDLINE_LINUX="" 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]# Uncomment to enable BadRAM filtering, modify to suit your needs 
# This works with Linux (no patch required) and with any kernel that obtains 
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...) 
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef" 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]# Uncomment to disable graphical terminal (grub-pc only) 
#GRUB_TERMINAL=console 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]# The resolution used on graphical terminal 
# note that you can use only modes which your graphic card supports via VBE 
# you can see them in real GRUB with the command `vbeinfo' 
#GRUB_GFXMODE=640x480 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux 
#GRUB_DISABLE_LINUX_UUID=true 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]# Uncomment to disable generation of recovery mode menu entries 
#GRUB_DISABLE_RECOVERY="true" 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]# Uncomment to get a beep at grub start 
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by drs305 on 2012-07-05
When you run update-grub and say "nothing happens" does it appear to run in the terminal (i.e. do you see "found..." , etc) or is the terminal blank?

If nothing seems to happen, perhaps you have removed the executible flag from the GRUB scripts in the /etc/grub.d folder. You can restore them with;

```
sudo chmod +x /etc/grub.d/*
sudo update-grub
```

Another possibility might be competing GRUBs. Do you have more than one OS with GRUB on it? If that is the case, the other OS might be controlling the boot and using its own files.

Can you use "sudo" with other commands without problems?

You could also try this to make sure your grub file is updated. This is what the "update-grub" command is supposed to do:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
This command will force it to write the output to /boot/grub/grub.cfg

---

### Post by KoosD on 2012-07-05
Drs305 ,sorry but none of the commands have any effect. I leave it for now and wait until I can put a network cable in the HP.

Thanks for the effort.

---

