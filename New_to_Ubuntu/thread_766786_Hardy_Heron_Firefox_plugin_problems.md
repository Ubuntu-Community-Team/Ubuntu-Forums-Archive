---
title: "Hardy Heron Firefox plugin problems"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by pzs on 2008-04-25
Here are a few pages with various embedded content that no longer work on Hardy Heron.

BBC weekly quiz (flash?): (looks OK at the start, but the interface doesn't work)

[http://news.bbc.co.uk/1/hi/magazine/7365576.stm](http://news.bbc.co.uk/1/hi/magazine/7365576.stm)

BBC iPlayer: (seem to start but then doesn't play)

[http://news.bbc.co.uk/1/hi/magazine/7365120.stm](http://news.bbc.co.uk/1/hi/magazine/7365120.stm)

Random video: (asks for age but I can't select it - I'm not sure if this one worked on Gutsy)

[http://www.1up.com/do/newsStory?cId=3167560](http://www.1up.com/do/newsStory?cId=3167560)

Finally, how come things like youtube embeds don't have a preview anymore - just a giant play arrow?

Impressed with the upgrade otherwise - very smooth.

Peter

---

### Post by joshsmith on 2008-04-25
you made a simple mistake. when you tried to install flash you installed swf-dec flash instead of adobe flash (installer) inside firefox

go into synaptic, remove swf-dec firefox plugin,
then go onto youtube, firefox will prompt you to install flash
you should select adobe flash instead.
(note if you have sound problems you may also need to install the package libflashsupport)

---

### Post by Kilz on 2008-04-25
Another option to get the Macromedia flash plugin is to install flashplugin-nonfree in synaptic.

---

### Post by pzs on 2008-04-25
That worked, thanks. In fact, I already had Adobe Flash installed, but the other version had taken over. As soon as I uninstalled it, all that stuff worked fine.

Peter

---

### Post by alexlittle on 2008-05-05
I was having the same problems with flash too, so thanks for the pointer to remove swf-dec - now all working fine! I'd got the swf-dec, flashplugin-nonfree and the mozilla-plugin-gnash installed, so needed to remove all except the flashplugin-nonfree.
Alex

---

### Post by twigusa on 2008-05-07
Just to clarify that this has to be done in synaptic as it won't show as installed under applications -> add / remove. This has been bugging since I installed. Thanks for the help.

---

### Post by ESFH on 2008-05-29
that didnt work for me
i looked in synaptic and swf-dec wasnt installed
i only have the flashplugin-nonfree installed
and yet BBC iplayer doesnt work
however youtube does seem to work

help?!

---

### Post by Bubba64 on 2008-05-29
> **ESFH said:**
> that didnt work for me
i looked in synaptic and swf-dec wasnt installed
i only have the flashplugin-nonfree installed
and yet BBC iplayer doesnt work
however youtube does seem to work

help?!

Install Ubuntu restricted extras in add remove and if you install all the gstreamer stuff you get quicktime and other stuff, then add vlc for the library and ffmpeg that should cover everything, all this is in add remove.

---

### Post by ESFH on 2008-05-29
> **Bubba64 said:**
> Install Ubuntu restricted extras in add remove and if you install all the gstreamer stuff you get quicktime and other stuff, then add vlc for the library and ffmpeg that should cover everything, all this is in add remove.

thanks for the help, i appreciate it
i did all that
iPlayer still doesnt work
why me :(

---

### Post by Bubba64 on 2008-05-29
> **ESFH said:**
> thanks for the help, i appreciate it
i did all that
iPlayer still doesnt work
why me :(

What plugins  in your browser are showing I just open add ons in FF and there is a plugin tab. I don't know the file that has this other than looking this way if you know how to show the plugins go ahead and I look at mine every thing that doesn't work for you listed in the thread works for me. Have you put medibuntu in the 3rd party in software sources and the key.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
You might have this already but here is a link to add the repository to the apt list. Also when I upgraded to Hardy the 3rd party repositories that are shutdown during the upgrade still said gutsy in software sources you can edit Gutsy to Hardy if this is the case.

---

### Post by ESFH on 2008-05-29
i couldnt quite follow what u meant exactly but i did follow the link and followed the instructions to add the Medibuntu repository to your system's list of APT repositories. 

this is what i copy & pasted into the terminal:
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install libdvdcss2

but, still no joy
i think i am doing everything correctly, but then why does it not work for me, when it works for everyone else -__-" thats the thing thats really getting to me

thanks for trying to help anyway

---

### Post by Kilz on 2008-05-29
> **ESFH said:**
> that didnt work for me
i looked in synaptic and swf-dec wasnt installed
i only have the flashplugin-nonfree installed
and yet BBC iplayer doesnt work
however youtube does seem to work

help?!

If youtube works, flash is installed. Why the iplayer doesnt work is hard to tell. Sadly I cant even test it being in the usa the bbc blocks me.

---

### Post by joshsmith on 2008-05-29
type about:plugins in the firefox address bar

there is a section called
Shockwave Flash
copy everything in that section and post it here (this will determine what flash plugin you have installed. if it is swfdec, look harder in synaptic)

copy everything else you find related to flash

on a second, and more general note, what do you mean by "doesnt work". always give as much information as possible. saying doent work tells us nothing.

---

### Post by kwacka on 2008-05-29
As FF3 is still beta it has a separate setup to FF2 (/usr/lib/firefox vs /usr/lib/firefox-3XXXXX).

I find that all plugins work with FF2, but need to set up soft links to plugin locations for FF3.

---

### Post by Bubba64 on 2008-05-29
In case any body has add ons (Mozilla Firefox) From FF2 that are not woring in FF3 Nightly tester tools will force them to work in FF 3.
[https://addons.mozilla.org/en-US/firefox/search?q=nightly%20tester%20tools](https://addons.mozilla.org/en-US/firefox/search?q=nightly%20tester%20tools)
Once installed the add ons window has a button on bottom right to enable this add on.
Also if you get everything working in FF 3 that comes with Hardy and you just can't wait for the latest version.
[http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html](http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html)

---

### Post by ESFH on 2008-05-29
> **joshsmith said:**
> type about:plugins in the firefox address bar

there is a section called
Shockwave Flash
copy everything in that section and post it here (this will determine what flash plugin you have installed. if it is swfdec, look harder in synaptic)

copy everything else you find related to flash

on a second, and more general note, what do you mean by "doesnt work". always give as much information as possible. saying doent work tells us nothing.

Copy and pasted from about:plugins:

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
-----------

screenshots of synaptic:

[http://img135.imageshack.us/my.php?image=screenshotmz8.png](http://img135.imageshack.us/my.php?image=screenshotmz8.png)

as u can see i searched for "swfdec" and none are installed, also a search for just "swf" shows none are installed either.
when searching for "flash" it shows 2 are installed:

flashplugin-nonfree
[http://img75.imageshack.us/my.php?image=screenshot2al4.png](http://img75.imageshack.us/my.php?image=screenshot2al4.png)

ubuntu-restricted-extras
[http://img75.imageshack.us/my.php?image=screenshot3nl9.png](http://img75.imageshack.us/my.php?image=screenshot3nl9.png)
----------

This is what iPlayer looks like:
[http://img338.imageshack.us/my.php?image=screenshot1nb2.png](http://img338.imageshack.us/my.php?image=screenshot1nb2.png)

i hope this answers everything in ur post, as accurately as possible

---

### Post by joshsmith on 2008-05-29
ok, i'm confused. cant think of a good explanation. but i'll make some guesses:

maybe you are out of hard drive space?
i'm guessing you are in the uk...

a good tactic would be to make a new firefox profile and try it there, ie close ff, move the folder .mozilla in your home directory to .mozilla1, start firefox

if not, you could try
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
which tels you how to isntall flash player 10

(OR, bbc just screwed something up)

---

### Post by Bubba64 on 2008-05-29
Here is a link that has helped many.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by Kilz on 2008-05-29
> **ESFH said:**
> Copy and pasted from about:plugins:

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
-----------

screenshots of synaptic:

[http://img135.imageshack.us/my.php?image=screenshotmz8.png](http://img135.imageshack.us/my.php?image=screenshotmz8.png)

as u can see i searched for "swfdec" and none are installed, also a search for just "swf" shows none are installed either.
when searching for "flash" it shows 2 are installed:

flashplugin-nonfree
[http://img75.imageshack.us/my.php?image=screenshot2al4.png](http://img75.imageshack.us/my.php?image=screenshot2al4.png)

ubuntu-restricted-extras
[http://img75.imageshack.us/my.php?image=screenshot3nl9.png](http://img75.imageshack.us/my.php?image=screenshot3nl9.png)
----------

This is what iPlayer looks like:
[http://img338.imageshack.us/my.php?image=screenshot1nb2.png](http://img338.imageshack.us/my.php?image=screenshot1nb2.png)

i hope this answers everything in ur post, as accurately as possible

[SIZE="6"]You Have Flash Installed.[/SIZE]

---

### Post by SFAOK on 2008-06-07
I was having the same problem but managed to solve it with: go to the Tools menu, Add-Ons, then pick plugins. I disabled the GCJ plugin, restarted FF and iplayer started working (not sure why - guess GCJ is running something in a way iplayer doesn't expect?).

There's a lot of advice around, I got lucky that I did something that fixed FF for me, however, I've only had Hardy installed for a few days so I reserve the right to find other problems in the future that my fix has obviously not solved ;)

---

