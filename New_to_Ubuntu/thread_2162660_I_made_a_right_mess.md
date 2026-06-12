---
title: "I made a right mess"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by DaveMcC on 2013-07-15
I am a photographer, not a computer person, so I need a lot of help, step by step.
My set up was Ubuntu 10.10 "Mavrick" for uploading photo's + a wee bit of gimp "resize down some photo's"
xp to edit photo's, funny how all editing programs for photo's are win based
Second hard drive which stores all my work, can be unplugged (that keeps it safe)
I then got a 3rd drive installed for win7 64bit as my D800 files kept killing xp, files from the D3 and D7K, didn't cause it to fall over

What I need to know is, how do I do a restore on Ubuntu 10, tryed ver 13, didn't reboot, tryed ver 12lts but ! gimp 2.6 has all the File - Edit - View - Tools etc missing from the top and Ctrl + V don't work, can't paste any photo's in, never mind opening them ????
Second, Need to copy from Google Earth the "MyPlace" folder, have been looking for a couple of weeks now for it, can't find it, it's needed as I have loads of place marks for long / lat readings.

Recap
win xp is going to be fully replaced. that will kill the boot menu thing "bug / grub ??? thing" hence
Restore Ubuntu 10 64bit............which I like better than ver 12 - 13 of Ubuntu

Thanks in advance

Dave

---

### Post by Cheesemill on 2013-07-15
I would highly recommend not installing 10.10 as it hasn't been supported for over a year now meaning that any bugs or security issues that have been discovered will never get fixed. It is a very bad idea using an unpatched out-of-date OS.

If you use 12.04 and take a closer look you will find that the menus for Gimp (and every other application) haven't disappeared they have just been moved to the top of the screen (the so-called global menu). This can easily be disabled to put the menus back in their old location.

---

### Post by DaveMcC on 2013-07-15
[QUOTE=Cheesemill;12732187
  This can easily be disabled to put the menus back in their old location.[/QUOTE]

How can that be done?? and the task bar down the side, it keeps catching my eye, "very off putting" like win8 silly stupid bar thing

Dave

---

### Post by Cheesemill on 2013-07-15
If you want to install 12.04 but have it behave like the old versions of Ubuntu instead of using the new Unity interface then take a look at this page on the wiki...

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by DaveMcC on 2013-07-15
That's not bad, I think I could do that, if not,,, Cheesemill,,,,,, you will have to come to Norn Iron and fix it for me, I'll even let you go to the riots, "if you want"
joking aside, that just leaves the hidden missing I can't find the "KML file from google earth" to back up, and restore into the new ubuntu version

Dave

---

### Post by Cheesemill on 2013-07-15
Have a look at the hidden files in your home folder (hit CTRL+H to see them).

There will probably be a folder called ~/.googleearth or ~/.config/googleearth that contains the user settings.

---

### Post by craig10x on 2013-07-15
By the way...the unity bar (it's really a dock) can be set to auto-hide and you can do that in system settings in appearance (behavior) section...then it will only slide out when you actually need it!
You can also increase the sensitivity in terms of how much you need to push against the left to make it come out...and you can also reduce the size of icons..i set mine to 38 pixels...to me, it looks better that way...The global menu is not really bad if you give yourself a bit of time to get use to it... and it is a space saver ;)

---

### Post by DaveMcC on 2013-07-15
> **Cheesemill said:**
> Have a look at the hidden files in your home folder (hit CTRL+H to see them).

There will probably be a folder called ~/.googleearth or ~/.config/googleearth that contains the user settings.

Ah, small problem, grub, as I have now to run off CD to get into ubuntu, how can I reactavate grub, think that's the boot booter?? or as I can not find the above, I am now lost

Dave

---

### Post by oldrocker99 on 2013-07-15
[http://community.linuxmint.com/tutorial/view/245](http://community.linuxmint.com/tutorial/view/245)

Is a very good resource for how to reinstall GRUB from a live CD/USB stick. Use netbootin to create a bootable USB stick to save yourself a good ten minutes or so. While you're running from the USB, if at all you can copy your /home folder to an external drive, then you can reinstall safely without losing anything important. ALL your own settings in GNU/Linux are saved in .hidden directories in your home folder. You can use a file manager to back up your drive, just use View/Show Hidden Files, or press CTRL-H as a toggle.

When you're reinstalling, you can use the "Something Else" for how it should be installed. I make two partitions, one ~128GB for the system folder, and the rest of the drive (plus the swap partition) for the /home folder on its own partition (select 'mount as /' for the system partition, and 'mount as /home' for the bigger partition).

This way, should you foul up your system to an unrunnable state (which I have certainly done myself:rolleyes:), you can always reinstall. This is what you have to do anyway, if you use, say, Mint, or Ultimate Edition, and this way, you simply have to reinstall your own personal favorite programs, and having a separately mounted /home partition will make all your programs set to go as you last used them.

---

### Post by DaveMcC on 2013-07-15
> **oldrocker99 said:**
> [http://community.linuxmint.com/tutorial/view/245](http://community.linuxmint.com/tutorial/view/245)

Is a very good resource for how to reinstall GRUB from a live CD/USB stick. Use netbootin to create a bootable USB stick to save yourself a good ten minutes or so. While you're running from the USB, if at all you can copy your /home folder to an external drive, then you can reinstall safely without losing anything important. ALL your own settings in GNU/Linux are saved in .hidden directories in your home folder. You can use a file manager to back up your drive, just use View/Show Hidden Files, or press CTRL-H as a toggle.

When you're reinstalling, you can use the "Something Else" for how it should be installed. I make two partitions, one ~128GB for the system folder, and the rest of the drive (plus the swap partition) for the /home folder on its own partition (select 'mount as /' for the system partition, and 'mount as /home' for the bigger partition).

This way, should you foul up your system to an unrunnable state (which I have certainly done myself:rolleyes:), you can always reinstall. This is what you have to do anyway, if you use, say, Mint, or Ultimate Edition, and this way, you simply have to reinstall your own personal favorite programs, and having a separately mounted /home partition will make all your programs set to go as you last used them.

Lets see if I understand what you have wrote, I am still running Live CD, "ver10.10 Mavrick" I click on Place/GB Filesystem, then copy / paste home folder to USB stick? 3 685 items 15.5gb in size which is 10% of the drive

Edit,,,,,,what if, I want to upgrade from 10.10 to 12.??lts does the above still work, as it says it's for mint, which I grow out in the back yard, sweet mint, peppermint, orangemint..........

Dave

Update or edit.** Error while copying**. The folder ".*UserPrefs*" cannot be handled as you do not have permission to read it.

OK, have got 12.04lts running here and thanks to Cheesemill and his link to copy paste in to change the look back to older looking version 

I have also found and been able to copy the files "MyPlace" for google earth, BUT but from past trys I have always had problems getting google earth installed, guess what ! ver 12 ain't any better, 
I had to start Terminal, then Sudo ??????????????????????/ followed by password 

I am doing my testing here on a seperate hard drive I have my work drive and win7 drive unplugged, so when I get this final part installed "finalised" I will (try :confused::rolleyes::neutral:](*,):-({|= it will be fun) and put ubuntu 12.04 onto my shared drive with xp, seperate partition, so as I get the choice of where to boot into 
Ubuntu
xp
win7

Installing google earth ?? please

Dave

Got it, this is what I needed

[http://www.liberiangeek.net/2012/04/install-google-earth-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/install-google-earth-in-ubuntu-12-04-precise-pangolin/)

Thanks al
Dave

:guitar::guitar:

---

### Post by Ultra Cronic on 2013-08-17
[INDENT] 					I am a photographer, not a computer person, so I need a lot of help, step by step.
My set up was Ubuntu 10.10 "Mavrick" for uploading photo's + a wee bit of gimp "resize down some photo's"
xp to edit photo's, funny how all editing programs for photo's are win based----snip2save--
[/INDENT]

---------------------


It may seem shallow and devoid of professionalism to rant, but Being a Video&#8221;naut&#8221; I never was happy with Linux video editing from the start but love the fact I have no License Cops spying on me on a software level so I put up with video editing idiosyncrasies as much as I can.  UNTIL!!!
 

     Ultima Edition 3.5 64 bit came along.   That was the only Linux OS that offered a &#8220;Working&#8221; version of Cinelerra out of the box with no tweaking and dep chasing.  It was like running Windows XP with  
 Adobe Premiere and Photo suite on it. Sure it has some quirks  about it, I hate not being able to use Control &#8220;C&#8221; and control&#8221;V&#8221; in the terminal, but the Multi Media part of the deal is a two thumbs up.  
 

 Now if they could get the muon software center [I call it &#8220;moron&#8221; software...ctr.] to work and give me my cut and paste xterm features I would be all in with this one.  
 

 I know your request is a &#8220;Still-Pic&#8221; request in nature, But any OS that can run Cinelerra well can do just about anything Media related,  STAY AWAY from the 32 bit version, Cinelerra takes a dump every time I use it for a BIG video. Gimp may work for your photos however.  If you can borrow a 64 bit machine and or a hard drive and install 64 bit UE 3.5 [it's based on Linux ubuntu 13.04 LOADED to the hill with extras].  You don't have to chase dependencies and 3rd party codecs to get this to work, These guys have done it for you. I'm not a Lawyer so I'm not sure of the ethics in this one.
They have several Versions to suite ones tastes, Some are centered around "Gamers" and others Media.
I am experimenting with 3.5 .
 Google it Ultima Edition 3.5 read on....
 

 OK nuff for now.

---

