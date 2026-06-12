---
title: "NEED Vent- New To Linux"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Rych on 2008-09-23
Ok so I see a lot of posts which tell me to insert code and do stuff that I'm just not able to do at this time having just installed Ubuntu.

I NEED Ventrillo

I am a WoW Addict- I play every night and just got into a raiding guild that requires me to use Vent when raiding.

I know there are other programs that are native linux programs, other games and other ways to voip but I wait to talk to my raiding guild in my favorite game on my computer.

That being said could someone walk me through the idiots guide to getting Vent to work on Wine?


I have WoW and Wine installed by a friend. Don't know how to get vent on there.

Thanks!

---

### Post by Bablefish on 2008-09-23
I just checked it seems they are actually working on a Linux version
[http://www.ventrilo.com/download.php](http://www.ventrilo.com/download.php)

---

### Post by digitalvectorz on 2008-09-23
Hey, check this out.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9832)

hopefully that helps.

---

### Post by Rych on 2008-09-23
Wow that would help.

I don't understand that "How To"

It's like me telling you that in order to do open heart surgery you have to make a bilateral incision over blablabla in six different languages.

I don't understand the first step and I know if I make my first cut I'm going to kill my pc. 


SO

Configuration:

You must place a copy of msgsm32.acm in ~/.wine/drive_c/windows/system for Ventrilo to work. This file can either be obtained from an existing Windows installation (C:\WINDOWS\System32), or it can be downloaded from Filefront (recommended) or Driverguide(free registration required).

Edit ~/.wine/drive_c/windows/system.ini and add the following under the drivers32 section: MSACM.msgsm610=msgsm32.acm

Set winecfg audio settings to use ALSA, choose emulation for the acceleration, and tick the driver emulation box.* 



CAN SOMEONE REPEAT THIS IN ENGLISH? Thanks

YT- Noob

---

### Post by Rych on 2008-09-23
Ok I downloaded that thing and went to "Browse C drive" then I went to WINDOWS and SYSTEM the folder was empty and I put the file in there.


That is all I have done so far :)

EDIT : I did the sound thingy in "Configure Wine" then went to audio. ALSA was already ticked. I changed the drop down menu to Emulation. 

I'm scared :)

---

### Post by mikewhatever on 2008-09-23
Now, you need to open that file for editing, presumably with a text editor, and add MSACM.msgsm610=msgsm32.acm under the driver section.

---

### Post by jerome1232 on 2008-09-23
And you thought it was open heart surgery, these are actually quite simple next step it's asking you to edit a text file and insert the line it tells you to. We can do that.

It says 'Edit ~/.wine/drive_c/windows/system.ini and add the following under the drivers32 section: MSACM.msgsm610=msgsm32.acm'

So assuming you are using Ubuntu we can use the defualt text editor for this you can do it command line (easier) or point and click I'll give the command line.

Press alt+f2 then type 'gnome-terminal' and hit enter, now copy and paste this command, it's telling gedit to open our file.

```
gedit ~/.wine/drive_c/windows/system.ini
```
For me this is a small text file so you should be able to see the drivers 32 section, otherwise hit ctrl+f to bring up the search function and type 'drivers32' since that is the section we are looking for and add the line 'MSACM.msgsm610=msgsm32.acm' underneath where it says drivers32. Now hit ctrl+s to save.

Now you should be back at a terminal window, let's do the last change.

Type winecfg to bring up the wine configuration tool. Click on the Audio Tab and make sure the box that says ALSA is checked.

According to your guide it wants you to use the drop down menu towards the bottom take it off a full and change it to emulation. Then check the box for driver emulation it's down towards the bottom as well.

Hope this helps

---

### Post by hyper_ch on 2008-09-23
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

