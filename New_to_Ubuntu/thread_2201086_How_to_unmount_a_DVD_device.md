---
title: "How to unmount a DVD device?"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-01-22
[visually impaired] How does one unmount a DVD device in Terminal? EDIT: I used umount /media/cdrom0 and was told that it was not mounted (according to mtab). I am trying to install an .iso on a blank disc in the DVD-R drive. Startup Disk Creator will not recognize the blank disk for some reason.It says the dvd is already mounted.

---

### Post by coldcritter64 on 2014-01-22
> **bc.haynes said:**
> [visually impaired] How does one unmount a DVD device in Terminal? EDIT: I used umount /media/cdrom0 and was told that it was not mounted (according to mtab). I am trying to install an .iso on a blank disc in the DVD-R drive. Startup Disk Creator will not recognize the blank disk for some reason.It says the dvd is already mounted.

Try the command,
```
eject -T /dev/sr0
``` the -T is a toggle switch for the eject command, you can keep using this to open and close the dvd drive tray. /dev/sr0 is the main device to look at for optical drives, most if not all other optical devices in /dev/ are just a link to it.

Ejecting the drive tray and closing again should reset any mount problems, try that 1st; if not post back any terminal errors here between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the terminal output posted into your editor and then click on the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the message toolbar. You may need to select the advanced editor here, if you need to post back errors.

---

### Post by bc.haynes on 2014-01-22
I tried what you said and it didn't work.
```
ben@ben-ThinkCentre-M78:~$ eject -T /dev/sr0
ioctl: Input/output error


```

---

### Post by coldcritter64 on 2014-01-22
> **bc.haynes said:**
> I tried what you said and it didn't work.
```
ben@ben-ThinkCentre-M78:~$ eject -T /dev/sr0
ioctl: Input/output error


```

Ok, I think the software may have locked the drive. I used to get that problem when using startup disk creator; most of the time I would end up having to use a paperclip and force eject the drive (if the manual eject button on the drive also fails it can become necessary to use the override mechanism) and then reboot to clear the mount problems. I try to avoid manually touching (mounting/unmounting) any device handled by mtab, it can get nightmarish ;).

I would suggest, shut down startup disc creator and clear the system mounts with a reboot (not very elegant but effective), if the drive still won't eject on the command line on reboot or with the hardware button (this has happened here) it becomes necessary to use the paperclip and the drive manual override mechanism (if available). Once the drive is free reboot. Check it is working with the eject command. Load a blank disc (_*iirc*_, this should always be done first before even opening startup disc creator) then open startup disc creator. Good luck.

---

### Post by bc.haynes on 2014-01-22
I am trying to burn a .iso to a blank DVD. I have rebooted the system (as coldcritter64 suggested). I open the DVD drive, insert a blank DVD, and close the drive. I immediately get an error message that I cannot burn the DVD because it is mounted. I close the windows, start Startup Disc Creator, and disc creator does not recognize the DVD drive. Then, I ;
```
umount -f /dev/sr0
```
Then, I open the DVD drive and close it with the blank DVD inside. Again I get the error that the drive is mounted. Startup Disc Creator will not recognize the DVD. I have tried all I can think of to do, even, using a different manufacturer's blank DVD. 

A moderator has gotten after me for posting this in another forum. I did not believe it was double-posting. It was a different scenario than the one coldcritter64 answered. I am sorry. Thank you for doing your job ( without pay?), moderator. I appreciate it.:guitar:

---

### Post by lisati on 2014-01-22
Hi bc.haynes: if you are having trouble reading the screen, you can make what you are reading larger by holding down the Ctrl key and using your mouse wheel to adjust the size of the writing on the display.

---

### Post by lisati on 2014-01-22
> **bc.haynes said:**
> 
A moderator has gotten after me for posting this in another forum. I did not believe it was double-posting. It was a different scenario than the one coldcritter64 answered. I am sorry. Thank you for doing your job ( without pay?), moderator. I appreciate it.:guitar:

Please do not post the same question in multiple parts of the forum, it dilutes the community's ability to help.

---

### Post by bc.haynes on 2014-01-22
> **lisati said:**
> Please do not post the same question in multiple parts of the forum, it dilutes the community's ability to help.

Somehow, I have incurred the wrath of the ubuntu gods. A second person has asked me not to double-post in the forums....even used the same line to chastize me. Ladies, I said I was sorry. I don't (knowingly) plan to double-post. I promise, cross-my-heart-and-hope-to-die-forgiven, I won't double-post any more. Now, please, do something constructive and answer my post. I really want to burn the 13.10 .iso so I can try it. I bet the weather in New Zealand is nice this time of year....it's freezing here.  ;)

---

### Post by cariboo on 2014-01-23
Startup Disc Creator, as well as Brasero can be problematic at times, I'd suggest using K3B for anything to do with burning discs. If you just have to use the command line to unmount a disc, use:

```
df -h
```

To see where the disc is mounted, then use the location the above command that shows you where the disc is mounted along with the umount command.

As a side note, please use your browsers zoom command to make things large enough for you to read, instead of formatting the font to the largest size allowable by the forum.

---

