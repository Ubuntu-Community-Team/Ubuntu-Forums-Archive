---
title: "[SOLVED] ok, just 2 more things and ubuntu would be perfact!!! some1 help?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by SchindlerShadow on 2008-08-10
ok now iv fixed most of the major probloms, and i need help with 2 more things.

1. for some reson i cant burn disks! it gives me an error!

2. i cant update the info on the update manager! the last update was 29 days ago! and whenever i press check it says.........

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.gz](http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

can some1 help? ty. :guitar:

---

### Post by hyper_ch on 2008-08-10
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by powerpleb on 2008-08-10
> **SchindlerShadow said:**
> 
1. for some reson i cant burn disks! it gives me an error!
What's the error?

> 
Could not download all repository indexes
System>>Administration>>Software Sources... pick a new server

---

### Post by Elfy on 2008-08-10
The two feisty repos give me a 404 as well - they are either down or have gone. The awn download/installation page is here
[http://wiki.awn-project.org/Installation](http://wiki.awn-project.org/Installation)

You might need to edit your sources - what version are you actually running as the middle link is for a gutsy repo.

If you actually post the erro you get for burning cds it would help I suspect :)

---

### Post by SlalomMan on 2008-08-10
I would check your sources.list file...run this command:

"gksudo gedit /etc/apt/sources.list"

And if you don't mind, post the content of it. It looks like you might have added those lines to the list somehow and it can't get the updates, so it is just stopping the whole update. So you might want to look at that file and if the lines that you just mentioned are there (i.e. "http://download.tuxfamily.org...") you could either comment them out by putting a "#" (minus quotes) in front of the line or deleting the line altogether. I'm not sure about CD burning.

However, if you don't have much free space on your drive, it will fail. If you are using brasero, it seems to make a temporary copy of the cd on your hard drive, so if you don't have enough space for that, it won't burn.

Hope this helps.

---

### Post by northern lights on 2008-08-10
> **SlalomMan said:**
> I would check your sources.list file...run this command:

"sudo gedit /etc/apt/sources.list"
Please _never_ run graphical apps with 'sudo'. If they need to be run as superuser, use ```
gksu GRAPHICAL APP
```
For references, read [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

-->So in this case, the options would be```
gksu gedit /etc/apt/sources.list
```or```
sudo nano /etc/apt/sources.list
```

---

### Post by SchindlerShadow on 2008-08-10
> **powerpleb said:**
> What's the error?


System>>Administration>>Software Sources... pick a new server

i still get this, and i canged the sever to main,

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.gz](http://packages.dfreer.org/dists/gutsy/main/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


let me try to burn a dvd, give me a sec.

---

### Post by bpowell2005 on 2008-08-10
> **SchindlerShadow said:**
> ok now iv fixed most of the major probloms, and i need help with 2 more things.

1. for some reson i cant burn disks! it gives me an error!




Okay, I'm going to split this into two topics within this thread.

You can't burn disks, you get an error...what's the error exactly? What are you using to burn the disks? Brasero? Please post the output of the error here.

Thanks!

---

### Post by Elfy on 2008-08-10
> i still get this, and i canged the sever to main,
Could not download all repository indexesYes - as I said 2 of them are down, they are both repos for awn and I think they have moved.

---

### Post by bpowell2005 on 2008-08-10
Also, what version of Ubuntu are you running? Hardy?

---

### Post by SlalomMan on 2008-08-10
> **northern lights said:**
> Please _never_ run graphical apps with 'sudo'. If they need to be run as superuser, use ```
gksu GRAPHICAL APP
```
For references, read [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

-->So in this case, the options would be```
gksu gedit /etc/apt/sources.list
```or```
sudo nano /etc/apt/sources.list
```

My mistake; I guess I never learned otherwise. Let me just edit that post...

---

### Post by SchindlerShadow on 2008-08-10
> **bpowell2005 said:**
> Okay, I'm going to split this into two topics within this thread.

You can't burn disks, you get an error...what's the error exactly? What are you using to burn the disks? Brasero? Please post the output of the error here.

Thanks!

im running hardy and im useing the cd/dvd creater that comes with it, im trying to burn a dvd, but cd burning dosent work ether, im trying to burn a full sized dvd .iso, give me a sec im trying it agen to get the error. :guitar:

---

### Post by bpowell2005 on 2008-08-10
> **SchindlerShadow said:**
> im running hardy and im useing the cd/dvd creater that comes with it, im trying to burn a dvd, but cd burning dosent work ether, im trying to burn a full sized dvd .iso, give me a sec im trying it agen to get the error. :guitar:

Well, to answer your update question, I'd go into System, Administration, Synaptic package manager, go to settings and Repositories, and look for those three repos that are causing an error...they might be in "Third Party"...and uncheck them...then tell Synaptic...

You could also sudo nano /etc/apt/sources.list and look for those three repositories and put a "#" in front of them and then run a "sudo apt-get update" which would do the same thing.

I have a pretty standard Ubuntu Hardy installation, and I don't have those three repos you mentioned in my sources.list file.

---

### Post by SchindlerShadow on 2008-08-10
> **bpowell2005 said:**
> Well, to answer your update question, I'd go into System, Administration, Synaptic package manager, go to settings and Repositories, and look for those three repos that are causing an error...they might be in "Third Party"...and uncheck them...then tell Synaptic...

You could also sudo nano /etc/apt/sources.list and look for those three repositories and put a "#" in front of them and then run a "sudo apt-get update" which would do the same thing.

I have a pretty standard Ubuntu Hardy installation, and I don't have those three repos you mentioned in my sources.list file.

wooo now thats workin, now i still need time to get the burning error, ty

---

### Post by bpowell2005 on 2008-08-10
We'll get there! Just post the details of the error when you get a chance and somebody here will have already seen it and solved it!

---

### Post by SchindlerShadow on 2008-08-10
> **bpowell2005 said:**
> We'll get there! Just post the details of the error when you get a chance and somebody here will have already seen it and solved it!

ok well it worked on a cd, now let me try a dvd. itl take like 3-4 hrs. XD

---

### Post by SchindlerShadow on 2008-08-10
ok i got it, it showed up at neerly the end of the writing, but the disk is still blank! it sayed

Error writing to disc

There was an error writing to the disc:
Unhandled error, aborting

wtf? whats wrong? :confused::confused::confused::confused:

E: i ejected the disk, put it back in, and now for some reason the usb dvd writer is not mounting! wtf?

EE: you know wat? ima put an internal dvd writer. the internal cd witer burned the cd fine! so ima try that, i need a few mins pce!

---

### Post by bpowell2005 on 2008-08-10
> **SchindlerShadow said:**
> ok i got it, it showed up at neerly the end of the writing, but the disk is still blank! it sayed

Error writing to disc

There was an error writing to the disc:
Unhandled error, aborting

wtf? whats wrong? :confused::confused::confused::confused:

E: i ejected the disk, put it back in, and now for some reason the usb dvd writer is not mounting! wtf?

What program are you using to burn disks?
You had a successful CD burn, right?
It's DVD that's giving you the error?
Were you burning files to the DVD, or burning an .iso file to DVD?

---

### Post by nothingspecial on 2008-08-10
If I my make a suggestion.

```
sudo apt-get install tovid
```

I never had any luck burning dvds till I found this.

---

### Post by bpowell2005 on 2008-08-10
> **nothingspecial said:**
> If I my make a suggestion.

```
sudo apt-get install tovid
```

I never had any luck burning dvds till I found this.

Does Tovid work for data DVD's as well, or only for video DVD?

---

### Post by nothingspecial on 2008-08-10
> **bpowell2005 said:**
> Does Tovid work for data DVD's as well, or only for video DVD?

Sorry, I should have read the whole thread.
As far as I know it`s only for videos.
My appologies.

Nice app though.:)

---

### Post by SchindlerShadow on 2008-08-10
> **bpowell2005 said:**
> What program are you using to burn disks?
You had a successful CD burn, right?
It's DVD that's giving you the error?
Were you burning files to the DVD, or burning an .iso file to DVD?

in order,
1 the defult 1 that comes with ubuntu hardy
2 yes but with the cd burner, it only burns cds, the external dl dvd/cd burner i think unmounts in the midd of the burning, so i just put a new internal dvd/cd burner hope it works!
3 yes it is dvd
4 it is an iso 2.5gbs

now ima see if it works wish me luck!

---

### Post by SchindlerShadow on 2008-08-10
> **SchindlerShadow said:**
> in order,
1 the defult 1 that comes with ubuntu hardy
2 yes but with the cd burner, it only burns cds, the external dl dvd/cd burner i think unmounts in the midd of the burning, so i just put a new internal dvd/cd burner hope it works!
3 yes it is dvd
4 it is an iso 2.5gbs

now ima see if it works wish me luck!

WOOOOOO! it works! and it only took 5 mins!!! and i just relized its dl! :lolflag: thx ppl, now i have everything working in ubuntu and im just so happy that i got it to work! this is the 1st time i ever got something to work so fast! now i have all of ubuntus fechers working! Wooooooooooo! and its al thx 2 the ubuntu communaty!

---

### Post by bpowell2005 on 2008-08-10
Glad to hear it! Be sure to mark the thread as Solved!

Thanks!

---

### Post by SchindlerShadow on 2008-08-10
thx, umm but can u help me with 1 thing? what r some good apps for ubuntu?? like a good rmvb to dvd converter? ty

---

### Post by nothingspecial on 2008-08-10
It is possible I believe by using mencoder
```
sudo apt-get install mencoder
```
if you don`t already have it.
Don`t know how to do it though.
Best bet is to start a new thread in the multimedia forum - it`s a bit slower than here but they know about this stuff.

---

### Post by SchindlerShadow on 2008-08-11
> **nothingspecial said:**
> It is possible I believe by using mencoder
```
sudo apt-get install mencoder
```
if you don`t already have it.
Don`t know how to do it though.
Best bet is to start a new thread in the multimedia forum - it`s a bit slower than here but they know about this stuff.

yea... looks like this is text based.... i need a gui XD

---

