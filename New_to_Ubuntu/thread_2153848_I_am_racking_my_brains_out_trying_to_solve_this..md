---
title: "I am racking my brains out trying to solve this."
date: 2013-06-12
forum: New to Ubuntu
---

### Post by Maelstorm on 2013-06-12
i've got an i7950/nvidiagtx 460se.  i tried installing ubuntu 12.04. everything went fine up untill install was over.  When i opened firefox i could not click any links or buttons in firefox. i could click file edit view ect and the side bar with other icons.  somehow i don't remeber how pure luck mostly i finally would get to be able to click inside fire fox but then i couldn't click on anything outside.  if i saved a file the dialog box would pop up and if i tried to click it it just din't work. instead the click went straigth through to firefox.   this happened with EVERY app. if i opened anything i couldn't click on anything in it i had to tab over to that and hit enter or space.  i did this with default non proprietary nvidia driver. i did it with all 3 bundled nvidia drivers. i even downloaded the nvidia drivers from it's website and i think i installed it right (long ass methods that varied from one to another.)  after about 5 hrs i gave up and tried mint. same problems.  i tried the irc chat but seems slammed and i was just told that proprietary drivers just don't work most of the time.  so basically no help there.

---

### Post by searchfgold6789 on 2013-06-12
Which driver are you using now (from Additional Drivers or nVidia website and what version), and what is the state of the machine?
Can you post the contents of /var/log/Xorg.0.log ?

---

### Post by Maelstorm on 2013-06-13
> **searchfgold6789 said:**
> Which driver are you using now (from Additional Drivers or nVidia website and what version), and what is the state of the machine?
Can you post the contents of /var/log/Xorg.0.log ?

can't post the /var/log/Xorg.0.log as i removed .. i'll try resintalling today again and since i know it will happen i'll post it afterwards.

After fresh install it uses nouveau and it does it.
i did the recommended driver (duno what number but ti's the first one in the list when i clicked the driver icon.  Still did it
i tried the 2nd driver (post update)  and it still did it.
i tried the latest driver on the list .. still did it

i tried downloading the latest .run file from nvidia (319 i belive) and it gave me an error about install script and after the install almost semed to work but no it still messed up.

i followed multiple guides (including blacklisting the nouveau driver. still did it.)

i even followed one guide that had me ctrl-f1 to exit to terminal and do it all from command prompt.  still din't work.

this help narrow it down?  I really don't think it's the video drivers.  it has to do with mouse focus locking into inside firefox.

example: if i was in the install right now i could type all this but i could not click on file edit view ect..   if i right clicked an image and save image.  the popup with save options would be unclickable.  if i clicked on anything on that it the mouse would actually ignore it and still be clicking on firefox (if there is a link or something to click that would get clicked instead of the new pop up.  also can't click on icons on the right side bar.

i have to close firefox .. and sometimes i can click it.  most of the time i still can't click any icons unless i restart the machine.

i tried using special key to open the ubuntu icon (top icon) and i could type xterm to get the shell.  from there i could type but not paste into it.  if i tried to type in a dialog box in firefox any typing went to the terminal instead.  i could not click on firefox to get it to shift focus back untill i closed xterm.

Could mouse drivers be causing this? i'm using a rat 7 but i din't load any special settings for it i just went with whatever ubuntu defaulted to (all the buttons worked fine).

---

### Post by searchfgold6789 on 2013-06-13
Good call on the mouse! I found a guide here: [http://fcns.eu/2011/04/01/cyborg-rat-7-mouse-under-linux/](http://fcns.eu/2011/04/01/cyborg-rat-7-mouse-under-linux/)

---

### Post by Maelstorm on 2013-06-13
> **searchfgold6789 said:**
> Good call on the mouse! I found a guide here: [http://fcns.eu/2011/04/01/cyborg-rat-7-mouse-under-linux/](http://fcns.eu/2011/04/01/cyborg-rat-7-mouse-under-linux/)

brb pounding my head against a brick wall for all the time i've spent messing with video drivers. lol thanks. i'm writing the info down so when i re-install i'll be doing this. it looks like the exact problem i am having.  i'll reply here later on tonight with if it fixes it up.

Update:

i followed the instructions you linked but it seemed to mess up a little. 

when i first did the edit i realized there was no xorg.conf file.   so i decided to run the nvidia install from the default 3 options in base install.   that generated an almost empty xorg.conf file.   i then edited it in pico instead and added what it stated. 

seems to be working now. thanks!

---

