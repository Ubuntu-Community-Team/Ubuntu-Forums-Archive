---
title: "What is the most out of the box / generally fuctional for home user?"
date: 2018-06-03
forum: New to Ubuntu
---

### Post by mawil10132 on 2018-06-03
What is the best out of the box / general functionality for a home user of the Ubuntu variants?

I ask this as initially I installed Ubuntu 18, but it didn't automatically allow my laser printer to function and simple browser functions which I use a lot didn't operate such as cut n paste and then failed touch pad functions.

When I tried Ubuntu 18 MATE, (and continue to use,)  these issue were resolved, although when I plugged the printer into USB messages came across saying drivers were required, if I continue on, the printer worked fine.

There are a lot of Ubuntu variants to try and I was hoping someone could advise of the best variant of any Linux which will function out of the box for what most users coming from majors OS as no brainer installs where virtually all aspects function.

I went out of my way to very recently buy an $800 Dell laptop hoping that what I read was try that Dell was Linux friendly.  I want to have a friendly and fully functional out of the box experience and wonder if the enthusiasm about the functionality of Ubuntu is real or over simply over zealous.  

Is there another Linux OS that I should be looking at if I want to have main stream OS functionality.  Overall I'm liking what I see but don't want to become an enthusiast Linux programmer.  Although I have no issues with once in a while, 1-2 times a year opening Terminal to fix things but that is all.  Let me finish with this, I sincerely want Linux to work for me, I wish to completely remove myself from Windows or Apple and Android.  But I suspect I often hear slanted views of what Linux can do as far as replacing the Main OS's.

Michael

---

### Post by Autodave on 2018-06-03
Some info on your system might be helpful for someone to help you: especially your printer.

You will get many opinions on what version to use. Personally, I like Xubuntu.  I switched to Linux 12 year ago and have never looked back. Installs then were troublesome. Now, pretty much as simple as it can get. My last install (Xubuntu 18.04)was on this machine. It was a clean install: not an upgrade. My HP wireless laser printer happened to be on at the time and and I didn't even have to do a thing to make it work: it was recognized automatically!

---

### Post by The Cog on 2018-06-03
Printers can be a problem but that's not the fault of Linux, it's because the printer makers don't bother to make Linux drivers. I have had good results with HP. My wireless HP 5030 just appears as an option when I choose File->Print, without even bothering to go into printer setup.

Like Autodave I use Xubuntu, and I have never seen any problems with touchpad or browser functionality. But I haven't seen many complaints about that from other *buntu flavours either. I don't want to push what happens to be my chosen flavour - they are all different and so are users. I recommend giving each one a try to see which feels best to you.

It's probably best to start a separate thread for your touchpad and browser problems if they persist - putting multiple problems in one thread creates confusion.

---

### Post by SeijiSensei on 2018-06-03
My guess is you have a pretty large hard drive. You could install other versions of Linux alongside MATE.  Install from the ISO of another distribution and pick "manual" when you're asked to partition the drive.  You'll be able to shrink the MATE partition and add another partition for the new operating system.  You'll be able to switch among them when you reboot.  Most Linux distributions require less than 40 GB of drive space, so you could easily have a number of them to evaluate on even a 500 GB drive.

Another good method for testing on machines with at least 4 GB of RAM is to install [VirtualBox]("http://www.virtualbox.org/").  This program lets you create "virtual machines" into which you can install various distributions and operating systems.  Most Linux distributions run well in 1-1.5 GB of RAM.  You can allocate the amount of memory to devote to the virtual machine during installation.  If you choose to go this route, I recommend following the method described here to use Oracle's own repository for VB:  [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions).  For 18.04, replace "<mydist>" with "bionic" in the instructions.  Make sure to install the [Extension Pack]("https://www.virtualbox.org/wiki/Downloads") as well.

The disadvantage of a virtual machine is that runs in an entirely emulated environment.  By default the VM cannot see outside its virtual machine image.  Among other limitations, the VM cannot address the video hardware directly which may matter if gaming on Linux is something you care about.   It might also make it more difficult to use advanced desktop effects whose performance might depend on the graphics hardware.  I don't use anything like that so I cannot say.  For the record, I use [Kubuntu]("http://cdimage.ubuntu.com/kubuntu/releases/bionic/release/"), since I have been a KDE user for a very long time.

---

### Post by mawil10132 on 2018-06-03
> **Autodave said:**
> Some info on your system might be helpful for someone to help you: especially your printer.

You will get many opinions on what version to use. Personally, I like Xubuntu.  I switched to Linux 12 year ago and have never looked back. Installs then were troublesome. Now, pretty much as simple as it can get. My last install (Xubuntu 18.04)was on this machine. It was a clean install: not an upgrade. My HP wireless laser printer happened to be on at the time and and I didn't even have to do a thing to make it work: it was recognized automatically!

Printer = Brother, HL-L2340DW,  I found this, but cannot tell if it is a legit page. 

There is an Installer and the Driver apparently,  also, Two versions? LPR PrinternDriver and Cupswrapper Printer Driver

[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2340dw_us_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2340dw_us_eu_as&os=128)

---

### Post by Holger_Gehrke on 2018-06-04
Looks legit enough to me, especially since the information shown by 'whois brother.com' (registered through godaddy.com, first registered in 1995, last renewed 2015, valid to 2020, registered to "Brother International Corporation" in New Jersey) fits. A bit of searching yields this [page with detailed installation instructions]("http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on").

Holger

---

### Post by SeijiSensei on 2018-06-04
Use the "Driver Install Tool" at the Brother site for the easiest method.

However I'd first make sure you don't already have the printer installed.  Open a browser on the machine and visit [http://localhost:631/](http://localhost:631/).  That will bring up the CUPS interface on your machine.  See if your printer is already installed.  If not, walk through the "Add Printers" procedure.  Enter your own username and password if prompted.

---

