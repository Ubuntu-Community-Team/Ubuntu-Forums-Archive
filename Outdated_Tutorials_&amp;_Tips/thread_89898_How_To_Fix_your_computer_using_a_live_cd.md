---
title: "How To: Fix your computer using a live cd"
date: 2005-11-13
forum: Outdated Tutorials &amp; Tips
---

### Post by wondering_jew on 2005-11-13
Last night I was trying to add a grub splash image and I edit /boot/grub/menu.lst restart my computer and *BAM* grub won't load so my computer is un-bootable it just sits there and restarts every 5 seconds as grub trys to load and fails. My first instinct is to call my co-sci major friend who turned me on to this linux thing just over a year ago but he doesn't answer. Now what? 
 
Heres what I did: 
First I popped in a live cd. I used a warty (4.10) live cd since thats what I had 
 
From a terminal type "mount hda1" (change hda1 to what ever partition you boot from) the icon for hda1 then pops up on the desktop and you have access to all the files on the hard drive. 

Then It is just a matter as going in and editing the file (as root).
 I did this by typing "sudo nautilus" and finding the file through the gui (places->computer->hda1) and undoing my changes. Everything worked and I had a great sense of newbie pride :)

      On a side note I wonder if this presents a security risk since you could hypothetically change any file owned by root without a password with just a live cd...although I am glad this is the case.  Oh and I made the grub splash image work on the second try :)

---

### Post by ubuntu_demon on 2005-11-14
Yeah you can always do that. If you can still get into grub you can also boot your pc into recovery mode (from grub) and get root acces that way.

If you are running a corporate environment or school you can prevent booting from cd/usb/floppy + install a bios password + grub password + remove the recovery mode grub lines. This makes it harder to get in. 

But for most bioses an overriding password can be found using google and then they can pop in the live cd. They can also just steal your pc or harddrive ofcourse. If your harddrive is encrypted you can protect your data a little while longer. (encrypting your harddrive has drawbacks also)

So the average desktop users shouldn't do all this extra protection stuff because it becomes harder to fix your pc. Just make sure there aren't real assholes near your pc.

---

### Post by BIGtrouble77 on 2005-11-14
jew,
You might wanna edit your post and convert it to more of a HOWTO format, and be a little more specific.  You may want to add in the ability to restore a system backup (tar'd backup) too.

---

### Post by ubuntu_demon on 2005-11-14
yeah indeed but this is a nice start :)

---

### Post by wondering_jew on 2005-11-15
[QUOTE=BIGtrouble77] You may want to add in the ability to restore a system backup (tar'd backup) too.[/QUOTE]

Hmmm you'll have to forgive my ignorance in such matters. To tell you the truth I was happy to have figured out as much as I did... I don't really know what I'm doing yet :)

---

### Post by ubuntu_demon on 2005-11-15
[QUOTE=wondering_jew]Hmmm you'll have to forgive my ignorance in such matters. To tell you the truth I was happy to have figured out as much as I did... I don't really know what I'm doing yet :)[/QUOTE]
it's good to learn and share. I'm sure there are other users who can benefit from your experience :)

---

