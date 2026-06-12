---
title: "Need installation help"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by Dobbes on 2012-07-26
I have an extra laptop that didn't have a legit copy of windows 7 on it so I thought I'd give Ubuntu a try on that.
So I got it all installed using the Windows Installer that they provide, and after it was installed I used the OS-uninstaller tool to delete windows 7 all together. But the one thing I forgot to do was to change/edit/fix the boot thing to where it will boot to Ubuntu automatically. and now it wouldn't boot properly, saying that "Bootmgr" doesn't exist or something along those lines.
I then got the LinuxLive USB Creator in attempt to make a "Boot disk" out of my USB drive (Which the original windows installer was in the beginning) 
I got the computer to boot using the USB drive, and when it asked to install Ubuntu again I said "Sure"
After it finished installing it asked for me to reboot the computer so I did, and whenever it starts up the computer just gives me a blank screen, no text or anything, just a blank screen and a little line blinking at the top. I waited about 10 minutes to see if it was doing something but nothing happened. I restarted the computer and went into the bios and told it to boot with diagnostics, Which was a huge mistake. Whenever I restart the computer it does the diagnostics check and doesn't come up with any errors, but I can't get into the bios. If I am fast enough I can boot off my USB stick but that just runs ubuntu OFF my USB stick, which is where I think the computer installed it all.

How can I boot the computer normally and installed Ubuntu 12.04 Unity without breaking it more, I have no experience in this kind of thing thinking it would be easy, and I just messed it up more, so I am asking for help from people who know what their doing.
Please help, I'd love to delve deeper into Ubuntu.

---

### Post by anewguy on 2012-07-26
What is the make/model of the PC?  What wireless and video is it using? (you may have to check the manufacturers website for some of this info).  What are the specs of the PC?  Does it meet the minimum requirements?

---

### Post by daslinkard on 2012-07-26
When you are able to boot up through the USB are you able to get to the option of trying Ubuntu versus Installing Ubuntu?  If so I would recommend selecting the "Try Ubuntu" and once the OS loads you should be able to see on your desktop where you can install 12.04.

At this point in time you're going to have the options of what you want to do, if you want to upgrade, run along with another OS, etc.  Here you'll be able to select Ubuntu 12.04 as your sole OS and should re-install and get your squared away.

Good Luck!

---

### Post by Dobbes on 2012-07-26
@anewguy - It is a Lenovo T61 I believe, and I'm sure it can run it because when I first started off it ran fine.
My computer was connected to a wired connection

@daslinkard - When I first booted it with the USB drive it asked if I wanted to try or install and I chose install, I guess thats where I messed up?
When I boot it up with my USB drive it just starts Ubuntu normally only it is very slow as if it is running a lot of things (Or running off a USB drive lol)

---

### Post by daslinkard on 2012-07-27
No worries....I think that if you bring it back up in the try mode and then select the install from the desktop I think you'll be much better off.  In looking at the specs of the PC, the age of the PC should be fine in handling Ubuntu.

Like I said earlier, try Ubuntu, then install from the desktop and see if that gets you going.

---

### Post by Dobbes on 2012-07-27
> **daslinkard said:**
> No worries....I think that if you bring it back up in the try mode and then select the install from the desktop I think you'll be much better off.  In looking at the specs of the PC, the age of the PC should be fine in handling Ubuntu.

Like I said earlier, try Ubuntu, then install from the desktop and see if that gets you going.

Well the issue I am having is that, that option doesn't come up anymore, It just starts Ubuntu off of my USB drive and won't boot unless I tell it to boot off of the USB drive.

---

### Post by daslinkard on 2012-07-27
When you boot off the USB and the Ubuntu desktop appears there should be an image on the Desktop that when you hover over it says Install.  Do you see that option?  This should give you the option again to install Ubuntu.

The option that I have seen work in the past would be to reload Windows and then proceed forward with re-installing Ubuntu.  This could be very time consuming and it might not be something that you want to do.  However, installing Windows over the system will get the remnants of the Linux OS gone and then will allow for you to do a fresh install of Ubuntu.

---

### Post by Dobbes on 2012-07-27
> **daslinkard said:**
> When you boot off the USB and the Ubuntu desktop appears there should be an image on the Desktop that when you hover over it says Install.  Do you see that option?  This should give you the option again to install Ubuntu.

The option that I have seen work in the past would be to reload Windows and then proceed forward with re-installing Ubuntu.  This could be very time consuming and it might not be something that you want to do.  However, installing Windows over the system will get the remnants of the Linux OS gone and then will allow for you to do a fresh install of Ubuntu.

There is nothing on the Desktop, no icons except Terminal, which I put there myself.
I'd rather not do a windows installation since the first copy of windows on this laptop was not genuine and I don't have that copy anywhere else.

---

### Post by daslinkard on 2012-07-27
Maybe someone else has a suggestion....I understand not wanting to put Windows back on as it would be a pain on all accounts.

---

### Post by mastablasta on 2012-07-27
> **Dobbes said:**
> So I got it all installed using the Windows Installer that they provide, and after it was installed I used the OS-uninstaller tool to delete windows 7 all together. But the one thing I forgot to do was to change/edit/fix the boot thing to where it will boot to Ubuntu automatically. and now it wouldn't boot properly, saying that "Bootmgr" doesn't exist or something along those lines.
.
 
so you used wubi (windows installer) to install Ubuntu inside windows and then you removed windows?!? ofcourse it won't work! you instilled it inside the operating system and then removed the operating system.
 
and you also believe you installed it to usb rather than to hard disk.
 
easy solution - get a new live media (live USB, live CD) to boot from it in live session (use the installed version to donwload it and burn it, download it elsewhere at a friend and burn it, order it by mail...) and run install. 
then format the hard disk and install it porpperly as a single linux OS.
 
here is an install how to: [http://www.psychocats.net/ubuntu/installing/](http://www.psychocats.net/ubuntu/installing/)

---

### Post by Dobbes on 2012-07-27
> **mastablasta said:**
> so you used wubi (windows installer) to install Ubuntu inside windows and then you removed windows?!? ofcourse it won't work! you instilled it inside the operating system and then removed the operating system.
 
and you also believe you installed it to usb rather than to hard disk.
 
easy solution - get a new live media (live USB, live CD) to boot from it in live session (use the installed version to donwload it and burn it, download it elsewhere at a friend and burn it, order it by mail...) and run install. 
then format the hard disk and install it porpperly as a single linux OS.
 
here is an install how to: [http://www.psychocats.net/ubuntu/installing/](http://www.psychocats.net/ubuntu/installing/)

That guide you linked seems to be useful, I just wish all the images weren't broken so I could see what they are talking about. I am working on putting another LinuxLive on my USB, but I don't know if I'm retarded or not, but your instructions aren't very clear.

---

### Post by Dobbes on 2012-07-27
I think I fixed it, I booted with my USB drive and used Boot-Repair, Apparently ubuntu was installed on the computer but all the boot info was on my USB drive, so after Boot-Repair did its thing it works normally
[http://paste.ubuntu.com/1114334/](http://paste.ubuntu.com/1114334/)

Does anyone know if there is a way to edit the BIOS info without getting to the BIOS screen? Cause I can't anymore.

---

