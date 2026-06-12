---
title: "adobe flash blocking prompts"
date: 2016-07-14
forum: New to Ubuntu
---

### Post by nginmu on 2016-07-14
I use Firefox on Lubuntu. Every time I land on a webpage that uses flash, Firefox blocks Flash because it's outdated / vulnerable. So I click through the prompts to enable Flash for that particular domain 'Allow and remember'. But, Firefox never does seem to remember and even for the same page / domain, asks me the same question again and again.

I tried to update Flash but didn't seem to be able to.

I can use Flash ok, but I have to reauthorise the admittedly unsafe / outdated version every single time.

What can I do to make Flash enabled web content work safely and without continual prompting.. is there any kind of opensource alternative out there or is the only option, to just keep on individually allowing every piece of Flash content & accept the usage of an old vulnerable version?

---

### Post by ajgreeny on 2016-07-14
Which version of Lubuntu, firefox, and adobe flash are you using?

I have not seen that message for a very long time and was under the impression that it had been overcome with updates to the flash versions currently available.

Depending on your OS version it may even be possible to get flash version 22,0,0,192 installed and used in firefox by making sure you have the packages **adobe-flashplugin** from the canonical-partner repos and **browser-plugin-freshplayer-pepperflash** from the ppa at [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu).

---

### Post by nginmu on 2016-07-14
Linux 3.19.0-64-generic (i386)
Ubuntu 15.04

Firefox 44.0
Mozilla Firefox for ubuntu
Canonical - 1.0

Shockwave Flash 11.2.202.559 (listed in Firefox plugins)
"Shockwave Flash is known to be vulnerable and should be updated" "Update now"


[URL="https://blocklist.addons.mozilla.org/en-GB/firefox/blocked/p1123"]https://blocklist.addons.mozilla.org/en-GB/firefox/blocked/p1123
[/URL]
Tried to update but it came up with an APT file to download, Flash version 11.2.202.632, then said unknown channel: vivid-partner
Tried to check vivid-partner is there in sources, it does seem to be, I put in the link for the source and it comes up as canonical partners (which was already there anyway)


The Firefox plugins list offers options to 'ask to activate', 'always activate', and 'never activate'. I can only select 'ask to activate' though, the other options are greyed out.

I'm sorry I'm unsure how to get browser-plugin-freshplayer-pepperflash from the ppa

---

### Post by Dennis N on 2016-07-14
Is 15.04 correct for your Lubuntu? Since 15.04 has expired support, the best thing to do would be to update to Lubuntu 16.04 (and the current Firefox) so that you can install the adobe-flashplugin package from the Ubuntu Canonical Partners repository.

---

### Post by Impavidus on 2016-07-14
Your 15.04 system hasn't received updates for 6 months. Firefox is now at version 47, flash at 11.2.202.632 (or something above 20 if you use the other method). So that explains your problem.

You can try and upgrade. You can only upgrade to the next version, 15.10, which is almost dead too, and then upgrade to 16.04 LTS. But it may be better to do a clean install of 16.04 LTS. Lubuntu 16.04 LTS has 3 years of support.

---

### Post by nginmu on 2016-07-14
Ok peeps, many thanks - I will try a clean install of Lubuntu 16.04

---

### Post by pauljw on 2016-07-15
have you installed the flashplugin-installer?  It's in the repositories and will keep flash up to date.

---

### Post by nginmu on 2016-09-30
Trying a new install of  16.04 - I'm still running on 15.04 (i think?) and IIRC the whole HDD was used to install lubuntu originally. I now have a fresh download of the i386 16.04 CD image on the existing desktop - can I use that to install 16.04 as a dual boot with the old install? like say, repartition the drive in half and run the two side by side for a while before ultimately deleting the older install?

(do i need some kind of CD drive emulator, or put it on a USB stick and try to coax the BIOS to boot from USB etc?)

---

### Post by Impavidus on 2016-10-01
The easiest way if you don't have a dvd drive is using a live usb (and if you have a working dvd drive the live usb may stil be the best option):
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://askubuntu.com/questions/372607/how-to-create-a-bootable-ubuntu-usb-flash-drive-from-terminal](http://askubuntu.com/questions/372607/how-to-create-a-bootable-ubuntu-usb-flash-drive-from-terminal)

You can use the live usb to resize the partition of your 15.04 system to create unallocated space and then to install Lubuntu 16.04 LTS to dual boot both systems. It will be best if you move to 16.04 as soon as you can and then remove 15.04.

---

### Post by nginmu on 2016-10-01
I guess it depends if this machine is capable of booting from USB? Hope so. Thanks for the pointer.

Dang it! Trying to install mkusb [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) to create the bootable USB from the .iso, but despite following all the preparatory instructions closely all I end up with in the terminal is...

```

me@mymachine:~$ sudo apt-get install mkusb mkusb-nox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mkusb
E: Unable to locate package mkusb-nox

```

Can anyone suggest what might be wrong here or, an alternative way of creating a bootable USB from the .iso?

---

### Post by buzzingrobot on 2016-10-01
You ought to start a new thread with that mksub question, since it's effectively hidden at the end of your old Flash thread.

Meanwhile, double check that you have correctly installed mksub's PPA.  Here's it's page on Launchpad: [https://launchpad.net/~mkusb/+archive/ubuntu/ppa](https://launchpad.net/~mkusb/+archive/ubuntu/ppa)

(Re: Flash in Firefox -- Always install/update with the package provided by Canonical. The updates are released very quickly and users receive them during routine updates.  Which means, of course, you need to update regularly.)

---

### Post by nginmu on 2016-10-09
I ended up using something called rufus, to put the 16.04.1 .iso on a usb stick. Used that to install 16.04.1 and bob's your uncle, flash is working in firefox at the very latest version with no problems at all.

---

