---
title: "“Unsafe swap space detected” during attempted Lubuntu 13.10 install"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by james102 on 2014-02-23
Hi.  I'm a novice when it comes to fixing problems with computers so bear with me.   While trying to install Lubuntu 13.10 in place of Windows 7  Starter on an almost unused Asus EeePC 1015BX I got the message "Unsafe swap space detected"  as per the photo below:

[URL="http://askubuntu.com/questions/393418/unsafe-swap-space-detected"]Unsafe swap space detected

[/URL]I tried the suggestion in the link above, but I fear I've done  something wrong because when I now boot up, the screen goes black with a  cursor flashing in top left hand corner.  And being a novice, I've not a  clue what to do from there.

Any suggestions would be extremely appreciated.

---

### Post by david98 on 2014-02-23
In my experience[COLOR=#333333][FONT=UbuntuRegular] the blinking cursor screen is presented by buntu itself and not Grub, so I assume the boot process gets halted for some reason try h[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]olding shift during boot, then hit e to edit the GRUB entry. Remove the part that says "quiet splash" and replace it with the word "text" to see what's happening during boot.[/FONT][/COLOR]

---

### Post by fdrake on 2014-02-23
+1 david98

it looks like it may be a video card issue: try this
replace "quite splash" with "nomodeset text"

---

### Post by james102 on 2014-02-23
Thanks to you both for your quick replies.

I tried holding down shift during boot but it seemed to have no effect - machine booted to cursor screen as before, and pressing e had no effect.

Can you suggest something else to try?  Like I say, I'm a novice, so step-by-step instructions would be extremely helpful.

---

### Post by david98 on 2014-02-23
My opinion to do now would be to boot up in a live session ie the cd/dvd or usb you used to install buntu then use gparted to completely format the hdd again. And try a new fresh install. Just out of curiosity did you boot into a live session first to have a play about with buntu before you installed it as this is highly recommended so you can check if you have any hardware compatibility problems.

---

### Post by james102 on 2014-02-24
Thanks again for your reply/patience.

Before attempting install I did try a couple of live Lubuntu versions - 12.04 and 13.10.  Both felt quick enough in use - miles quicker than the agonisingly slow Windows Starter 7 - though 13.10 took noticeably longer to boot (over 5 minutes).  Could live with that though.  Dare say I didn't do extensive check regarding hardware - just tried opening programs/browser and a few keyboard function shortcuts (eg adjusting brightness).  One thing - I looked for lubuntu-restricted-extras in Software Center but could only see Kubuntu/Ubuntu/Xubuntu extras.

I wondered - would you advise someone like myself to install a different distro, ie a novice who's just looking for a distro that's both relatively novice-friendly to install/maintain and usable on a 1GHz/1GB netbook?  I ask partly because I was thinking of trying live versions of Xubuntu and Ubuntu this evening.  Also, how advantageous/otherwise is it to have an LTS version?

---

### Post by david98 on 2014-02-24
Xbuntu and ubuntu should both run on your system perfectly. I imagine though xbuntu would be a little faster as unity in ubuntu can be a little resource heavy. You could have gnome or KDE desktop environment but that's a different topic. So to answer your question yes I would download both of them have a play about with them and find one you like. Hope you stick at it because once you have it all set up and working correctly it is much faster than windows in my opinion and a hell of a lot easier to use. Yes using a Command line can be daunting to people who have had no reason to in the past but you quickly learn the basic concepts and become more than comfortable using it.

---

### Post by james102 on 2014-02-25
After much frustration I finally got something to install.  Not exactly sure why/how but after formatting hard drive (I think), another failed 'full encryption' Lubuntu install attempt and a Xubuntu install which seemingly wouldn't recognise my password (after 3 attempts it kicked me out to a wall of text), I managed to get Lubuntu 13.10 to install (without full encryption).  I have no idea if the following is good or bad but it's what I've ended up with:

Partition        ________ File System        ________ Mount Point        ________ Size        ________ Used        ________ Unused        ________ Flags

/dev/sda1        _________ext4                    ________________ /                  ____________297GiB    _______ 7GiB        _________290GiB        _________boot

 &#8595; /dev/sda2    ________extended                                 __________________________748GiB _________      -                ____________ -

        /dev/sda5    ________linux-swap                              __________________________748GiB       __________- ____________               -        

(Tried to use scrot to copy/paste the above info from gparted but couldn't get it to work)

Seems my head's just not wired for grasping stuff like Linux so think I might have to buy a Windows 8 tablet for the time being and just use this frustrating little netbook for messing around with Linux (which I suppose is good in a way cos it means the netbook won't have been a complete waste of money).

Again, thanks for your replies/patience.

---

