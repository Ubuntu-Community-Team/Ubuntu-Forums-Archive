---
title: "[SOLVED] Firefox 3.0 locks up on this page for me.  Anyone else?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by crjackson on 2008-06-26
When I go to this page and wait about 30 seconds, the browser locks up and a force quit must be issued. 
[http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml)

Is this a Firefox bug, or is there some setting I can change to fix this?

---

### Post by philinux on 2008-06-26
Says 404 page not found, maybe it was their server.

---

### Post by crjackson on 2008-06-26
> **philinux said:**
> Says 404 page not found, maybe it was their server.

I didn't paste the link correctly.  Try again please.

---

### Post by Fury5000 on 2008-06-26
I couldn't duplicate the prob... im on 8.04 with ff3 and adblock plus/easylist

---

### Post by Fury5000 on 2008-06-26
oh.. I just remembered something.. I DID have a prob on that particular website in the past that was either flash or vid driver related.  I would go to the main Linux page and if I scrolled down it would lock up solid.

---

### Post by crjackson on 2008-06-26
> **Fury5000 said:**
> oh.. I just remembered something.. I DID have a prob on that particular website in the past that was either flash or vid driver related.  I would go to the main Linux page and if I scrolled down it would lock up solid.

Yes, that's what it does.  I've tried on 2 different systems now with different video cards.  Both do the same thing.  I haven't tried with FF2 yet.  So does this seem like something that a bug report should be filed on, and would I file it with launchpad or Mozilla?

---

### Post by Fury5000 on 2008-06-26
are you running "adobe" flash on both machines?.. I have not seen the problem your describing since the flash was repaired.  Load up Epiphany and see what it does.  If it does the same thing I would think it to be your flash version.

---

### Post by crjackson on 2008-06-26
> **Fury5000 said:**
> are you running "adobe" flash on both machines?.. I have not seen the problem your describing since the flash was repaired.  Load up Epiphany and see what it does.  If it does the same thing I would think it to be your flash version.

Both machines have adobe (only) flash installed.  I visit many sites that are flash enabled and none of them have this problem.

```
    File name: libflashplayer.so
    Shockwave Flash 9.0 r124
```

---

### Post by sports fan Matt on 2008-06-26
no lock up here but an interesting find: The cursor starts to almost flash and jump wildly right where the big black area under "boot menu is"

---

### Post by Fury5000 on 2008-06-26
damn.. I wish I could remember what the issue was with that site and my pc.  It was the only web site that gave me that problem and it was a site that I visit often.  What happens when you visit the site with a diff browser on that same pc?.. The results of this would be key.

---

### Post by crjackson on 2008-06-26
> **Fury5000 said:**
> damn.. I wish I could remember what the issue was with that site and my pc.  It was the only web site that gave me that problem and it was a site that I visit often.  What happens when you visit the site with a diff browser on that same pc?.. The results of this would be key.

haven't tried that yet.  running off to work now...

---

### Post by philinux on 2008-06-26
No probs here, I'm using flash 10

---

### Post by crjackson on 2008-06-26
> **philinux said:**
> No probs here, I'm using flash 10
Okay, logged in at work now...

Cool, have you had any issues with flash 10 at all?  Did you download the binary from the flash site to install, or is there a better way?

---

### Post by o.besner on 2008-06-26
The page works perfectly for me. I have firefox 3, every updates, and I installed Flash (9) and Java with the "Ubuntu Restricted Extras" package

Someone said it could be the graphic driver... I've tweaked my Xorg.conf with nvidia-xsettings so the resolution and the refresh rate is correct. Maybe you could check it out, if you have an Nvidia card. But I'm pretty sure it's not the graphic card. Probably Flash...

Is your installation up to date, or are you running firefox beta ?

---

### Post by crjackson on 2008-06-26
> **o.besner said:**
> The page works perfectly for me. I have firefox 3, every updates, and I installed Flash (9) and Java with the "Ubuntu Restricted Extras" package

Someone said it could be the graphic driver... I've tweaked my Xorg.conf with nvidia-xsettings so the resolution and the refresh rate is correct. Maybe you could check it out, if you have an Nvidia card. But I'm pretty sure it's not the graphic card. Probably Flash...

Is your installation up to date, or are you running firefox beta ?

It's not the beta version and all updates are installed.  I've tried on 2 different machines.  One has the nVidia card listed in my sig, and the other is an ATI card with restricted drivers installed.

I have a few more machines at the house that have Gutsy/FF2 installed, I'll give them a try tomorrow and see.

---

### Post by silkstone on 2008-06-26
No problems here - Flash 10 beta on FF3.

To install Flash 10, I followed the guide in the thread below. Scroll right down to the section on Troubleshooting - Adobe Flash. It tells you how to do it from the tar archive downloaded from Adobe's website.

I also found it necessary to delete libflashsupport.

Before this, FF was exiting regularly when trying to load flash video. It hasn't missed a beat since.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by philinux on 2008-06-26
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Above poster spot on.

I'm on 64 bit and have libflashsupport installed with no probs at all.

---

### Post by Fury5000 on 2008-06-26
thanks for the info on flash 10...I didnt even know I could run it.  I just installed it and will do some tests with it.  After FF3 went final I was starting to have crashing issues again on youtube.  This will prob fix that.

---

### Post by silkstone on 2008-06-26
It should do. I was getting problems with You Tube and the BBC website videos. The first one would run OK, but FF then closed while loading the second or third. Good luck!

---

### Post by crjackson on 2008-06-27
I installed the new version of flash and sadly that didn't fix the problem.  Any other ideas?

---

### Post by Fury5000 on 2008-06-27
so... how did that test go with the alternate browser?...hmmm?...  see what that does.. 

then... maybe an interesting test would be to boot from a live cd...run FF Beta and go there and see what it does.  I think that would be running a universal vid driver and might let u know if thats the issue.

If that page works from the live CD then I would think it to be the vid driver.  That might have been the prob I had..

---

### Post by silkstone on 2008-06-27
How did you install it? Did you follow the guide under 'Troubleshooting - Adobe Flash' near the end of this post?

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Also, have you uninstalled libflashsupport, and deleted the file pluginreg.dat in .mozilla/firefox/xxxx/  ?

---

### Post by crjackson on 2008-06-27
> **silkstone said:**
> How did you install it? Did you follow the guide under 'Troubleshooting - Adobe Flash' near the end of this post?

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Also, have you uninstalled libflashsupport, and deleted the file pluginreg.dat in .mozilla/firefox/xxxx/  ?

I followed the instructions near the end of the post.

I didn't uninstall libflashsupport or delete pluginreg.dat

---

### Post by crjackson on 2008-06-27
There is no problem with live CD and no flash installed.  The page worked flawlessly.

---

### Post by silkstone on 2008-06-27
Try uninstalling libflashsupport. The version in the repos is for Flash 9 anyway.

---

### Post by crjackson on 2008-06-27
> **silkstone said:**
> Try uninstalling libflashsupport. The version in the repos is for Flash 9 anyway.


10-4, I'll do that after I get home from work and report back.  What exactly is libflashsupport intended for anyway?

---

### Post by Fury5000 on 2008-06-27
> **crjackson said:**
> There is no problem with live CD and no flash installed.  The page worked flawlessly.

Ok good... well I dont even know if there is "flash" effects running on the page in question.  I dont have time to confirm at the moment going out the door.  If no flash then it would have to be your vid driver.  Maybe some java problem also.

---

### Post by crjackson on 2008-06-27
> **Fury5000 said:**
> Ok good... well I dont even know if there is "flash" effects running on the page in question.  I dont have time to confirm at the moment going out the door.  If no flash then it would have to be your vid driver.  Maybe some java problem also.

I'm skepticle about it being a video driver problem.  I've now confirmed the same issue on 3 of my systems.  Each of them with a different video card/driver (nVidia, ATI, Intel).  It's obviously someting all three systems have in common, I just have to nail it down.

---

### Post by Fury5000 on 2008-06-27
Yea cant be vid on all 3 pc's..  and the prob started after ff3 final...yet we cant duplicate it.  You might have some add-on or plugin that we dont that is causing this problem.  Something you use on all 3 machines.

---

### Post by markbuntu on 2008-06-27
Libflashsupport must be removed for flash 10 to work properly. If you downloaded flash10b from adobe you must replace the libflashplayer.so in usr/lib/flashplugin-nonfree with the libflashplayer.so in the package you downloaded. Do not run the installer. If you did, move the new libflashplayer.so to usr/lib/flashplugin-nonfree and replace the file that is there with the one you downloaded.

The reason for this is to keep your flash integrated with the update scheme. If it is not in usr/lib/flashplugin-nonfree any update may be ignored because any libflashplayer.so in another place may be found first by firefox.

---

### Post by crjackson on 2008-06-28
> **markbuntu said:**
> Libflashsupport must be removed for flash 10 to work properly. If you downloaded flash10b from adobe you must replace the libflashplayer.so in usr/lib/flashplugin-nonfree with the libflashplayer.so in the package you downloaded. Do not run the installer. If you did, move the new libflashplayer.so to usr/lib/flashplugin-nonfree and replace the file that is there with the one you downloaded.

The reason for this is to keep your flash integrated with the update scheme. If it is not in usr/lib/flashplugin-nonfree any update may be ignored because any libflashplayer.so in another place may be found first by firefox.

As it turns out I must have removed libflashsupport as some point during the v10 install.  I just checked and it's not installed, so that's not the problem.

---

### Post by Fury5000 on 2008-06-28
I know im beating a dead horse here but... what happened when you ran a secondary browser..  like Epiphany...  that would be the same flash but on a non FF3.0 platform.  Just trying to rule one thing out at a time.

---

### Post by crjackson on 2008-06-28
> **Fury5000 said:**
> I know im beating a dead horse here but... what happened when you ran a secondary browser..  like Epiphany...  that would be the same flash but on a non FF3.0 platform.  Just trying to rule one thing out at a time.

It works great with Epiphany.  No lockups.  How do I get flash support on Epiphany?  Currently it's not playing flash at all.

---

### Post by crjackson on 2008-06-28
This is my version.  Does everyone else show the same?

```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0
```

---

### Post by crjackson on 2008-06-28
> **Fury5000 said:**
> Yea cant be vid on all 3 pc's..  and the prob started after ff3 final...yet we cant duplicate it.  You might have some add-on or plugin that we dont that is causing this problem.  Something you use on all 3 machines.

I don't have any addons installed.

---

### Post by Fury5000 on 2008-06-28
> **crjackson said:**
> This is my version.  Does everyone else show the same?

```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0
```

yup.. i got those same numbers...  

Didnt Epiphany prompt you to install flash?.. On my system flash was automatically in there and updated at the same time FF called for it.  It reads Flash 10 when I look at the settings in Epiphany.  I guess I could un-install Ephipany and re-install just to see what happens when  I visit a flash site.

---

### Post by Fury5000 on 2008-06-28
ok.. just did a test.. picked another browser out of the repository... called Galeon... ran it... went to youtube and flash was already working.. so in Epip it should also be working right out of the box.  If not something is damaged.  How on 3 machines I dont know.  I would think a broken update for one but not all 3.

---

### Post by crjackson on 2008-06-28
> **Fury5000 said:**
> ok.. just did a test.. picked another browser out of the repository... called Galeon... ran it... went to youtube and flash was already working.. so in Epip it should also be working right out of the box.  If not something is damaged.  How on 3 machines I dont know.  I would think a broken update for one but not all 3.

I didn't test Epip on 3 machines only one.  Flash is installed using the guide for flash 10, not through the repos.

---

### Post by crjackson on 2008-06-28
Is it possible to completely remove FF3 and reinstall it without messing up anything else.  Perhaps if I installed FF3 from scratch it wouldn't have this issue.

---

### Post by kenpogi on 2008-07-02
I've been reading these posts as I have the same problem, machine is a Sony TX2 running Hardy, when I clicked on your Softpedia link the screen locked and I had to "force quit", I have just removed FF3 completely and reinstalled Firefox 2 and it now works, it did not ask for Adobe flash or anything else, just went straight to Softpedia website, I'm not very Linux savvy but I've been trying to run Linux for 9 months now and its very frustrating!!
Hope my experience helps.

---

### Post by crjackson on 2008-07-02
> **kenpogi said:**
> I've been reading these posts as I have the same problem, machine is a Sony TX2 running Hardy, when I clicked on your Softpedia link the screen locked and I had to "force quit", I have just removed FF3 completely and reinstalled Firefox 2 and it now works, it did not ask for Adobe flash or anything else, just went straight to Softpedia website, I'm not very Linux savvy but I've been trying to run Linux for 9 months now and its very frustrating!!
Hope my experience helps.

Thanks for the reply.  I've been considering reinstalling Ubuntu from scratch.

---

### Post by crjackson on 2008-07-15
As it turns out it WAS/IS a browser theme issue.  I changed and tried several different themes.  I'm now using "Modern Modoki 3.01" and with this theme the problem is GONE.  I has installed a system wide theme called "MacUltimate Leopard" which I REALLY like.  The problem is it even changed the browser theme so the default is no longer the Firefox default.  IOW when the Firefox default theme is selected, you actually the MacUltimate Leopard browser theme.  That theme is okay, but rather boring and buggy as it turns out.

Tonight I tried several different themes and this one fixed the long standing issue.  I put this theme on several of my systems because I liked it so much (mostly the icon set) and so that seems to be the root of all my page loading evils.  Issue Solved.  Thanks to everyone for your suggestions.

---

### Post by Fury5000 on 2008-07-15
> **Fury5000 said:**
> Yea cant be vid on all 3 pc's..  and the prob started after ff3 final...yet we cant duplicate it.  You might have some add-on or plugin that we dont that is causing this problem.  Something you use on all 3 machines.


Ah!.. thanks for posting a follow up to this problem for those curious.  I figured it had to be one add-on item that you were running on all 3 machines.  Wow.. I would not have guessed themes to cause this much trouble.  Now when people have problems we need to ask what theme they are using and tell them to go back to the default and see if the problem goes away before moving to the next step.  wonderful.  :???:

---

