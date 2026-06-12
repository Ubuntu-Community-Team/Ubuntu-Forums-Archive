---
title: "Adobe Shockwave Doesn't Work?"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by mschooler93 on 2011-10-09
Apparently, Shockwave doesn't have a Linux (or Ubuntu) install option. I searched it, and found a few threads elsewhere that people said it won't work at all in Ubuntu. I tried what they say worked for them, running Firefox and Shockwave in Wine, but that doesn't work. 
I have Lucid, and I need shockwave to play a thing for a test. Apparently, I need firefox to go to the website (my school's only advice, from their tech support) but I can use any browser for the part that I need shockwave for. 

[SIZE="1"](Tech Support's only advice, is "make sure firefox is up-to-date" "is firefox completely up to date, at 3.6.x?" wat. facepalm.jpg [/SIZE]

---

### Post by binary00mind on 2011-10-09
> **mschooler93 said:**
> Apparently, Shockwave doesn't have a Linux (or Ubuntu) install option. I searched it, and found a few threads elsewhere that people said it won't work at all in Ubuntu. I tried what they say worked for them, running Firefox and Shockwave in Wine, but that doesn't work. 
I have Lucid, and I need shockwave to play a thing for a test. Apparently, I need firefox to go to the website (my school's only advice, from their tech support) but I can use any browser for the part that I need shockwave for. 

[SIZE="1"](Tech Support's only advice, is "make sure firefox is up-to-date" "is firefox completely up to date, at 3.6.x?" wat. facepalm.jpg [/SIZE]It is not true that schockwave does not work on Wine. 
I have it on my wine (Lucid)both flash & schockwave plus Java. 

Also off the subject but it is good to have installed Visual Basic 6 [[COLOR="Blue"] Visual Basic 6 Runtime [/COLOR]](http://majorgeeks.com/Visual_Basic_Run_Time_d523.html) 
and this little baby [[COLOR="Blue"]Smartalec Common Runtime [/COLOR]](http://majorgeeks.com/Smartalec_Common_Runtime_d4142.html) 

I cannot find previously working download links for the Adobe Flash and schockwave. 
You will have to go to the official site. 
The problem is that the Adobe site will see that you are on linux and may offer you the linux version only. 
However I just visited the site and it seems that they changed their policy. 

If you still have problems get in touch with me via skype or AIM

---

### Post by madjr on 2011-10-09
yea, no shockwave (natively), but gladly it has never been very popular.

Also HTML5 (and the new versions of flash) are going to substitute it, so it really has no future.

even silverlight was abandoned recently

---

### Post by mschooler93 on 2011-10-09
> **madjr said:**
> yea, no shockwave (natively), but gladly it has never been very popular.

Also HTML5 (and the new versions of flash) are going to substitute it, so it really has no future.

even silverlight was abandoned recently

Yeah, well popularity has no relevance is taking a test, where it is required to run. Most schools and businesses don't embrace newer technologies quite so fast as other people.

I have tried running Shockwave on firefox through wine, but it doesn't let me install it. I have the installer (.exe, for Windows, full) and after 5% it says it cannot find something in C:\Windows (I think system32) and it is a folder for Adobe, I believe. And, I don't think there is a Linux version of it (that I can find, which doesn't mean much) if there is, let me know that will make this a lot easier.

I have to go to a church thing, so I'll run the installer and post the error when I get back, Which I should have done first.

---

### Post by madjr on 2011-10-09
> **mschooler93 said:**
> Yeah, well popularity has no relevance is taking a test, where it is required to run. Most schools and businesses don't embrace newer technologies quite so fast as other people.

I have tried running Shockwave on firefox through wine, but it doesn't let me install it. I have the installer (.exe, for Windows, full) and after 5% it says it cannot find something in C:\Windows (I think system32) and it is a folder for Adobe, I believe. And, I don't think there is a Linux version of it (that I can find, which doesn't mean much) if there is, let me know that will make this a lot easier.

I have to go to a church thing, so I'll run the installer and post the error when I get back, Which I should have done first.


Not sure why anyone would code a test in shockwave and not flash. First time i've heard about something like that  (and am a web developer...)

personally, if you have an old windows disk somewhere you can set it up in virtualbox or if someone has a windows computer you can use for a while and get done with that... is very improbable that you will need to use shockwave more than once or twice.

else you can try binary00mind's suggestion and look for a way to get it working on wine.

also i think the app "playonlinux" might make it easier for you if someone made a script for it.

ps. As an affected user, you should give feedback to the institution about using something other than shockwave for the future to avoid similar cases from others.

---

### Post by mschooler93 on 2011-10-09
All right, I have screenshots now.
The first one is the error it gives me, the second is a clearer shot of the second window, and the third is all the steps it took, before crashing. This includes the directory, and everything. 

This is the site I am trying to get onto, if anyone knows a workaround for this particular site, instead of trying to fix the whole shockwave problem.
[explorelearning]("http://www.explorelearning.com/index.cfm?method=cExtAccessSecure.dspResource&ResourceID=63&certificate=authorizer%3dE2020%26userid%3dGizmos4Test%26expires%3d2011%2f10%2f10+02%3a21%3a18%26hash%3d2hIZ4Bjo2nwof8vC02H3Tg%253d%253d") 
And, they use this site for all things like this (where I have to take a test on what it shows me) so they must have some kind of deal with them. Normally, you can't even use this without paying for it, so the school pays them for access, so even if they wanted to switch to another one (without shockwave) they would probably have to wait awhile, and apparently it works with everyone else, and I am the only one having this problem (because everyone else uses Windows XP, and I'm the only "odd" one.)

---

### Post by -kg- on 2011-10-09
Just for S&Gs, you might want to [check out this thread]("http://forums.adobe.com/thread/13494"), especially the last post.  While I've never had any particular success with Gnash, I've never tried it as a Shockwave player.  It might just work.

Lot of problem switching back and forth, though.  You might want to install VirtualBox, then install Ubuntu with Gnash for experimentation purposes.  If it doesn't work then nothing hurt, and you won't have to go through the hoops of switching back to Flash Player, et. al.

If you decide to install VB, be sure to read the manual carefully.  There's a bit of setup you'll need to do prior to installing a VM that will save a lot of pain and frustration.

---

### Post by binary00mind on 2011-10-10
I'm on Windows now doing my work so the only way I could do the shockwave thing was on Vbox emulator (PCLinuxOS)...I installed Flash & shockwave (on another emulator Wine) with no problems but as soon I went to the site that you provided in the last post both Internet Explorer and Firefox froze...I had to kill both processes after 10 minutes...amazing. 
I will try this on XP Pro and Win7 also on Vbox but it is on Lucid so I must reboot.  

The interesting thing is that now I'm on Win7 and I know that I have shockwave and flash installed here and I still failed to see that site in full....The page is empty. with two links to various pdf files....that is it.

---

### Post by mschooler93 on 2011-10-11
I'm setting up VirtualBox now, so I'll see if that works. 

In the meantime, I was talking to the tech support for my school, and the guy there says I have to use the most recent Firefox (which he quoted as 3.6.x) on Windows XP, he said it won't work on later Windows (idk why) and definitely won't work on Mac or Linux. So, they are supposed to be sending me a Windows laptop, for free (which I have to use Windows on it, I have to give it back when I'm out, etc.) so that's kind of good. When I eventually give it back tho, I think I'm going to save the file on it that makes it never start up (shutdown -s, saved as *.bat in startup folder):p

Edit: 
Okay, I got Windows XP working on Virtualbox. It was much easier than I thought or made it out to be. 
I have the whole thing working (shockwave, flash etc.) it's just it's very, very slow. Logging in and navigating to the page takes about 10 minutes. But, then again my computer is not the best. And, it is taking up an extra 10 GB, when I only had about 80 to begin with. I think it's about time to get another one.
Thanks for all the help, guys :p

---

### Post by madjr on 2011-10-11
> **mschooler93 said:**
> I'm setting up VirtualBox now, so I'll see if that works. 

In the meantime, I was talking to the tech support for my school, and the guy there says I have to use the most recent Firefox (which he quoted as 3.6.x) on Windows XP, he said it won't work on later Windows (idk why) and definitely won't work on Mac or Linux. So, they are supposed to be sending me a Windows laptop, for free (which I have to use Windows on it, I have to give it back when I'm out, etc.) so that's kind of good. When I eventually give it back tho, I think I'm going to save the file on it that makes it never start up (shutdown -s, saved as *.bat in startup folder):p

Edit: 
Okay, I got Windows XP working on Virtualbox. It was much easier than I thought or made it out to be. 
I have the whole thing working (shockwave, flash etc.) it's just it's very, very slow. Logging in and navigating to the page takes about 10 minutes. But, then again my computer is not the best. And, it is taking up an extra 10 GB, when I only had about 80 to begin with. I think it's about time to get another one.
Thanks for all the help, guys :p

glad the virtual box suggestion worked :)

anyway XP could use less than 10 gb if i remembered..

as for the *bat that's kinda "ebil" prank :p

i think i would just install **wubi** on it :)

---

