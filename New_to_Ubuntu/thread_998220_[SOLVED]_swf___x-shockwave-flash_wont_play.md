---
title: "[SOLVED] swf   x-shockwave-flash wont play"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by capnthommo on 2008-11-30
i think i managed to lose the previous attempt so sorry if it looks like i'm repeating.
anyway, i cant get anything to happen when i try to play a swf x-shockwave-flash file.  when i try to open/play using gnash swf viewer nothing happens.  i have tried to use other apps eg mplayer but either nothing happens or i get an error message.  can you tell me what i'm doing wrong?  remember, after 10+ years of only using windows i am not comfortable with much more than 'point at the icon and click' processes so i am a bit scared of entering things into a terminal as is so often advised.  perhaps i need an evening class in ubuntu!  help
nigel

---

### Post by SunnyRabbiera on 2008-11-30
Well the default flashplayer included with ubuntu wont really play most flash files that well, for that you will need the official flashplayer.
Lucky for you there is a installer available for ubuntu here:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

In the pulldown menu just select the version of ubuntu, done :D

Now as for actual shockwave, there you will probably face issues, adobe has yet to release shockwave for anything other then windows, a way around this is to install wine, install firefox in wine and then install shockwave player.

---

### Post by capnthommo on 2008-11-30
okay thanks, i have downloaded adobe and i already have wine (though i dont really understand it) so do you mind if i ask how you install firefox (i already have that too) in wine and then install shockwave player as you recommend.

---

### Post by Chunky Dunk on 2008-11-30
To install flash do "sudo apt-get install flashplugin-nonfree"

As for Shockwave, there are instructions here: [https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)
That tells you how to use the Windows version of Shockwave under Wine, since there's no native Linux version of it.

If all goes well, you should be able to open these files in Firefox.

---

### Post by gandaran on 2008-11-30
> **capnthommo said:**
> okay thanks, i have downloaded adobe and i already have wine (though i dont really understand it) so do you mind if i ask how you install firefox (i already have that too) in wine and then install shockwave player as you recommend.
shockwave files plays in linux firefox with flash installed just as they will play in a firefox installed in wine with windows flash.
now there is another type of shockwave with activex control, these files only play in internet explorer, that's why there's an activex shockwave player for windows and not for linux, these files will never play in linux or any version of firefox.

---

### Post by SunnyRabbiera on 2008-11-30
> **capnthommo said:**
> okay thanks, i have downloaded adobe and i already have wine (though i dont really understand it) so do you mind if i ask how you install firefox (i already have that too) in wine and then install shockwave player as you recommend.

Installing the windows version of firefox under linux is easy, first download it here:
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

just download the english windows version, when finished just click the installer like you would do in windows and wine will do all the rest.
But you may wish to configure wine a tad before doing this.
Dont worry, its easy, go to your wine submenu, select "configure wine"
In the first tab there is a pulldown menu that will make wine work likje XP if you select the xp option, after that hit ok and you will be fine to go.
Installing shockwave should not be an issue, again you will be installing it the windows way so no command line or anything like that needed.

---

### Post by capnthommo on 2008-11-30
so, gandaran, if the file is of the activex type there is no point trying to view in ubuntu/firefox anyway?  is that right?
thanks
nigel

---

### Post by SunnyRabbiera on 2008-11-30
> **capnthommo said:**
> so, gandaran, if the file is of the activex type there is no point trying to view in ubuntu/firefox anyway?  is that right?
thanks
nigel

well you could also try ie4linux:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

It could work in some cases, just be careful as ie4linux is made mainly for testing though I have yet to bump into any major mission critical issues.

---

### Post by Farmer of Bricks on 2008-11-30
Quite Simple Steps:
1. Go to [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/").
2. Click on the drop-down box that says "Select version to download..."
3. Click on ".deb for Ubunti 8.04+"
4. Click on "Agree and install now"
5. In the box that pops up, choose "Save file" (Assuming you're using Firefox, shouldn't be too different for other browsers)
6. Click "OK"
7. Save it to some place that you can access easily.
8. Open your file browser. (in KDE, it can be Konqueror or Dolphin, not sure what in GNOME or XFCE)
9. Go to the file where you saved the file. 
10. Click on the file (Should be called "install_flash_player_10_linux.deb")
11. If "Install package" is clickable, click it. 
12. Give the prompt your password. 
13. Wait while the package installs.
14. When the dialog closes, hit "Quit"
15. Restart any open web browsers. 
16. There you are.

If on step 11 there's a bit of red text saying "Error: Wrong architectire 'i386'," then you'll have to click cancel and do some more drastic stuff.
Open up the package manager. 
Search for flashplugin-nonfree
Install it.
This may or may not work, depending which repositories you've enabled. I suggest you look around on the forums for "flashplugin-nonfree"

---

### Post by capnthommo on 2008-11-30
Okay, everybody it seems to have worked, now i can see a vid of my wife and my dog dressed as elves and doing a barn dance to a bluegrass version os the twelve days of christmas - bizarre.  thanks to all for the support, it really is appreciated cos this is probably the steepest learning curve i have ever experienced (so worth it though).  as i have said, my only computer experience previously has been with various windows versions and they dont tend to encourage actual learning about the process do they.  you may be able to do some pretty cool things, but you dont actually learn how you have done them.  all part of the process of keeping the power with microsoft i suppose.  but i begin to realise i have been a bit like a lab rat - you know - press the button and some food drops into the cage.  anyway, thanks again
nigel

---

