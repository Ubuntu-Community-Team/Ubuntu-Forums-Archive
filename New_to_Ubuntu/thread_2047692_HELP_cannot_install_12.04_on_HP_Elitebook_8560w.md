---
title: "HELP cannot install 12.04 on HP Elitebook 8560w"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by sarc on 2012-08-25
I have done many install on other notebooks before.  Install on external USB drive from a USB stick.  The internal hard disk has WIn7 64 bit enterprise (it's for work and I don't want to install on notebook internal hard disk).  I have bitlocker encryption on system drive.

Complete failure.  Symptoms are:

1. First couple of times computer froze at install step connecting to internet.  I hard power off a few times, same result.

2. After those few times I would get the initial purple screen showing the keyboard and stick man figures, then quick flashing message (to quick to read, something about Linux) , then just a blinking cursor on black screen (tried waiting up to 30 min on some tries, no luck)

3. I downloaded the ISO again (in case there was some file corruption on my download image), tried creating startup disk using different USB sticks, using 12.04 32 and 64 bit, burning on CDROM, and with earlier version (11.04 if I remember ). Tried with the target USB Hard Disk connected or disconnected.  Same result: purple screen, flashing message, cursor.

I tried abut 20 times in different combinations.

Please help!

---

### Post by black veils on 2012-08-25
do you get to the install process or does it fail before that?

does your windows system still work ok?

---

### Post by C.S.Cameron on 2012-08-25
My Elitebook 8560w boots ok from external USB3 HDD as long as it is from a USB2 port and not the USB3.

Edit:
It will boot a USB2 drive from the USB3 port also.

---

### Post by sarc on 2012-08-25
Hi
all I get is the very first purple screen with the keyboard and human stick figure for a few seconds, then just black screen with cursor.

Yes Win7 still works fine.

> **black veils said:**
> do you get to the install process or does it fail before that?

does your windows system still work ok?

---

### Post by sarc on 2012-08-25
> **C.S.Cameron said:**
> My Elitebook 8560w boots ok from external USB3 HDD as long as it is from a USB2 port and not the USB3.

Edit:
It will boot a USB2 drive from the USB3 port also.

I can boot an external USB drive with the Ubuntu 11.10 of another PC (drivers are different of course so it does not work well).  But I cannot run install from the Elitebook

---

### Post by Bashing-om on 2012-08-25
sarc;

  Have you tried holding the shift key down to get to the boot options screen?

 Perhaps try some of the offered options to boot? 

[INDENT]HTH <==BDQ
[/INDENT]

---

### Post by jibawakee on 2012-08-25
Have you tried to use all the boot flags when you boot from the live cd/usb before installing

---

### Post by hkxghost on 2012-08-26
Hi sarc,

I made the following post in a different place earlier today as I was working to solve this problem yesterday (I added a bit of formatting here..):

[quote=myself]
I managed to get it installed, but I had to use Kubuntu instead  of Ubuntu since that one did get to the main menu and displayed the  options (Try Kubuntu, F1, F2, etc.). In one of the F menus, there&#8217;s an option to set **acpi=off**. If you do  that, you&#8217;ll be able to boot all the way to the desktop and then  install.

After you get Kubuntu 12.04 installed, then you can use ```
sudo  apt-get install ubuntu-desktop
``` to get Ubuntu in place. To boot Ubuntu instead, go to a terminal and do the following:
```
 sudo dpkg-reconfigure kdm
``` and select lightdm from the list and then &#8220;OK&#8221;.

 Restart machine.

 It should now be using lightdm as the default manager. If everything  works fine up to this point, then you only need to check what you need  to do in order to remove all KDE components.

For example, ```
sudo apt-get  remove kde-full --purge
``` might be a good one to start looking into.

 Good luck.[/quote]

This assumes that you want to remove KDE. If not, then skip the last part. Hope this helps..

-x

**EDIT: I forgot to mention: my EB 8560w has an nVidia chipset (Quadro 2000M). There's a known bug. See [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/864739").**

---

### Post by Terl on 2012-08-26
@sarc,

To expand what Jibawakee said, as soon as the screen comes up with the keyboard and the little figure, hit a key, a menu should appear, if you hit F6 key, you should get a small menu of boot options.  Try the nomodeset option, select it and hit enter to toggle it on and hit escape and it should hopefully boot.

I have an HP desktop and had to do that.  You will have to add it to your grub configuration after the install but that is all easy.

---

### Post by hkxghost on 2012-08-27
**@sarc:** Has any of this helped you at all or are you still stuck? Has this been solved? Any updates?

Thanks,
-x

---

### Post by sarc on 2012-08-27
Hello all
thanks for the posts!  I'm on business trip now and will be able to try again this weekend.

>>My Elitebook 8560w boots ok from external USB3 HDD as long as it is from a USB2 port and not the USB3.
How can I tell which USB port is 2 or 3? 

>>Have you tried holding the shift key down to get to the boot options screen?
Holding shift key down did not do anything - still same black screen

>>Perhaps try some of the offered options to boot? 
HTH <==BDQ
Have you tried to use all the boot flags when you boot from the live cd/usb before installing
Thanks bit I don;t know how to do it - is it via the 

thanks for bug report link!  It's exactlysame issue as I'm having.  Can anyone tell me how to do this fix 

"Yep, same here... nomodeset for booting the live CD, no problems after installation w/updates...
Seems like everything is working now! (Except for the touchpad on/off button...)
Still a quite annoying bug for people who don't know about the workaround..."

I can boot from either US or CD (12.04...)

---

### Post by hkxghost on 2012-08-27
> **sarc said:**
> thanks for bug report link!  It's exactlysame issue as I'm having.  Can anyone tell me how to do this fix

Please look at my previous post. As far as "how to fix", it seems you have 2 options:

[LIST=1]
[*]Either wait for the Ubuntu devs to include the fix in a future release (probably not what you want..), or
[*]Try installing from the Kubuntu Live CD and make sure that **acpi=off** is marked as indicated previously.
[/LIST]
 This is what I did in mine and it worked just fine. No more problems to report on my end. 

You can optionally install Ubuntu Desktop Gnome/Unity and remove KDE after you're done with the install.

-x

---

### Post by sarc on 2012-09-12
OK this is what I did.

Tried all manners to get 12.04 to install, could not even get command line.  From CDROM (not USB) I could get the GRUB menu and choose compatibility mode, but still ended up with garbage screen and no response from keyboard input on 1st boot.

Switched to Mint 13, I could install Mint no problem, at boot menu after install, still no screen even in comaptibility mode regardless of what I did (note: I did install the NVIDIA restricted driver during Mint initial install - I tried both versions).

With Mint I could easily get to command line but useless because no networking was working at all.  Editing fstab and Grub menu was no use.

SO THEN:
Installed Mint 13 on *ANOTHER* notebook (HP Probook 6555b)on a USB drive.  Went without a glitch. 
Booted the USB drive on the 8560, select compatibility mode on GRUB menu (press SHIFT key on boot, which did not work at all with 12.04) .  EVERYTHING WORKED on compatibility mode.
(p.s. I tried this trick with 12.04 and failed)
Intalled the NVIDIA restricted driver from compatibility mode.  Rebooted.
BINGO.
Running Mint happily ever since.

---

