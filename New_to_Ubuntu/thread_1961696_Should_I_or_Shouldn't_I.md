---
title: "Should I or Shouldn't I?"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by sl23 on 2012-04-19
Ubuntu v11.10 via CD

Hi I've been tempted before by Ubuntu when an old laptop of a friend needed recovering and now again I find a similar problem with an Acer 2930. The recovery partition is corrupt and though I finally made the recovery discs for it after 8 attempts they are as corrupt as the recovery partition!

Anyway, I love the idea of Ubuntu, my previous experience with Ubuntu wasn't good as I couldn't get the Wi-Fi to work. But a short go on the live CD has been fairly good going apart from an unknown crash. Basically the desktop background and icons remained as did the Firefox window, but the 'Taskbars' at the top and left disappeared and a crash report window opened, though I couldn't send the report.

Is this a common problem with Ubuntu, I mean does it crash on a regular basis? I hate Windows as it's so bloated and there's just so much garbage included with a laptop when bought that I'd love to switch. My problem is that I use a few apps not available on Ubuntu. Mainly music apps like Muzys, Mu-Lab, Reason. Is there any chance Ubuntu will run Windows apps one day?

The other thing that puts me off is that the one good thing about my current laptop setup is that I have Windows on C: and all my data and apps on D: the reason is that ALL my apps are portable with exception of certain things like Novation Automap, AVG Free, Reason. So when I need to reinstall Windows my apps are untouched and ready to go again without the need to reinstall everything.

If Ubuntu install goes wrong and Firefox and how ever many other apps there are installed it means losing all the settings, bookmarks and all other data if a fresh install is needed. Can't the apps be made portable and saved to a USB device like on Windows? If these things could be sorted I'd definitely be a convert!

It's a fantastic effort and I really like it but it's just not what I need, shame. I'll likely install to my 2930 just for the internet for my girlfriend though. But I'm concerned about stability as I already said. But I'd like to install as dual boot so keeping Windows intact while using Ubuntu on the D: partition, is that possible?

Thanks for your help

Scott

---

### Post by MG&amp;TL on 2012-04-19
Ubuntu is (most of the time) very stable. Some hardware combinations may cause problems, but on the whole, it's very stable. Running from CD is also going to be very slow and potentially buggy.

As for windows, you can setup a dual boot, meaning that windows is untouched, so your stuff remains where it is. You can even access your windows partition from ubuntu.

As for separate partitions, that is one road you can go down with the partitioner, but for just trying ubuntu out, I suggest leaving it. You can do that when you become a serious distro-hopper. :)

I'm not familiar with the apps you mention; but there are many music apps available on ubuntu-see if you like those. If you're lucky, they may even run in wine.

---

### Post by audiomick on 2012-04-19
You should, of course... ;)

> **sl23 said:**
> Ubuntu v11.10 via CD

Hi I've been tempted before by Ubuntu when an old laptop of a friend needed recovering and now again I find a similar problem with an Acer 2930. The recovery partition is corrupt and though I finally made the recovery discs for it after 8 attempts they are as corrupt as the recovery partition!
For me, that is a no-brainer. Stick a Linux on it.

> ...I couldn't get the Wi-Fi to work...
... does it crash on a regular basis?
Yes, wifi can be a problem. On the other hand, that, like a lot of other things, is getting better all the time. Suck it and see. It might work now. If it doesn't, there is a fair chance that someone here will know what to do.


>  I hate Windows ...chance Ubuntu will run Windows apps...
I'll bet you don't hate windows as much as me. :) I have a windows install on my laptop because there are a number of programs I need for work to do with Professional Audio that only run on windows. For programs that don't occupy such a narrow niche, you have a good chance that they might run in Wine. For Programs that are very general. like an Office suite, there is almost certainly an alternative for Linux that may even be better than the windows program you are using now.

> 
The other thing that puts me off is that the one good thing about my current laptop setup is that I have Windows on C: and all my data and apps on D: 
...
If Ubuntu install goes wrong and Firefox and how ever many other apps there are installed it means losing all the settings, bookmarks and all other data if a fresh install is needed....
This is easy. All your data is stored by default on the /home folder, as are all your config files. Put the /home folder in a partition of it's own, and you can re-install as often as you want. Retain the /home partition in the new install, and you are back where you where before it broke. Remember: an Ubuntu install comes with a heap of common programs installed by default, like firefox and Libre Office. This means that you don't have to spend another several hours after the install re-installing your programs. Most of them will be there as soon as the install is finished. For the ones that aren't, installing a program in Ubuntu is generally a matter of a couple of minutes, and doesn't usually require a re-start.

> But I'd like to install as dual boot so keeping Windows intact while using Ubuntu on the D: partition, is that possible?

Yes, this is possible. The easiest way is to use the "install along side of" option in the installer. That will put Ubuntu onto it's own partition (without a separate /home), leave the windows install there and offer you the choice at boot of which OS you want to boot into.

I would suggest looking a little deeper and thinking about making your own partition scheme, but you don't have to if you don't want to.

---

### Post by cortman on 2012-04-19
There are two kinds of Ubuntu: LTS and current version. The LTS (long term support) is guarenteed bug fixes, support, and program compatibility for five years. LTS versions are rock solid.
Ubuntu releases a new iteration of the system every six months. These can be a bit buggy at times.
Current LTS is Ubuntu 10.04. It's still supported for another year.
The impending release, 12.04, is the next LTS. It will be supported until 2017. Current release date for 12.04 is April 26.
If you want stability, I would recommend installing 10.04. It's available on the main Ubuntu download page. You can upgrade to 12.04 when it comes out, or you can wait the extra year, after which it will be even more stable.
I would heartily recommend Ubuntu! If your recovery disks/partition is corrupt anyway, you have nothing to lose.
And if you run into any problems, always feelf ree to post on these forums. No question is too stupid.
Good luck!

---

### Post by dzponce11 on 2012-04-19
That's a no brainer: YES.
Just go for a LTS release.

~~~~dzponce11

---

### Post by Cheesemill on 2012-04-19
> **cortman said:**
> There are two kinds of Ubuntu: LTS and current version. The LTS (long term service) is guarenteed bug fixes, support, and program compatibility for five years. LTS versions are rock solid.

Sorry, I really can't help myself. LTS stands for **L**ong **T**erm **S**upport, not service.

---

### Post by audiomick on 2012-04-19
> **MG&TL said:**
> ...there are many music apps available on ubuntu-...

> **sl23 said:**
>  Mainly music apps like Muzys, Mu-Lab, Reason....Novation Automap,... Reason.
Scott


Didn't twig to this when I read your post earlier, Scott. You need to have a look at Ubuntu Studio, whether you decide to keep using Windows or not.

[http://en.wikipedia.org/wiki/Ubuntu_Studio]("http://en.wikipedia.org/wiki/Ubuntu_Studio")

---

### Post by cortman on 2012-04-19
> **Cheesemill said:**
> Sorry, I really can't help myself. LTS stands for **L**ong **T**erm **S**upport, not service.

Gaaaa! Did I actually type that???

Sheesh. Cortman the grammar nazi just took a blow.

Thanks. :)

---

### Post by 23dornot23d on 2012-04-19
[COLOR=Red][B]Just in case you do not already know ....

           The 12.04 LTS release is due out in just 1 weeks time .....[/B][/COLOR]

Your specifications for the computer appear to be suitable too .... 
[http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire2930/Aspire2930sp3.shtml](http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire2930/Aspire2930sp3.shtml)

Only way to know for sure is to try it in a weeks time though ..... first as a LiveCD

  [_[COLOR=Blue]**12.04 ..... VIDEO of the BETA**[/COLOR]_]("http://www.youtube.com/watch?v=PW0UXluiGCA")

Then if all is ok >>> do a full install of the full New version >>> in 7 days time ......

---

### Post by Mark Phelps on 2012-04-21
> **sl23 said:**
> ...The recovery partition is corrupt and though I finally made the recovery discs for it after 8 attempts they are as corrupt as the recovery partition! 
Then ... you're not doing it right!  But why go to all that trouble when, in a few minutes, you could download and install the FREE version of Macrium Reflect and image off your Windows install to an external drive.  Whole process can be done in less than 30 minutes, including the download and install.

> My problem is that I use a few apps not available on Ubuntu. Mainly music apps like Muzys, Mu-Lab, Reason. Is there any chance Ubuntu will run Windows apps one day? 
Linux's ability to run Windows apps varies considerably by app, and by the particular version of each app.

Rather than guess, or make presumptions based on the generalizations of others, go to the WineHQ site and look up the apps and versions yourself.  If the app and version you want to use is not listed, or rated less than  Gold, you're wasting your time intending to use it in Linux.

> The other thing that puts me off is that the one good thing about my current laptop setup is that I have Windows on C: and all my data and apps on D: 
Ubuntu is NOT Windows -- the filesystem isn't organized the same way.  Apps are installed to where the installer puts them.  Unless you download source and build apps by hand, you won't have a choice as to where they are installed.

You're in Linux now, you need to stop thinking like Windows.

> Can't the apps be made portable and saved to a USB device like on Windows? 
While you can install Ubuntu to a USB stick, that's not the same as making apps portable.

Again, you need to stop thinking like Windows.

So, to answer your original question -- if you want everything to be just like Windows, then you need to stay in Windows.  Linux is not Windows.  There is simply no way to make it just like Windows -- and MOST folks here would say that is a GOOD thing!

---

### Post by sl23 on 2012-05-06
Thanks for all your replies I didn't expect all that :)

I originally tried v10.04 which had problems with Wi-Fi so I gave up on that. I tried v11.10 I think it is and that seems so much better. Ubuntu seems so mush fresher and cleaner than windows somehow?

I don't expect Ubuntu to be like Windows it's just that reinstalling all apps and settings should be made easier and it seems it is in Ubuntu according to audiomick's reply. The /home folder is a good idea if it really is that simple.

Currently the laptop has a CORRUPT but working Vista on it. I made the recovery discs but they don't work. I already created a partition copy using Macrium before I started messing about. But this puts it back to a state that is still CORRUPT! Just in case you didn't get that the first time! :P :)

Hence why I tried Ubuntu. I spoke to the tech guy at work and he says it uses less system resources than Windows and is better to use, but I suppose that's more a personal choice. Thing is Windows is ok but I have an app that pretty much replaces every app that it comes with! Most are more efficient or simply do more.

I'll probably give the dual boot a try on this laptop first see if I get on with it and if it's good I'll Format the HDD and just have Ubuntu installed. I think it's fantastic what's been done with Ubuntu and definitely give it a go. Big thanks to all your advice, much appreciated :)

---

### Post by Curtis6767 on 2012-05-06
If you lower your expectations, then you'll probably be fine.

I installed 12.04 LTS on 4/25. This was the final release version/image.

For reasons I've still never figured out, missing dependencies and other incompatibilities, my system got borked and I had to do a fresh install this past Friday. Things are going well now, but two weeks is not a very long shelf life.

My advice for you would be to stay away from anything that can't be downloaded through the Software Center. That really won't limit you because there are several thousand apps available there. In some cases these will be older, time-tested apps but they will be, hopefully, stable, and should integrate seamlessly with your system. 

There are hundreds of users on these forums who have been linux heads for years and years. They don't think twice about telling people how to download this app or that app via repositories using ppa's and by other esoteric means, but the thing is they know how to fix things when things go wrong via these alternative methods. 

As a linux/Ubuntu noob, I am now approaching Ubuntu with kid gloves. I am not giving up at all as I am now using Ubuntu over Win7 about 95% of the time. I'm just being cautious and taking my time, logging everything I do and backing up constantly. But if I ever get in a situation like I was in this past week where the only solution is a fresh install, I probably will either go back to Win7 or maybe try to find a more stable Linux option.

GL

---

