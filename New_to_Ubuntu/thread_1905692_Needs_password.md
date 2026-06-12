---
title: "Needs password"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by hollysc on 2012-01-07
I just received a dell mini with linux Grub and ubuntu.  there is no desktop, it was erased before I got the machine.  it has 300 updates that I cannot download because it is asking for a password.  the guy that sold me the computer is out of the country and cannot be reached   any help  any suggestions are welcome!!

---

### Post by mörgæs on 2012-01-07
Moved to a new thread.

---

### Post by hollysc on 2012-01-07
ok can I tell you I have no idea what that means   sorry, I am pretty new at linex and don't actually start the class until this month

---

### Post by lisati on 2012-01-07
"Moved to a new thread" means that your question has split off from the discussion where you asked it to a discussion of its own.

Do you use a password to login to the machine? If so, use that one to check for and apply updates.

---

### Post by fabricator4 on 2012-01-07
> **hollysc said:**
> ok can I tell you I have no idea what that means   sorry, I am pretty new at linex and don't actually start the class until this month

Have a look at these instructions:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

If you've just been given the computer then you can probably just start from scratch and re-install.  That way you'll get the latest release, and it will be your own.

Download Oneiric from here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Chris

---

### Post by hollysc on 2012-01-07
it also says 100% of root partition is in use?

---

### Post by matza55 on 2012-01-07
Do as > fabricator4 says. It's better to do a system for beginning - your own.

---

### Post by fabricator4 on 2012-01-07
> **hollysc said:**
> it also says 100% of root partition is in use?

It's either badly configured ( / is too small) or the drive is full of junk.  Just another reason to download the LiveCD iso and start from scratch.

Information to get you started here:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Chris.

---

### Post by hollysc on 2012-01-07
ok I went to download the ubuntu and it won't because there isnt any room.  If I were working on my laptop or desktop I would know what to delete, but I don't recognize the same files on this mini.  Can I delete Ubuntu?  Or Grub or do I go into system files  like .bin

---

### Post by wildmanne39 on 2012-01-07
Hi, if youi delete system files or grub you will break the system, plus you can not do that without fixing your password issue.

Do you have another computer you can use to dowload ubuntu with? and if it is a very old computer you may want to use lubuntu or xubuntu they will run better on an old computer, if you have fixed your password issue you can post the results of this command:
```
sudo lshw
``` 
```
cat /etc/lsb-release; uname -a
```
and we can tell you if the latest ubuntu will run on it.
Thanks

---

### Post by hollysc on 2012-01-07
Ok, I am not really as dumb as a brick, I just feel like it LOL   The mini has GNOME   Fluendo  Ubuntu and Grub?   it is an N series (which I don't think really means much)  It says disk is 100% full and I don't care if I erase everything that is currently on it I just would like to be able to use it.  So folks any help at all.  It says it is Ubuntu 8.04 released in april 2008   I hope this information helps.  and I will try the codes you posted   thanks

---

### Post by wildmanne39 on 2012-01-07
Hi, > Do you have another computer you can use to dowload ubuntu with?if you do download lubuntu livecd and use it to reformat the drive and install.
Thanks

---

### Post by Bartender on 2012-01-07
Unbuntu 8.04 is out of date.  There's no support for it anymore.  Even more reason to do as others have suggested.  Wipe it and start from scratch.

There are about a million posts and YouTube videos and tutorials for installing Ubuntu.  If you can, get a geek friend with a fast connection and a modern machine to help you download a version of Ubuntu, then make the bootable CD.  You may want to go with 10.04, the LTS release, which will be supported until April 2013.  

Because of the controversy over Unity and GNOME3, it's hard for me to say what you should go with.  Some think Xubuntu is preferable to Ubuntu because the Xfce desktop isn't Unity & it's not GNOME3.

I liked Steven J. Vaughn's recent [article]("http://www.computerworld.com/s/article/9222979/Fedora_Mint_openSUSE_Ubuntu_Which_Linux_desktop_is_for_you_").  It might help you decide which distro to try.

Anyway, the install you have now, even if it was working right, isn't supported and needs to be replaced.

This [video]("http://www.youtube.com/watch?v=7IK35nZuTlk") shows a Mint install.  It'd be better with some vocals, but it's an example of what's out there on YouTube.  Of course, this video is only helpful AFTER you've downloaded and burned a Mint LiveCD, then booted from it!

---

### Post by fabricator4 on 2012-01-07
> **hollysc said:**
> ok I went to download the ubuntu and it won't because there isnt any room.  If I were working on my laptop or desktop I would know what to delete, but I don't recognize the same files on this mini.  Can I delete Ubuntu?  Or Grub or do I go into system files  like .bin

Go to the Home folder and see if the previous owner has left all his junk in there.  With a bit of luck you'll be able to delete enough files and dross that you will be able to download Ubuntu. and burn the ISO.

If that fails you should be able to download directly to a USB stick or similar.

You'll to clear enough space to save the 700MB ISO file to, plus a bit more because the operating system would probably appreciate a few hundred MB to work in.

If you did get the password for the admin account it would give you a few more options, such as delete all the .deb installation files out of /var/cache/apt/archives and uninstalling and old kernels (but NOT the current kernel which is required to boot the machine.

Once you've downloaded the ISO you should really check the md5sum on it to be sure the file is good before you burn it.  This could save you untold hours of pain and misery if by some slim chance the download gets corrupted.  It only takes a minute to test the file and instructions for checking the MD5sum are here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Chris.

---

### Post by hollysc on 2012-01-07
I finally just gave up!  I downloaded onto the thumbdrive and tried to open that or load it into the mini, nothing.  It still says the disk partition is 100% full and I still can't find how to get some free space.  I give and will just stick with windows and my laptop.  thanks for all your help though

---

### Post by wildmanne39 on 2012-01-07
Hi, I am sorry to hear that.

---

### Post by fabricator4 on 2012-01-08
> **hollysc said:**
> I finally just gave up!  I downloaded onto the thumbdrive and tried to open that or load it into the mini, nothing.  It still says the disk partition is 100% full and I still can't find how to get some free space.  I give and will just stick with windows and my laptop.  thanks for all your help though

You can't just boot off the USB that you copied the ISO to, you have to make a bootable USB out of it first:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Just install Unetbootin and use it to make a LiveUSB out of the ISO you have already downloaded.

Chris

---

### Post by mörgæs on 2012-01-08
> **hollysc said:**
> I finally just gave up!  I downloaded onto the thumbdrive and tried to open that or load it into the mini, nothing.  It still says the disk partition is 100% full and I still can't find how to get some free space.  I give and will just stick with windows and my laptop.  thanks for all your help though

Since you have another computer available it is really a simple process. There is no need for giving up so early :-)

First: Download the ISO to the Windows computer. The file should be around 700 MB. Let us know when that is done.

---

### Post by Bartender on 2012-01-08
> **hollysc said:**
> I finally just gave up!  I downloaded onto the thumbdrive and tried to open that or load it into the mini, nothing.  It still says the disk partition is 100% full and I still can't find how to get some free space.  I give and will just stick with windows and my laptop.  thanks for all your help though

Use your laptop to [download Ubuntu ]("http://www.ubuntu.com/download/ubuntu/download")
 Install a free program called [ImgBurn]("http://www.imgburn.com/").  You need that program or something similar to create a bootable CD from the download, which comes in the form of an .iso.  ImgBurn will recognize that it's an .iso and make the bootable CD.  Burn it at 4X or so, not maximum speed.  Pop the CD in the Dell.  You'll have to make sure that the Dell will boot from the optical drive, or find the button that gets you to the boot-up device menu while the PC is starting.

---

### Post by critin on 2012-01-08
> **hollysc said:**
> I finally just gave up!  I downloaded onto the thumbdrive and tried to open that or load it into the mini, nothing.  It still says the disk partition is 100% full and I still can't find how to get some free space.  I give and will just stick with windows and my laptop.  thanks for all your help though

You are overthinking this.  Use your other computer and download the OS you want to use.  Visit You Tube 'linux reviews' and watch a few, there are some great ones.  Insert your thumb drive, open unetbootin,  (you are using unetbootin, right?)  Browse to the IOS you downloaded and create it from unetbootin.  Boot the other computer from the thumbdrive and choose Try.  After looking around and deciding it's the os you want, choose Install and let it do its thing.  When it gets to the part asking you to chose partitions, choose --erase and use entire disk.

 > I downloaded onto the thumbdrive and tried to open that or load it into the mini, nothing.

How did you do this--the procedure?  I've not tried to make a bootable live os this way though it probably can be done.  You don't just 'load' to install, it must be booted up by the thumbdrive.  Netbootin is much easier.

You don't need space to run the live thumb drive or live cd.

---

### Post by sailor2001 on 2012-01-08
[www.RenewablePCs.com](www.RenewablePCs.com)

---

