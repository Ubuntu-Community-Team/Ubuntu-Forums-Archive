---
title: "how too ?'s and lingo ?'s"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by uper104 on 2008-04-25
ok so heres the deal... im ian... im working from an ubuntu machine in my computers class and i kneed to figure out some lingo and some other trivial stuff.

1. i would like to customize my desktop to look and work like windows vista

2. i have a 3D desktop launcher that i cant seem to figure out. I've read some post and still cant seem to figure it out. i just need to know how to open multiple desktops 

3. some of the lingo like deskletts and beryl's and stuff ... if somone can describe or direct me a link to a dictionary lol 

thanks

---

### Post by tonyr1988 on 2008-04-25
1) [This site]("http://gnome-look.org/") has a bunch of the interface customizations you may want. One of the cool things about Linux is that you can do whatever you want with it - want it to look like Windows XP, Vista, Mac, DOS? Go ahead! You can get different login screens, icon sets, overall themes, wallpapers, etc. from that site. If you need any more help looking for one (or installing it), let us know.

2) I'm confused by what you're asking? By default, Ubuntu comes with 2 desktops you can switch between, but are you talking about something else?

3) Beryl is old - it is now called *Compiz Fusion*. It basically adds a lot of cool, pretty 3D effects. You need a decent graphics card to run it, and sometimes it slows down your system (and it's still in development, so it will occassionally crash). However, if you want to go ahead and do it, go to System->Preferences->Appearance->Visual Effects for different levels.

[http://www.youtube.com/watch?v=E4Fbk52Mk1w](http://www.youtube.com/watch?v=E4Fbk52Mk1w)

That shows some of the features of Compiz Fusion, with some annoying music. :)

---

### Post by uper104 on 2008-04-25
idk what it is but its called

3D desktop launcher 

i have an icon on my... i guess you could say "start bar"  with the command 

3ddesk

when i click on it it zooms the desktop back and i can make it spin and stuff with my mouse... but im pretty sure i can make a 2nd desktop and a third and fourth.

reason beeing i saw a picture and it had 4 desktops on it...

---

### Post by uper104 on 2008-04-25
ok... i dont think you understand... im a COMPLETE Noob... Is there a program i kneed to run this ??

i got a compiz file called X-C_Blacklight_1.2 

and its just a bunch of folders with pictures and files it says wont run.

---

### Post by tonyr1988 on 2008-04-25
> **uper104 said:**
> ok... i dont think you understand... im a COMPLETE Noob... Is there a program i kneed to run this ??

i got a compiz file called X-C_Blacklight_1.2 

and its just a bunch of folders with pictures and files it says wont run.

Were you following a tutorial or anything? If so, link me to it.

Compiz is pretty easy to install now, but if you're going off of an old guide (for an older version), they're probably making you do a lot of extra stuff you don't need to do. :D

---

### Post by mrgooding on 2008-04-25
> **uper104 said:**
> 
reason beeing i saw a picture and it had 4 desktops on it...

Do you mean in the bottom right hand corner where you can switch desktops (i.e. have four different desktops but use on one monitor)? I think it's configured by default to have two, but i'm sure theres a way to enable four or more.

---

### Post by tonyr1988 on 2008-04-25
> **uper104 said:**
> idk what it is but its called

3D desktop launcher 

i have an icon on my... i guess you could say "start bar"  with the command 

3ddesk

when i click on it it zooms the desktop back and i can make it spin and stuff with my mouse... but im pretty sure i can make a 2nd desktop and a third and fourth.

reason beeing i saw a picture and it had 4 desktops on it...

3ddesk is old....it's basically replaced by Compiz now. You must be following guides made for old versions of Ubuntu, before things got easier. :P

What guide did you follow to install 3ddesk?

---

### Post by tonyr1988 on 2008-04-25
> **mrgooding said:**
> Do you mean in the bottom right hand corner where you can switch desktops (i.e. have four different desktops but use on one monitor)? I think it's configured by default to have two, but i'm sure theres a way to enable four or more.

If that is what you're talking about (maybe not), right-click it and select Preferences. You can set the # of desktops there.

I have a feeling you're talking about something else, though. Can you take a screenshot of some of your problems if you get a chance? Hit the print screen key on your keyboard, save the file somewhere (your desktop works), and attach it to a post.

---

### Post by uper104 on 2008-04-28
hokay... i found out that people were deleting buttons on me 

so i had no aplications button no places and no system button... (verry frustrating)

but now i re-installed it and it fresh nothing on it but the updates 

i saw compiz in ther but im not sure if i have it... :confused:


right now im trying to install flash player to watch videos and stuff 

FOR WITCH IM TOTALLY LOST...



and i found out that if you go on to gnome-look.org or what ever just search 


animated thunderdome and it will show you the pic i saw with the cube desktop 



ware is the install button for the flash player...:( or the auto start or the run program button ????

---

### Post by uper104 on 2008-04-29
how do you install compiz

the command is $ autogen.sh but when i put it into the terminal box it comes up and says its not avalible 

is there a sertain place i kneed to put the file so it reads it?

---

### Post by Paraphysicist on 2008-04-29
Compiz should be installed by default on your machine.  To enable it, you need a video card and drivers that support accelerated 3D graphics.  To check and see if compiz is installed, go to:

system > administration > synaptic package manager

Enter your password. Click on search and type in compiz.  There should be a green box to the left compiz.  A green box means you have it, an empty box means not installed.  

Find compizconfig-settings-manager.  You need that as well.  If it doesn't have a green box next to it, click the box and click 'mark for installation'.  Then click apply.

Before trying out compiz, check and see if you have a 3D video card enabled.  Go to:

system > administration > restricted drivers manager

If a card is not enabled, enable one.  After that's done, go to:

system > preferences > appearance > visual effects > custom

Then to tweak the settings in compiz just go to 

system > preferences > advanced desktop effects settings


EDIT: to install java or flash, you can go through the synaptic package manager and check those boxes.

---

### Post by uper104 on 2008-04-29
ohkay coolz i went trhough and did what you said 

now i have a theme and my archive wont open it what do i do ?

---

### Post by Paraphysicist on 2008-04-29
Is your video card driver enabled?

---

