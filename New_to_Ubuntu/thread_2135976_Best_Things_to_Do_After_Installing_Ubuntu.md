---
title: "Best Things to Do After Installing Ubuntu"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by azzzrael on 2013-04-16
Hello everyone! I just installed Ubuntu 12.10 on my laptop and was wondering if I could get some applications/tips on what I should do after. This is my first time running Ubuntu.

So far I've: installed flash, codecs, updated drivers, updated software, etc and all the standard stuff. But now I'm kinda clueless on where to go next. I'm looking for some direction on maybe customizing the look, making ubuntu run a bit faster, I guess the cool little "tweaks". It would be awesome if you guys could push me in the right direction!

PS. My laptop always boots with a boot menu and it's a tad bit annoying when I have to hit Ubuntu everytime I boot up. Is there anyway to have it automatically boot into Ubuntu?

---

### Post by speartip on 2013-04-16
These threads might help.
[http://www.omgubuntu.co.uk/2012/10/10-things-to-do-after-installing-ubuntu-12-10](http://www.omgubuntu.co.uk/2012/10/10-things-to-do-after-installing-ubuntu-12-10)
[http://www.youtube.com/watch?v=GVHLM0IxUQM](http://www.youtube.com/watch?v=GVHLM0IxUQM)
[http://www.techdrivein.com/2012/10/20-things-to-do-after-installing-ubuntu1210-quantal-quetzal.html](http://www.techdrivein.com/2012/10/20-things-to-do-after-installing-ubuntu1210-quantal-quetzal.html)
[http://www.webupd8.org/2012/10/things-you-do-after-installing-ubuntu.html](http://www.webupd8.org/2012/10/things-you-do-after-installing-ubuntu.html)

As for your boot Menu it should by default boot into Ubuntu after 10 seconds.
If you want to change that, then open a terminal & type:
```
sudo gedit /etc/default/grub
```
Look for the line that starts "GRUB_TIMEOUT=" & change the seconds to whatever suits.
Save the file, then run:
```
sudo update-grub
```

Hope this helps.

---

### Post by ibjsb4 on 2013-04-16
Heres something that can keep you busy for years :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=customize+unity&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=customize+unity&sa=Search&cof=FORID:9)

And welcome to the forums :)

---

### Post by pfeiffep on 2013-04-16
I followed these [steps]("https://sites.google.com/site/easylinuxtipsproject/speed") and had excellent success

---

### Post by cortman on 2013-04-16
If you're running standard Ubuntu and not a derivative (lubuntu, kubuntu, xubuntu, etc) you may want to turn off Amazon search results in the dash. Search in the dash for the Privacy application and turn off "Include Online Results".
And just enjoy using Ubuntu! :)

---

### Post by midfingr on 2013-04-17
You could try these two programs, but use with caution. Both can be installed via 'Software Center'.

**Preload**:
> preload is an adaptive readahead daemon. It monitors applications that users run, and by analyzing this data, predicts what applications users might run, and fetches those binaries and their dependencies into memory for faster startup times. Note: this does not decrease system start up time


**Prelink**: Keep an eye on free disk space (via system monitor for example).
Open a terminal and type:
```
sudo prelink -amR
```
Prelink man page: [http://linux.die.net/man/8/prelink](http://linux.die.net/man/8/prelink)

---

### Post by DuckHook on 2013-04-17
Do not attempt to load a lot of utilities, apps or tweaks until you are more familiar with Ubuntu and Linux in general. I know how tempting it is: you open the Software Center and there are over 50,000 packages, all just the click of a button away, but new users get themselves into trouble all the time because they install things willy-nilly and don't know what changes are being made to their system. Instead, I recommend that you read up on these resources:

Linux is not Windows intro:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

General Ubuntu Intro:

[https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://owlcroft.com/ubuntu/](http://owlcroft.com/ubuntu/)
[https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

Command line learning:

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by AnaheimSam on 2013-04-17
Ubuntu Tweak comes with a janitor app that helps to clean your computer. (Think Disk Cleanup in Windows.)
It also comes with an app that helps change the cosmetic appearance of your GUI.

As for your second question, after about 10 seconds in GRUB, Ubuntu should load on its own. I'm pretty sure that there is a solution to have Ubuntu load automatically on start up, but if you have more than one OS, it's just not worth the trouble, and it's best you leave it alone.

---

### Post by DuckHook on 2013-04-17
> **AnaheimSam said:**
> Ubuntu Tweak comes with a janitor app that helps to clean your computer.

The janitor app has hosed many an install, especially for new users unfamiliar with the way Linux works. Since Ubuntu does not accumulate anywhere near the amount of crud that Windows does, I strongly recommend against Janitor. It's much safer to let the caches bloat a little than deleting that old kernel that will end up saving your bacon after the next bad update.

---

### Post by BBQdave on 2013-04-17
> **DuckHook said:**
> Do not attempt to load a lot of utilities, apps or tweaks until you are more familiar with Ubuntu and Linux in general.

+1

The *best thing to do after installing Ubuntu* is use it :) 

Check out the default applications, play around for a week or two - then evaluate if there is functions missing in what you need out of the distro. Might be time then to check out other applications to add - to meet the missing functions, if any :)

---

### Post by send2 on 2013-04-17
> **DuckHook said:**
> The janitor app has hosed many an install, especially for new users unfamiliar with the way Linux works. Since Ubuntu does not accumulate anywhere near the amount of crud that Windows does, I strongly recommend against Janitor. It's much safer to let the caches bloat a little than deleting that old kernel that will end up saving your bacon after the next bad update.

Wow, that last statement is so true! When I first installed Ubuntu and needed to intall an nvidia graphics driver, my graphics went south, I had to go into Ubuntu and used an old version of the kernel to get to my desktop and install the correct video driver :P

---

### Post by AnaheimSam on 2013-04-18
DuckHook:
I beg to differ.
One time, I ran janitor, and it found that I had just over 1GB lying around in the apt cache. This was just after a week after a clean install. Granted, I had been installing things left and right to make my experience a bit more enjoyable, but still, 1GB of stuff just lying around? No bueno.

Besides which, there is always an option to not throw out the old kernels. In fact it's as simple as clicking a single button.

Which reminds me...
BACKUP EVERYTHING!
[URL="http://ubuntuforums.org/member.php?u=1811240"][COLOR=#000000]
azzzrael[/COLOR][/URL]:
For you, I would also recommend setting up an Ubuntu One account. The client is already installed on your system. You get 5GB to start for free. You can put all of your personal files (music, vids, pics, texts, etc.) on it. In the event of a failure of your system, or even your machine, your files will be safe on Ubuntu One. Saved my hind end on more than one occasion.

---

### Post by fantab on 2013-04-18
> **azzzrael said:**
> PS. My laptop always boots with a boot menu and it's a tad bit annoying when I have to hit Ubuntu everytime I boot up. Is there anyway to have it automatically boot into Ubuntu?

Are you Dual Booting or is it just Ubuntu? The answer will help us tell you how to automatically boot into Ubuntu.

**If Dual Booting** with Windows or any other OS then open TERMINAL and run the following Commands:

```
gksudo gedit /etc/default/grub
```

This will open the grub file in gedit. Look for Line: **GRUB_TIMEOUT=10** ('10' means time in seconds; Grub will take 10 seconds before booting Ubuntu, the default OS) CHANGE the value to '3' or what ever suits you, just **DONT make it '0'**. and save the file. Then run from Terminal:

```
sudo update-grub
```

**If Only Ubuntu** on your computer then: run the First command above andsearch for line: **#GRUB_HIDDEN_TIMEOUT=0** and delete '**#**' in the line, save the file and update-grub as shown above.

For more help regarding this [READ HERE]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen").

---

### Post by DuckHook on 2013-04-18
> **AnaheimSam said:**
> ...I had just over 1GB lying around in the apt cache.

The way to look after this is with *apt-get autoremove* followed by *apt-get autoclean*. If one is absolutely intent on recovering every last smidgeon of HDD space, then *apt-get clean*. The difference is not so much functional as psychological: resorting to the command line generally forces a pause and a chance for sober second thought. Using Janitor for critical tasks is too easy and therefore too dangerous. Generally, all one-click procedures for critical system tasks give me the willies. Too many disasters on these forums arise from such conduct. Your 1GB is highly unusual and far from the norm, but even were it the norm, it is not a high price to pay for safety in the age of 1, 2 and 3 TB drives.

> Besides which, there is always an option to not throw out the old kernels. In fact it's as simple as clicking a single button.

Again, the problem that we helpers often face on these forums is not function; rather, it is lack of knowledge. New users do not understand the utility of old kernels. Therefore, they will not keep them when faced with a query from Janitor. After all, the mindset when using it is to "clean up" detritus. The thinking goes: old kernels, being old = obsolete = useless = detritus. There is not enough context in Janitor to allow for using it knowledgeably and this is deadly when combined with the natural lack of knowledge of the new user. If you have the knowledge to find it useful, then I am happy for you, but I cannot recommend it to anyone else because I've seen the fallout on these forums from its victims. Its advantages do not come close to outweighing its disadvantages. It is using a sledgehammer for the work of a taphammer.

> Which reminds me...
BACKUP EVERYTHING!

Amen!

---

### Post by The Spectre on 2013-04-18
> **azzzrael said:**
> Hello everyone! I just installed Ubuntu 12.10 on my laptop and was wondering if I could get some applications/tips on what I should do after. This is my first time running Ubuntu.

So far I've: installed flash, codecs, updated drivers, updated software, etc and all the standard stuff. But now I'm kinda clueless on where to go next. I'm looking for some direction on maybe customizing the look, making ubuntu run a bit faster, I guess the cool little "tweaks". It would be awesome if you guys could push me in the right direction!

PS. My laptop always boots with a boot menu and it's a tad bit annoying when I have to hit Ubuntu everytime I boot up. Is there anyway to have it automatically boot into Ubuntu?

Welcome to the Forums and the World of Ubuntu.):P

Something that you might want to do is install VirtualBox and then install Ubuntu 12.10 into VirtualBox plus install all available updates and then create a Snapshot of it.

Then you can do all of the tweaking, experimenting, testing and installing of different software into the VirtualBox Ubuntu to get used to it without fear of messing up you main computer.

And if things do get messed up in the VirtualBox Ubuntu all you have to do is restore it to the saved Snapshot to start over.

This is what I did when I first started with Ubuntu and it helped me out allot with getting comfortable with Ubuntu and running commands in Terminal.

And I still use VirtulBox for testing things I am not sure of.

---

### Post by DuckHook on 2013-04-18
> **The Spectre said:**
> ...install VirtualBox and then install Ubuntu 12.10 into VirtualBox plus install all available updates and then create a Snapshot of it.

Then you can do all of the tweaking, experimenting, testing and installing of different software into the VirtualBox Ubuntu to get used to it without fear of messing up you main computer.

And if things do get messed up in the VirtualBox Ubuntu all you have to do is restore it to the saved Snapshot to start over.

+1

Excellent plan. Vbox is not that hard to install and is the ideal place to experiment and break your system. Roll back to snapshot... voila: instant time warp. Also, you can install as many different OSes as your HDD has room for. Only drawback: must have reasonably fast HW, else runs like a pig.

---

