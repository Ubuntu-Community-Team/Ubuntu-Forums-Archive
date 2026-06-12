---
title: "How do I download Oneiric Ocelot?"
date: 2011-06-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xxhopingtearsxx on 2011-06-01
Simple instructions please.. can someone tell me how to get Oneiric Ocelot?
And I'm sure I'm not the only one who's clueless on this.
Is it just like a regular Ubuntu distro upgrade?

---

### Post by ranch hand on 2011-06-01
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Do not use this if you are expecting it to work.  It will break regularly.  It is early days so it is supposed to do so.

This is not a production OS.  You install it, it breaks, you file the needed bug (or add your "me too" to someone elses).  It may work again in a day or two.  It may be a week.

---

### Post by arpanaut on 2011-06-02
> Is it just like a regular Ubuntu distro upgrade?It will be come October, at present it has just reached "alpha" status.
Do not install as a production OS
It can break, it will break, do not expect stability until the "beta" stage.
and maybe not even then.

If you have sufficient disk space, spare drive or an external and are brave;
have at it.  Just remember the "cutting edge" can get bloody.

---

### Post by oldfred on 2011-06-02
since you have to download it all the time. Do this for all additional downloads.

I have all my ISOs in a folder called of all things ISO

```
cd ISO

zsync [http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-amd64.iso.zsync)

```zsync only downloads the changes, you have to run it in the same folder as the ISO you download the first time.

Because link is long, copy the link not the text as it has been shortened with .. in the middle.

---

### Post by 23dornot23d on 2011-06-02
I just installed it ..... its fast ..... to boot up ....

Clean installation .... enjoyed it ......

But once you see the Desktop ..... its UNITY .....

One of the most closed down and restricted desktops I have seen ...... 

and no sign of Gnome-Shell .... 

UNITY - never fails to amaze me ..... alt+f2 and a dialogue box pops up ..... let go of the 
keys and it disappears - how do you enter a command .......

How do you get a program to run in the desktop .... no classic mode so no easy way to
work in fallback mode as far as I can initially see ......

Software Center has a continuous gif going making you think its doing something when
its actually stuck in a endless loop ....... now been going for 30 mins .... 2383 items available .... ( or not )

ctrl+alt+f1 ....... the terminal ...... sure am glad to see this ....... 

This looks like it may work ..... aptitude is not installed ..... apt-get update will not work
because there is a error in the sources.list on line 19 ...... soon sort this out ....

Once I can get aptitude on here ..... vi works which is good ....

This was the first few minutes looking at it ...... it can only get better now ...... ;)

Network works ...... and now have aptitude working ..... gedit is one thing almost uptodate .... 
see if we can get a useable desktop up .... LXDE works .... see if we can fix things ....
Ricotz ppa testing ..... obviously not been set up for Gnome-Shell ....
That's answered my first question .....

---

### Post by cariboo on 2011-06-02
> **23dornot23d said:**
> I just installed it ..... its fast ..... to boot up ....

Clean installation .... enjoyed it ......

But once you see the Desktop ..... its UNITY .....

One of the most closed down and restricted desktops I have seen ...... 

and no sign of Gnome-Shell .... 

UNITY - never fails to amaze me ..... alt+f2 and a dialogue box pops up ..... let go of the 
keys and it disappears - how do you enter a command .......

How do you get a program to run in the desktop .... no classic mode so no easy way to
work in fallback mode as far as I can initially see ......

Software Center has a continuous gif going making you think its doing something when
its actually stuck in a endless loop ....... now been going for 30 mins .... 2383 items available .... ( or not )

ctrl+alt+f1 ....... the terminal ...... sure am glad to see this ....... 

This looks like it may work ..... aptitude is not installed ..... apt-get update will not work
because there is a error in the sources.list on line 19 ...... soon sort this out ....

Once I can get aptitude on here ..... vi works which is good ....

This was the first few minutes looking at it ...... it can only get better now ...... ;)

Network works ...... and now have aptitude working ..... gedit is one thing almost uptodate .... 
see if we can get a useable desktop up .... LXDE works .... see if we can fix things ....
Ricotz ppa testing ..... obviously not been set up for Gnome-Shell ....
That's answered my first question .....

You don't need the ppa's anymore, gnome-shell is in the repositories, I'm using it right now. I don't know if it's included in the basic install, but I have gnome-session-fallback installed, which gives you the latest version of the classic two panel interface.

---

### Post by alphacrucis2 on 2011-06-02
> **cariboo907 said:**
> You don't need the ppa's anymore, gnome-shell is in the repositories, I'm using it right now. I don't know if it's included in the basic install, but I have gnome-session-fallback installed, which gives you the latest version of the classic two panel interface.


AFIAK Gnome shell isn't intended to be included with the basic install. The intention is that you would have to manually install it from the repos if you want it.

---

### Post by cariboo on 2011-06-02
> **alphacrucis2 said:**
> AFIAK Gnome shell isn't intended to be included with the basic install. The intention is that you would have to manually install it from the repos if you want it.

I know gnome-shell won't be installed as part of the basic install, but what about gnome-session-fallback?

---

### Post by alphacrucis2 on 2011-06-02
> **cariboo907 said:**
> I know gnome-shell won't be installed as part of the basic install, but what about gnome-session-fallback?

Oh right. I misunderstood your question. I don't know what the intention is for gnome-session-fallback either.

---

### Post by 23dornot23d on 2011-06-02
> 
You don't need the ppa's anymore, gnome-shell is in the repositories,  I'm using it right now. I don't know if it's included in the basic  install, but I have gnome-session-fallback installed, which gives you  the latest version of the classic two panel interface.


ok thanks for that ... but it was not an option in the boot menu ...... 

I have now managed to get a desktop and will see what works ..... 

The Nvidia drivers loaded up ok - I am using 173.14.30 at the moment ....

---

### Post by floydsp on 2011-06-02
can some one help me

floyd@floyd-NY599AA-ABA-e9237c:~$ cd ISO
floyd@floyd-NY599AA-ABA-e9237c:~/ISO$ 
floyd@floyd-NY599AA-ABA-e9237c:~/ISO$ zsync [http://cdimage.ubuntu.com/daily-live...md64.iso.zsync](http://cdimage.ubuntu.com/daily-live...md64.iso.zsync)
failed on url [http://cdimage.ubuntu.com/daily-live...md64.iso.zsync](http://cdimage.ubuntu.com/daily-live...md64.iso.zsync)
could not read control file from URL [http://cdimage.ubuntu.com/daily-live...md64.iso.zsync](http://cdimage.ubuntu.com/daily-live...md64.iso.zsync)

I get this know I am doing something wrong...my zsync file is in ISO
I found my error [http://cdimage.ubuntu.com/kubuntu/daily-live/current/oneiric-desktop-amd64.iso](http://cdimage.ubuntu.com/kubuntu/daily-live/current/oneiric-desktop-amd64.iso)


floydsp

---

### Post by ubuntu27 on 2011-06-02
> **floydsp said:**
> can some one help me

floyd@floyd-NY599AA-ABA-e9237c:~/ISO$ zsync [http://cdimage.ubuntu.com/daily-live...md64.iso.zsync](http://cdimage.ubuntu.com/daily-live...md64.iso.zsync)
failed on url [http://cdimage.ubuntu.com/daily-live...md64.iso.zsync](http://cdimage.ubuntu.com/daily-live...md64.iso.zsync)
could not read control file from URL [http://cdimage.ubuntu.com/daily-live...md64.iso.zsync](http://cdimage.ubuntu.com/daily-live...md64.iso.zsync)

floydsp

That file does not exist. [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I believe what you want is "oneiric-desktop-amd64.iso.zsync"

so, you need to type

```
zsync oneiric-desktop-amd64.iso.zsync
```

---

### Post by sparker256 on 2011-06-02
> **floydsp said:**
> can some one help me

floyd@floyd-NY599AA-ABA-e9237c:~$ cd ISO
floyd@floyd-NY599AA-ABA-e9237c:~/ISO$ 
floyd@floyd-NY599AA-ABA-e9237c:~/ISO$ zsync [http://cdimage.ubuntu.com/daily-live...md64.iso.zsync](http://cdimage.ubuntu.com/daily-live...md64.iso.zsync)
failed on url [http://cdimage.ubuntu.com/daily-live...md64.iso.zsync](http://cdimage.ubuntu.com/daily-live...md64.iso.zsync)
could not read control file from URL [http://cdimage.ubuntu.com/daily-live...md64.iso.zsync](http://cdimage.ubuntu.com/daily-live...md64.iso.zsync)

I get this know I am doing something wrong...my zsync file is in ISO


floydsp

made a test directory called test. In it had oneiric-desktop-amd64.iso

bill@billsim-1110-64:~$ cd test
bill@billsim-1110-64:~/test$ zsync [http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-amd64.iso.zsync)

Is working as I type. I do love multiple windows.

Bill

---

### Post by floydsp on 2011-06-02
Thanks for the replies but Kubuntu 11.10 installer fails when I go to install....typing this now on live cd

floydsp

---

### Post by kevpan815 on 2011-06-02
[http://cdimage.ubuntu.com/releases/11.10/alpha-1/](http://cdimage.ubuntu.com/releases/11.10/alpha-1/) is where you will find the Alpha 1 Milestone Build, however it is usually recommended that you wait 4 the Official Announcement 2 be posted here before trying 2 download it, as the ISO Image either May or May NOT be done Uploading 2 the Download Server right now!

---

