---
title: "where to go next"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by boblemur on 2008-07-26
hey all,

i was just wondering, iv installed ubuntu and im loving it... i have worked through all of the problems with the operating system that i had, some sound issues etc...

and now im wondering where i should go from here.... im into development so i dont really mind diving into the deep end of things :p

i was wondering if anyone had any cool ideas for how to customize the os, what else is possible? and is there anything i should learn about?

---

### Post by Xerp on 2008-07-26
I take it then that you've already played with Emerald, compiz fusion and the various icons themes :)

If you want to get into development, then gcc is your friend...

---

### Post by wishyjr on 2008-07-26
hey. this might seem overly simple but try going to the Applications menu and selecting Add/Remove Programs - you can browse about for cool software that you may like or better still try synaptic!

EDIT: oh, speaking of Add/Remove Programs, i found that using this was really handy for installing things that aren't setup by default. One thing in particular is restricted drivers and media codecs. If you can't play certain music or video files, check it out.

---

### Post by steveneddy on 2008-07-26
I would say that it's time to do whatever you did before Ubuntu on your computer.

Customization is easy and eye candy can be fun.

I hope you are a driver writer.

---

### Post by adamogardner on 2008-07-26
being new,  my only brilliant idea for OS customization are to add .wav file sound effects from soundsnaps.com.  Perhapes if you don't mind jumping in the deep end, you'd like to fix the script in gedit to pause before shut down (after you hit restart or power off) and play the closing sound effect of a girl robot saying "connection disengaged.  To me the idea of writing "scripts" to alter what is happening on the computer is out of this world (for now).  So far I got the pause.  just not the play.  In addition, sound effects for screen lock would be fun to :gedit" working.

---

### Post by wishyjr on 2008-07-26
girl robots saying anything sound ace!! has anyone ever found a sound package of that nature? ... sorry, getting off topic.

---

### Post by winsane on 2008-07-26
If I knew what kind of software to use or how to build a package, I would put something together, I have all kinds of cool effects (girls, movie clips, music, sound fx)I am a sound file junkie!  Is it easy to create packages?

---

### Post by winsane on 2008-07-26
btw....
boblmur...
Linux and programming go hand in hand.  Get a solid knowledge of programming and Linux will open worlds up to you.  Check out some stuff on the net regarding python and c++ then decide what parts of it interest you.  Most people who stick with Linux are extreme geeks, so that seems like the way to go to me.

Just my opinion, though.

---

### Post by WRDN on 2008-07-26
If you want to start developing programs, you can either use gcc/ g++ or, if you prefer, download an IDE. For C/ C++ development, I personally use "Code :: Blocks", which I have found to be very reliable.
If you want to program in Python, the tools are already installed. If on the other hand, you prefer C#, "Monodevelop" would be for you.

Once you have a grounding in language X, you may want to learn the GTK library (used for most Gnome applications), so you can create a User Interface.

---

### Post by steveneddy on 2008-07-26
> **adamogardner said:**
> being new,  my only brilliant idea for OS customization are to add .wav file sound effects from soundsnaps.com.  Perhapes if you don't mind jumping in the deep end, you'd like to fix the script in gedit to pause before shut down (after you hit restart or power off) and play the closing sound effect of a girl robot saying "connection disengaged.  To me the idea of writing "scripts" to alter what is happening on the computer is out of this world (for now).  So far I got the pause.  just not the play.  In addition, sound effects for screen lock would be fun to :gedit" working.

gedit is just a text editor.

What in the heck are you talking about?

If you go to 

System --> Preferences --> Sounds

select the Sounds Tab, there is a listing there for a closing sound.

Just browse for the sound and it will play when you shut down.

---

### Post by adamogardner on 2008-07-26
QUOTE=steveneddy;5464344]gedit is just a text editor.

What in the heck are you talking about?

If you go to 

System --> Preferences --> Sounds

select the Sounds Tab, there is a listing there for a closing sound.

Just browse for the sound and it will play when you shut down.[/QUOTE]

.  It is true that there is a preference sound setting for shutdown.  However, when I hit shutdown there is no time for a sound effect to sound off.  Unless you know something I don't there needs to be written in a pause before shutdown.  For me it does not just play.  never has.  Of course I could be wrong about the avenue to take in making this happen. I believe you are wrong for assuming so brashly that I'm talking "heck" in reagards to this sound efffects setting that I've been working on for 2 months (not continuously w/out break)  the pause is easy enough to accomplish,  what I don't get is how to make the .wav file play during pause.

---

### Post by boblemur on 2008-07-26
hey thanks for the advice, i really like python and im confident with the language and iv done a little bit of like win api stuff is the gtk simmular??

i just find its hard because i dont know where to start with programming, i have used c quite a bit but not really c++ what language is most of ubuntu programmed in? is it all c++ 

i have prity much converted every program i used in windows :) so im very happy with that...

i went

itunes  > amarok ( i'm still working on a full script to convert itunes to amarok )
msn     > pidgin (i like otr built in)
eclipse > eclipse :p

only think left is my games which do play but they are not that big a deal concidering i still dual boot..

i use vmware to boot my native windows partition so i can still access anythin i need :)



my problem is i dont really know where to start if i want to start adding/changing things about the opperating system does anyone know of a good guide to thinks such as where to find settings and what the folders in root contain etc (eg in windows you know your programs are in /program files/ but with linux i find it hard to keep track of where things are and such?

i have played around with the eye candy thats fun. but i was looking for a way to expand the functions of the opperating system its just i have no ideas of what to add/change

---

### Post by ghostdog74 on 2008-07-26
you should play around with you system more using the terminal, and refrain from using GUI too often. get used to commands to lets you navigate your system like mv,cp, find, ls, ps etc
then learn how to write proper shell scripts to automate your tasks. See my sig for learning bash

---

### Post by boblemur on 2008-07-26
iv actualy just finished a semester on unix at uni (which is what triggered my move to linux) so im actauly better at using the commandline than i am with the gui, which is unusual but good id say, i was just more looking to find more about the way the file system is structured

---

### Post by steveneddy on 2008-07-26
> **adamogardner said:**
> QUOTE=steveneddy;5464344]gedit is just a text editor.

What in the heck are you talking about?

If you go to 

System --> Preferences --> Sounds

select the Sounds Tab, there is a listing there for a closing sound.

Just browse for the sound and it will play when you shut down.

.  It is true that there is a preference sound setting for shutdown.  However, when I hit shutdown there is no time for a sound effect to sound off.  Unless you know something I don't there needs to be written in a pause before shutdown.  For me it does not just play.  never has.  Of course I could be wrong about the avenue to take in making this happen. I believe you are wrong for assuming so brashly that I'm talking "heck" in reagards to this sound efffects setting that I've been working on for 2 months (not continuously w/out break)  the pause is easy enough to accomplish,  what I don't get is how to make the .wav file play during pause.[/QUOTE]

I just didn't know why you would use a text editor for a sound file.

I understand now, I think.

You want a pause in the shutdown procedure so the system will play a sound, not a pause in the sound file?

Sometimes I read something into something that wasn't even there.

---

