---
title: "cant see anything but text and 8 bit graphics"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by madmanjohn on 2013-02-12
brace yourself-- im a brand new convert to be but i ak having issues and i think i know what it is but have no clue how to fix it, or what it would be callled in here.
 
tonight i have tried to run both 12.10 and 12.04.1 from usb, from live disc, and under full install to a 1tb drive and i keep having the same issue whidch makes me think its a driver problem
 
i get a purplish menu screen with the normal choices and a line of fkeys across the bottom
 
no matter what i click next, the next screen i will get will say ubuntu with a line of running dots
 
it goes out and the next thing i get looks like denim stripes and thast as far as it goes, no matter how long i wait or what i try
 
when i boot back into win 7, there is usually an ubuntu folder on the drive i was installing to but virtually nothing in it
 
my guess is its a video driver issue----, but i never get to a screen where i have any options and if i am, all i get is dots--like 8 bit graphics--win 95 style
 
if it helps, im running a 4 screen config with dual ati 5 and 6000 hd series cards on a quad with 16gb of ram and a ssd for my main and a 1tb im experimenting with for ubuntu
 
any help at all would sure be nice--im lost here
 
edit  -1 hour later
 
I have seen some startup screen shots - i have nothing that looks anything like these - everything im seeing is all like bad video drivers-- nothing clear or normal
 
i removed one then the other video card  -no change -  - everything is still pixelated and nearly unreadable-- and i cant get 5 seconds beyond any screen before i get the bluish pruple denim looking screen  -- the screen flashes on and off about every 10 seconds-- but there is absolutely no print
 
if i hit f4 i see something similar to the pendrive linux im used to seeing for my OCZ ssd toolbox-- that looks normal but it rapidly runs the a bunch of lines then the blue screen--similar to a windows blue screen but no restart and no print on it and it willl sit like that forever and blink on and off about every 10 seconds-----really i have no clue what is wrong
 
if i cant get beyond this im stuck in windoze forever i guess - help please

---

### Post by mastablasta on 2013-02-12
> **madmanjohn said:**
> when i boot back into win 7, there is usually an ubuntu folder on the drive i was installing to but virtually nothing in it
 

 
Ah you are trying to do a wubi install ment for testing the OS and done "inside" windows.... 
 
can you boot with live media? try boot options particulary no modeset.:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
 
> 
if it helps, im running a 4 screen config with dual ati 5 and 6000 hd series cards on a quad with 16gb of ram and a ssd for my main and a 1tb im experimenting with for ubuntu

 
otherwise your setup will need proprietary drivers from AMD (they can be installed later). though i am not sure if the dual card setup is supported in their linux driver and if it is i am not sure if it works out of the box (with no setup). 
even if the drivers work i am not sure if default unity desktop interface is good for a quad monitor setup or if it supports it. as i know some people complain even about 2 monitor support from Unity. a better user interface for 4 monitors might be KDE (Kubuntu) or XFCE (Xubuntu).
 
oh and BTW Ubuntu needs about 5-6 GB disk space for the os, you will need 16GB for swap and any additional programmes take very little space usually. because unlike in windows here most libraries are shared. and you have 1 TB set aside for it :)

---

### Post by d4m1r on 2013-02-12
Hi, it would help if you specified exactly which model number of ATI video cards you have and how many. It does sound like an issue with your proprietary drivers (or lack of).

---

### Post by madmanjohn on 2013-02-12
After reading both posts-- ill go into a bit more detail - and thanks for the replies i might add :)


i started out by creating a live dvd from the iso---i also added the ati linux drivers and the linux realtek network drivers but as the default tarballs thinking that i would be able to find them on the disc once i got to a certain point--- my windows 7 ssd was disconnected so i wasnt trying to run it in windows

that didnt work-- try again from a flash drive  -installed it with the pendrive installer  -same thing

i get a menu but it looks nothing like any screenshots ive seen. its pixelated purple and barely readable text but it does let me select an option,(run live cd install to hard drive memory check etc) and has a listing of f key commands across the bottom - soon as you make the selection -- any of them, it takes you to a similar looking screen with 5 running dots-- you see that for about 10 seconds then it blacks out, and in a few seconds and comes back to this blueish denim screen-- it repeats that process as long as you let it run-- at one point a yellow box popped up after about 40 minutes - no text to be seen thru all of this-- and a green bar across the top---thats all ive ever seen of it so far

next i tried removing all but one video card--- this is an asus m5a99gx pro 2.0 mobo - no onboard graphics so i started with the visiontek ati hd5670 first thinking the older might be better with just 1 monitor  -same results

swapped to the colormaster hd6520 card-- same results - in windows they use the same driver-- 

the whole thing i am trying to do here-- first of all im tired of windows backwards thinking and 50 running processes all up in the way -- but this is a production machine that i use at home for my work - i could live with two monitors if need be but after 5 years of having 4 monitors with my last 3 computers id have to have at least 2--- but the goal here is for me to start breaking into the open source world--- but im a code noob - -so either way right now id be happy seeing it run with just one monitor---

is there a way to compile this somehow with the drivers in thier proper place ?

let me know and thanks

edit: i searched about graphics problems and couldnt find this --as i describe it-- but also

would or could this also be an ahci issue? or possibly uefi> i tried changing uefi settings but the mobo takes it back to the same settings no matter what i do and it seems to be in default non uefi mode - like i say ive been in a windows world for 15 years--- this is all completely new to me but trying to learn

and if your wondering nothing is over clocked-- everything is at natural settings

---

### Post by JiuJitsu500 on 2013-02-12
Well, I do know of one thing you could try... but I forget how to do it in a normal ubuntu install.

there's a setting called "nomodeset" you need to run instead of "quiet splash" at boot so this takes virtually no graphics power.

I think you hit any key as soon as you see any purple after booting from the USB which lets you select language, etc. It's in the linux option (F6 I think), just change that to "nomodeset" and you should be okay. If not when in that menu you may have to press TAB in order to edit stuff - in that event just find where it says "quiet splash" and change it to "nomodeset"

report back if anything goes wrong, I've never even heard of something so crazy as your setup like that. sounds like a more than powerful enough rig to run ubuntu a few times over, so it has to be in graphics.

And, someone please correct me if I'm wrong, but I remember doing this a few times a number if years ago in Karmic and Lucid.... but that's quite some time ago.

EDIT: [Here]("http://ubuntuforums.org/showthread.php?t=1986975") is another post about it.

---

### Post by madmanjohn on 2013-02-13
Update:

I grabbed my previous computer, a 3 year old biostar with ati hd 3200 graphics onboard with the 700 chipset and an empty hard drive and it went like a snap, installed and runs perfectly.

That confirms my suspicion about the drivers so now my qustion is

in windows we can use software to slipstream drivers and updates etc

can i use this install to create a version of 12.10 with the most recent drivers and if thats possible, then i have another dinosaur lappy that id like to compile dsl or puppy to load from floppy but may have to save that for a different thread

nothing like going from 0 to 100 in seconds flat---i am learning a fee things here and thanks to all those that responded

---

### Post by JiuJitsu500 on 2013-02-13
YEs, using remastersys or like apps, but that's not necessary and would be difficult to get them to load at boot. try with nomodeset... OH, and ensure you have the correct architecture!!! 32bit environments will run on 64 bit architecture, but NOT the other way around.

So for your old dinosaur, use a 32-bit .iso, and puppy is already very small, fast, and works excellent. I like the ubuntu-based ones better than the slax-based.

---

### Post by madmanjohn on 2013-02-13
Update  -well i have it running in the newer computer but had to go back to a ati hd 4000 series card to do it

found another post on another forum but lost the link--the hd 5000 and up series are not natively supported by ubuntu, but i do have 2 desktops, and running it now on the older card

the new problem i have is i have newer proprietary drivers but i am lost in here and almost as lost in command line  -all new to me

as for puppy  - somehow i need to integrate wakepup to run from a floppy as there is no useable cdrom and it will not boot from the usb on its own - problem im having is i cant get the puppy i have running now on the usb stick to see the download of wakepup-- once again--- i have no clue what to do with anything command line-- and these are all tarballs  --its a learning curve i guess


plus im finding out most of the applications i use for work cant run in here--- thats another twist i hadnt plannned on and unfortunately the ones available to run in here are not as advanced---- hopefully i can persuade some to run in wine if not then its back to win 7 and the graveyeard for the lappy

i just wish commandline was more logical-- some commands dont make any sense at all and some fit perfectly--oh well thanks to everyone for coming to my rescue--- i havent given up yet but it gets hard not to get discouraged when your lost and to find out most of my hardware and software wont run to its full potential or not at all in here was a major setback 

i really thought this would be more advanced :( thanks to everyone--- im not giving up yet

---

### Post by mastablasta on 2013-02-13
> **madmanjohn said:**
> --the hd 5000 and up series are not natively supported by ubuntu, but i do have 2 desktops, and running it now on the older card
 
what do you mean not natively supported? sure they are.
 
> 
i just wish commandline was more logical-- some commands dont make any sense at all and some fit perfectly--oh well thanks to everyone for coming to my rescue--- i havent given up yet but it gets hard not to get discouraged when your lost and to find out most of my hardware and software wont run to its full potential or not at all in here was a major setback 

 
ok first off the ramblings don't provide any clues or anything that others might help you with. the do help you to maybe release soem pressure. but it would be far better to propperly set up questions and issues. you will get fast and very good responses that way.: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
command line is as it is. there is a nice free e-book book about it (linuxcommand.org), you can copy paste command sinto terminal if you dont' want to type them...
 
hardware should be linux compatible otherwise you won't be able to run it. if you buy it with that in mind then everything will work as ti should. another option is linux preloaded mashcine. yet another hardcore option since linux is opensource you can create your own drivers, modify the OS etc :P
 
as for the software - you do not mention what you need and what alternatives you tried. often linux alternative is just different but doesn't have less functions as windows commercial software. in fact often they have more functions available. also often there are plugins made for the project by community that enhance the software dramaticly.
 
take thunderbird for example i think it is far more advanced than Microsoft outlook. but you might need to add some plugins that are only a few click away.
 
there are also some alternatives that are not in software center for various reasons. but they are actually very good. i use opensource in windows as well as in linux. so transition from one os to another is not really that painful. 
 
so to me the only issue is games and i hope that will change as well.

---

