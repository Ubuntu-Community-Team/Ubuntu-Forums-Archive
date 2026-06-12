---
title: "Use GUI from Unbuntu Install CD instead of terminal"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by aka-John99 on 2011-11-21
I attempted to follow instructions from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I  succeeded in burning the iso Cd and used it but instead of the fancy  GUI shown in the download page I am only getting a terminal interface. 

[LIST]
[*]Is there a common reason for this e.g. is it likely to be due to a corrupt iso image, 
I did not do a checksum check
[*]is there a simple method of going into the GUI from the terminal 
"exit" just redisplays a command line interface
[*]not sure that i am able to display manpages fully and correctly, probably need to pause/scroll or change screen resolution
[/LIST]
I  have found [http://manpages.ubuntu.com/](http://manpages.ubuntu.com/) but have not really had time to  try to look through it, and in any event want some sort of novice advice  not notes on eacjh and every command. I did install the browser search  plugin in Firefox Windows, but not sure that is working properly  returning** "*[B]No matching titles found - Full text search results below**"*[/B]  but not then giving anything else - probably a problem with Firefox, will look at it again later.


:confused:Total novice
Using a Windows PC with old Athlon cpu, and ca 1GB RAM
Many years ago I did dabble with unix, and have used DOS & even C

Once I learn more about Unbuntu I may well consider changing one or more of my computers to dual boot

---

### Post by fantab on 2011-11-21
> **aka-John99 said:**
> I attempted to follow instructions from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I  succeeded in burning the iso Cd and used it but instead of the fancy  GUI shown in the download page I am only getting a terminal interface. 

[LIST]
[*]Is there a common reason for this e.g. is **it likely to be due to a corrupt iso image, **
I did not do a checksum check
[*]is there a simple method of going into the GUI from the terminal 
"exit" just redisplays a command line interface
[*]not sure that i am able to display manpages fully and correctly, probably need to pause/scroll or change screen resolution
[/LIST]
Yes, it is possible that you have corrupt or incomplete .iso. Was it a torrent download or direct download? Do that checksum check to confirm.
If need be download it again and burn the .iso to disk at the slowest possible speed. Try again.

Good Luck.

---

### Post by westie457 on 2011-11-21
It is also possible that you downloaded an iso for the server edition or the alternate install. AFAIK neither of those has the GUI installer.

The alternate install will give you a desktop when the install completes. The server install will not.

If all you did was click on the big download button then do as fantab suggested

---

### Post by ajgreeny on 2011-11-21
It is definitely worth downloading with a torrent client, as that checks the file integrity as it downloads.

I can't help you with how to do that in windows as I have no windows to use any more, but I know there are many torrent clients available.

---

### Post by Hylas de Niall on 2011-11-21
> **ajgreeny said:**
> It is definitely worth downloading with a torrent client, as that checks the file integrity as it downloads.

I can't help you with how to do that in windows as I have no windows to use any more, but I know there are many torrent clients available.

'utorrent' is about the best and simplest (and very small) on Windows.

[http://www.utorrent.com/](http://www.utorrent.com/)

---

### Post by mastablasta on 2011-11-21
did you get terminal or GRUB?
 
If terminal it is quite possible that graphics card is not supported. or it is supported btu something went wrong on boot (it happened to me on older mashine)
 
i think 
```
 
startx 

``` 
command should start the interface.
 
or i think unity uses this to start: 
 
```
 
service start gdm


```
 
if you get the first picture where you select what you want to do (try it, install etc.) this is GRUB menu (bootloader). if try it takes you to terminal you can start the above commands. additionally you might try one of the boot parameters found in the GRUB menu (such as nomodeset, xforcevesa etc.). 
 
some mashines just don't want to get to live session but can work well when you install it to them it really depends. with more data on your hardware people here oculd tell you how it stands with Linux compatibility.

---

### Post by aka-John99 on 2011-11-21
Thanks for the replies. I have not yet tried the checksum or re downloading, but have had a quick look at the linked beginners guide and some of the other documentation. Another problem is that this ageing computer has only 1GB of RAM and will not upgrade further, I do however hope to  be able to use a newer machine early next year.

I will post back with progress report in due course, but it may be a while before I have spare time to try this. I may try using Wubi to see if it runs that way (especially if that allows me to run with additional files on an external hdd)

---

### Post by aka-John99 on 2011-11-22
I will mark this as solved. Not entirely sure what problem is/was possibly system incompatibility, it is at least booting into GUI on Netbook LTS version of the CD.

I did the downloads with Firefox, and guess it has at least rudimentary error checking on downloads. I did get round to MD5 checksum and they agreed with posted values. The CD burner also ran a verification on the disk images. I tried the Netbook version of Lucid, presumably that may be slightly easier to run and it does open the Gnome desktop.

Thanks again for the replies.

---

### Post by aka-John99 on 2012-01-19
I have two presumably related problems.
I have just about given up on the Ubuntu on the legacy desktop.

[B][U]Installing Ubuntu
[/U]( background info only here,  see thread for full detail 
[http://ubuntuforums.org/showthread.php?t=1907850](http://ubuntuforums.org/showthread.php?t=1907850)
[/B][COLOR=#980101]**[ubuntu]**[/COLOR]                          [Installing 32 bit LTS Lucic on 2nd HDD 2nd primary partition]("http://ubuntuforums.org/showthread.php?t=1907850")  )

I seem unable to make CD that then passes integrity check on that machine.

[LIST=1]
[*]obtain iso file, do checksum verification
[*]burn is file to cd on the legacy desktop
[*]IF I can get the CD to boot try internal integrity check option it fails with message about one errors
[*]take same disk, put it in another machine and it seems ok
[LIST]
[*] run internal integrity check it passes
[*]will even install and run on another machine
[/LIST]
 
[/LIST]
_**THIS THREAD Unreliable Booting or CD not booting at al**_

I suppose it stands to reason the CD will not work and install if it fails the integrity test, but then why will it work on another machine?
Is it an indication the CD reader is not working correctly ?
At some stage  I could manage to borrow a working CD RW drive from another computer to see if that helps.

Any other ideas ?

I have currently installed Debian on the troublesome desktop. I may return to investigate the problem  some stage.
The last time I tried to boot a Lucid LTS live CD error message seen was something like:
BusyBox v1..13.3 ...
(initramfs) mount:
mount is /dev//loop0 on //filesytem.squashfs 
failed: input/output error    cannot mount dev/loop0   (/cdrom casper filesquasfs)
on //filessytem.squasfs

I scrawled the above on a scrap of paper ! should have tried to copy it.
I do not understand the message but guess it is telling me the application files did not mount and so it is reverting to a simplified CLI terminal

---

### Post by mastablasta on 2012-01-19
you could be able to install by maybe using Alternate CD (which uses text mode to guide you).
 
yes it could be the drive i malfunctioning. 
 
Can you use a USB key? if so you can boot from it. create a live usb using Linuxliveusb or Unebootin
 
If computer can't set the BIOS to boot from usb you can use PLOP boot manager to do it.
 
1GB RAM is more than enough for smooth linux experience. 512 MB also but with a lighter desktop.

---

### Post by aka-John99 on 2012-01-21
mastablasta Thanks for the reply.

Not continuing with this at present until
- I have a reliable CD drive (it has a cd drive and a dvd drive already unlikely both are faulty)
- I have checked out PSU, that is possibly getting hammered booting up from a CD, so I will check the 12V & 5V actual voltage levels may then be thinking of installing an additional psu. (Could also temporarily disconnect power to unused hdd and cdd/dvd for a trial  ) 

> **mastablasta said:**
> you could be able to install by maybe using Alternate CD (which uses text mode to guide you).
 
yes it could be the drive i malfunctioning. 
 
Can you use a USB key? if so you can boot from it. create a live usb using Linuxliveusb or Unebootin
[COLOR=YellowGreen]No, bios will not boot direct from USB,and it is USB version one, so unsuitable[/COLOR]
 
If computer can't set the BIOS to boot from usb you can use PLOP boot manager to do it.
 
1GB RAM is more than enough for smooth linux experience. 512 MB also but with a lighter desktop.
[COLOR=YellowGreen]I have max MoBo allows 1GB, but some of that is taken by integrated graphics.[/COLOR]


---

