---
title: "Frustrated with Ubuntu, cannot get Flash Plugin to work"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by softest bullet ever shot on 2008-05-16
I don't know if this is an Ubuntu 8.04 issue or Firefox 3.0 beta 5 issue, but I have been messing around with Ubuntu for couple days and I still can't get any flash pages to work in Firefox.  I tried installing the flash-nofree plugin and gstreamer plugins and the sun java5 plugins ( I don't remember the exact name).  I installed the flash plugin when I was prompted to do so in Firefox, but still no luck.  

Is there any package I am missing?  


So far my experience in Ubuntu hasn't been thrilling.  I replaced SuSE 10.2 with Ubuntu because I was told that Ubuntu was the most user friendly.  But so far I cannot get anything with Flash to work for me over the internet, I had to do a Google Search just to change my grub default settings (  A GUI may be nice as opposed to editing a file, the average computer user is not familiar with vi nor changing something in /etc, I had the impression this was for the common user), and I still have yet to find a way to configure NFS Servers or Clients.  

Sorry to vent.  I trust that many are indeed happy with Ubuntu.  But as far as my experience goes, it is not ready for the everyday user, if only for the reason that most users like having a workable Flash plugin that is easily obtainable.

---

### Post by CloudFX on 2008-05-16
Hi,

I'll help you go through installing flash player.
First, go to this [ site](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash), and under Select Version to Download, select .tar.gz.  Select Agree and Install to download the file.

You must now extract the folder inside the .tar.gz file, by dragging it into a different folder.  To make things easier, please drag the folder onto your desktop.

Now open up a terminal, and type in the following
```
cd Desktop/install_flash_player_9_linux
./flashplayer-installer

```

Go through the steps, and you should be done!

---

### Post by hufferd on 2008-05-16
If you find out how to get it working let me know - cause - flash player will not work for me as well :confused:

All plugins as near as I can tell are installed ??

~D

---

### Post by robalcorn on 2008-05-16
I experienced the same thing and I found a reboot solved it for me.

---

### Post by dazzlindonna on 2008-05-16
All of my problems were solved a few minutes ago when I followed the incredibly wonderful instructions provided in this thread - [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by lazyart on 2008-05-16
> **softest bullet ever shot said:**
> I don't know if this is an Ubuntu 8.04 issue or Firefox 3.0 beta 5 issue, but I have been messing around with Ubuntu for couple days and I still can't get any flash pages to work in Firefox.  I tried installing the flash-nofree plugin and gstreamer plugins and the sun java5 plugins ( I don't remember the exact name).  I installed the flash plugin when I was prompted to do so in Firefox, but still no luck.  

Is there any package I am missing? google medibuntu.  

> 
So far my experience in Ubuntu hasn't been thrilling.  I replaced SuSE 10.2 with Ubuntu because I was told that Ubuntu was the most user friendly.  But so far I cannot get anything with Flash to work for me over the internet, I had to do a Google Search just to change my grub default settings (  A GUI may be nice as opposed to editing a file, the average computer user is not familiar with vi nor changing something in /etc, I had the impression this was for the common user), and I still have yet to find a way to configure NFS Servers or Clients.

Average user probably doesn't edit grub either.  Average user probably won't use vi either and instead turn to gedit in the gui (it shows up as Text Editor) or nano in the cli.  

> 
Sorry to vent.  I trust that many are indeed happy with Ubuntu.  But as far as my experience goes, it is not ready for the everyday user, if only for the reason that most users like having a workable Flash plugin that is easily obtainable.

I disagree-

The "everyday user" likely knows how to use google.

4 days and you proclaim it's not for the everyday user.  Had you googled ubuntu&flash you probably wouldn't have posted this.
 Another google for ubuntu&nfs and you'd be saying how easy it was to get going with ubuntu.

Help is here if you ask for it.  No need to be negative.

---

### Post by wolfen69 on 2008-05-16
a simple
```
sudo apt-get install flashplugin-nonfree
```
would have sufficed

---

### Post by softest bullet ever shot on 2008-05-16
By the way, I found this link, [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490) which solved by problem.  I had to follow these instructions to install whatever mess I put on there.  Next time I opened Firefox, it prompted me to install the plugin, and it worked this time.  There is a good possibility I had problems because I had somehow screwed something up.  

> **lazyart said:**
> google medibuntu.  



Average user probably doesn't edit grub either.  Average user probably won't use vi either and instead turn to gedit in the gui (it shows up as Text Editor) or nano in the cli.  



I disagree-

The "everyday user" likely knows how to use google.

4 days and you proclaim it's not for the everyday user.  Had you googled ubuntu&flash you probably wouldn't have posted this.
 Another google for ubuntu&nfs and you'd be saying how easy it was to get going with ubuntu.

Help is here if you ask for it.  No need to be negative.

You're right lazyart, I am sorry for being negative.  I was frustrated but nevertheless should have taken some deep breaths for posting this.  

That being said, how user-friendly a system is can be evaluated relative to other systems.  I think quickly accessing your default boot options and your NFS client through the Admin GUI would be a nice feature( or at least have them be easier to find, maybe I just can't seem to find them), and it is something easily accessible with SuSE's YaST.  Yes, search engines make everything fairly easy, but if you can easily access things without having to search, that is even better.  

I am willing to spend more time with Ubuntu, I think I just started off on the wrong foot.  Sorry to just come out and bash it like that.

---

