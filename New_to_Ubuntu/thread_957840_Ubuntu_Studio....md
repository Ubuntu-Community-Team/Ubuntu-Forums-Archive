---
title: "Ubuntu Studio...?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by IBUA on 2008-10-24
Hey,

Just before i go and explain what i'm going to ask, ill just quickly say i don't really know much about Linux/Unbuntu and i'm only considering (at this stage) about adding it to my computer and so on. So if i ask stupid questions sorry! and if this is in the wrong place sorry again :S. (And sorry for the wall of text)

ANYWAY

Basically i'm a musician (:guitar:) and i've been getting really annoyed with all the stupid windows DAWs and multi track recorders and stuff as they are so expensive and annoying to use blah blah blah, and basically i've heard about and researched a little about specific programs (I'm most interested in Ardour) and i think i'd mostly likely go to for Ubuntu studio.

But when i've tried researching all of the stuff i need to know, i can never prperly find it anywhere in one place at all, and when i do find something relevant it goes into too much "computer talk" so i get lost. If this stuff has all been asked before i'd be grateful if you could point me in the right directing

But basically i have a few questions and stuff to ask and to check before i go ahead and go and get it and to install and so on.
(BTW i'm on Windows XP)

1. firstly i was wondering if you can install the Ubuntu OS on a external hard disk drive and still be able to, at boot up, have the choice from selecting windows/ubuntu.

2. Secondly if i did install it on the harddisk drive, would i still be able to have (for exmaple) all my music on there and would the music files still be accesible from windows and ubuntu.

3. How do i install it all saftely and without ruining the rest of the computer, and would some one, if i do decide to choose Ubuntu, be able to give me a fairly easy sort of step by step guide of setting it up and so on? (TBH i shouldn't really dabble with this stuff as i share my computer with my brothers, but the music recording program(s) look so good, espeically as it's free. So this is why im checking)

So yeah, they are pretty much all my questions... i'll probably end up asking more later but hey.

Thanks for all the help!

---

### Post by taseedorf on 2008-10-24
Yes, you can dual boot between windows and vista.  Ubuntu will install a program called GRUB which is a bootloader.  It is the first thing you see after your bios screen, and you can pick windows or Ubuntu.  

Your music will still be accessible.  :)

3rd... there are many step by step guides available.  Search google or here for step by step guide to install Ubuntu.  However, if you insert the install cd, and boot it, it is VERY straightforward.....

---

### Post by eternalnewbee on 2008-10-24
Someone here once wrote that people who don't ask stupid questions make stupid mistakes, so don't hesitate to ask. And welcome to the Ubuntu Forums

---

### Post by simtaalo on 2008-10-24
this is a good guide to installing ubuntu studio
[http://ubuntuforums.org/showthread.php?t=900676](http://ubuntuforums.org/showthread.php?t=900676)

---

### Post by garyed on 2008-10-24
I'm with you on this.
I've been running Cakewalk music software since DOS when digital audio was just a dream. I turned to Ubuntu Studio to get away from Windows a year a so ago. I love it but its a lot more work getting things set up & running right.
I dual boot with XP & it works like a charm.
Being paranoid about my existing Windows system & music I bought an extra internal HD just to use for Ubuntu. I originally downloaded Ubuntu live CD & installed it & then upgraded to Ubuntu Studio after running it a little while to see how it felt.

The main thing for music is to get "Jack" set up & working right. 
"Jack" is a program that controls your audio interface & syncs midi & audio.
Once you have that working, Ardour will multi-track audio great & it can sync up with Rosegarden which handles the midi side. I haven't learned how to deal with VSTi's yet but I've heard they work too. I'm slowly learning U-studio & 
I plan one day to be Windows free.
By the way I use an M-audio audiophile 2496 for midi & audio recording.
Good luck.

---

### Post by Squish on 2008-10-24
You can actually get away without having to partition at all.

Check out wubi: [http://wubi-installer.org/]("http://wubi-installer.org/")
It installs ubuntu on the ntfs drive, and is accessible from windows (and vice versa), and installing is pretty much painless.

The only drawback is that you have it on a ntfs partition... which is a crummy filesystem(You know, defragging and such).

---

### Post by IBUA on 2008-10-25
Thanks for all the help, it's been very useful!

1.But how (when installing) do i install it on the external harddisk drive space rather than the actual computer? (If this is possible)

If that makes sense...

and 2. The WUBI Thingy, is that just a windows installer... not like a "try and test" thingy...

Haha sorry for all the bad words e.g. "thingy" but like i said before i don't know most computer speak like "defragging" :S...

---

### Post by DrMelon on 2008-10-25
When you choose to install, you can pick the drive you want to install to. Your external drive should be listed in the places where you can install Ubuntu; providing that it's plugged in of course.

---

### Post by IBUA on 2008-10-25
> **DrMelon said:**
> When you choose to install, you can pick the drive you want to install to. Your external drive should be listed in the places where you can install Ubuntu; providing that it's plugged in of course.

Ah yes. haha i just realised thank. but thank you.

New quesiton haha.

As my friend and i swap around places where we record stuff, would i be able to unplug the HDD with Ubuntu Studio on it, and take it to his place and plug it it and run it from his computer... or does it need to be configurered ro something. (So basically would it work as a Bulky "live CD" thingy... sort of)
----------------
Now playing: [Lacuna Coil - Our Truth](http://www.foxytunes.com/artist/lacuna+coil/track/our+truth)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by simtaalo on 2008-10-25
you should be able to do that as long as you changed the boot order in the bios. you could also install ubuntu onto a usb drive and use that to take around and boot from.

if you do a search theres many threads on this.

---

### Post by Squish on 2008-10-25
oh man, thats oodles of fun. I love the portable OS.

Wubi is something you run off windows, and you can do it either from a disk, which will install ubuntu for you on windows, or it can be a utility that will automatically download and install all the needed files. Its a great product.

Defragging:
Many file systems (The method to which data is stored on a harddrive), will get cluttered over time, and will ultimately need to be tidied up. Defragging is organizing the filesystem, so they can run more efficiently.

Windows Microsystems (ntfs, fat32, etc...) get cluttered really easy, not so much with the Linux ones (ext3, reiserfs, etc...)

---

