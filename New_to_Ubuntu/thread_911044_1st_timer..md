---
title: "1st timer."
date: 2008-09-05
forum: New to Ubuntu
---

### Post by stat!c on 2008-09-05
Ok new to any flavour of *nux please be gentle,  I have attempted to find the solution on the net.

I have a Pentium III, 512MB RAM  I'm trying to load Ubuntu 8.04.1 LTS Desktop Edn via disk.
Once the kernel is loaded I get
"ubuntu@ubuntu:~$_" come up on a black screen.

What instructions are required to fully load to the "GNOME" ?

(I have successfully loaded Mandriva on the same machine.)

Please help......

---

### Post by isecore on 2008-09-05
You are obviously missing something in your installation.

Not to sound rude, but you're sure you installed from the desktop CD and not the server-version? I've not used Ubuntu Server but I assume that the server edition skips the GUI unless you tell it explicitly to install it.

Alternately you could try running

```
sudo aptitude install ubuntu-desktop
```

after you login and see if that pulls in everything that's missing.

---

### Post by pmlxuser on 2008-09-05
what display driver do you have. i think your system has got a problem with the display driver.

another possibility is you have a defect CD. solution try another copy of CD.

But you can visit  and search the forum: of course be specific on what type/brand of machine you are using is it a laptop /desktop for people to help better.

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: 
```
glxinfo
```

---

### Post by Threbus5 on 2008-09-05
Hi,
I agree with the previous post.

I had a couple instances of inability to properly install. One resulted from a corrupt download and another from poor CD's.
Try another download and a new CD.
Verify the download and during the burn process select to verify the burn.

Oh, and be sure that you obtain the desktop version, not the server version.

Take care.

---

### Post by Crafty Kisses on 2008-09-05
You can always try the alternate CD, and remember to check the md5sum.

---

### Post by stat!c on 2008-09-06
I have run the following scripts with the results:

"sudo aptitude instal ubuntu-desktop"
Result:  "This aptitude does not have Super Cow Powers."

"glxinfo"
Result:  "Error: unable to open display."

The software I have is definately the desktop edition it is a copy sent direct to me from CANONICAL in The Netherlands.  I am using a PC.  The video card is a SiS 6326 AGP.

So far nil progress.......

---

### Post by psycosmyth on 2008-09-06
May as well list your hardware specs.
You may have a bad disk. I have had many.
Someone in your area may be able to send you a better copy.
Did you search the forums hard for that card?
There were many posts last year on that card not being supported.

---

### Post by SteveNorman on 2008-09-06
> **stat!c said:**
> I have run the following scripts with the results:

"sudo aptitude instal ubuntu-desktop"
Result:  "This aptitude does not have Super Cow Powers."

  

install has 2 "ll's", did you type it in that way? The command line is picky

---

### Post by stat!c on 2008-09-06
> **SteveNorman said:**
> install has 2 "ll's", did you type it in that way? The command line is picky

You were right used 2 l's this time.
Read package lists, built dependency tree etc. etc.
"the following packages have been kept back:
ssl-cert"
everything else says that it has been. . .Done.

Still hanging on black screen
Ubuntu@ubuntu: ~$_

---

### Post by dRock1286 on 2008-09-06
> **psycosmyth said:**
> May as well list your hardware specs.
...
Did you search the forums hard for that card?
There were many posts last year on that card not being supported.

I have also had many problems with other people using that brand of video display.

---

### Post by dRock1286 on 2008-09-06
Check out [THIS]("http://www.linuxforums.org/forum/ubuntu-help/104790-sis-graphics-drivers-ubuntu-7-04-a.html")...Specifically post #4.  See if that helps you.

---

### Post by stat!c on 2008-09-06
> **dRock1286 said:**
> Check out [THIS]("http://www.linuxforums.org/forum/ubuntu-help/104790-sis-graphics-drivers-ubuntu-7-04-a.html")...Specifically post #4.  See if that helps you.

Hmmm gave it a go, this is what it came up with:
(gksu:8542): Gtk WARNING **: cannot open display:

Please be patient I haven't got a clue.
My specs:  Pentium 3, AMD 900MHz processor, 512MG RAM, 20G, SiS 6326 AGP.

I'm guessing I will not be able to run this ver. of ubuntu with current video card.

---

