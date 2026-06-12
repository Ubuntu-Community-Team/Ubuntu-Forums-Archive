---
title: "ms office"
date: 2010-05-24
forum: Recurring Discussions
---

### Post by saakeman on 2010-05-24
I think dis is a problem for most of us {microsof office in ubuntu):neutral: 

any it pros on ubuntu help us all !

---

### Post by sandyd on 2010-05-24
> **saakeman said:**
> I think dis is a problem for most of us {microsof office in ubuntu):neutral: 

any it pros on ubuntu help us all !
what do you mean it doesn't work?

it works... if you want to use it...

and no, despite what you think, thats not windows 7... 
I just haven't changed my computer back to normal... yet... :|

---

### Post by mbzn on 2010-05-24
Open Office is more than 90% problem free with ms-office files. Have you tried open office?

X-over
[http://www.builderau.com.au/program/unix/soa/Use-Microsoft-Office-in-Linux-You-can-now-/0,339024638,320267310,00.htm](http://www.builderau.com.au/program/unix/soa/Use-Microsoft-Office-in-Linux-You-can-now-/0,339024638,320267310,00.htm)

or wine
[http://www.wine-reviews.net/microsoft/running-ms-office-2003-under-linux-with-wine-0952.html](http://www.wine-reviews.net/microsoft/running-ms-office-2003-under-linux-with-wine-0952.html)

---

### Post by jfreak_ on 2010-05-24
@Carlee - Did you put any special configuration( ie additional libraries etc) into wine before installing?

---

### Post by saakeman on 2010-05-24
> **mbzn said:**
> Open Office is more than 90% problem free with ms-office files. Have you tried open office?

X-over
[http://www.builderau.com.au/program/unix/soa/Use-Microsoft-Office-in-Linux-You-can-now-/0,339024638,320267310,00.htm](http://www.builderau.com.au/program/unix/soa/Use-Microsoft-Office-in-Linux-You-can-now-/0,339024638,320267310,00.htm)

or wine
[http://www.wine-reviews.net/microsoft/running-ms-office-2003-under-linux-with-wine-0952.html](http://www.wine-reviews.net/microsoft/running-ms-office-2003-under-linux-with-wine-0952.html)

i love openoffice and use it on ubuntu but the powerpoint is not as good as ms office 

--------------------------
join 
facebook= dustbin of history

---

### Post by saakeman on 2010-05-24
> **carlee said:**
> what do you mean it doesn't work?

it works... if you want to use it...

and no, despite what you think, thats not windows 7... 
I just haven't changed my computer back to normal... yet... :|

Is that a skin for ubuntu looks like windows 7/vista ???

---

### Post by mk1w86 on 2010-05-24
Which version of MS Office are you using and what is it you need that OpenOffice doesn't do?

---

### Post by sandyd on 2010-05-24
> **jfreak_ said:**
> @Carlee - Did you put any special configuration( ie additional libraries etc) into wine before installing?
hmm lets see....

```

winetricks allfonts fontfix droid fontsmooth-rgb msxml6 
```
overrides: usp10, ole, riched20

oh, and a few micelaneous wine hacks as well.

---

### Post by geeklove2rock on 2010-05-24
> **saakeman said:**
> I think dis is a problem for most of us {microsof office in ubuntu):neutral: 

any it pros on ubuntu help us all !
why dont you prefer ubnutu documentation section may be this help you

[https://help.ubuntu.com/community/Microsoft_Office](https://help.ubuntu.com/community/Microsoft_Office)
enjoy

---

### Post by sandyd on 2010-05-24
> **saakeman said:**
> Is that a skin for ubuntu looks like windows 7/vista ???
[http://dolphinaura.com/linux/windows-7-look-for-kde](http://dolphinaura.com/linux/windows-7-look-for-kde)
not reccomended.

---

### Post by sandyd on 2010-05-24
alright...

to install microsoft office, run the following in the terminal...
```

sudo apt-get install wine
wget -c [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
chmod 667 winetricks
sh ./winetricks allfonts fontfix fontsmooth-rgb msxml6 wsh56
winecfg

```click on "libraries"
Set new overrides for the following (Just type each in and press add)
```

riched20
usp10
```double click the MS Office Installer.

Done.

---

### Post by jfreak_ on 2010-05-24
> **carlee said:**
> hmm lets see....

oh, and a few micelaneous wine hacks as well.

Any memory of what they were?

---

### Post by sandyd on 2010-05-24
> **jfreak_ said:**
> Any memory of what they were?
their git hacks - very experimental and specific to msoffice. I was fooling around with them to see if I could fix some still-not-working things.

not reccomended for anyone elses use, unless you feel like manually editing the wine source code.
their not really needed

---

### Post by bobbob1016 on 2010-05-24
> **saakeman said:**
> I think dis is a problem for most of us {microsof office in ubuntu):neutral: 

any it pros on ubuntu help us all !

Don't say "most" I have no desire to use MS Office, OpenOffice does everything I need.  OpenOffice is free, MS Office is not.  OpenOffice reads/writes in files that pretty much any other OpenOffice can read/write afaik.  MS Office defaults in a way that requires you to buy the newer MS Office to open (see: 2k7 saving in docx without telling people "Only 2k7 can read these files" and all the headaches that caused).

---

### Post by sandyd on 2010-05-24
> **bobbob1016 said:**
> Don't say "most" I have no desire to use MS Office, OpenOffice does everything I need.  OpenOffice is free, MS Office is not.  OpenOffice reads/writes in files that pretty much any other OpenOffice can read/write afaik.  MS Office defaults in a way that **requires you to buy the newer MS Office to open** (see: 2k7 saving in docx without telling people "Only 2k7 can read these files" and all the headaches that caused).
wrong.
[http://www.microsoft.com/downloads/details.aspx?familyid=941b3470-3ae9-4aee-8f43-c6bb74cd1466&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=941b3470-3ae9-4aee-8f43-c6bb74cd1466&displaylang=en)

---

### Post by philinux on 2010-05-24
Moved to Recurring

---

### Post by bobbob1016 on 2010-05-25
> **bobbob1016 said:**
> Don't say "most" I have no desire to use MS Office, OpenOffice does everything I need.  OpenOffice is free, MS Office is not.  OpenOffice reads/writes in files that pretty much any other OpenOffice can read/write afaik.  MS Office defaults in a way that requires you to buy the newer MS Office to open (see: 2k7 saving in docx without telling people "Only 2k7 can read these files" and all the headaches that caused).

> **carlee said:**
> wrong.
[http://www.microsoft.com/downloads/details.aspx?familyid=941b3470-3ae9-4aee-8f43-c6bb74cd1466&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=941b3470-3ae9-4aee-8f43-c6bb74cd1466&displaylang=en)

Let me rephrase that, "Up until recently, Office <= 2k3 couldn't read docx."  That says it was released 1/6/2010.  2k7 still saves in a new format by default, one that 2k3 and below can't natively read.  Even if the date was for the latest release, and it was released when 2k7 was, it was still a pain.  My school didn't include the patches afaik, and shouldn't be expected to rework their deepfreeze images when a new version of Office, that they aren't upgrading to, comes out.

---

### Post by mamamia88 on 2010-05-25
actually with the newest version of ubuntu and the newest version of wine, office 2007 installed without a problem.  word, excel, powerpoint,outlook, and publisher all work fine.

---

### Post by saakeman on 2010-05-29
> **mk1w86 said:**
> Which version of MS Office are you using and what is it you need that OpenOffice doesn't do?

ms powerpoint

---

### Post by lisati on 2010-05-29
> **saakeman said:**
> ms powerpoint

Open Office has "impress" which does the same job.

---

### Post by Random_Dude on 2010-05-29
> **lisati said:**
> Open Office has "impress" which does the same job.

I think the main problem is (not only with powerpoint, but mostly with powerpoint) the compatibility between Impress and MS Powerpoint.
When you change from one to another the layout becomes completely messed up. It's not a problem if your doing a presentation by yourself, but if you're working with other people it becomes a issue.
I guess that this is impossible to avoid.

Cheers :cool:

---

### Post by saakeman on 2010-05-29
I think , if half of the world start using ubuntu then the programmers will start making programs for it .
Games will also be available    to play :)

---

### Post by juancarlospaco on 2010-05-29
*Get Lyx*

---

### Post by jerenept on 2010-05-29
Lucid lynx
Unless you are talking about licks?

---

### Post by mk1w86 on 2010-05-29
> **jerenept said:**
> Lucid lynx
Unless you are talking about licks?

This is LyX:

[http://www.lyx.org/](http://www.lyx.org/)

---

### Post by OLDMANHOOK on 2010-05-31
I don't get some of the posts Here the same people post in i hate MS but wants MS products to work i Ubuntu I Run a small business on all open source software including OOo, GnuCash, Scribus the only thing i have from MS is fonts and wireless KB and Mouse which work most people think they have to use MS office, but as i told two of my workers  if you need MS office Buy It now  they use OOo and ubuntu one even told the local school system to buy MS office if they want her child to use it What i'm saying is 99% of what you think you need you Don't Just think you do----- Gimp for Photoshop Firefox for IE Any Lunix Distro for OS. If You have a Need For MS Office Stick With Windows 7 Or dual boot the so called work arounds  and lines of code scare People away from LINUX,

---

### Post by rainbowagent7 on 2010-05-31
I'll just throw in my 2 cents. I love Ubuntu and everything about it, but there is still one little, tiny, itsy bitsy thing I crave from M$, and that is the grammar check on student office '07. Oo hasn't implemented one yet and I really, really need one for school because I'm hardcore into writing and the grammar check is crucial. Aside from that, I agree with most Ubuntu users on the fact that Microsucks is garbage. Anyways, peace!

P.S. I was originally checking this post to figure out how to install M$ Office '07, can anyone point me in the right direction? I'm running Ubuntu Hardy. Thanks in advance.

---

### Post by saakeman on 2010-06-01
The reason why i want MS OFFICE IS , everybody else has it !
and on open office presentation , when i move it to a person using MS OFFICE  the thing mess up on ms office powerpoint

---

### Post by saakeman on 2010-06-01
> **OLDMANHOOK said:**
> I don't get some of the posts Here the same people post in i hate MS but wants MS products to work i Ubuntu I Run a small business on all open source software including OOo, GnuCash, Scribus the only thing i have from MS is fonts and wireless KB and Mouse which work most people think they have to use MS office, but as i told two of my workers  if you need MS office Buy It now  they use OOo and ubuntu one even told the local school system to buy MS office if they want her child to use it What i'm saying is 99% of what you think you need you Don't Just think you do----- Gimp for Photoshop Firefox for IE Any Lunix Distro for OS. If You have a Need For MS Office Stick With Windows 7 Or dual boot the so called work arounds  and lines of code scare People away from LINUX,

That's the  problem  
we are afraid of losing our PROGRAMS
if your choice is ubuntu/linux then you will know that some of your programs will not work and you will know that you will have to get use to other programs 
i don't mean programs like PICASA  , SKYPE , VLC , FIREFOX (and many more)
Programs for windows thats what you will loose!

---

### Post by cph05a on 2010-06-01
if you're dead set on using MS Office, you can use it in Linux using [wine ]("http://www.winehq.org/")or [crossover]("http://www.codeweavers.com/products/cxlinux/").

I'd recommend crossover since it's really easy to use. On the other hand, wine is free.

---

