---
title: "A way to access a BIOS log for an error report?"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by whoscheesemine on 2008-10-09
I was using firefox and it crashed. Suddeny it seemed as though everything else was going sluggish as well, so I just decided to just restart the computer as I was in a hurry and had other things to do. I'm using a Dell Latitude D520 by the way. After BIOS loaded I got this weird error about not using a standard Dell 65 Watt power adaptor or something. I looked in the back and saw that the power adapter was only partially plugged in. I plugged it in all the way and I hit f3 to continue only realizing right after I pressed it that there was an option to push another button to reconfigure the device. Ever since then the laptop screen won't brighten past an annoying dim. I ran the on board diagnostics test and it says that I'm having an LCD connection error. Thought that kind of odd to just all happen at the same time, so I'm blaming it on the power adapter problem. I wish I could just see that error again. Is there anyway to bring up a log file or something? It also said something about the Laptop would be running slower and not charge very fast. This is a bit of an urgent issue for me as I'm going to have a to a power point presentation for my class here in a few days, and the screen is going to be too dim and we all have to use our own laptops.

---

### Post by porchrat on 2008-10-09
Ubuntu doesn't have a BIOS log, as ubuntu isn't running when the BIOS kicks in...in fact I don't think the average BIOS keeps a log at all.  Seems more like a hardware issue.  Perhaps try flashing your BIOS with a newer version?  Careful though...you can permanently ruin the machine if it isn't done correctly...thankfully it has never happened to me, but I do actually cross my fingers everytime I load a new BIOS.

However it does sound like your screen is a goner.  I would have DELL take a look at it.

One more thought though...does it load ubuntu at all?...and is it still dim while it is booting up?...(I mean before it gets to Ubuntu)

---

### Post by unutbu on 2008-10-09
Have you tried going into the BIOS menu and checking the settings? Perhaps the monitor is dimmed because the BIOS is setting the laptop in some kind of power saving mode (like when it runs on battery power alone). Maybe by changing a power management setting you can get things back to normal. Just remember to take notes on anything you change so you can restore the BIOS settings to their current state.

Also, according to sesticlj's 10-21-2007 post ( [http://www.techspot.com/vb/showpost.php?p=520946&postcount=8](http://www.techspot.com/vb/showpost.php?p=520946&postcount=8)
) you can reset the BIOS on the D520 by taking out the coin-sized battery and letting the laptop rest for a few minutes. 

Don't follow sesticlj's instructions about downloading svctag.rar since that is related to a different problem. My suggestion is simply to power off and remove the battery for a few minutes.

Maybe if all the BIOS settings are reset to default settings the laptop will start behaving.

---

### Post by ibuclaw on 2008-10-09
Could be a surge issue.

Hardware, Inserting Power Adapter + Surge = possible reason for messed up hardware.

Although I see no reason as to why, just need to ask anyway.
Is this odd behaviour happening across all OS's on your Laptop?

If you are good with your hands, you could try checking your graphics card for being inserted properly (with the power turned off).

Else, try restoring your default BIOS settings.

Regards
Iain

---

### Post by whoscheesemine on 2008-10-09
I'll try taking the battery out after work. I haven't had the opportunity to try other OS's on this laptop, as I just put a new harddrive in it a few weeks ago and only put Ubuntu 8.04 on it. I really hope it wasn't a surge. Yeah turns out I have to use some kind of partition manager to create a partition specifically for storing log files of BIOS. I'll go ahead and try to flash the BIOS now. I know I always hear those horror stories as well, but it still hasn't happened to me either. Just seems to be kind of a weird error for it to be a BIOS update that I need. I'm sure it was of no coincidence that right before I had this dim problem I had that powers and adapter problem, and only had my adapter plugged in half way. I did go to the power setting and turned off their power saving feature, and I still am having this problem. It stays dim from BIOS all the way to loading Gnome. Also, I cannot make it any brighter, nor darker.

***[COLOR="Red"]Edit #1:[/COLOR]***Okay, so resetting the BIOS left me no where. The only options left, I suppose, is installing another operating system on a seperate partition to see what happens. Now, I know a few of you are reading this thinking of a bunch of other things to try, but check this out:

[http://www.techsupportforum.com/hardware-support/laptop-support/54659-dell-laptop-display-just-stopped-working.html](http://www.techsupportforum.com/hardware-support/laptop-support/54659-dell-laptop-display-just-stopped-working.html)

This man practically has the same problem I did, except worse. As his screen is lit up, but is lacking any sort of picture; however, he is still able to toggle to CRT from his LCD with out any problem. Or was it only to a monitor? IDK but its all there. The bios flash did nothing. He checked the connections of all the cables. If anyone can think of anything else to suggest please lemme know. I'll probably install another partition after my speech class tomarrow.... errr today now rather. (damn all nighters). Let's just hope I'm able to switch to CRT for my presentation. Gosh, ever since the warranty ran out on this laptop (EVERYTHING IN THE WORLD has gone wrong with it. figures that throughout my 2 year warrenty, the only thing that happened to it was the 'T' key falling off. Dell of course replaced it free of charge, but I had to buy my own hard drive a day and a half after the warrenty went :-D.

Oh, and for the record, I'm using a 90 watt power adapter, which according to their website is what I'm supposed to be using. As, I had to purchase one after mine was stolen. 

I'm begining to feel that tinivole was correct when he said:

> Could be a surge issue.

Hardware, Inserting Power Adapter + Surge = possible reason for messed up hardware.

Although I see no reason as to why, just need to ask anyway.
Is this odd behaviour happening across all OS's on your Laptop?

If you are good with your hands, you could try checking your graphics card for being inserted properly (with the power turned off).

Else, try restoring your default BIOS settings.

Regards
Iain

This topic could definitely use a name change, as the topic has quickly changed to "WHY THE HECK WON'T MY LCD SCREEN WORK?!" do I have the ability to do that, or does an admin have to? 

Anyways, enough of my amphetamine fueled rant. I'll post back my results after I try installing a new partition. I truly appreciate all the feedback I received regarding this issue and welcome more as I'll probably glance back here once in awhile until I do install that new partition. You all are very much aware of the philosophy of "Ubuntu". Power to the users!

---

