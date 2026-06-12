---
title: "Integrating IDM with Firefox"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-11-15
Hey guys,

I'm trying to integrate Firfox with IDM(Internet Download Manager). And as most know, IDM does not run natively in Linux, so it has to be emulated through Wine.

So, in IDM, when I go to Downloads>Options>Integrate IDM into Browsers...and tick the Firefox box, I get an error message that pops up and says:

***IDM Cannot Find Mozilla Firefox browser on your computer. Please locate the browser executable file on the next dialog.***

Then a Windows type Browse box pops up, and I'm browsing to usr/bin...but there is no Firefox.exe in it.

So would anyone know how to integrate IDM with FF in Ubuntu?

Any help will be greatly appreciated.

Thanks.

---

### Post by stonecoldjha on 2008-11-15
unfortunately,all my efforts in this direction have failed.i too had tried implementing that using wine,for a wine installed windows version of firefox.i suggest that you should better use downthemall for firefox,it is a nice download manager.

---

### Post by h8uthemost on 2008-11-15
Yeah, I've been searching and searching, and just could not find anything on this. So I thought here would be my last stop before I gave up. Hopefully they make a Linux compatible IDM in the future.

And yeah, DTA is pretty good, I sometimes get inconsistent speeds though. 

Is this the reason why I'm not able to get Flashget to work in Linux too? I'm guessing since both IDM and Flashget do not run natively in Linux, you just can't use them?

Thanks for the help.

---

### Post by bscbrit on 2008-11-15
> and Flashget do not run natively in Linux

Flashget works perfectly for me in Ubuntu and has done for many years.  What kind of errors are you experiencing?

EDIT I'm mistaken, I'm using Flashgot (with Aria) and not Flashget to do my downloading.  Together, they work perfectly.

---

### Post by bscbrit on 2008-11-15
Rather than trying to find how to get a version of a Windows program that will run on Linux, why don't you use one of the many linux downloaders to do the task?  E.g. wget, d4x, curl, aria (1 and 2 - very different from each other) etc.  Or have I misread something here?

---

### Post by h8uthemost on 2008-11-15
Well, specifically, I'm downloading Rapidshare links. And I've been using jdownloader for my free account. But I'm going to get me a premium account at the end of the month.

So what would be a good downloader to handle premium RS links?

---

### Post by bscbrit on 2008-11-16
Well, I have no reason to believe that aria cannot download RS links.

aria is available from the repos. It is relatively old with a non-standard but perfectly usable GUI.  I've used it for many years and I've not had any problems with it.  It can automatically download and sort data according to type, actual source domain, referring source domain and several other options which means that, no matter how much I download, the data is always sorted and easy to manage.

Others prefer Downloader4X (in the repos as d4x).  This is similar to several windows downloaders and some relatively recent linux converts prefer it because of this familiarity.  I've never managed to persuade it to sort my data as effectively as aria - that's probably because I don't know how to rather than a failing of the program!

Downloaders such as wget (or GUI variants such as Gwget and Kwget) are also very powerful.  I've not used the graphics versions personally so I 
will not make any judgment on them. wget I have used numerous times in scripts to automate downloading web data on a regular basis. I've also produced a perl script which sits on another computer and uses LWP.  I feed it urls when I'm working and it will download them overnight when my network is usually under-utilised :-)  In short, with linux there are numerous options for downloading.

The biggest problem with any new downloader is that, to the user, it is **new**.  It is never exactly the same as the downloader that they have used previously and some simply do not have the patience to get used to the new one.  But any linux user - who has already realised that linux is NOT windows - shouldn't have too much problem in this area.

Flashgot is a FF add-on which will interface to any downloader.  A couple of clicks on a link or the entire web page that is displayed in FF, and the downloading of the data can be fully automated.  It doesn't get much easier than this...

---

### Post by h8uthemost on 2008-11-16
That's a lot of great info bscbrit. I was actually worried how jdownloader would handle a premium RS account. But I just got my hands on a premium RS account, and jdownloader handles the links beautifully. So for downloading from RS, I may stick with jdownloader. I'm not sure yet.

But for downloading everything else(as jdownloader only downloads from file hosts like RS), I'm going to try the ones you mentioned above, as I get inconsistent speeds with DownThemAll(the downloader I've been using with FF). I really like DTA  though as it's so simple.

I'm going to give Aria combined with Flashgot a shot, since you seem to like this quite a bit. After that I'm going to try Downloader4x, since I read about it somewhere else, and people seem to like it a lot. Then I'll get to the others you mentioned.

But as you said, as a new Linux user, it's just going to take me a while to get used to any new downloader, since it is all new to me. I've been using IDM for almost two years now on Windows, and that was by far my preferred downloader. So hopefully I'll be able to get hooked on one of the mentioned downloaders as much as I was with IDM.

Thank you for your help. I really appreciate it.

---

### Post by bscbrit on 2008-11-16
You're welcome.

Please use the Thread Tools to mark this thread as SOLVED if you are happy with the answers you have received.

See you around the forums.  Good luck.

---

