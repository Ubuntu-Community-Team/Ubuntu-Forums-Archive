---
title: "Why do we all need to compile software - example: digiKam 0.9.3"
date: 2008-02-17
forum: Recurring Discussions
---

### Post by PiggiePaul on 2008-02-17
This is something I don't really understand.

Now, given that there are MANY different flavours of Linux, I can appreciate the whole source code and compiling thing. You need it to make sure you end up a version that's right for what you run.

But......................

And here is the bit I don't get..................

Why do the (millions?) or users all using the same version of Ubunta (as an example) have to re-invent the wheel personally each time?

Now, (as an example) I (like many other here) are running the current Ubuntu version 7.1 Gutsy, and I'd like to run the Photo software: digiKam 0.9.3

Now if someone downloads the source, compiles it for Ubuntu 7.1 can't others then just use this compiled version, rather than everyone doing the same thing?

It kinda sounds like, selling the ingredients for a loaf to everyone, rather than actually 1 person doing the baking and everyone else being able to get loafs ready made.

Perhaps I'm misunderstanding something here?

Is it hard (if you know what you are doing) to take (as an example) the latest digiKam 0.9.3 source, compile it into a self installing package and upload it for others to download and install without every single person having to go through the compile process?

This is what I don't get :confused:

---

### Post by Joeb454 on 2008-02-17
You don't have to download and compile it from source.

Sometimes you do for the smaller app's...but check out [getdeb.net]("http://www.getdeb.net") :)

---

### Post by sb12 on 2008-02-17
people compile things to either optimize it for their system or to enable.disable features they dont need normally

e: also yea most lareger prgrams have debian packaes for you to use or are in synaptic.

---

### Post by zerhacke on 2008-02-17
It seems you have yet to discover apt-get or Synaptic or any of the other myriad of package managers.

---

### Post by julian67 on 2008-02-17
Gutsy was released in October 2007.  Digikam 0.9.3 was released in December 2007 so it easy to see why it isn't included in Gutsy.  I'm sure it will be in Kubuntu 8.04 come April and available from the repos for Ubuntu, Xubuntu, fluxbuntu etc.  If you always want the absolute latest versions of applications then Ubuntu isn't the distro to use because updates are mostly patches and fixes rather than new versions of applications (there are a few exceptions but not many), though at least you get cutting edge twice a year with new Ubuntu releases.  If you want to always have access to the newest versions of apps you need to be looking at using a distro that has rolling releases such as Arch or one like Debian that has Stable, Testing and Unstable versions where you can choose to run Testing or even Unstable. Most apps are actually very easy to compile from source, a few are not and I believe Digikam might be something of a challenge but why not try?

edit to above posters: digikam 0.9.3 is not available for Gutsy from the repos or from getdeb,  he won't find it that way ;-)

---

### Post by oldos2er on 2008-02-17
Why not just type "sudo aptitude install digikam" in a terminal?

---

### Post by julian67 on 2008-02-17
> **oldos2er said:**
> Why not just type "sudo aptitude install digikam" in a terminal?

[genius@work]because he won't get version 0.9.3 which he wants, but 0.9.2 which he doesn't. [/genius@work]

---

### Post by LaRoza on 2008-02-17
You can make it into a package yourself...

---

### Post by sb12 on 2008-02-17
from the digikam website:

Kubuntu

Achim Bohnet tries to provide the latest version of digiKam via his own repository. You can add the following to your /etc/apt/sources.list:
Feisty


deb [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./
Edgy


deb [http://www.mpe.mpg.de/~ach/kubuntu/edgy](http://www.mpe.mpg.de/~ach/kubuntu/edgy) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/edgy](http://www.mpe.mpg.de/~ach/kubuntu/edgy) ./

After that a apt-get update, apt-get install digikam kipi-plugins will get you up-to-date.

contains 0.9.3 ;p

---

### Post by PiggiePaul on 2008-02-17
> **Joeb454 said:**
> You don't have to download and compile it from source.

Sometimes you do for the smaller app's...but check out [getdeb.net]("http://www.getdeb.net") :)

Yes, indeed, getdeb is exactly what I mean.
I don't really understand why this is not done more :confused:

---

### Post by Joeb454 on 2008-02-17
Too much effort maybe?

Compiling has it's advantages though. Especially for more advanced users :)

---

### Post by PiggiePaul on 2008-02-17
> **LaRoza said:**
> You can make it into a package yourself...

Yes, and in time, (with any program) that's what I hope I'll be able to do.

But at the moment, that's flying and I'm still only crawling on the ground ;)

If I knew how, then it would seem obvious to get the source, compile it into a package (forgive me if I use the wrong terminology) and then upload it for others to just use, without all the hassle.

Of course, if you are experienced enough to do it yourself (or just enjoy customizing bits) then the normal option is still the same.

I suppose what I don't get is...............

(and I know some places do this)

If you/your team developed some software, then as well as the source on your website, you would obviously? offer self installing versions for a few popular Linux Flavors for download also, for those without the tools/knowledge to do it for themselves.

But perhaps I'm wrong?

It just seems an obvious (and helpful to users) thing to do.

Perhaps over the next few years, as Linux grows and grows in popularity and certain versions (Ubuntu?) become the leaders in the race? it will become more the norm for this to happen as it becomes more main stream.

I have to say, apart from a few hair pulling moments during the 1st few days (my 1st week!) I have nothing but praise in general for Ubuntu

And, or course, nothing but admiration and thanks to all those on these forums for their excellent help and advice they offer.

:D

---

### Post by Tyke91 on 2008-02-17
> **LaRoza said:**
> You can make it into a package yourself...
I'd love to know how to do that... I'd like to make a custom mod of Frets on Fire and then distribute it to my friends (all free, all people involved documented, GPL stuff) but i don't know how to compress it into a package

---

### Post by LaRoza on 2008-02-17
> **Tyke91 said:**
> I'd love to know how to do that... I'd like to make a custom mod of Frets on Fire and then distribute it to my friends (all free, all people involved documented, GPL stuff) but i don't know how to compress it into a package

See the Development and Programming forum, it has a forum for packaging and compiling.

Note, you don't need to know how to program.

---

### Post by sb12 on 2008-02-17
> **Tyke91 said:**
> I'd love to know how to do that... I'd like to make a custom mod of Frets on Fire and then distribute it to my friends (all free, all people involved documented, GPL stuff) but i don't know how to compress it into a package

[http://www.linuxdevices.com/articles/AT8047723203.html](http://www.linuxdevices.com/articles/AT8047723203.html) may help

---

### Post by PiggiePaul on 2008-02-17
> **sb12 said:**
> from the digikam website:

Kubuntu

Achim Bohnet tries to provide the latest version of digiKam via his own repository. You can add the following to your /etc/apt/sources.list:
Feisty


deb [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./
Edgy


deb [http://www.mpe.mpg.de/~ach/kubuntu/edgy](http://www.mpe.mpg.de/~ach/kubuntu/edgy) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/edgy](http://www.mpe.mpg.de/~ach/kubuntu/edgy) ./

After that a apt-get update, apt-get install digikam kipi-plugins will get you up-to-date.

contains 0.9.3 ;p

Thanks for the reply, and I did see this link on their site, but it didn't (and still does not) mean much to me.

Feisty and Edgy but no Gutsy, and even if there was I don't really know enough to follow your advice.

---

### Post by sb12 on 2008-02-17
> **PiggiePaul said:**
> Thanks for the reply, and I did see this link on their site, but it didn't (and still does not) mean much to me.

Feisty and Edgy but no Gutsy, and even if there was I don't really know enough to follow your advice.

if you look in the actual repo there is gutsy also, all you would do is edit your sources.list to include those two lines, and change feisty to gutsy.n then update and install

---

### Post by PiggiePaul on 2008-02-20
> **sb12 said:**
> if you look in the actual repo there is gutsy also, all you would do is edit your sources.list to include those two lines, and change feisty to gutsy.n then update and install

Thanks for your advice.
But your instructions are a little beyond me right now.

Unless you can do a more (step by step) and where what instruction for me to follow :)

I have found these:

 deb [http://www.mpe.mpg.de/~ach/kubuntu/gutsy](http://www.mpe.mpg.de/~ach/kubuntu/gutsy) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/gutsy](http://www.mpe.mpg.de/~ach/kubuntu/gutsy) ./ 

It's just what to do with them?

---

### Post by nhandler on 2008-02-20
Launch a terminal (Applications->Accessories->Terminal). Now type

```
gksudo gedit /etc/apt/sources.list
```

Copy these two lines.
> deb [http://www.mpe.mpg.de/~ach/kubuntu/gutsy](http://www.mpe.mpg.de/~ach/kubuntu/gutsy) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/gutsy](http://www.mpe.mpg.de/~ach/kubuntu/gutsy) ./ 

Paste them at the end of the document. Now hit Save, and close Gedit (the text editor). Now, in the terminal, enter the following commands

```
sudo apt-get update
sudo apt-get install digikam kipi-plugins

```

You will be prompted for you password when entering the above commands, just enter it and hit enter (You will not see anything as you type).

After you do everything above, you should have the latest version of gutsy.

---

### Post by PiggiePaul on 2008-02-21
> **Cheater said:**
> Launch a terminal (Applications->Accessories->Terminal). Now type

```
gksudo gedit /etc/apt/sources.list
```

Copy these two lines.


Paste them at the end of the document. Now hit Save, and close Gedit (the text editor). Now, in the terminal, enter the following commands

```
sudo apt-get update
sudo apt-get install digikam kipi-plugins

```

You will be prompted for you password when entering the above commands, just enter it and hit enter (You will not see anything as you type).

After you do everything above, you should have the latest version of gutsy.

Thanks (I think!)

Followed your instructions (and code) and after a lot of downloading and installing things, I now have DigiKam on my system.

1 thing is puzzling (worrying) me.

what exactly was it doing during all this work (which after issuing those console commands) looked a LOT MORE than just downloading and installing an app?

And what did you mean by the comment: [COLOR="Blue"]"After you do everything above, you should have the latest version of gutsy."
[/COLOR]

I need to ask as a couple of odd things have happened since doing this, and wondering what all that stuff going by in the terminal window was actually doing.

Going to re-boot, just in case.

---

### Post by Doorslammer on 2008-02-21
the person just showed you how to install  programs is all 
nothing wrong !! 

sudo = temp admin rights 
apt-get  = command-line tool for handling packages ( programs )

when you run apt-get  it will download the package you  told it to & any dependency packages needed for your program to install & run..
 nothing bad  happened to your system because of those commands..
you could alway look stuff up  google  works for everyone & you don't even have to install it .

---

### Post by PiggiePaul on 2008-02-21
> **Doorslammer said:**
> the person just showed you how to install  programs is all 
nothing wrong !! 

sudo = temp admin rights 
apt-get  = command-line tool for handling packages ( programs )

when you run apt-get  it will download the package you  told it to & any dependency packages needed for your program to install & run..
 nothing bad  happened to your system because of those commands..
you could alway look stuff up  google  works for everyone & you don't even have to install it .

Thanks for putting my mind as ease :)

Perhaps it was also to do with a system update (some new security patches) tonight.

Just that after installing DigiKam I minimized an application, then clicked once on the taskbar to maximize the program again and ubuntu kicked me out and I went back to the login screen!

Then about 10 mins later, I  loaded up Amarok and the fonts had got BIGGER on screen (just Amarok) then for no reason Amarok just killed itself.

So, I just was a bit worried.

Anyway, did a reboot of the machine, and seems ok, now, so perhaps just a combination of things.

Even my Amarok font is back to the right size again.

Odd huh?

---

### Post by nhandler on 2008-02-21
> **PiggiePaul said:**
> Thanks (I think!)

Followed your instructions (and code) and after a lot of downloading and installing things, I now have DigiKam on my system.

1 thing is puzzling (worrying) me.

what exactly was it doing during all this work (which after issuing those console commands) looked a LOT MORE than just downloading and installing an app?

And what did you mean by the comment: [COLOR="Blue"]"After you do everything above, you should have the latest version of gutsy."
[/COLOR]

I need to ask as a couple of odd things have happened since doing this, and wondering what all that stuff going by in the terminal window was actually doing.

Going to re-boot, just in case.

**sudo apt-get update** downloads a list of all the packages available in the repositories. Since we added some new repositories to /etc/apt/sources.list, we need to issue this command to be able to install the new packages.

**sudo apt-get install digikam kipi-plugins** installs digikam, kipi-plugins, and any of their required dependencies. It will use the repository we just added to download the package.

I had mean to say "After you do everything above, you should have the latest version of *digikam*."

---

### Post by zeltak on 2008-02-29
hi all

i am also trying to install digikam 0.9.3 but unfortunately the 
deb [http://www.mpe.mpg.de/~ach/kubuntu/gutsy](http://www.mpe.mpg.de/~ach/kubuntu/gutsy) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/gutsy](http://www.mpe.mpg.de/~ach/kubuntu/gutsy) ./ 

does not work with a 64 bit system (thats what i use)

I have tried to compile with no success any ideas of an 64bit deb file for gutsy?

thx

zeltak

---

### Post by PiggiePaul on 2008-02-29
> **zeltak said:**
> hi all

i am also trying to install digikam 0.9.3 but unfortunately the 
deb [http://www.mpe.mpg.de/~ach/kubuntu/gutsy](http://www.mpe.mpg.de/~ach/kubuntu/gutsy) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/gutsy](http://www.mpe.mpg.de/~ach/kubuntu/gutsy) ./ 

does not work with a 64 bit system (thats what i use)

I have tried to compile with no success any ideas of an 64bit deb file for gutsy?

thx

zeltak


Oh, that's a bit bad.....

Having asked about ubuntu 64-bit recently, I was lead to believe it ran "Normal" apps fine.

Perhaps I "Should" stick with "normal" ubuntu if there are 64-bit problems like this.
(as there seems to be little to gain)

---

