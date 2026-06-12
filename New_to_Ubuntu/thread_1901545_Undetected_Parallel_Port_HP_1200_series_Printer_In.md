---
title: "Undetected Parallel Port HP 1200 series Printer In Ubuntu 11.04"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by oldstumpy on 2011-12-28
****
Hi Everyone having problems installing my hp 1200 series printer in ubuntu 11.04 apparently HPLIP installer for this printer has the option for Parallel Printing disabled,i have tried to install it using start-system-admin-printing using different drivers but to no avail. It asks for a url when i click on other but i don't know what to put there. Any help with this issue would be greatly appreciated.Thanks very much oldstumpy

---

### Post by anewguy on 2011-12-28
What type of parallel port adapter do you have - is it internal built-in on the motherboard, a separate parallel port card, a USB to parallel adapter, or what?

If it's a separate parallel port card, if it was one of the cheaper ones on the market it is actually a multi-function chip on the card, and uses a driver to access it as a parallel port.  So far I have not seen any drivers for these type of adapters.

If it's a USB to parallel port card, we will need the model, etc.:

- with the adapter plugged into a USB port, open a terminal window:

prior to version 11.04:  applications/accessories/terminal

11.04 and up with Unity:  click on top most button (Dash home) of the Unity menu, type ter in the search string and click on terminal

- in the terminal window type:

lsusb <press enter>

Copy and paste the output from that to a reply here.

I'm thinking you need some of the CUPS packages installed, but I need to look to see which ones.

In the mean time, open a terminal window and type:

sudo modprobe lp <press enter>

Then go to user administration, click for groups, and be sure your userid is in the lp group.

Wait a few minutes and try printing again.  Post back what happens.

Dave ;)

---

### Post by oldstumpy on 2011-12-29
Hi:Dave,I am using ubuntu 11.04 version,classic view,i have one printer hooked up to usb port,a canon mx 420 all in one iuse a program called turboprint and vuescan for my copy,scan,and color printing machine,then i have an hp laserjet 1200 series laser for my day to day b&w printing which is hooked up to a parallel port built into mother board back of computer.The issue seems to be with the automatic installer HPLIP from hp which has parallel port disabled in that installer i am some what of a newbe and can't figure out howto in stall any other way.Dave any thoughts
on this issue,Thanks John Ps.Anybody else wishing to help it would much appreciated Thanks Again to Dave and anybody else.John

---

### Post by anewguy on 2011-12-29
I would try modprobing the lp module and adding your self to the lp group and then try again and post back what happens, as I mentioned in my first post.  I'm not sure the parallel port is actually "seen" until the lp module is loaded.  This might explain why the HPLIP doesn't show a parallel port as an option.  Please note we aren't making the loading of lp module permanent across boots yet, so do all of this testing without rebooting.  When everything is working we can make it permanent.

Dave ;)

---

### Post by oldstumpy on 2011-12-29
Hi:Dave I haven't got a clue about what you are talking about.I am new to all this stuff,please explain step by step.I Don't know what lp module is or lp group i don't know much about the terminal either.Please be patient with me.Thanks oldstumpy

---

### Post by anewguy on 2011-12-30
We're going to do a few things from what is normally called the command line - text based instead of a GUI.  The first thing you need to do is open a terminal window:

- slide your mouse to the left until the Unity menu appears.  Move up to the topmost box - "Dash Home".  Click once.

- enter ter in the search string, then click on the terminal icon.

You should now have a new window on your screen with a prompt in the format of youruserid@yourcomputername:~$.  This is the command line.

You need to see if a kernel module which helps with printing is loaded.  This module is called "lp". Type lsmod and press enter.  A list of the modules currently available to the kernel is shown.  Look through this list for "lp".  If it does not show then you need to load via typing sudo modprobe lp and pressing the enter key.  It will ask for a password - just type your normal password and press enter - and don't worry - it doesn't show on the screen that you are typing the password.

Do the lsmod again to be sure the module lp appears in the list now.  Also check and see if a module named "parport_pc" is in the list.  If not, try loading it via typing sudo modprobe parport_pc and pressing enter.  It may prompt for a password again - follow the same instructions as before.  If it says the module is not found or some other type error, and you are sure you typed the name in correctly, just move on to the next step.

You need to see if the lp group is defined via typing grep lp /etc/group and pressing enter.  It will hopefully return something.  If not, then you need to create the group via typing sudo groupadd lp and pressing enter.  You may be prompted for a password again.  Now do the grep lp /etc/group again to see if the group shows.  

You need to a member of the lp group.  Type grep lp /etc/group and press enter again.  Do you see a line with your userid in it, similar to the following:

lp:x:7:dave


If no line shows with your userid in it then you need to add yourself to the group via typing sudo adduser youruserid lp and pressing enter.  Do the grep  lp /etc/group again to be sure it added you to the group.

Now, DO NOT REBOOT - however just log out and back in.

Try the hplib thing to install your printer again and post back what happens.

Dave ;)

---

### Post by oldstumpy on 2011-12-30
Hi:Dave,ok i did that and this is what came up                     lp                     13349  0  Thanks for being patient with me. oldstumpy

---

### Post by oldstumpy on 2011-12-30
Hi:Dave,Ok you can disregard my last post i did everything you said to and all came up in terminal as you said it should.Printer is working as of now i found a cups driver that would work hopefully it will work fine now.But when i logged out and back in i checked the hplip device manager still no recognition of parallel port it is shaded out by default i think the hplip device manager only seems to recognize usb equipment so much for HP Support.My printer is recognized in printing-localhost from start-system-admin-printing so again printer working fine.I learned a few things thanks for being patient with me hope to work with you again some day.  Thanks for help oldstumpy

---

### Post by anewguy on 2011-12-30
Just glad it's working for you.  If someone else posts with the same problem, just play it forward.

Dave ;)

---

