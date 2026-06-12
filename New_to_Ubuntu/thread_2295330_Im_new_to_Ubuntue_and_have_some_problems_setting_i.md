---
title: "Im new to Ubuntue and have some problems setting it up."
date: 2015-09-17
forum: New to Ubuntu
---

### Post by immanuel3 on 2015-09-17
Hi, 
I have been using Mac and Windows for all my life. And decided to install Ubuntu about an hour ago, everything went great except for two problems I am experiencing.

Problem 1:

When trying to set my screen resolution and get my duel monitors set-up, I go to System-Settings >> Display.
But for some bizarre reason the window just crashes when I press on the "Display" icon and displays an error: "Ubuntu has experienced an internal error: ".

Problem 2:
This is the more serious problem I have previously been running windows 8.1 on my PC, so I basically installed Ubuntu as the only operating system and totally wiped win8.1.
I was planning on installing Ubuntu on my C drive which is an SSD and leaving my D drive for all my files like I did with win8.1.
When installing Ubuntu I had an option to install or create NTFS when installing Ubuntu(I forget exactly what the exact words where ). And I set my C drive (SSD) as my bootable drive.

Now when ever I try to access my D drive in "Files" I get this error:

Error mounting /dev/sdb1 at /media/immanuelsegol/C6B01678B0166F65: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/immanuelsegol/C6B01678B0166F65"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


I have no idea how to fully shut down windows lol :confused: :confused:. Because its not supposed to be installed! 

What have I tried to do to fix it:
1) I spent about an hour browsing forums and I cant find any solution that helped me. All the solutions involved a duleboot system.
2) I have tried to reinstall windows and Ubuntu but im unable to get access to my windows disc or my Ubuntu USB. So I cant reinstall Windows or Ubuntu.

I feel totally lost on this one.
What I really want to be able to do is install Ubuntu on my SSD and have my Hard drive totally empty for storing files.
Any help will be sooooo appreciated!!
Thank you in advance!

Update:
I don&#8217;t know if this was a good idea but I formatted my HDD and it seems to work fine I can access it and add folders and files.
Was that the proper thing to do?
My first problem is still not fixed and I cant seem to find anything about it online.

---

### Post by Geoffrey_Arndt on 2015-09-17
Well, it is nearly impossible to help with the zero information you have provided.   

What is:

>  make and model of PC?
>  what cpu?
> video system - what does PC have? (provide as much detail as possible)
>  what amount of ram?
>  Size of each hard drive (and perhaps a screen print of your partitions (using the program gparted for instance)

If your video is Intel - - probably no need to install video proprietary drivers, but for other types (amd/ati, nvidia) . . . installing the proprietary driver via "system settings>software & updates>additional drivers (tab)" may resolve your problem.

---

### Post by immanuel3 on 2015-09-17
Hi Arndt,
I'm using a 64 bit custom build PC.
Processor: Intel i7 4970k 
GPU: gtx 970
Ram:8 GB
X1 SSD : 128gb
X1 HDD : 1TB
Motherboard: GA-Z97P-D3
2 screen's
Was previously running Win8.1 64bit

I have attempted to install drivers using the terminal then when I reboot my PC just shows "starting version 219"
Thank you!
Sorry about any spelling it's 12:00pm here lol and I'm on my phone.

Should I just delete all partition's? Before I install.
Sorry for all these questions I'm just kinda stuck &#65533;&#65533;

---

### Post by yancek on 2015-09-17
The error you are reporting when trying to access the external drive is because you had windows installed and the default is to always hibernate so that it appears to take less time to reboot.  I don't use windows but, from what I have read here and elsewhere, you may have options in the BIOS for such things as Fast Boot or anything to do with hibernation.  If you can disable that you might be able to access the drive partitions.  Otherwise, hope someone else who uses windows has a suggestion.

---

### Post by Geoffrey_Arndt on 2015-09-17
When installing Ubuntu, you should not have a prompt or window to install any windows file system (ntfs).    Need to specify ext4 as default file system.      

If you have all your data saved off to flash media, you can do an install on ssd where on install, you can specify the whole disk for Ubuntu (and then let grub install to sda).

Then, make sure you have internet connection during install, and tick yes re installing restricted software (I don't recall exact wording).    Also, it's best to use the Ubuntu tools & gui to do the gpu drivers install . . . "systems settings>software & updates>additional drivers tab.     This ensure use of official buntu repo drivers versus the drivers as packaged by nvidia.

Assuming you don't want dual-boot, the above should work, but if you do want dual-boot, the reinstall procedure is totally different.

---

### Post by immanuel3 on 2015-09-18
Ok , yes I do not want to dule boot. I reinstalled Ubuntu and edited my partitions removing all of them on my D drive and only allocating 3 GB on my SSD(C drive) as Swap everything boots fine. But the same errors still appear as i described
In problem 1in my first post.
I will post images of my error message and my System property's.

Hi,
I will try to explain my problem in a bit more depth:
1 ) I boot up my PC and Linux prompts me to log after logging in I immediately get this error:
[ATTACH=CONFIG]264476[/ATTACH]

This is what the error detail's look like:
[ATTACH=CONFIG]264477[/ATTACH]

Now after I get that error I attempt to change my screen resolution and set up my Duke monitors.
This is what my screen looks like when I first bootup:
[ATTACH=CONFIG]264478[/ATTACH]

As you van see they are identical and the mouse movement is mirrored in them both, and the resolution is very low. So in order to fix that I go to the Systems-Settings >> Display when I press the Display Tab the same error that shows right after bootup shows up again.
At first I was sure it was a driver issue so I go to my software-updates >> Additional driver's, which looks like this:
[ATTACH=CONFIG]264479[/ATTACH]

When ever I choose another option other then the default my system totally crashes right before it enters the log in screen.

Additional images:
D drive:
[ATTACH=CONFIG]264480[/ATTACH]
C drive:
[http://i.imgur.com/qmcwVFC.jpg](http://i.imgur.com/qmcwVFC.jpg)


System properties:
[http://i.imgur.com/75YN8HV.jpg](http://i.imgur.com/75YN8HV.jpg)

Thank you for all the help so far!

---

### Post by QIII on 2015-09-18
immanuel3:

Please don't post large images by pasting them in to the body of your text.  There are users here who have slow connections and data transfer limitations.  You can actually cost people money by putting a lot of large images in your post.

Please edit your post by clicking "Edit Post" and then "Go Advanced", delete the large images and use the attachment functionality (the paper clip in the toolbar above the text entry box), which will create thumbnails that other users can click to enlarge if they choose.

Thanks!

---

### Post by immanuel3 on 2015-09-18
Sorry I posted this using my phone.

---

### Post by QIII on 2015-09-18
I'll fix it for you this time, but next time you owe me doughnuts.  :)

---

### Post by QIII on 2015-09-18
Ah!  5 images per post is all that are allowed.

I've left the imgur urls for the other two.

---

### Post by immanuel3 on 2015-09-18
Can anyone help me here?

Thank you QIII!

No one ran in to this problem yet?

Dose anyone know if this is a driver problem?
Or am I not installing it properly?

---

### Post by sotiris2 on 2015-09-18
So when you choose the nvidia driver it installs, you reboot and get a blank screen? I think setting nomodeset would solve this. Install the nvidia driver but don't reboot. Open a terminal (Alt+Ctrl+T) and paste this command in (paste in terminal is **SHIFT**+ctrl+V) > sudo nano /etc/default/grub It will ask for your password. Input (nothing will show in the screen while you input but it 's ok) and press enter. Use the arrow keys to move the cursor and find the line **GRUB_CMDLINE_LINUX_DEFAULT="stuff stuff"**. Add nomodeset to that line inside the quotes. Press Ctrl+X to exit and Y to save changes. Paste the following on the terminal > sudo update-grub When it's done you can reboot and it should work. 

In regards to your D drive. You **formatted** it to ext4 so it is now empty. If this is not what you wanted please don't do anything with it and await recovery instructions to recover your data.

---

### Post by immanuel3 on 2015-09-18
OK let me try that, thank you for helping I was losing hope that some one would reply.

OK so here is what I did.
Unfortunately I rebooted after installing the drives cuz I did not yet read your comment.
1) I installed nvidia drivers ([https://youtu.be/uGoBn1QNvuI](https://youtu.be/uGoBn1QNvuI))

2) I followed your instructions but I did reboot after the drivers where installed, and I was forced in to low graphics mod. I used all the commands you posted and all went well.
[http://i.imgur.com/KvRbCUX.jpg](http://i.imgur.com/KvRbCUX.jpg)

3)Here is where things get weird again.
My system boots normally and only uses one screen so it looks like my drivers work.
But this happens:
[https://youtu.be/ZF-0ywadsTY](https://youtu.be/ZF-0ywadsTY)

I log in and it dose not work, I used the on screen keyboard as well and it just seems not to work.


What should I do now?
And about the D drive its totally fine I want it empty.
Thank you for helping! 
This is making my head explode but when I'm finally able to get it running I will have a pretty go understanding of Linux hopefully.

---

### Post by sotiris2 on 2015-09-18
The error message is "systemd-udev: failed to apply ACL on /dev/dri/" (cuttoff in the video).  

I see a bug report for this or something similar [here](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/1406947) but I don't see a definitive answer. Some posts suggested adding a repository with newer version of the drivers but they were old and the drivers then referred are the same as the ones on your system. 

If you unplug the second screen can you reboot and login?

---

### Post by immanuel3 on 2015-09-18
No I tried that :(  and still there is a loop.
Do you think I should just reinstall for scratch?

---

### Post by sotiris2 on 2015-09-18
I am not sure that reinstalling will totally fix it (in the sense that you will be able to install nvidia drivers and get them to work properly with 2 screens). If you want it to just work like it did before installing the nvidia driver you can go into tty1 (alt+shift+F1) instead of logging in the graphical interface and issue > sudo apt-get purge nvidia-* and maybe after > sudo apt-get install xserver-xorg-video-nouveau and reboot. That should get you in the initial situation. Otherwise a reinstall might be good.

---

### Post by immanuel3 on 2015-09-18
OK let me try

Its unable to install xorg properly so I'll just do a fresh install

OK this is good I think!
I was able to boot properly.
[http://i.imgur.com/1h4EyEE.jpg](http://i.imgur.com/1h4EyEE.jpg)

Can you please guide me from here ?
Do I just go install the nvidia drivers and then put the commands you first sent me in to the terminal and reboot?
And should I just ignore the error?

Anyone else ?

---

### Post by immanuel3 on 2015-09-19
Hi, 
OK so I finally got it to work people.
Thank you so much for helping!!
I will make a guide for how I did it because it seems that I was experiencing a unique problem.

---

