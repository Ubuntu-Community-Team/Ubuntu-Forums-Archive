---
title: "Only works in Safe Graphics Mode (Intel G33)"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by insaini on 2008-06-23
ok so there is this thread here..

[http://ubuntuforums.org/showthread.php?t=817181&highlight=G33](http://ubuntuforums.org/showthread.php?t=817181&highlight=G33)

but it didnt help my cause..

to begin with.. i just put together a system comprised of

Core 2 Duo 7200
2GB DDR2 8500
250 GB HD
All in one board (graphics is Intel G33)
Kubuntu 8.04 (64-bit)

 Basically .. ive installed this thing atleast 7 times over now.. what's happening is that when I install in Normal mode.. it installs just fine.. no graphics problems or anything.. however once it gets to the login screen and i login.. thats when everything changes.. the mouse pointer becomes atleast 4 times the size.. the taskbar at the bottom seems fine.. but clicking on the menu icon or anything else results in an oversized window with fond that is like 200pt .. you cant even see the menu choices or anything..

When I install in Safe Graphics Mode.. the graphics look just fine.. but its using the vesa driver.. so when I attempted to switch it over using the instructions here [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html) (starting with instruction 5) .. then restart the X server.. it goes back to the EXACT same results as installing from Normal mode.. 

about the only thing I can think of now is to rebuild the driver.. but this is not making any sense to me.. maybe someone has seen this or knows how to fix this.. its kind of rediculous really..

thanks

Jesse

---

### Post by phidia on 2008-06-23
Try [the guide here]("https://help.ubuntu.com/community/Video") from the community wiki.

---

### Post by insaini on 2008-06-24
> **phidia said:**
> Try [the guide here]("https://help.ubuntu.com/community/Video") from the community wiki.

thanks for the link.. however this has not helped me..

I ran the command
sudo dpkg-reconfigure -phigh xserver-xorg  

and this didnt ask me any questions at all..simply stated it overwrote a configuration file and that was that.. i looked at the xorg.conf and well it was your basic 8.04 config file once again using the vesa driver..

lspci | grep VGA 

returns that i have a 82G33/G31 Express Integrated Graphics ..

I did a search and it seems there are numerous people having problems specifically related to this 

it may even be blacklisted in some config file or something?

in any case i think i may be stuck buying a new video card which i really dont want to do..

does anyone know more about this.. and if building the driver from scratch would fix this?

J

---

### Post by phidia on 2008-06-24
Don't run the dpkg command with the phigh option and you will get to make the selections yourself. > sudo dpkg-reconfigure xserver-xorg
You will need to know your video card and monitor specs though.

---

### Post by insaini on 2008-06-24
> **phidia said:**
> Don't run the dpkg command with the phigh option and you will get to make the selections yourself. 
You will need to know your video card and monitor specs though.

Thanks ill give that a try when i get home today..

---

### Post by insaini on 2008-06-25
> **phidia said:**
> Don't run the dpkg command with the phigh option and you will get to make the selections yourself. 
You will need to know your video card and monitor specs though.

Well I tried this out.. but apparently the only thing important enough to ask questions about is my keyboard.. seriously.

This is actually incredible.. i really cant believe its this difficult to get something that should be reasonably simple working.. 

I even selected the exact monitor as it was coming up as PlugNPlay .. so I specifically chose the monitor I have.. a Sony Multiscan 20se .. and when I restarted.. it went straight to the console.. rediculous.. 

sorry for the rant.. but its frustrating especially when you had some high hopes .. i built the system specifically for ubuntu.. i guess I should have built something with a lot more obsolete hardware..  either that or im stuck waiting for some major updates..

I will try building the video driver.. but i doubt it will work.. i even tried the 915resolution package.. but ive read its for the i810 driver.. which again takes me straight to the console .. the intel driver works.. the resolution is just rediculous.. i cant even check to see what resolution its giving me because everything is absolutely huge.. cant even take screen caps or anything.. the mouse pointer becomes like 6x the size.. im sure it has to do with the resolultion.. but the taskbar itself seems just fine even the icons in the task bar are fine.. but when you click on anything.. or even right click on the desktop.. the resolution is so bad that the entire screen is filled with like the bottom corner of whatever window pops up.. 

is there anyway i can set the resolution of the monitor in the xorg.conf file? id like to set it to 640x480 at least maybe it will help.. and just exactly how do i use the 915resolution package?  i still think it might at least help a little..

J

---

