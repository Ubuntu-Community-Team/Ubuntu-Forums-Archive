---
title: "Greetings! new user here. A couple general questions before I go forward."
date: 2014-03-31
forum: New to Ubuntu
---

### Post by miek2 on 2014-03-31
Just wanted to say Hi / introduce myself. I have been a long time windows customer but recently windows 7 failed on me and I figure it was the perfect opportunity to try a free operating system (as I don't love the windows 8 interface).

I build my own pc's - currently on a 64bit amd phenom. I booted 12.04 from a usb without issues. things are running (I wish i could say smoothly). I'm doing my best to read and self-educate from the forum.

So far I had a couple of questions

1) is there an ideal partition / swap arrangement? I am running off a 60gb SSD of which I allocated 2gb to swap. the rest is the OS. Anything wrong with that picture??

2) Firefox, Ubuntu Software Center, both will cause the os to crash at times (all the windows disappear and there is no way to maximize/minimize/log out / restart and i am forced to do a hard reset on my machine (Which i read can be damaging to the OS/files).

3) Is there any downside to downloading of of the other interfaces (xubuntu or kubuntu) before i get everything stable or should I play around with ubuntu first? 

4) I have had no luck installing dedicated gfx for my radeon hd 6850 or my brother mfc 295cn printer. I tried acouple walk throughs but often came to some sort of error during installation with permissions, etc.

I'm sure I'll get the hang of this soon (If i don't its probably back to windows : /). 
Thank you for all who have posted on this site and the community overall. The linux community is certainly a special thing - I wish I got into this a few years ago when I had more time and the attention span to learn !!

Mike.

---

### Post by Mk32 on 2014-03-31
Welcome to the forum!

Swap space is something you may not have to worry about. It depends on how much RAM your system has. My ThinkPad has 6GiB and I've been watching its usage for a couple of months now, and it has never gone over 1.5GiB. (Right now it's using 734MiB of 5.74GiB, which is about average.) Swap -- actually, I stopped monitoring it because it wasn't using any. 

On the other hand, if you're stuck with 1GiB of RAM, you will need swap. Most people say the swap partition should be equal to the size of your installed RAM base. Swap is used if the Live CD detects the HDD has a swap partition available. (Mine has 4GiB set aside, something I may change in the future to zero. It triple boots, and I've been making heavy use of Windows 7 recently.)

Thus, if you have 8GiB of RAM and are running a 64 bit version, I wouldn't even bother with swap at all. 

Now, if you say you're booting from USB, did you $ dd the Live CD iso onto the thumbdrive and boot that way, or did you install onto the thumbdrive? Any kind of hard-reset, crashing of the Software Center or other things hints to low-level trouble.

---

### Post by quadrplax on 2014-03-31
I read somewhere that your swap space needs to be greater than or equal to you're RAM size in order to use Hibernate, so if you want to be able to do that, and it works on you're computer, then swap space could be a good thing to have.

---

### Post by miek2 on 2014-03-31
Thanks Mk32 - I have 8gb ram. In terms of the install - I used the tool to create a bootable thumb drive (ubuntu website). I'm actually on my third iteration of the install because i feel like I botched the first two stubbornly trying to get drivers working. So far its working well (I updated the OS and updated any programs using the synaptic package manager. Fingers crossed it lasts.

---

### Post by Mk32 on 2014-03-31
Mmmm. Hibernation. SSDs. They say not to mix the two. 

Seeing that you must be new to Linux, or at least Ubuntu, I'll toss you some of the applications I install: 

- Okteta: hex editor
- Screen Ruler (use the middle mouse button to rotate it 90 degrees...weird)
- Debian Live Magic
- ConvertAll
- GIMP...ish. It is really cramped on my 12.5" display (1280x800). GNU Paint is a little simpler but lacks Undo and is a little too basic. 
- Pidgin Instant Messenger
- FileZilla
- Audacity
- VLC
- 10.04 comes with OpenOffice, I forgot if 12.04 does not. 12.04 didn't last long with me :)
- GParted -- awesome partition tool


I have the full list on my iMac G4, which I can't access right now. Mostly CLI stuff like Netatalk, conky, vnstat, curl, stuff like that. I am mildly allergic to CLI stuff.

**EDIT:** Oh yeah. I use a 8GB thumbdrive partitioned into a 2GB thumbdrive part and ~6GB 10.04LTS. Because I work with Macs it has uudeview, macutils, Netatalk 2.1.6, etc on it. Neat. Emergency bootable OS and still has a universal FAT32 volume.

---

### Post by miek2 on 2014-03-31
12.04 came with libreoffice... how does that compare with open office?

---

### Post by PondPuppy on 2014-03-31
I've only used Libre. The review on  [http://andybrandt531.com/2013/09/libreoffice-apache-openoffice-taught/](http://andybrandt531.com/2013/09/libreoffice-apache-openoffice-taught/) says the programs have not diverged much since Libre was forked from Open, so it's almost a coin toss as far as features go.

---

### Post by mastablasta on 2014-04-01
> **miek2 said:**
> 2) Firefox, Ubuntu Software Center, both will cause the os to crash at times (all the windows disappear and there is no way to maximize/minimize/log out / restart and i am forced to do a hard reset on my machine (Which i read can be damaging to the OS/files).

that is not normal. make sure you check the md5sum after download and before creating the USB. you cna try other usb creators such as unetbootin or linuxliveusb.

hard reset in linux is very rare. before doing it try ctrl+alt+F1 (thorugh F6) to get into CLi console, then login and then shutdown or reboot the computer via command (e.g. sudo shutdown -r will reboot it)

another option is REISUB command (soft/safe reboot) : [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

> 
3) Is there any downside to downloading of of the other interfaces (xubuntu or kubuntu) before i get everything stable or should I play around with ubuntu first? 
No they are all fine versions of Ubuntu with different desktop environment.
> 
4) I have had no luck installing dedicated gfx for my radeon hd 6850 or my brother mfc 295cn printer. I tried acouple walk throughs but often came to some sort of error during installation with permissions, etc.


this is how you install the drivers: [http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers](http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers)

> 
I'm sure I'll get the hang of this soon (If i don't its probably back to windows : /). 


file permissions in linux are there for a reason (a security layer). Windows doesn't have them so it is very easy for users to to run and install drivers. it is also very easy to install malware. ;-)

---

### Post by oldfred on 2014-04-02
If you cannot get to a terminal and shutdown from that remember the Elephants.

       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

My 64GB SSD has two / (root) partitions, one currently 12.04 and one soon to be 14.04. I have all data on rotating drives and testing 14.04 on a partition on rotating drive. 

I once installed Kubuntu desktop on my Ubuntu Desktop. But things got mixed up. There are some KDE apps like KmyMoney, K3b and others that I want, so I could not just uninstall Kbuntu as it uninstalls everything. Often better just to create another 20 or 25GB / partition and use that for testing or experimenting. Keep working install clean and working well.

One advantage of Linux is the choice of desktops.
One disadvantage of Linux is the choice of desktops.

I prefer full Ubuntu, but do not like Unity as my monitor is an older 4:3 and I like the menus and top & bottom panels. So I installed fallback or flash back which is similar to the old gnome2 look. Have not tried that yet in 14.04 to see if it still works. Several threads on issues with that during testing.

---

