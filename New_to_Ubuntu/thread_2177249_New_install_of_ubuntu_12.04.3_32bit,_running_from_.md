---
title: "New install of ubuntu 12.04.3 32bit, running from dvd it works but not if i install."
date: 2013-09-27
forum: New to Ubuntu
---

### Post by azsheepdog on 2013-09-27
I am trying to revive an older intel 2.8 w/ HT  and an  MSI 915p neo2 motherboard. 2 gigs of ram. I just got a NVidia GeForce gt 610 for it.  If I run the OS from the disk without installing it works fine.  But if I install it . I get a 12.04 splash but it then goes dark but not in powersave. I have tried multiple fresh clean installs.

 Searched around and found out about hitting ctrl alt f1 to get it in text mode.  when I do this, I briefly see the text login screen but it goes blank again. 

While highly skilled in the windows environment it does me no good here.  What can I do or try to get someplace to test or get answers needed for troubleshooting. 

again it will load if I run it from the install disk without install,  but I do need to do a nomodeset at the little man screen to get to the install window or it too goes to a blank screen.

Thanks in advance

---

### Post by DuckHook on 2013-09-28
This is a very low-end system and it won't run Ubuntu very well if at all. The limited resources may be why the system is choking. I would suggest Lubuntu based on your system specs. Try downloading a LiveDVD/USB version of Lubuntu 13.04 32-bit and see if that doesn't solve your graphics issue.

---

### Post by mörgæs on 2013-09-28
I do not agree that this is low-end, on the contrary the GT610 is a great graphics card.

With such new hardware 13.04 is a good choice. You could also try the fairly stable 13.10 beta.

In all cases it's likely that NOMODESET should be a permanent boot option.

---

### Post by azsheepdog on 2013-09-28
> **mörgæs said:**
> 

In all cases it's likely that NOMODESET should be a permanent boot option.


13.04 does boot, but it is maxing out the cpu. Both cores are at 100% constantly. 

  How do it get 12.04 to permanently boot with NOMODESET?

---

### Post by Sef on 2013-09-28
> 
[LIST]
[*][INDENT]How do it get 12.04 to permanently boot with NOMODESET?

When you get to the first menu, instead of starting the install, you have to hit and F#.  Forget which one it is.  It sayss something like options.[/INDENT]

[*]
[/LIST]

---

### Post by DuckHook on 2013-09-28
> **mörgæs said:**
> I do not agree that this is low-end, on the contrary the GT610 is a great graphics card.

With such new hardware 13.04 is a good choice. You could also try the fairly stable 13.10 beta.

In all cases it's likely that NOMODESET should be a permanent boot option.

I was more concerned with his CPU/MB/DRAM. It is probably a single core hyperthreaded P4. I have a similar CPU and MB combo in an old HP. Granted, my graphics card is not as good as the OP's, but I found that Lubuntu ran well whereas Ubuntu yielded only a black screen. But I'm happy to defer to your knowledge and experience.

@OP

*mörgæs* is a forum guru and knows what he is talking about. If you want to try alternatives, it is easy these days with a LiveDVD/USB, so feel free to experiment on your own.

---

### Post by azsheepdog on 2013-09-28
> **Sef said:**
> When you get to the first menu, instead of starting the install, you have to hit and F#.  Forget which one it is.  It sayss something like options.[/INDENT]
[*]
[/LIST]


Ok yes, that part I know, instead of installing I get to the first menu , its f6 and hit select NOMODESET  but how do I get it to do this after install?  How do I permanently set it to that?

Edit: never mind found [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)  , a little cryptic but as soon as I get off work , will try this out for setting it permanently.

thanks

---

### Post by oldfred on 2013-09-28
I have old nVidia 9600GT and have to use nomodeset to install and first boot, but then immediately install the nVidia proprietary drivers and have no issues. 

I have done it from both command line & from system settings. Older versions drivers was a separate icon in system settings, newer versions have it as a tab in all the other updates.

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

### Post by azsheepdog on 2013-09-28
> **DuckHook said:**
> I was more concerned with his CPU/MB/DRAM. It is probably a single core hyperthreaded P4. I have a similar CPU and MB combo in an old HP. Granted, my graphics card is not as good as the OP's, but I found that Lubuntu ran well whereas Ubuntu yielded only a black screen. But I'm happy to defer to your knowledge and experience.

@OP

*mörgæs* is a forum guru and knows what he is talking about. If you want to try alternatives, it is easy these days with a LiveDVD/USB, so feel free to experiment on your own.


While its not the best, I can run 12.04 from dvd without any issues, I was able to load up firefox, install flash, played a youtube video at 720p and everything ran great.   So I think I have enough system resources for 12.04 it just will not boot up if I actually install it.    I run 13.04 from dvd and its super slow, capped cpu. installing is no better, capped, cpu but it actually does load.

  So I would like to get 12.04 running. it seems to be more optimized.

---

### Post by whitesmith on 2013-09-28
The fact that both cores are maxed out suggests that we're dealing with a relatively new graphics board married to an inadequate mobo. The OP's system runs a 2.8Ghz P4 w/hyperthreading, so we have only one physical core that supports 2 threads. Under these circumstances I would choose Lubuntu over Ubuntu. Also what kind of RAM is in the box? I hope it's DDR.

---

### Post by azsheepdog on 2013-09-28
yes it is ddr.  I am sure it probably has something to do with the newer graphics card.  I am having a hard time figuring out how to get it to permanently boot in nomodeset.  Once I find a walkthrough on how to set that permanently or at least once from the install I will be able to get into the OS and actually do some driver updates.  I found a walkthrough but its missing a picture so I think there is part of the process I am missing.   again 13.04 is pegged but 12.04 works great from dvd.

---

### Post by azsheepdog on 2013-09-28
Well lubuntu 13.04 works but a little underpowered for what I was looking for. My uneducated guess is that it is still a compatibility issue with the GeForce 610 and the 12.04 LTS.  I will need to start studying my Linux.

---

### Post by mörgæs on 2013-09-29
What do you mean by underpowered? It supports the same applications as Ubuntu.

---

### Post by Easy Limits on 2013-09-29
Once you get the Nvidia drivers installed you should not have to boot with nomodeset.

---

