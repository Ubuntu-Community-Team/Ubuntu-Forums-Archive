---
title: "Video - Low-graphics"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by paul105 on 2014-03-03
An absolute newbie trying to get Ubuntu working.  I got 12.04 LTS to load so that now when I boot the computer goes to GRUB letting me select Ubuntu or Windows XP - fine so far.

When I select Ubuntu I get a message which says that Ubuntu couldn't detect my video card and/or monitor and advising me to set up graphics manualy - Not great but I can live with that.

My system is using the on-board video in an ECS K8M800-M2 motherboard connected to an Acer X223w monitor.

When I select OK it goes to another screen asking me to select between:

Run in Log-graphics mode for just one session
Reconfigure graphics
Troubleshoot the error
Exit to Console log-in

The problem is that if I select any option except Exit to Console log-in, the computer locks up.  Sometimes I can escape to GRUB, but even that seems sporadic.

If I select Exit to Console log-in, then I get some sort of command line which looks to me like UNIX (I know just enough UNIX to recognize it, but not enough to do anything.)  I can't find any command which will either let me configure my video/graphics or go to the GUI.  Getting *really* frustrated!

Since the Run in low-graphics, Reconfigure & Troubleshoot options don't seem to work correctly I'm pretty much stuck.

Any help/suggestions/ideas would be greatly appreciated.

---

### Post by ibjsb4 on 2014-03-03
My google-fu tells me that that mother board runs VIA UniChrome Pro which is part of the KM-series 400 and in turn leads to OpenChrome and ..

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
[http://manpages.ubuntu.com/manpages/hardy/man4/via.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/via.4.html)
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=VIA+UniChrome+Pro+&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=VIA+UniChrome+Pro+&sa=Search&cof=FORID:9)

And that&#8217;s all I know about your video.  So wait for a second opinion on this next part ..

I don't think you will be able to run standard (Unity) Ubuntu.  You need something less resource hungry like Xubuntu or Lubuntu.

---

