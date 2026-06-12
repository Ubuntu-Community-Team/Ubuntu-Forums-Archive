---
title: "[SOLVED] xsane not starting in Hardy"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by ageer1 on 2008-06-28
Good Morning to all,

I just upgraded to Hardy and when I attempt to start Xsane it flashes the ¨scanning for devices¨ message and quits. The scanner works fine in XP.Is there any hope for this problem.

Thanks,
        Joe

---

### Post by ageer1 on 2008-06-28
I should have mentioned that it worked fine in Feisty and Gutsy.

Thanks,
       Joe

---

### Post by philinux on 2008-06-28
You just might get some help if you post your specs including the make and model of the scanner. :)

---

### Post by drs305 on 2008-06-28
If it's a usb scanner, do you see it when you run:
```
lsusb
```

**Added:** If it's listed, note the ID number and see if it matches what is shown in the applicable .conf file in /etc/sane.d

---

### Post by ageer1 on 2008-06-28
The computer is a PowerSpec (ie; generic), 1g ram, dual cpu´s, running at 3Gig. Scanner is a Cannon CanoScan Lide 50. I would have posted that before but I wasn´t sure it was relevant as all worked well ¨out of the box¨ in both Feisty and Gusty.

---

### Post by philinux on 2008-06-28
With it plugged in does it show up in

lsusb

---

### Post by ageer1 on 2008-06-28
Thanks for the help. I don have an etc/sane folder. I have an etc/sane.d folder and within it I have a cannon630u.conf file which has the following:

# Options for the canonusb backend

# Autodetect the Canon CanoScan FB630u
usb 0x04a9 0x2204

# device list for non-linux-systems (enable if autodetect fails):
#/dev/scanner
#/dev/usb/scanner0

I also have a canon.conf file containing:

#canon.conf
/dev/scanner
#/dev/sg0

and a canon-pp.conf file containing:

# Define which port to use if one isn't specified - you should only have 
# one of these lines!
# This is the default port to be used - others will be detected
ieee1284 parport0


# Define the location of our pixel weight file, can begin with ~/ if needed.
# You can have as many of these as you like - lines with ports that don't exist
# will be ignored.
#
# Parameters are:
# calibrate /path/to/calibration-file port-name
#
# The format of port-name is dependant on your OS version.
#
# If a file isn't speficied, the default name will be
# ~/.sane/canon_pp-calibration-[port-name]

calibrate ~/.sane/canon_pp-calibration-pp0 parport0

# calibrate /etc/sane/my_calibration parport1


# Enable the next line if you're having trouble with ECP mode such as I/O 
# errors.  Nibble mode is slower, but more reliable.

#force_nibble

# Set a default initialisation mode for each port.  Valid modes are:
# AUTO		(attempts to automatically detect by trying both methods)
# FB620P	(10101010 style.. also works for FB320P)
# FB630P	(11001100 style.. also works for FB330P, N340P, N640P)

init_mode AUTO parport0
# init_mode FB620P parport0
# init_mode FB630P parport0

lsusb gives me: 

esky@ubuntu:~$ lsusb
Bus 005 Device 003: ID 04a9:2213 Canon, Inc. LiDE 50/LiDE 35
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 047d:106d Kensington 
Bus 001 Device 001: ID 0000:0000  


Is this the info you needed? The ID´s don´t seem to match up, but I´ve no clue what that means, or what to do about it??

Thanks,
       Joe

---

### Post by ageer1 on 2008-06-28
Thanks for the help philinux.

Yes it shows up. See my answering post above.

Thanks,
       Joe

---

### Post by drs305 on 2008-06-28
> **ageer1 said:**
> 
# Options for the canonusb backend

# Autodetect the Canon CanoScan FB630u
**usb 0x04a9 0x2204**


lsusb gives me: 

esky@ubuntu:~$ lsusb
Bus 005 Device 003: ID **04a9**:2213 Canon, Inc. LiDE 50/LiDE 35


Is this the info you needed? The ID´s don´t seem to match up, but I´ve no clue what that means, or what to do about it??

Thanks,
       Joe
Sorry about the typo. Yes, it's sane.d

Actually, the numbers I was looking for do match up. And apparently the power/usb cords are ok since the computer is aware of the scanner.

**Added:**
```
sane-find-scanner
scanimage -L

```

Also try this. You should have a file in /home/username/.sane/xsane with a .drc extension. It describes your scanner and is probably something like Canon:CanoScan50.drc  For the first command, run it but do _not_ include the .drc extension in the filename. For the second, include the .conf extension for whatever the file is in /etc/sane.d/ :
```

xsane -d /home/drs64/.sane/xsane/filename
xsane -d /etc/sane.d/canonfilename.conf

```

---

### Post by ageer1 on 2008-06-28
I get:

esky@ubuntu:~$ /home/esky/.sane/xsane/Canon:LiDE35_40_50
bash: /home/esky/.sane/xsane/Canon:LiDE35_40_50: No such file or directory

Thanks,
     Joe

---

### Post by drs305 on 2008-06-28
> **ageer1 said:**
> I get:

esky@ubuntu:~$ /home/esky/.sane/xsane/Canon:LiDE35_40_50
bash: /home/esky/.sane/xsane/Canon:LiDE35_40_50: No such file or directory

Thanks,
     Joe

With the colon, you might have to put the entire name in quotes. I am assuming from your post there is a file named "/home/esky/.sane/xsane/Canon:LiDE35_40_50.drc"?

Did you run it with the "xsane -d " in front of "/home/esky/.sane/xsane/Canon:LiDE35_40_50"?

Did any of the other commands provide anything useful?

---

### Post by ageer1 on 2008-06-28
My screwup. Forgot the xsane -d!! Yes, the file exists.:)

Now I get ¨scanning for devices¨ then a seg fault:

esky@ubuntu:~$ xsane -d /home/esky/.sane/xsane/Canon:LiDE35_40_50
Segmentation fault
esky@ubuntu:~$ xsane -d ¨/home/esky/.sane/xsane/Canon:LiDE35_40_50¨
Segmentation fault

Thanks,
     Joe

---

### Post by drs305 on 2008-06-28
> **ageer1 said:**
> My screwup. Forgot the xsane -d!! Yes, the file exists.:)

Now I get ¨scanning for devices¨ then a seg fault:

esky@ubuntu:~$ xsane -d /home/esky/.sane/xsane/Canon:LiDE35_40_50
Segmentation fault
esky@ubuntu:~$ xsane -d ¨/home/esky/.sane/xsane/Canon:LiDE35_40_50¨
Segmentation fault

Thanks,
     Joe

Did you get the same for the first two commands as well?

Look at your groups list and see if you are listed in the "scanner" group.
```
groups
```
You should see your username, and probably 6-10 groups. One of them should be "scanner". If you aren't listed, add yourself to the "scanner" group.
```
sudo adduser esky scanner
```

---

### Post by ageer1 on 2008-06-28
I seem to be in the scanner group. 

esky@ubuntu:~$ groups
esky adm dialout fax cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev sambashare

Does this help.

Thanks,   
      Joe

---

### Post by drs305 on 2008-06-28
> **ageer1 said:**
> Does this help.


Well, it doesn't help in that it is something that is supposed to be there and is - so that didn't present an easy fix.

You might just try reinstalling xsane. I'll keep thinking about this but it looks like we are going to have to find some reinforcements to solve this issue.

Anyone?

---

### Post by ageer1 on 2008-06-28
The first thing I tried was to do a ¨Complete Removal¨ and then re-installation, obviously with no satisfaction. Any other thoughts?

Thanks,  
      Joe

---

### Post by drs305 on 2008-06-28
One final try. Rename or move your /home/esky/.sane folder. Restart xsane and it will rebuild it. Synaptic may not have removed this file during the uninstall of xsane.  Good luck.

---

### Post by ageer1 on 2008-06-28
Thank you, thank you, thank You!!

That did it!! Xsane now opens and I am able to scan an image, however, now it can´t find my printer!! Any advice on that one? As I have said this all worked fine in Feisty and Gutsy.

Thanks,
      Joe

---

### Post by drs305 on 2008-06-28
Okay, here we go AGAIN ;-)  

What kind of printer? If usb run the lsusb command again with the printer power on. Try going to the install printer (system, admin, printing) and see if your printer is there. If so, check the address and make sure it's correct (e.g. if it's a usb printer there probably shouldn't be a 'serial' in the address).

If it's not there, try adding a new printer. Hardy seems to be improved in detecting and installing printers from the earlier versiona.

---

### Post by ageer1 on 2008-06-28
Hi drs305,

Sorry for the delay, she who must be obeyed came home and I had to go out for awhile. 

Found out I can´t print from Open Office or gedit either. I could before the xsane problem!

esky@ubuntu:~$ lsusb
Bus 005 Device 003: ID 04a9:2213 Canon, Inc. LiDE 50/LiDE 35
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 047d:106d Kensington 
Bus 001 Device 001: ID 0000:0000  

I also tried using the ¨printing Troubleshooter¨ and it gave me a message of ¨Can not get the ticket cach for esky. Printer´s stated reasons: none¨. (It does show up in admin:printing with a status of ¨idle¨.

---

### Post by drs305 on 2008-06-28
What kind of printer?
Did you try to add a new printer?
Are you using CUPS?

I'd probably start searching the forum for the error message and then start a new thread about printer problems. Mention that the scanner wasn't working and that you deleted the .sane folder in case it's relevant.

---

