---
title: "Make Live-Xubuntu persistent"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by windows-crasher on 2011-09-19
Hey folks,

I'm traveling at the moment and last week my laptop fell down and the hard drive crashed :( I had access to a windows PC (but no longer) and managed to install Xubuntu live version on a usb stick with which I am able to use my computer and access the internet now. It's the first time I am using any linux distribution and it works fine for me!

The only problem is that whenever I install Skype for example, it's gone after a reboot. I googled and found out that what I am searching for is a "persistent Xubuntu version" (on a USB device). I tried the advices I found on the internet but none of them worked for me.

Is there an easy way to make this Xubuntu version I am using now persistent? 

I am sure there are plenty of solutions out there and if I had access to a Windows PC I would just create a new installation but I don't :(

I'd really apprechiate any help, thanks!!

Ben

---

### Post by Lisiano on 2011-09-19
Sorry but unless you have a nearby Linux or Windows PC you can't really do anything. You could keep a copy of the Skype.deb on the USB so you don't have to redownload it.

---

### Post by anewguy on 2011-09-19
You need access to a running PC, then follow this wiki (note it does say for kubuntu as well):

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

Again, this wiki has not been updated to indicate the persistence has been added unetbootin.  If it's an option in unetbootin be sure to enable there.  I personally haven't used unetbootin in at least 6 or 7 months and at that time persistence wasn't there.

Dave ;)

---

### Post by Lisiano on 2011-09-19
It's there, you just need to download from SourceForge, the repo one is outdated a bit (Up to 10.04 only) but works.

---

### Post by windows-crasher on 2011-09-19
Thanks a bunch for the quick replies! :-)

I found the wiki but the only other computer I have access to is a Mac (never worked on a Mac before either)...

Where do I get Skype.deb from? I downloaded Skype from the Ubuntu Software Center so far.

Lisiano, can you explain that to me please?

Thanks again!

Ben

---

### Post by varunendra on 2011-09-19
Do you have a spare USB flash drive? If yes, then you may try this:

[LIST=1]
[*]Boot the laptop with the current Live USB
[*]Plugin the second USB, let it get detected,
[*]"Install" the OS on the 'other' USB just like you would on a native hard drive.
[*]While installing Grub (at the '**manual partitioning**' stage), make sure you install it on the USB drive on which you are "installing" Xubuntu.
[/LIST]
After the installation is finished, you can use that 'other' USB as a hard drive with permanent installation.

I have no spare USB drives around to experiment with this myself, but I'm sure it should go smooth.



**_EDIT_:**
Just wanted to add this: You can find the .deb packages downloaded via software center (or synaptic or apt-get) in **/var/cache/apt/archives** directory. All downloaded packages are stored there unless you delete them. (In your case, they're deleted with reboot, since the entire filesystem is volatile).

---

### Post by anewguy on 2011-09-20
> **Lisiano said:**
> It's there, you just need to download from SourceForge, the repo one is outdated a bit (Up to 10.04 only) but works.

Not doubting you in anyway - just stating where the wiki is and that it may be out of date.  ;)

Dave ;)

---

### Post by varunendra on 2011-09-21
Positive or Negative, I would like to see a reply from *windows-crasher* how it went with him.

---

### Post by windows-crasher on 2011-09-21
Hi,

thanks to all for the replies. I bought a second USB flash device yesterday and tried to install Xubuntu but somehow it failed at a very early stage. I will try it again today and post the error message.

---

