---
title: "Brother DCP-197C Scanner Function"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by NDW57 on 2012-10-04
I recently installed Ubuntu 12.04 and  have just manged to install the printer function for a Brother DCP-197C from the "tool" on their website. Unfortunately no such tool for the scanner function exists and despite my no doubt clumsy, yet persistent attempts, I have not manged to get the scanner function going. I think I've managed to install the Brscan3 file from the Brother website using Ubuntu Software Centre but still no scanning. What have I done wrong or not done? I also installed the Sane Utility Software direct from Ubuntu in case that would help - no luck so far.

---

### Post by roger_1960 on 2012-10-04
Hi

You need to follow all the instructions here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html)

and do this:

> Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04
1. Open "/lib/udev/rules.d/40-libsane.rules" file.
2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


The lines to be added---------------------------

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
 
3. Restart the OS.

I have always found these instructions to be OK (although my brother is not the same model as yours)

Hope this helps

Roger

---

### Post by thane1 on 2012-10-04
Yes.. follow Roger's post.  And with Brother site instructions, be sure to read them carefully, being sure not to miss anything and you should get there in the end.  They're really good at supporting us linux users.  (In case you've not set up a scanner in linux before).. Once you've got the driver successfully installed, the "Simple Scan" program is a really easy (almost foolproof) scan program to use.  Just turn on the printer, then start Simple Scan and hit the gui scan button.  I'm on linux mint 13 and its in my repos, but I imagine you can get it in ubuntu from the repos if its not installed by default (haven't used ubuntu since unity came out.. personal preference).  Sane will work too, although you may have to set it up for your system.  Simple Scan just seems to work.

---

### Post by NDW57 on 2012-10-06
Hi. My guess is I've done something wrong but when I tried to enter "/lib/udev/rules.d/40-libsane.rules" all I got was "permission denied" and I could get no further. Tried "sudo" and "Sudo su" with no improvement.

---

### Post by plucky on 2012-10-06
> **NDW57 said:**
> Hi. My guess is I've done something wrong but when I tried to enter "/lib/udev/rules.d/40-libsane.rules" all I got was "permission denied" and I could get no further. Tried "sudo" and "Sudo su" with no improvement.

Try ```
gksudo gedit /lib/udev/rules.d/40-libsane.rules
``` as you are trying to edit the file if you are running Ubuntu.

```
sudo nano /lib/udev/rules.d/40-libsane.rules
``` should also work.

Good luck

---

### Post by Ruhani04 on 2012-10-06
Take a look at this if you are running 64bit:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

---

### Post by NDW57 on 2012-10-06
Just tried those things - apart from the 64-bit option - definitely 32 bit.
Have tried "Simple Scan" and Scan Utility". The scanner starts up and it sounds as though it's reading but all I get then is a wheel or circles twirling round eternally. I've also tried scanning from the controls on the machine with no luck there either. I'm wondering if the scanner simply isn't sending the image to the PC.
Any thoughts or suggestions?

---

### Post by plucky on 2012-10-07
> **NDW57 said:**
> Just tried those things - apart from the 64-bit option - definitely 32 bit.
Have tried "Simple Scan" and Scan Utility". The scanner starts up and it sounds as though it's reading but all I get then is a wheel or circles twirling round eternally. I've also tried scanning from the controls on the machine with no luck there either. I'm wondering if the scanner simply isn't sending the image to the PC.
Any thoughts or suggestions?

Have you tried launching simple-scan with gksudo?

```
gksudo simple-scan
```

If that works,it could be a permissions problem with the usb port.

Post output for ```
lsusb | grep -i Brother
```

Good Luck

---

### Post by NDW57 on 2012-10-07
Hi all. Thanks for your help. The scanner now seems to be working absolutely fine. Plucky's last suggestion did the trick so it must have been the usb port. Have switched the PC off and back on and it still works - problem solved !
Have a great day.

---

