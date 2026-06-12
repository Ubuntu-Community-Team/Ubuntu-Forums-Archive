---
title: "New user"
date: 2015-07-16
forum: New to Ubuntu
---

### Post by Esteban_Brown on 2015-07-16
Hello, I'm new to this and I will like to installed ubuntus on my laptop: Toshiva, Satellite C55-B Processor: Intel(R) Celeron (R) CPU 2840 @ 2.16 GHz
Memory: 4.00 GB
System Type: 64 bit

---

### Post by howefield on 2015-07-16
So, what's the problem then, where are you stuck ?

It would also help to know if there is currently an operating system on your machine :)

---

### Post by slickymaster on 2015-07-16
Have a read at [Welcome to the Ubuntu installation guide!]("https://help.ubuntu.com/community/Installation")

---

### Post by grahammechanical on 2015-07-16
If you are asking for permission, then, you do not need permission. We are not charged to download and install Ubuntu.

But you should check the system requirements. Give some thought the video adapter. Does it have enough of its own memory to run Ubuntu? You may need to use Lubuntu or Xubuntu instead.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Without further information all we can do is make guesses as to your problem.

Regards.

---

### Post by huff2 on 2015-07-16
Before you install it on your laptop you should create a virtual machine, VirtualBox is what I use, and install Ubuntu on that first to see if you like it. Just my thoughts.

---

### Post by Noah0504 on 2015-07-16
Also, you can burn the ISO to a DVD or make a bootable USB disk and run the Live Image to see if you like it.  This will also allow you to make sure you won't encounter any hardware issues.

---

### Post by Esteban_Brown on 2015-07-16
I download the 12.10 vertiom and i can not boot it, that is how far I got

---

### Post by Noah0504 on 2015-07-16
Well for what it's worth, that release is almost 3 years old.  I'm not sure if you have any sort of bandwidth cap (or access to broadband for that matter), but the current release and the Long Term Support release are available under the downloads page of the Ubuntu website.  I would maybe suggest downloading one of those?  After that, you can either burn the ISO to a DVD or create a bootable USB installer.

---

### Post by QIII on 2015-07-16
Hello!

12.10 has reached End of Life (EOL) and is no longer supported.  The first thing you should do is get an ISO of a supported release (12.04 LTS, 14.04 LTS or 15.04) and try again with that.  There is little point in having everyone help with problems installing an unsupported release.

If you are new to Linux, I would suggest using 14.04 LTS if your machine supports it.  It is supported until 2019.

---

### Post by Bucky Ball on 2015-07-16
Go [here]("http://www.ubuntu.com/download/desktop"). 14.04 LTS is supported until April 2019. Burn install media, boot from it and 'Try Ubuntu'. That will not change your hard drive and the OS runs from the install media.

There is no need for a virtual machine to try Ubuntu without installing it.

---

### Post by Esteban_Brown on 2015-07-17
How I can do it?

---

### Post by howefield on 2015-07-17
> **Esteban_Brown said:**
> How I can do it?

You are not really giving enough information for others to be able to help you.

Do what, exactly ?

You have been advised to get a current up to date and supported version, have you done that or are you still intent on installing 12.10 ?

---

### Post by toxx on 2015-07-17
> **Esteban_Brown said:**
> How I can do it?

Download the live boot ubuntu 14.04 iso from the ububtu downloads page

Then download unetbootin
Then plug in your usb stick
then burn iso to usb
then if you have win7 or above, use the boot menu to restart the computer using uefi usb , or if you're on an older os, restart the computer, go into bios settings,and select the usb drive.

Now you can try linux, and there is also a desktop item to install ubuntu

---

### Post by Esteban_Brown on 2015-07-18
I already updated the ubuntu vertion to and when i try to installed i keep getting this: filec:\ubuntu\install\boot\vmlinuz.cfi is corrupted for more info, please see the log file c:\use\fuv\appdata\local\temp\wufi-14.04-rev286.log

---

### Post by howefield on 2015-07-18
> **Esteban_Brown said:**
> I already updated the ubuntu vertion to and when i try to installed i keep getting this: filec:\ubuntu\install\boot\vmlinuz.cfi is corrupted for more info, please see the log file c:\use\fuv\appdata\local\temp\wufi-14.04-rev286.log

Is this a Wubi installation, and what does the log say (you can post it here between [code ][/code ] tags if you wish) ?

---

### Post by Esteban_Brown on 2015-07-19
I tried with a new vertion 14.04.4 and this is what i got:  [COLOR=#000000]* filec:\ubuntu\install\boot\vmlinuz.cfi is corrupted for more info, please see the log file c:\use\fuv\appdata\local\temp\wufi-14.04-rev286.log*[/COLOR]

---

### Post by slickymaster on 2015-07-20
> **Esteban_Brown said:**
> I tried with a new vertion 14.04.4 and this is what i got:  [COLOR=#000000]* filec:\ubuntu\install\boot\vmlinuz.cfi is corrupted for more info, please see the log file c:\use\fuv\appdata\local\temp\wufi-14.04-rev286.log*[/COLOR]

Can you please [do what howefiled ask you to in his post]("http://ubuntuforums.org/showthread.php?t=2287016&p=13323233&viewfull=1#post13323233") and past here the content of that log file, [using code tags]("http://www.google.com/url?q=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D2171721%26p%3D12776168%26viewfull%3D1%23post12776168&sa=D&sntz=1&usg=AFQjCNEl9aLbIoHVXZYLQvugZhl0WwWGFg") for the effect.

---

### Post by Esteban_Brown on 2015-07-20
If I understand what howefiled is asking me is this: [http://releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso](http://releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso) that is the vertion that I'm trying to install

---

### Post by MGrowl on 2015-07-20
Either burn a cd, or get a live USB and install it from there. Make sure your BIOS can boot from USB. I don't understand what the problem is, it's easy installing ubuntu if you can read.

---

### Post by mastablasta on 2015-07-20
> **MGrowl said:**
> ... it's easy installing ubuntu if you can read.

Most guides are in English though. If person trying to install it is not fluent in English they might have a problem following the English instructions.

either way Esteban should check MD5sum of the downloaded image to make sure, the file downloaded with no errors at all.

Community made Ubuntu manual exists in a couple of other languages (in case the language is the barrier here).

---

### Post by MGrowl on 2015-07-20
@mastablasta No offense meant. I'm also still learning. I just think it's easy enough to install, regarding manuals in different languages.

---

### Post by earruda on 2015-07-20
Nice to know that you are interested in using a Linux distro.

I would recommend you gt the latest ubuntu version, which is 15.04, or the LTS version, which is 14.04. LTS stands for Long Term Support, which means that you won't have to upgrade to a newer Ubuntu version for a longer time and still get the latest software versions.

---

