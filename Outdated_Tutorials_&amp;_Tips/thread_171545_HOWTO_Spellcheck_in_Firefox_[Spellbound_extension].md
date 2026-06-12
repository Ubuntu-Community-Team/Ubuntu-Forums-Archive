---
title: "HOWTO: Spellcheck in Firefox [Spellbound extension]"
date: 2006-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Fass on 2006-05-06
I was having difficulties making the [Spellbound](http://spellbound.sourceforge.net/) extension work for my regular user, but managed to solve it by making the extension compatible with newer versions of Firefox and fixing some permissions. Hopefully this little guide will be of use to other people.

First, I had to install the extensions as root, so:

```
sudo -H firefox
```

Go to [Nightly Tester Tools](http://users.blueprintit.co.uk/~dave/web/firefox/buildid/nightly.html) and install the latest version.

Shutdown and restart Firefox (still as root).

Then go to [http://spellbound.sourceforge.net](http://spellbound.sourceforge.net) and follow the instructions to install the extension (and the dictionaries you want), but when you choose to install, tick the *"Install using Nightly Tester Tools to override compatibility."* This makes Spellbound work with the latest Firefox versions.

Restart firefox as root again to finish the installation of the extension. Shut it down.

Start firefox as a normal user and install the extension (but not the dictionaries), again using Nightly Tester Tools to override compatibility and then close firefox.

As root, change the properties of the files in /usr/lib/firefox/components/myspell so that the dictionaries can be read and written to by all:

```
sudo chmod go+rw /usr/lib/firefox/components/myspell/*.*
```

Start firefox as your normal user. Write something misspelt in the text entry field of any website (google will do), rightclick and choose "Check spelling." It should work now! :)

If you don't have a /usr/lib/firefox/components/myspell/ directory, I have seen that it sometimes is located at /usr/lib/mozilla-firefox/components/myspell instead. You can use locate to find it like this:

```

sudo locate -u
locate /components/myspell/
```

Then just substitute your path in the examples above.

---

### Post by barbarian on 2006-05-07
Yes, it worked perfectly. Thanx:cool: 
Unfortunately there is no Estonian dictionary though.

---

### Post by Fass on 2006-05-07
[QUOTE=barbarian]Yes, it worked perfectly. Thanx:cool: 
Unfortunately there is no Estonian dictionary though.[/QUOTE]

It uses myspell dics, so you can simply add one of those.

```
sudo apt-get install myspell-et
```

Then create the following symlinks:

```
sudo ln -s /usr/share/myspell/dicts/et-EE.aff /usr/lib/firefox/components/myspell/et-EE.aff
sudo ln -s /usr/share/myspell/dicts/et-EE.dic /usr/lib/firefox/components/myspell/et-EE.dic
sudo ln -s /usr/share/myspell/dicts/hyph_et_EE.dic /usr/lib/firefox/components/myspell/hyph_et_EE.dic
```

Seems to work. Lets me pick Estonian in the spellchecker and spellchecks Estonian phrases I googled.

---

### Post by barbarian on 2006-05-08
> sudo apt-get install myspell-et

Unfortunately *myspell-et* in Dapper only, so I will wait till June, but thanks, anyway I will use Your advise.

---

### Post by PvSinNL on 2006-05-09
Just on a side note: There is a development version of Spellbound available that's supposed to work with FF 1.5. See [this thread]("http://forums.mozillazine.org/viewtopic.php?t=351130") on Mozillazine for further info. (Disclaimer: I haven't tried it on Ubuntu yet, but it worked for me in XP.)

---

### Post by Fass on 2006-05-09
[QUOTE=PvSinNL]Just on a side note: There is a development version of Spellbound available that's supposed to work with FF 1.5. See [this thread]("http://forums.mozillazine.org/viewtopic.php?t=351130") on Mozillazine for further info. (Disclaimer: I haven't tried it on Ubuntu yet, but it worked for me in XP.)[/QUOTE]

Good tip. Just installed it and its "spell as you type" feature works pretty well. Alas, the dics still have to be installed with root and permissions changed.

---

### Post by dcstar on 2006-05-12
[QUOTE=PvSinNL]Just on a side note: There is a development version of Spellbound available that's supposed to work with FF 1.5. See [this thread]("http://forums.mozillazine.org/viewtopic.php?t=351130") on Mozillazine for further info. (Disclaimer: I haven't tried it on Ubuntu yet, but it worked for me in XP.)[/QUOTE]
I've been using it for months, work fine with FF 1.5.x (actually Swiftfox 1.5.0.3) on Breezy.

---

### Post by dmizer on 2006-05-13
spellbound has probably been the one of the longest lived frustrations in linux for me.  that and printing.

i have followed every advice in every link i can find to install the dictionary but nothing works.  all i get is a pop up message upon install that says "dictionary (v 0.3) has been successfully installed." i click on "OK" and the listing in my extensions goes away.  when i restart firefox, spellbound does not work and there is no dictonary listed in my extensions.

i have tried installing the dictionary with the tester tools, i have tried saving it and dragging it over to the extensions window ... everything i do gets the same results.

i also get the same results if i install the dictionary as root or as user.

edit to add: i am using firefox 1.5 as installed per this wiki: [https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29%7C%281.5%29#head-989f6d047637b584e6af702799965c7570a81f6b](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29%7C%281.5%29#head-989f6d047637b584e6af702799965c7570a81f6b)

also, dictonary appears in /opt/firefox/components/myspell:
```
dmizer:/opt/firefox/components/myspell$ ls
en-US.aff  en-US.dic  README-en-US.txt
```

---

### Post by Fass on 2006-05-13
Dmizer, is it the entire extension that doesn't work, or just the dictionaries? Because if it's just the dics, could you try what I wrote about in post 3? You can find the en-us [myspell dics for ubuntu here.](http://packages.ubuntulinux.org/cgi-bin/search_packages.pl?keywords=myspell-en-us&searchon=names&subword=1&version=all&release=all)

---

### Post by dmizer on 2006-05-13
spellbound did indeed install fine.  it's in the list of extensions.  but it's not finding the dictionary.

i did indeed try what you suggested in post 3, but as i mentioned before, the dictionary already appears in my .../components/myspell folder.

edit to add: the myspell dictionary for english is already installed on my machine.  but just for good measure, i removed the contents of /components/myspell and created symbolic links as you suggested in post 3.  still no joy

---

### Post by dcstar on 2006-05-13
[QUOTE=dmizer]spellbound did indeed install fine.  it's in the list of extensions.  but it's not finding the dictionary.

i did indeed try what you suggested in post 3, but as i mentioned before, the dictionary already appears in my .../components/myspell folder.

edit to add: the myspell dictionary for english is already installed on my machine.  but just for good measure, i removed the contents of /components/myspell and created symbolic links as you suggested in post 3.  still no joy[/QUOTE]
To get around the issues I also had with Spellbound/Dictionaries, I log on as root (not "sudo") to install both in my root Firefox, then select the dictionary in Spellbound (and test).

Then I log out of root, log in as my normal user and repeat the process, all seems to work ok when I do this.

---

### Post by dmizer on 2006-05-14
actually i tried that earlier.  i did it again, but there are problems then too.  the spellbound function appears when i right click now, but it lables everything as misspelled and no suggested corrections.

when i checked the options for spellbound, the english dictionary was selected.

---

### Post by dmizer on 2006-05-23
i really need to get this fixed, my spelling is absolutely terrible. lol

why exactly is this plugin requiring so many hoops? what does it need as far as permissions such that it will only (sometimes) install via root?

---

### Post by dmizer on 2006-06-20
i believe my issue was fairly unique.  here's the deal:

i have been using firefox for ages now, and as such, i have it customized exactly to my taste.  so when i installed 1.5 in breezy, i just carried over the firefox folder from windows, renamed it .mozilla.  this worked for most of my extensions no problem. but spellbound did not install (a small asside note, i needed to remove and reinstall forecast fox at that time too).

anyway ... carying this folder over from windows must have had something to do with my hangup because once i decided to try this technique in a fresh install on the same machine, it worked fine.

---

### Post by stanz on 2006-06-20
Hi All,
Thank You Fass, I was just searching Ffox for this - and then found your help.
Did you know, Ffox doesn't have this in it's extentions & search? Makes me wonder!
I'm kinda still a newbie here...but, let me throw this out.
When I installed Ubuntu {each 10 or 20 time}, I got Ffox from the Ffox homepage & threw it in my */opt* folder,-
using the 'HowTo' from here, and I also adjusted permissions for ease of use, as I'm the only user- here.
With that, I have no: */usr/lib/firefox/components/* , cause I ditched the old version, that came with Ubuntu.
~*This is not a problem- just some different info, for your HowTo.*~
My first question about starting your instructs is with the code.
If you would describe what the " *-H firefox *", is for, in more detail, it would do more of teaching me [and others?]
something, it would help me *understand* - what i'm doing & what 'IT'S' doing.
= with my Ff in */opt* , I didn't do that step =
Loading the nightly build extention- again, was a help, and your  link to  SpellBounds page ~ a  Big  Thanks !
Thats pretty much all I needed, already having Ffox in my */opt* folder !
For those who can load it this way ~ It may relieve some pain... tho, I would
keep your instructs- if ever on a more multi-user system.
Thanks for helping me correct my sh*tty grammer ~ easilier!!!!   =D>

---

### Post by Fass on 2006-06-23
[QUOTE=stanz]If you would describe what the " *-H firefox *", is for, in more detail, it would do more of teaching me [and others?][/QUOTE]

The "-H" switch makes sudo set the HOME environment variable to the home directory of the target user, in our case root, meaning that when you run "sudo -H firefox" it will understand to put all extensions and config files in /root and not in your user's home directory.

A good place to find out what different switches do (or to find out what switches you can use for a particular programme/command) are the man pages.

---

### Post by vtel57 on 2006-08-01
Here's a simple way that I found to install SpellBound (I hate Aspell!) on my Ubuntu 6.06 Firefox 1.5 browser (Thanks to [Ubuntu Linux Blog by Ralph](http://ralph.n3rds.net/index.php?/archives/2005/12.html) for this info):

First off, go [HERE](http://exchangecode.com/spellbound/spellbound-dev.xpi)(Warning! This is a direct download link) and install the SpellBound development version into your Firefox browser using the regular Extension Manager method. 

Next, go to [Dictionaries for Mozilla](http://dictionaries.mozdev.org/) at the Mozdev site and Right click --> Save Link As on your dictionary of choice to download it to your favorite download location on your system... desktop, my_downloads directory, etc.

Now, close your FF browser and open the Terminal. Use the following command to launch FF again:

```
$ gksudo firefox
```

An un-customized version (root) of Firefox will open. That's fine. That's what it's supposed to do. In the browser, go to File --> Open File... --> and point it to your dictionary package that you just downloaded in the previous step here. The FF Extension Manager will pop up and ask you if you want to install the dictionary. Click "Install". Once this is finished, shut down the browser and exit the Terminal.

Restart FF using your usual launcher (shortcut). Open a text posting area here at these forums or anywhere and type this word... "Testign" (purposely mis-spelled), then Right click --> Check Spelling. When the SpellBound window opens, the word testign will be in the window, but no suggestions will be visible. This is because you have to choose the dictionary the extension should use. 

At the bottom left of the SpellBound window you'll see "Language" --> Download More. Click to activate the pulldown menu and you should see your dictionary that you installed just a few moments ago. Choose it. Your SpellBound extension will now function normally. You can set your preferences for SpellBound in the Extension Manager: Tools --> Extensions.

Also note: SpellBound development build will work fine in ThunderBird too. All you have to do to get it to work with TB is download the development package and the dictionary of choice and then manually install them using TB's Extension Manager.

This method was pretty simple (I'm a Linux newbie) to me. It worked like a charm on my system.

Hope this was helpful to you.

Regards,

~Eric

---

