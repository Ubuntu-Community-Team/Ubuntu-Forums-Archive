---
title: "Installing ubuntu"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by halle3211 on 2014-01-02
Hi there, I got an Acer c710 for Christmas. I wanted to try to install ubuntu. I followed instructions from web. At the end of the process I got an error message. I would like to try again but do not know how much of the process failed. Is my hard drive already partioned rrom my last attempt and if I simply try again will it mess things up? I do not know a whole lot about this stuff but I do know I would like more than chrome os on here. Hope to find some help.

---

### Post by chkneater on 2014-01-02
I'm not sure about compatibility, but I'm willing to go on a limb and say yes...

What you need to do is with a WIRED connection download the version you want from Canonical (ubuntu partners) I'd recommend 13.04 since 13.10 is still sort of being tested.  After D/L, check the MD5 sums, just like it says on the web site.  If the numbs match, then stick the DVD in and try running it without installing at first, just to look around and see if your original attempt actually did anything.  If you want Ubu exclusively, use Gparted to format to EXT3 or 4 and make a seperate swap partition also (it only needs to be about 4GB at most).  You want root to be /, not your login or anything else when you install.  After you're SURE the OS's are gone, click the install icon and follow the instructions.

Also, if want to share files with windows systems make an NTFS partition that you can store stuff in; that way Ubu can see the files and use them as well as windows.  Don't use it for booting tho.

Hope that helps, any questions, well you know how to ask!!

Also, while you're installing it should ask about installing updates at the same time and I would recommend to do that to save you some time and frustration.

---

### Post by Impavidus on 2014-01-02
Don't install 13.04. It reaches end of live this month. 13.10 is fine, 12.04 if you want something rock-solid, but it's already getting a bit old.

I never tried Chrome OS, but you should be able to dual boot it (I think). Show us the layout of your partitions. This may help. From the live disk, open gparted and post a screenshot.

---

### Post by chkneater on 2014-01-02
my bad, I forgot 13.04 was not LTS like 12.04,  I've not had any probs with 13.10, I'm pretty happy with it, with one exception....

---

### Post by whitesmith on 2014-01-02
> **halle3211 said:**
> At the end of the process I got an error messageWould you share it with us?

---

### Post by halle3211 on 2014-01-02
Really new at all this....don't know how to get to live disk

I live in the mountains 75 miles from the nearest city. Otherwise I would just take it to someone who knows what they are doing. I don't know how to go back to where I was and get the error message, or see how far along the install got. I was in developer mode. My daughter was helping me and did most of the commands straight from what she was reading on internet. I would like to start from scratch but don't know if this would really mess it up is it is partially done. I believe she was using crouton to install. I am sorry about being so naive about all this. To be honest, I didn't understand most of the replies.

---

### Post by chkneater on 2014-01-02
The LiveDVD is downloadable from Canonical, DL it, burn it at slowest speed possible, then place the disk in the drive and reboot.  It will prompt you for languages, and then ask if you want to try ubuntu without installing.  This will allow you to do most things a full install can do without changing anything on your comp, but most importantly you can check if there is any remaining parts of the previous OS.

If you want JUST Ubu, then use Gparted while using the LiveDVD and reformat to Ext3 or 4 and also make a swap partition.  Then click on the install Ubuntu icon right there on the desktop.  It's important but not necessary to have a wired connection only because if the wireless goes out in the middle of your install you'll have to re-do.  Also install the updates when the installer asks. 

If you want both Ubu and Chrome the installer will give you the choice, just skip the part above I mentioned about formatting.  The installer should go through that with you.

---

### Post by halle3211 on 2014-01-02
I don't have a dvd drive :(

and I don't have a wired connection available here.

---

### Post by chkneater on 2014-01-02
That's ok, you can do it wirelessly, just be sure to check the MD5 sums before installing.  Wired just a little safer is all.

> **halle3211 said:**
> i don't have a dvd drive :(

usb?

---

### Post by halle3211 on 2014-01-02
Because this is a chromebook, I can't just download it. From everything I see online, I have to go into developer mode and manually type in the commands, or is there a simpler way?

---

### Post by monkeybrain20122 on 2014-01-02
> **chkneater said:**
>  I'd recommend 13.04 since 13.10 is still sort of being tested.

I  would definitely not recommend 13.04 as it will reach end of life in about three weeks. 13.10 is not 'sort of being tested', it was released in Oct and is the latest stable release. 12.04 is the LTS.

---

### Post by chkneater on 2014-01-02
> **halle3211 said:**
> I live in the mountains 75 miles from the nearest city. Otherwise I would just take it to someone who knows what they are doing. I don't know how to go back to where I was and get the error message, or see how far along the install got. I was in developer mode. My daughter was helping me and did most of the commands straight from what she was reading on internet. I would like to start from scratch but don't know if this would really mess it up is it is partially done. I believe she was using crouton to install. I am sorry about being so naive about all this. To be honest, I didn't understand most of the replies.

Thats OK, most of em didn't relate anyway.  Shouldn't need many commands.  Just go to the official Ubuntu page and DL the newest (13.10) version to hopefully your USB drive and reboot.  After you boot it will ask you what language and if you want to try it without installing or install it.  Try it without installing at first just to see if there are still parts of your OS on there.  Reinstalling won't hurt a thing unless you have things stored on there you want to keep, in which case you would need to move them to a disk or something so they don't get deleted during installation.

---

### Post by halle3211 on 2014-01-02
Okay, I tried that but it doesn't give me the option to download directly to USB, it tries to download it to chromebook but won't

I used to have an IT guy that could remotely access my computer and just do whatever I got stuck on, no matter where I was. I would give anything for him to still be around.

---

### Post by sudodus on 2014-01-02
No you cannot download the iso file directly to the USB boot device. You should download it to some other place, typically a 'Download' directory (in Windows and Linux). And then you should use [some special tool]("https://help.ubuntu.com/community/Installation/FromUSBStick") to flash it to a USB device (for example a pendrive). Of course, it might be easier to download and flash to the USB device in another computer, that you are familiar with, rather than this brand new Christmas gift.

---

### Post by chkneater on 2014-01-03
> **monkeybrain20122 said:**
> I  would definitely not recommend 13.04 as it will reach end of life in about three weeks. 13.10 is not 'sort of being tested', it was released in Oct and is the latest stable release. 12.04 is the LTS.

Ok, once was enough.

> **halle3211 said:**
> Okay, I tried that but it doesn't give me the option to download directly to USB, it tries to download it to chromebook but won't

I used to have an IT guy that could remotely access my computer and just do whatever I got stuck on, no matter where I was. I would give anything for him to still be around.

yeah, I guess if the command lines aren't working out and you have no DVD drive you'll have to download it onto another device and like Sudodus suggested.  That way you can test it before installing it also.

---

### Post by FiremanEd on 2014-01-03
This is just a thought, but if you feel that you just don't have the resoures to do what has been suggested in the thread by the other members, perhaps buying a pre-installed live USB of Ubuntu 13.10, for example, [https://www.osdisc.com/products/linux/ubuntu/ubuntu-1310-desktop-8gb-usb-flash-drive-64bit-pc.html]("https://www.osdisc.com/products/linux/ubuntu/ubuntu-1310-desktop-8gb-usb-flash-drive-64bit-pc.html")

---

### Post by king.of.random on 2014-01-03
Just another thought on this topic. If you are going to install Ubuntu via a usb stick then you may need to go into your laptops BIOS and change the boot order so that it attempts to boot from usb drive first.

---

### Post by halle3211 on 2014-01-04
Think I give up. Have to just live with chrome os for now. Can do more on my iphone than I can on this. Just thought having a real operating system would be good. Have looked at so many instructions from internet regarding a chromebook and they all involved going into developer mode and partitioning the hard drive, which I tried. Now I don't have a clue what part of the process has been done and what has not. Would like to start over and do it right.

---

### Post by FiremanEd on 2014-01-04
I believe that support for chromebooks is evolving and will get easier down the road for Ubuntu installs and Linux.  So, don't dispair and keep researching!

---

### Post by JeQhdMD on 2014-01-04
Halle - -  A chromebook is an entirely different animal and needs to be installed very differently than a typical dual boot (or even a stand alone) Linux system.

Here's the article that's often recommended for these devices:

[http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/](http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/)

I also have the Acer c710 & will be doing this in the next couple weeks.   If all doesn't work as indicated, the repair seems super easy - if I'm recalling the article correctly, just restart the chromebook and restore the system by pressing the space bar.

I am really hoping there will be a "Chromebook II" offering soon, that comes as a dual boot with ChromeOS and any top Linux distro such as Ubuntu.  The world of tablet OS's, webapps, and touchscreen guis is most useful (to me) on a smartphone - - on everything else, it's just not my "cup of tea" . . . . the Chromebook is a super easy, fast way to get on the internet and manage mail etc., but it doesn't have the privacy I need for sensitive content - I much prefer my Acer Timeline 14" laptop instead.

---

### Post by halle3211 on 2014-01-05
Well when you are ready to get started perhaps we could chat and I could work on mine at the same time. I am quite lost in all this.

---

### Post by JeQhdMD on 2014-01-06
*I'll post back on what i learn - and if any adjustments are needed to the article.*

---

### Post by tfrue on 2014-01-06
So you have two options, either use Crouton or ChrUbuntu to install Linux on your Chromebook. Crouton will make it so you can keep your Chrome OS live and switch to Linux with a hot key, while ChrUbuntu will make your Chromebook and dual boot computer.

Here is an article on using Crouton, [here]("http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/")


If you are wanting to remove the Chrome OS, and just use Linux or have a dual boot, then use Chrubuntu, then try this [article]("http://chromeos-cr48.blogspot.fr/2013/10/chrubuntu-for-new-chromebooks-now-with.html")

Good Luck, 
Chris

---

