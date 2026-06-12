---
title: "Well now I've really screwed things up..."
date: 2012-12-03
forum: New to Ubuntu
---

### Post by Elect GMax on 2012-12-03
My wireless card was behaving very erratically and I wanted to know why. A quick "ndiswrapper -l" revealed that yes, the **net**8192cu drivers were installed and yes, the device was present... but there were "alternative drivers available", namely, **rtl**8192cu. The best advice that I could find said to use "sodu rmmod (alternate driver name here)", so I did, which temporarily disconnected me. I figured that upon rebooting, the proper drivers would be loaded and I'd reconnect, but no, rebooting only restored the old rtl drivers! Going totally nuclear, I searched my entire file system for anything with "rtl8192cu" in the name, figured out where those files and folders were, and used some "sudo rm rtl8192cu -r" with extreme prejudice.

Now my card can't even *try* to connect and "ndiswrapper -l" says that the rtl drivers ARE STILL THERE.

[img]http://icons.iconarchive.com/icons/icons-land/vista-style-emoticons/256/Cry-icon.png[/img]

All this just to play multiplayer Minecraft.

---

### Post by mamamia88 on 2012-12-03
Try completely purging ndiswrapper and starting over?

---

### Post by techvish81 on 2012-12-04
you should have asked somebody before deleting files.  windows too will be killed if you delete system files.  
sorry dude, but you have to have some patience and courage to do any new thing.

---

### Post by squakie on 2012-12-04
If you do need to reload ubuntu, keep in mind that the newer versions (say, from 11.04 and up) have vastly improved wireless support.  Your wireless may not work right "out of the box", but normally these things can be made to work now without the need for ndiswrapper.  I was a big proponent of ndiswrapper and ndisgtk, but the need for those now is very rare.

The first thing to try is to hard-wire a connection between your computer and your router, then check "Additional Drivers" - a lot of the time it finds what is needed.

If that doesn't work, please post a new thread with a title something like "<ubuntu release> <wireless adapter> wireless not working" and post as much as you can about your wireless adapter, etc..  Then please wait for a response rather than deleting files, installing ndiswrapper, etc..

Best of luck - I'm sure you'll probably need to re-load ubuntu first.  You could always boot from a livecd or "liveusb" and backup any important data you might want to save.

---

### Post by Elect GMax on 2012-12-04
> **techvish81 said:**
> you should have asked somebody before  deleting files.  windows too will be killed if you delete system  files.

Yeah but Windows actually uses new drivers when I install them so I don't have to delete the old ones.

> **squakie said:**
> keep in mind that the newer versions (say, from 11.04 and up) have vastly improved wireless support.

12.04 here.

> **squakie said:**
>  The first thing to try is to hard-wire a connection between your computer and your router

If that was even possible, I wouldn't be bothering with the wireless adapter at all.

---

### Post by techvish81 on 2012-12-04
> **Elect GMax said:**
> Yeah but Windows actually uses new drivers when I install them so I don't have to delete the old ones.



12.04 here.



If that was even possible, I wouldn't be bothering with the wireless adapter at all.


it is because hardware manufacturers are only focused to windows, so they only release drivers for windows, while in ubuntu,  drivers are mostly open source and developed by community.  still there is sometime new version of a driver which can be downloaded and installed in ubuntu (if there is any).  most of hardware work out of the box, but still problems occur sometimes with some hardware (wireless and printers mostly).  

so people using linux are advised to search for information about the campatibility of particular piece of  hardware before they buy. however most of those hardware problems can be fixed if you are not afraid of terminal and code editing.

driver issues are not so rare in windows too, you can take a look at [sevenforums]("http://www.sevenforums.com/") to confirm this.

you are using ubuntu 12.04,  you can try 12.10 to see if it is fixed in the latest driver.

---

### Post by Elect GMax on 2012-12-04
> **techvish81 said:**
> it is because hardware manufacturers are only focused to windows, so they only release drivers for windows, while in ubuntu,  drivers are mostly open source and developed by community.  still there is sometime new version of a driver which can be downloaded and installed in ubuntu (if there is any).  most of hardware work out of the box, but still problems occur sometimes with some hardware

Yes, I knew all of that before I ever touched Linux, but it doesn't really help me.

---

### Post by squakie on 2012-12-05
If you installed an alternate driver, then removed it, why are you even looking at ndiswrapper?  You should delete it completely and then use the native driver.  If that doesn't work, post back here and we can go from there.  As previously mentioned, ndiswrapper is rarely needed now, especially since you have 12.04.

---

