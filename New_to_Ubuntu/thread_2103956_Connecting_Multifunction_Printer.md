---
title: "Connecting Multifunction Printer"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by Kruxoli on 2013-01-11
Hi, I have a Brother MFC-7860-DW printer/scanner/fax and I am attempting to connect it to my laptop running Ubuntu 12.10.  I connected the printer via USB and can print with no issues.  Scanning, however, is another story all together.

I have the simple scan app, but that doesn't seem to work/connect to the printer.

I looked online, but so far, I've been unsuccessful.  I found the place on the Brother website for the scanner drivers and stuff, but when I attempt to follow Brother's directions, I get error messages.  

Like I said, I downloaded the files (both the .DEB and .RPM files) and tried running the commands as the directions on Brother's website lay it out, but it doesn't work...

root@kruxoli-ThinkPad-T60p:/home/kruxoli# dpkg  -i  --force-all  brscan-skey-0.2.4-0.i386.deb
dpkg: error processing brscan-skey-0.2.4-0.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 brscan-skey-0.2.4-0.i386.deb

I even tried extracting the file, then replacing the .DEB name with the extracted file name.  Still no dice.  What am I doing wrong here?

I'm hoping someone can help me.  I'm REALLY new to Ubuntu (been running it for a couple of days now since Windows crapped out on me) and I could really use some simple, step by step directions.  Please go easy on me.  THANKS!!!

---

### Post by audiomick on 2013-01-11
If you have a .deb package, you should be able to just right click on it and choose "install via software centre" or something very similar to that out of the context menu.

If you want to install a .deb from the terminal, I believe you should use dpkg.

---

### Post by smoka on 2013-01-11
The error is basically saying the file isn't in the same directory.

Some good step-by-step instructions here I found useful when installing Brother printer, check out this thread:

HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies! 
[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)

---

### Post by pdc on 2013-01-13
so Kruxoli ......if you are still there ........

if one were re-tracing your steps, one would go here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

and the 7860 needs the brscan4

You don't tell us if you have 32bit or 64bit installed

........if 32bit..................

from the Brother site I reckon you should download [COLOR="SeaGreen"]brscan4-0.4.1-3.i386.deb[/COLOR]

the commands would be ..after your open a terminal ..

> [COLOR="Red"]cd Downloads[/COLOR]

> [COLOR="Red"]sudo dpkg  -i  --force-all brscan4-0.4.1-3.i386.deb[/COLOR] 

............then check that it was installed  ...........

>  [COLOR="Red"]sudo dpkg  -l  |  grep  Brother[/COLOR]

____________________________

then the scankeytool ......if 32bit ............

get it from the page used above:

...........close the terminal.......open it again......

> [COLOR="Red"]cd Downloads[/COLOR]

> [COLOR="Red"]sudo dpkg  -i  --force-all brscan-skey-0.2.4-0.i386.deb[/COLOR]

that should get things installed...........

---

### Post by Kruxoli on 2013-01-15
> **pdc said:**
> so Kruxoli ......if you are still there ........

if one were re-tracing your steps, one would go here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

and the 7860 needs the brscan4

You don't tell us if you have 32bit or 64bit installed

........if 32bit..................

from the Brother site I reckon you should download [COLOR="SeaGreen"]brscan4-0.4.1-3.i386.deb[/COLOR]

the commands would be ..after your open a terminal ..





............then check that it was installed  ...........



____________________________

then the scankeytool ......if 32bit ............

get it from the page used above:

...........close the terminal.......open it again......




that should get things installed...........

Hi, thank you all for your help.  I followed the steps quoted above (and yes, I am running 12.10 32-bit), but Simple Scan gives me the following error:

Failed to scan
Unable to connect to scanner

Now, I have the MFC-7860DW plugged into the USB port and I have it set up on a wireless network (which I am also connected to).

I tried XSane, and I got the following:

Error
Failed to open device 'brother4:bus5;dev1':
Invalid argument.

UGH.  Now what did I do wrong?  Sorry, like I said in the OP, I'm really new to this OS, and I could use all the help I can get.

---

### Post by pdc on 2013-01-15
Simple Scan is a "front engine" to run the back-engine sane


XSane is a flasher "front engine" to run back-engine sane:

.........as I understand it.......brscan is an ALTERNATIVE back-engine ..

......so you have to use that......

.........all a bit confusing.............

I don't have a Brother device, but

this link

[http://www.driverlook.com/easy-5-steps-to-install-brother-scan-key-tool-driver-on-linux/](http://www.driverlook.com/easy-5-steps-to-install-brother-scan-key-tool-driver-on-linux/)

probably says the same as the Brother site.....you have done the first 4 steps already..........

EDIT: before we run brscan I think you need to edit a file:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

> [COLOR="Red"]gksudo gedit /lib/udev/rules.d/50-udev-default.rules[/COLOR]

......*that should open a blank file in [COLOR="Magenta"]gedit[/COLOR], a text editor, with sudo powers so what you can create is saved to the system* ..........

then copy and paste into the blank page

> [COLOR="SeaGreen"]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/COLOR]
 

and SAVE and close .....now to get brscan running............

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn4.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn4.html)

Step 5. Run scan-key-tool and try the test scanning
5-1. Run scan-key-tool (The program will run as a background process.)
and in a terminal one copies and pastes

> [COLOR="Red"]brscan-skey[/COLOR]

and to check if the scan-key-tool detect your scanner device

> [COLOR="Red"]brscan-skey -l[/COLOR]

I am guessing but if you copy and paste

> [COLOR="Red"]man brscan-skey[/COLOR] in a terminal, it may give you a huge series of options ........

......do you have an icons created on your system saying brscan? If not we need to create a launcher to give you a GUI launcher, when we sort out which commmand is best ...........

and here is a FAQ from Brother

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html)

.....that we both may have to work through!!!!!!!!!!!!!!!.........if we can't get things working!

_________________________________________________________________________

**[COLOR="Blue"]LATE EDIT[/COLOR]**: more searching..........found this link

[http://raywoodcockslatest.blogspot.co.nz/2010/05/scanning-functionality-for-brother-mfc.html](http://raywoodcockslatest.blogspot.co.nz/2010/05/scanning-functionality-for-brother-mfc.html)

great how-to: helps me understand the Brother system better

___________________________________________________________________________

.........but wait.........there's more !!

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn5.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn5.html)

*how to get brscan starting up, when computer starts*........

    [COLOR="SeaGreen"]1. Open "Startup Programs" (System > Preference > Sessions > Startup Programs)
    2. Click "Add"
    3. Type "brscan-skey" and click ok[/COLOR]

---

### Post by Kruxoli on 2013-01-16
> **pdc said:**
> Simple Scan is a "front engine" to run the back-engine sane


XSane is a flasher "front engine" to run back-engine sane:

.........as I understand it.......brscan is an ALTERNATIVE back-engine ..

......so you have to use that......

.........all a bit confusing.............

I don't have a Brother device, but

this link

[http://www.driverlook.com/easy-5-steps-to-install-brother-scan-key-tool-driver-on-linux/](http://www.driverlook.com/easy-5-steps-to-install-brother-scan-key-tool-driver-on-linux/)

probably says the same as the Brother site.....you have done the first 4 steps already..........

EDIT: before we run brscan I think you need to edit a file:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)



......*that should open a blank file in [COLOR="Magenta"]gedit[/COLOR], a text editor, with sudo powers so what you can create is saved to the system* ..........

then copy and paste into the blank page



and SAVE and close .....now to get brscan running............

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn4.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn4.html)

Step 5. Run scan-key-tool and try the test scanning
5-1. Run scan-key-tool (The program will run as a background process.)
and in a terminal one copies and pastes



and to check if the scan-key-tool detect your scanner device



I am guessing but if you copy and paste

 in a terminal, it may give you a huge series of options ........

......do you have an icons created on your system saying brscan? If not we need to create a launcher to give you a GUI launcher, when we sort out which commmand is best ...........

and here is a FAQ from Brother

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html)

.....that we both may have to work through!!!!!!!!!!!!!!!.........if we can't get things working!

_________________________________________________________________________

**[COLOR="Blue"]LATE EDIT[/COLOR]**: more searching..........found this link

[http://raywoodcockslatest.blogspot.co.nz/2010/05/scanning-functionality-for-brother-mfc.html](http://raywoodcockslatest.blogspot.co.nz/2010/05/scanning-functionality-for-brother-mfc.html)

great how-to: helps me understand the Brother system better

___________________________________________________________________________

.........but wait.........there's more !!

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn5.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn5.html)

*how to get brscan starting up, when computer starts*........

    [COLOR="SeaGreen"]1. Open "Startup Programs" (System > Preference > Sessions > Startup Programs)
    2. Click "Add"
    3. Type "brscan-skey" and click ok[/COLOR]

Hey, thanks again, I really appreciate it.

OK, so I ran the first script in Terminal and the text editor popped up, but the document wasn't blank.  There were two tabs on the document, one was 50-udev-default.rules, and the other was *Untitled Document 1.
I cut & pasted the stuff you provided into the *Untitled Document 1 tab and hit "save."  It then asked me what folder to save it in (I selected rules.d) so I picked, saved and closed the text editor.
I then ran the next line into Terminal, but nothing happened at all:

kruxoli@kruxoli-ThinkPad-T60p:~$ brscan-skey
kruxoli@kruxoli-ThinkPad-T60p:~$ 

So I ran the next line:

kruxoli@kruxoli-ThinkPad-T60p:~$ brscan-skey -l
kruxoli@kruxoli-ThinkPad-T60p:~$ 

Again, nothing happened.  And my Brother device is plugged into the USB port and turned on.

So I ran the next line:

root@kruxoli-ThinkPad-T60p:/home/kruxoli# man brscan-skey
No manual entry for brscan-skey
See 'man 7 undocumented' for help when manual pages are not available.
root@kruxoli-ThinkPad-T60p:/home/kruxoli# 

And then I saw the last thing you posted, so I typed 'brscan-skey' into the COMMAND line.

Now, how do I test this to see if it scans?

And, just so I have this straight, I am not to use Simple Scan or Xsane?

Sorry for all the questions, as I'm sure you can tell by this point, I'm pretty much lost here...

I really do appreciate all your help with this.

And, I do not have any icons that say brscan or anything like that save for the files I downloaded form the Brother site...

---

### Post by pdc on 2013-01-16
first let's see just what you have installed:

if you copy and paste this command

> sudo dpkg -l | grep brscan

into a terminal, and copy and paste the result back, it will tell us;

---

### Post by Kruxoli on 2013-01-16
> **pdc said:**
> first let's see just what you have installed:

if you copy and paste this command



into a terminal, and copy and paste the result back, it will tell us;

OK, here's what I got...

kruxoli@kruxoli-ThinkPad-T60p:~$ sudo dpkg -l | grep brscan
ii  brscan-skey                               0.2.4-0                                   i386         Brother Linux scanner S-KEY tool
ii  brscan4                                   0.4.1-3                                   i386         Brother Scanner Driver
kruxoli@kruxoli-ThinkPad-T60p:~$

---

### Post by pdc on 2013-01-16
oh dear: it's harder when one does not have one of these devices;

I now think from further reading that with the brscan installed, that xsane etc should work

.......eg from here

I see from here

to check the configuration with 

> [COLOR="Red"]brsaneconfig4 -q | grep SCANNER[/COLOR]

and further iterations on brscan

[http://bleedux.wordpress.com/2011/08/01/brother-dcp-7065dn-receiving-data-but-not-printing/](http://bleedux.wordpress.com/2011/08/01/brother-dcp-7065dn-receiving-data-but-not-printing/)

the final section on scanning

---

### Post by Kruxoli on 2013-01-17
> **pdc said:**
> oh dear: it's harder when one does not have one of these devices;

I now think from further reading that with the brscan installed, that xsane etc should work

.......eg from here

I see from here

to check the configuration with 



and further iterations on brscan

[http://bleedux.wordpress.com/2011/08/01/brother-dcp-7065dn-receiving-data-but-not-printing/](http://bleedux.wordpress.com/2011/08/01/brother-dcp-7065dn-receiving-data-but-not-printing/)

the final section on scanning

Thanks again.  So I ran the script, but nothing happened...

kruxoli@kruxoli-ThinkPad-T60p:~$ brsaneconfig4 -q | grep SCANNER
kruxoli@kruxoli-ThinkPad-T60p:~$ 

root@kruxoli-ThinkPad-T60p:/home/kruxoli# kruxoli@kruxoli-ThinkPad-T60p:~$ brsaneconfig4 -q | grep SCANNER
kruxoli@kruxoli-ThinkPad-T60p:~$: command not found
root@kruxoli-ThinkPad-T60p:/home/kruxoli# kruxoli@kruxoli-ThinkPad-T60p:~$ 
kruxoli@kruxoli-ThinkPad-T60p:~$: command not found
root@kruxoli-ThinkPad-T60p:/home/kruxoli# 

When I open Xsane this is what I get:

Error
Failed to open device 'brother4:bus5;dev1':
Invalid argument

Am I relegated to not being able to use the scanner?  UGH.

---

### Post by pdc on 2013-01-17
> Error
Failed to open device 'brother4:bus5;dev1':
Invalid argument

I think this is due to permissions issues: you may not be a "member" of the group that the scanner is a part of: it used to be called scanner and now I believe it is lp; 

if you type

> [COLOR="Red"]sane-find-scanner[/COLOR]

and then 

> [COLOR="Red"]scanimage -L[/COLOR]

and then 

> [COLOR="Red"]sudo sane-find-scanner[/COLOR]

and then 

> [COLOR="Red"]sudo scanimage -L[/COLOR]

..........does you get any recognitions?

for the now if you type

> [COLOR="Red"]sudo xsane[/COLOR] in a terminal, does that launch xsane?

.......there may be all sorts of dire warnings but various folks do it fine ..

---

### Post by Kruxoli on 2013-01-17
> **pdc said:**
> I think this is due to permissions issues: you may not be a "member" of the group that the scanner is a part of: it used to be called scanner and now I believe it is lp; 

if you type



and then 



and then 



and then 



..........does you get any recognitions?

for the now if you type

 in a terminal, does that launch xsane?

.......there may be all sorts of dire warnings but various folks do it fine ..

OK, ran the first script.  Here's what came back:

root@kruxoli-ThinkPad-T60p:/home/kruxoli# sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

Ran the 2nd script.  Here's what came back:

root@kruxoli-ThinkPad-T60p:/home/kruxoli# scanimage -L
device `brother4:net1;dev0' is a Brother MFC-7860DW MFC-7860DW
device `brother4:bus5;dev1' is a Brother MFC-7860DW USB scanner

Ran the 3rd script.  Here's what came back:

root@kruxoli-ThinkPad-T60p:/home/kruxoli# sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

Ran the 4th script.  Here's what came back:

root@kruxoli-ThinkPad-T60p:/home/kruxoli# sudo scanimage -L
device `brother4:net1;dev0' is a Brother MFC-7860DW MFC-7860DW
device `brother4:bus5;dev1' is a Brother MFC-7860DW USB scanner

Ran the last script...Xsane opened, and it saw my scanner!!  Best of all, it WORKED!!!

Every time I need to scan, I need to open Xsane via Terminal, but whatever, IT WORKS!!!!

THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  THANK YOU!!!!!  

:popcorn:  :KS  :guitar:  :p  :p  :p  ;)  ;)

---

### Post by pdc on 2013-01-18
belatedly.......that's great........I had subscribed to the thread, but didn't get notice you had posted .......

............great it is working ............. enjoy ........ you may be able to spare some time to do some more reading around this issue .. if you can puzzle out any whys that would be good!

---

