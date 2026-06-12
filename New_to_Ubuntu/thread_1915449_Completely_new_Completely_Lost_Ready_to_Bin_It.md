---
title: "Completely new: Completely Lost: Ready to Bin It"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by FarmerM on 2012-01-26
Ok totally new to Linux so please be gentle.

v11.10

1. Cannot access or find the list of applets down left side of window. Were there but clicked on one and now they disappeared.

2. Now have 2 windows .. 1 with list of files, another with All Settings (looking for displays).  I cannot move, size or close either of these windows (no icons to do it)

I have tried Alt + F1-F10 and none of them do anything!
Did have some (299) updates this morning and then restarted.

How do I get back to the original screen with the icons/applets?
How do I force windows to close and how do I know when system is frozen? (and what do I do then?

While I am here how do I know what security/firewall.anti-virus I have and what do I need?

Sorry for the Newbie Q's :-(

TIA

Michael

---

### Post by Double.J on 2012-01-26
Hi there, welcome to the forums!

1)Did you restart after the updates? If the system doesn't seem to want to restart, open a terminal with  CTRL+ALT+T and paste in
```
sudo shutdown -r 0
```It'll ask for your password and then restart. if this doesn't work - hard restart by holding the power button :)

2) Do you mean that you're top panel and side one are now missing? if they still are after reboot, try opening a terminal with CTRL+ALT+T, then type
```
unity --reset
```
Does this help?

All the best!

---

### Post by FarmerM on 2012-01-26
Thanks for reply.

Completely rebooted computer.

Ctrl+Alt+T  does nothing !
Blank screen (with background)

Assume keyboard working as I had to type in a password to login.

I know that there is a learning curve with new software but this is crazy!
Perhaps XP has it's advantages!?

---

### Post by Double.J on 2012-01-26
hmm that is odd.. try restarting again, and when you get to the login screen click on the cog next to the box you put your name in and select "Ubuntu 2D" see if you can successfully log in to to this desktop?

If you can, open the terminal again with CTRL+ALT+DEL, and paste in this
```
sudo apt-get update && sudo apt-get upgrade
```

Then press the windows key and type "additional drivers" into the search box and see if you have any available display drivers?

All the best :)

---

### Post by FarmerM on 2012-01-26
help appreciated
where do I find these tips & tricks?

2D worked;
assume you meant CTR ALT T ?

It is currently doing something so hope it is working
Cheers

---

### Post by FarmerM on 2012-01-26
Appears to work now, TY.
Certainly not intuitive!
Could not have got  there without your help.

Trip to bin delayed.
Thanks again
M

---

### Post by Double.J on 2012-01-26
Glad it worked for you :)

Stick in there; your problem was not the norm! There's a few bugs still in the user interface, that caused the settings to get messed up. 

Ubuntu has two versions on the go at any given time; normal and LTS (Long Term Support) which are designed to be more stable. most people choose the normal version as this is newer, with the lts coming out every 2 years (next one in april).

There are a lot of tips out there for ubuntu beginners. This one looks quite good:

[techradar]("http://www.techradar.com/news/software/operating-systems/25-ubuntu-tips-for-beginners-906002")

Hope it helps :)

---

### Post by SeijiSensei on 2012-01-26
On Linux systems, you have a choice among a variety of "desktop environments." The current Ubuntu release, 11.10, uses a new interface called Unity.  I prefer KDE, and so use [Kubuntu]("http://www.kubuntu.org/").  It's easy to shop around; just download the appropriate CD image, boot from it and choose "Try Ubuntu".  Your computer will be left unchanged, and you'll get a preview of what's available in a different DE.  If your computer allows you to [boot from a USB device]("https://help.ubuntu.com/community/Installation/FromUSBStick"), you can transfer the CD to a USB key and boot from that.  That method generally has better performance (in terms of speed) than a CD-based session.

Other alternative DEs include [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") and [Xubuntu]("http://www.xubuntu.org/").

---

### Post by Mark Phelps on 2012-01-26
> **FarmerM said:**
> How do I get back to the original screen with the icons/applets?

The new Unity interface seems prone to breakage -- moreso than the previous interfaces.

IF what you've tried so far doesn't restore the launch panel (on the left), then try the actions in the link below:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by grahammechanical on 2012-01-26
You are not the only person to say that suddenly the system broke. But we know that although Forest Gump was of the opinion that stuff happens (expletive - replaced), it does not just happen. We do stuff that causes other stuff to just happen. Is that not true?

Linux lets us do stuff and because we do not pay for it we can easily bin it. Or re-install.

What did you do? This problem is not solved. You are now using the desktop user interface that is not broken because it uses a different window manager to the one that was broken. Ubuntu (Unity 3D) is still busted.

Regards.

---

### Post by oldos2er on 2012-01-26
> **FarmerM said:**
> While I am here how do I know what security/firewall.anti-virus I have and what do I need?


See [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by FarmerM on 2012-01-27
Thanks everyone for the replies.
This part of Linux is great.

BUT!!!
I have binned it :-(
Sorry simply do not have the time to search around for answers to questions that I have the answers to in Windows.

I am no fan of Windows but, unfortunately, it is easier to get to know and use.

I wanted a quicker, more secure OS... neither of which I have been able to confirm.

I know that I am going to be shot down in flames but so be it. 

Even things like banking where the main banks do not want to provide support for Linux and trading apps again that do not support Linux, mean currently that I do not have time for the learning curve and unnecessary problems that would ensue.

I would love to migrate but it is not now for me.

Best Wishes,
M

---

### Post by nothingspecial on 2012-01-27
Thst's fine :)

If you ever try Ubuntu again and have a question. Feel free to come back here and ask.

Issue resolved, thread closed.

---

