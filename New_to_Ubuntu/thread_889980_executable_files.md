---
title: "executable files"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by homer_jay_666 on 2008-08-14
ok you know those diamond files that are light purple with the cogs on them? how do you get those to work??? they're on my desktop. i tried the whole sudo thing and so on... nothing... no idea what i'm doing with those... can someone spell this out for me?

---

### Post by sayakb on 2008-08-14
Try this: Assuming that the fie is on your desktop, open a terminal (Applications->Accessories->Terminal)
```
cd ~/Desktop
./filename
```
If it is a windows executable, at a terminal, type in:
```
sudo apt-get install wine
```
And after the command finished installing wine on your computer, just double click on the executabe to open it with Wine.

---

### Post by t0p on 2008-08-14
What exactly have you tried? How about clicking on them?  Or typing in the executable's name (plus path if you're not in the same directory)

---

### Post by homer_jay_666 on 2008-08-14
ok that first piece of advice worked, by the way it's for a keygen, no i'm not going to use the keygen, it just came with something i downloaded and deleted (nerolinux - piece of crap) it tells me access denied. but if thats how it works then i think i shouldn't have any problems if and when i do download something. but with the windows - wine - can i just run wine and run the program through that? or do i have to use the terminal?

---

### Post by sayakb on 2008-08-14
Any king of discussion about keygens, pirated software, software cracking etc. goes against the forum rules. Please be careful.
Also, why exactly do you need nero linux anyway ;)
Use Brasero or Gnomebaker. If you have Hardy, you should have Brasero already installed (Applications->Sound & Video->Brasero)

---

### Post by drubin on 2008-08-14
> **LinuxIsInnovation said:**
> Any king of discussion about keygens, pirated software, software cracking etc. goes against the forum rules. Please be careful.
Also, why exactly do you need nero linux anyway ;)
Use Brasero or Gnomebaker. If you have Hardy, you should have Brasero already installed (Applications->Sound & Video->Brasero)

Brasero is tops! I would recommend using it as well, I used to use nero before ubuntu.

---

### Post by homer_jay_666 on 2008-08-14
wasn't aware of that sorry:( but i tried brasero i tried k3b and when i burned my dvd iso i made with devede it sucked... horribly... there's a thread somewhere i made about that so thats why i downloaded it, couldn't figure it out so just got it off nero and... well nero sucks lol. but it's what i used when i did windows

---

### Post by drubin on 2008-08-14
what issues are you having with brasro?

---

### Post by homer_jay_666 on 2008-08-14
well it's the same for both brasero and k3b. i convert with devede and burn to dvd but when i tried to play the dvd in dvd player for tv it's jumpy and pixelated, the sound is five seconds off. it's just crap. but if i play the same disc on computer it runs perfectly. never had that problem with nero

---

### Post by damis648 on 2008-08-14
> **homer_jay_666 said:**
> well it's the same for both brasero and k3b. i convert with devede and burn to dvd but when i tried to play the dvd in dvd player for tv it's jumpy and pixelated, the sound is five seconds off. it's just crap. but if i play the same disc on computer it runs perfectly. never had that problem with nero

This could be a DeVeDe issue, and as I see it, that is more likely.

---

### Post by homer_jay_666 on 2008-08-14
thats what i'm thinking too... but i think i may have figured it out but i have yet to test it... have you used devede? it says something about disc space usage? well mine was 119% which may have been the problem so now i'm trying at 99%... oh and since this technically is a thread about files... how do you use tar.gz? it's on my desktop... i just downloaded brasero 0.8... i'm really no good at using the terminal so what should i do? i feel like such an ***... i hope i get better with ubuntu cause i personally like it better than windows even if it is a pain in the *** to get used to

---

### Post by damis648 on 2008-08-14
> **homer_jay_666 said:**
> thats what i'm thinking too... but i think i may have figured it out but i have yet to test it... have you used devede? it says something about disc space usage? well mine was 119% which may have been the problem so now i'm trying at 99%... oh and since this technically is a thread about files... how do you use tar.gz? it's on my desktop... i just downloaded brasero 0.8... i'm really no good at using the terminal so what should i do? i feel like such an ***... i hope i get better with ubuntu cause i personally like it better than windows even if it is a pain in the *** to get used to

Brasero is preinstalled. See Applications>Sound & Video>Brasero Disc Burning. If it is not there, install it using Applications>Add/Remove. Also try Gnomebaker. A .tar.gz is an archive, known as a tarball. It is like a zip file. It usually will contain source code to an application to compile. In the linux world, software is usually not downloaded from sites like in Windows, but kept in software repositories, or central locations on the internet where software can be found. Use Add/Remove or Synaptic to install software.

---

### Post by homer_jay_666 on 2008-08-14
yea i know brasero is on. i've used it, but i want to upgrade it, and as far as i could tell synaptic doesn't do that so i downloaded the tar.gz file... but i don't know how to use it... i can extract it, thats not a problem. i just don't know how to install it

---

### Post by homer_jay_666 on 2008-08-14
what the hell??? i just used devede to convert avi and it converted to mpg... but now it won't burn the damn thing!!!

---

### Post by damis648 on 2008-08-14
> **homer_jay_666 said:**
> yea i know brasero is on. i've used it, but i want to upgrade it, and as far as i could tell synaptic doesn't do that so i downloaded the tar.gz file... but i don't know how to use it... i can extract it, thats not a problem. i just don't know how to install it

It does do that. You have the update manager that will do it. System>Administration>Update manager. If it says there are no updates, that means that the new version hasn't entered the repos yet, for whatever reason. Do not attempt to upgrade in any way except from the repos/some repos. Try gnomebaker if it isn't working for you.

---

### Post by homer_jay_666 on 2008-08-14
well the latest brasero (0.8.1) isn't in there and it looks a lot better than what i have... but i'm about at the end of my rope here... i'm not sure what to do now...

---

### Post by damis648 on 2008-08-14
> **homer_jay_666 said:**
> well the latest brasero (0.8.1) isn't in there and it looks a lot better than what i have... but i'm about at the end of my rope here... i'm not sure what to do now...

Try gnomebaker.

---

### Post by sdowney717 on 2008-08-14
use k9 copy to shrink the dvd to an iso file.
write the iso to dvd disk using k3b

this works very well.
[http://packages.ubuntu.com/hardy/kde/k9copy](http://packages.ubuntu.com/hardy/kde/k9copy)
[http://k9copy.sourceforge.net/](http://k9copy.sourceforge.net/)

---

### Post by homer_jay_666 on 2008-08-15
why k9? better than devede? but anyways i figured it all out, it was me screwing with devede, but in the end it all got straightened out. movies are a lot better, sounds sometimes gets off but it's easily fixable. thanks for the help. oh and i have no idea how to burn with gnomebaker. all it does for me is data cd/dvd and audio cd?

---

### Post by estyles on 2008-08-15
When you get files to install in a .tar.gz or .tgz file, that's called compiling from source (simplifying a little, but generally true).  Compiling from source is considered "Advanced".  It's generally a bad idea for beginner and intermediate users (I consider myself an intermediate user at best).  Most of the time, by far, you will be better off sticking with what's in the respos.  I have only successfully built from source once, and later found an .rpm package (which is red hat's package format) for the same program that could be installed via Alien.  Still something of an advanced installation method, but infinitely simpler than compiling from source.

It's not that compiling from source is inherently difficult.  Ideally, you just type a couple of lines (ugh, I forget exactly what, but it's basically something like "make, sudo make install" or something - been a while, and most packages will give you instructions).  The problems are:

1) If it doesn't work, it's very hard for a beginning/intermediate user to troubleshoot.
2) You have to resolve dependencies yourself.  If your makefile requires a certain library, it won't get it itself like apt-get does, you need to get the libraries you need.
3) It's not strictly safe.  Downloading from the repositories means the software has been approved by Ubuntu.  Compiling someone else's code could potentially install malicious software on your computer.  Make sure you trust wherever you're getting it from.
4) It's not guaranteed to work with Ubuntu.  Again, because it's not in the repos, that means it hasn't been approved.  Not that everything in the repos works 100% bug-free, but there's a better chance of it.

---

