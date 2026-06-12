---
title: "wicd gutsy wg111v3 usb adapter"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by MichaelSM on 2008-10-16
I have had wireless running OK with Gutsy for a while using ndiswrapper and the Windows .inf file for my Netgear (wg111v3) adapter.

What I wanted was connection at boot, which Network Manager could not provide. By following various instructions readily available, I uninstalled Network Manager and installed WICD, an alternate network gui. The WICD .deb is attached below.

Having done all this, I re-booted, and using the WICD applet gui I hit 'Connect,' and it wouldn't.

After consulting PAGES of info, full of complicated instructions in Terminal etc. I opened the WICD Manager and hit 'Preferences.' which at the top beside  WPA Supplicant Driver is a drop-menu including a number of choices one of which of course was 'ndiswrapper' which is the module (?) I'd previously used for my wireless. Having re-highlighted it, I went back to 'Connect,' and couldn't connect. Again.

Back to Preferences and the WPA supplicant driver drop menu. I have no idea what 'wext' IS, but it was at the top of the menu so I gave it a shot.

Next time I went to 'Connect', I was on line within seconds ....!

Having ticked the obvious automatic connect box, now on reboot I'm connected instantly, which is all I ever wanted.

Now, a couple of points. This note possibly applies only to an installation where the WG111v3 .inf was already in the machine. For all I know (which isn't much, let's face it !) the 'wext' with its 'W' might or might not refer to a certain chipset. If it's of any help to know, I plugged in a spare TL-WN321G usb adapter and it wouldn't work under any options in the drop-menu I mentioned earlier. 

Hope this is of some help.

Michael.

---

### Post by hyper_ch on 2008-10-16
better to do a repository install of wicd as they offer their own ubuntu repositories: [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

Besides that, good writing :)

---

### Post by MichaelSM on 2008-10-17
Thanks for the reply, Hyper_C.

Following your advice I went to SourceForge and added its version of wicd to my repositories. Same all.deb package 1.5.3.

Re. Network Manager; it's hard to find a post anywhere which doesn't encourage us to get rid of it....!

Here's a question. The box I'm using at the moment is Linux Mint Daryna (Gutsy) and 'though it indicates three updates available, Daryna + Network Manager won't/can't get their act together to download the files.(This is with the wireless modem/router connected by Ethernet) Should I switch to wicd and see what happens?

Of course I shall.

Yes; thanks for your note. I like to write properly but I can get too talkative.

Cheers,

Michael.

---

### Post by hyper_ch on 2008-10-17
no clue, I use solely the "real" *buntu... have a go.. maybe it works, maybe not.

---

