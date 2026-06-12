---
title: "[SOLVED] From Panels to Pain! Can't get into Ubuntu!"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by mochiko on 2008-07-26
OKie dokie.
I am a completely nooby noob.

Just some time ago, I posted some stuff on how my panels kept disappearing whenever I clicked the Log Out Icon(Green Man).

I also noticed how a lot of applications weren't starting up when I clicked on them from the Menu Bar. 
For example, I would click on 'Exaile' and the window tab shows up in the panel bar(not the window itself) and the cursor becomes round and shows that it's loading but in the end it just disappears  and the app. never opens. 


So then! It was kind of hard to open up my terminal to try out some of the suggestions people gave, or even search for some gnome2 watever files because i couldn't open the file browser! I tried the ctrl+alt+f2 and it still didn't work. . . 

So I shut it down and when I tried to log in, this little window pops up and says that there's a problem. I can't remember exactly, but it said:

[INDENT][/INDENT]"Can't log in because either there's an installation problem or not enough disk space. Try logging in with a failsafe 'something'and try if you can fix the problem"

And so I tried logging in with some failsafe session thing and it doesn't let me get in. The failsafe terminal does work though.

Does this mean I can never log into Ubuntu ever again?!!??! 
Nooo! I'm using my mac osx right now..

Also, does this affect any data I have on Ubuntu? I have Hardy Heron and well all these problems started popping up recently. I updated some stuff, added some programs, removed some as well.

Right now I can't get into Ubuntu!

thanks, 
really lost.

---

### Post by coffeecat on 2008-07-26
> **mochiko said:**
> "Can't log in because either there's an installation problem ***or not enough disk space.***

Best to take one thing at a time. Do you know how big the root partition is of your Ubuntu install? Do you have a separate /home partition and, if so, how big is it? If you don't know, boot up from the live CD and go to System > Administration > Partition Editor. Don't change anything! Just look. How big is/are the hard disc partition(s) for your Ubuntu install? How much space is used and how much is free?

If an ext3 partition gets more than about 90% full you can run into problems.

---

### Post by mochiko on 2008-07-27
All right, I did what you said, and here's what I saw..


/dev/sda2  
 70.0 GB   and of this **21.35GB**is used

/dev/sda3
58.34 GB   and of this **4.70GB**is used    

/dev/sda4
20.51GB   and of this **19.89 GB** is used



So I guess it is the disk space that's causing the problem then?

---

### Post by eightmillion on 2008-07-27
What are these partitions mounted as? If you are able to use a terminal, could you post the output of this command?:
> df

---

### Post by dew5 on 2008-07-27
Could try a fresh reinstall from your live cd..
 
dew5

---

### Post by ajmorris on 2008-07-27
> **dew5 said:**
> Could try a fresh reinstall from your live cd..
 
dew5

that is not needed. If /dev/sda4 is indeed the partition that ubuntu is installed onto (the df command will tell you where it is mounted), then you will have to resize your partitions, and give it more room. If this is not the partition ubuntu is installed onto, then you can try to re-install gnome (apt-get remove purge ubuntu-desktop && apt-get install ubuntu-desktop) however, it appears that lack of HD space is the problem

AJ

---

### Post by mochiko on 2008-07-27
> **eightmillion said:**
> What are these partitions mounted as? If you are able to use a terminal, could you post the output of this command?:

I'm sorry I don't know what these partitions are mounted as... my friend installed ubuntu for me and he knows a lot but he's at camp now and i can't contact him for another week.. 


I will try that in the terminal, and see what I get, thanks!

---

### Post by eightmillion on 2008-07-27
> I'm sorry I don't know what these partitions are mounted as... my friend installed ubuntu for me

No problem. That command will tell us where those partitions are mounted.

---

### Post by mochiko on 2008-07-27
It does work! I couldn't log in, but I at the log in page there was an option to use the failsafe terminal and i did that, typed in df and the command worked.. 


I started to write it down because I don't know how I can save it.. I typed skype and brought it up (thinking maybe i can send the copied result to myself or something, hahaha.. ) and thought it would work with Epiphany but it said there was no space. 

I will write it down i guess, byt the top line was like:

Filesystem  1k-block  Used  Available Use% Mount

so yeah i shall just do that again and give the whole deal in a few minutes.

---

### Post by mochiko on 2008-07-27
Filesystem	1-K blocks	Used	Available 	Use%	Mount
/dev/sda4	21341280	20678408    0	        100%	/
varrun	          498880	100	 498780	         0	/var/lock
udev	           498880	64	 498816	         1	/dev
devshm	          498880	0	 498880 	 0      /dev/shm
overflow	1024	        12	 1012	         2	/tmp

---

### Post by mochiko on 2008-07-27
hey, if that's too messy, i've attached a word doc where it's in columns.

i wonder if it works..

---

### Post by eightmillion on 2008-07-27
Your root partition is completely full. You can fix this by moving or deleting things from it. To remove a file called foo.bar you would use the command:> rm foo.bar
Since your other partitions are not mounted, this would probably be your best option. Remember, the command 'df' will tell you how full your partition is. You'll probably want to get that down to at least 90% full.

---

### Post by kansasnoob on 2008-07-27
> **ajmorris said:**
> that is not needed. If /dev/sda4 is indeed the partition that ubuntu is installed onto (the df command will tell you where it is mounted), then you will have to resize your partitions, and give it more room. If this is not the partition ubuntu is installed onto, then you can try to re-install gnome (apt-get remove purge ubuntu-desktop && apt-get install ubuntu-desktop) however, it appears that lack of HD space is the problem

AJ

Yep, this says there's no toe room in them shoes:
> /dev/sda4
20.51GB and of this 19.89 GB is used

Since the OP is not comfortable with repartitioning and such, how about just transferring files:confused:

---

### Post by mochiko on 2008-07-27
wait so i have to delete foobar?
what files should i delete though? like, can i delete applications like, "rm Solitaire"?

Also, I'm trying to delete space from the terminal, using this command.. is there a way to bring up my file directory to view it in the terminal? isn't there some command.. like "ls" or something?

---

### Post by Martje_001 on 2008-07-27
You still have got Windows? Try [this](http://www.fs-driver.org/download.html) to acces your Linux partition through Windows.

---

### Post by Martje_001 on 2008-07-27
If you want to delete an application you can do:
```
sudo apt-get remove application
```
also, to remove some unnessery (no idea how you spell it) files:
```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

---

### Post by mochiko on 2008-07-27
> **Martje_001 said:**
> You still have got Windows? Try [this](http://www.fs-driver.org/download.html) to acces your Linux partition through Windows.


hi!
no, i don't use windows, i have a Macbook and right now i'm in OSX.

oh, thanks for the application removing command, i'll try that..

---

### Post by mochiko on 2008-07-27
hm...

i was wondering if it's possible to run the cd and just increase the space on this ubuntu partition.. 

i've deleted a bit of stuff and it still shows that i have 100% full.

---

### Post by Martje_001 on 2008-07-27
It's possible. Go to a terminal and typ:
```
gksudo gparted
```
Now you can increase the partition size. You could also access your hard drive to clean up your files.

Also do a 'fsck' on your drive to make sure everything is OK.

---

### Post by mochiko on 2008-07-27
> **Martje_001 said:**
> It's possible. Go to a terminal and typ:
```
gksudo gparted
```
Now you can increase the partition size. You could also access your hard drive to clean up your files.

Also do a 'fsck' on your drive to make sure everything is OK.

I see.. 
but the thing is, when i type it the partition editor window comes up, but i can't resize the partition which ubuntu is on, it's locked. 

the other partitions i click, the option to resize/move is available. 

Right now, i'm looking at my files through the live session cd and the only problem is that i can't delete them! it's saying i don't have the permission to delete them.

i tried gksudo nautilus, using rm and this and that, and nothing seems to fly. 

poop!

what's going on... why can't i delete my own files when i'm using sudo??

---

### Post by mochiko on 2008-07-27
Okie 

Somehow, I managed to do something and got back in!
Better yet, i checked out the green man and he's fine, and the panels don't disappear anymore, and even the deskbar applet works and all.

Still i wonder why it is that it gets messed up once you pass about 90%. 

Anyways, I would just like to thank all you guys!
THANKS DUDES!

P.S my friend will be proud of my loser self once he comes back from camp!

---

