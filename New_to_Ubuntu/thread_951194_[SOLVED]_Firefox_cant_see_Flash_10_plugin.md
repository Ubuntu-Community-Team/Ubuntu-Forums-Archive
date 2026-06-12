---
title: "[SOLVED] Firefox cant see Flash 10 plugin"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by SILLAT on 2008-10-17
I've been installing Adobe Flash player 10 .deb file all night om Ubuntu Hardy 8.04 with no success because Firefox cant see the Flash plugin even tho the installer says the file is installed successful ! !
Anybody else having this same problem an can help me with a fix for this or a workaround, flash player 9 is hell on Hardy i really wanna upgrade to see if there is any improvements in flash 10.

---

### Post by eternalnewbee on 2008-10-17
> **SILLAT said:**
> I've been installing Adobe Flash player 10 .deb file all night om Ubuntu Hardy 8.04 with no success because Firefox cant see the Flash plugin even tho the installer says the file is installed successful ! !
Anybody else having this same problem an can help me with a fix for this or a workaround, flash player 9 is hell on Hardy i really wanna upgrade to see if there is any improvements in flash 10.

Try this:
sudo apt-get install libflashsupport

---

### Post by SILLAT on 2008-10-17
hey thnx for trying but the system says 
"libflashsupport is already the newest version"
i jus dont kno y it cant see the plugin an its installed already !

---

### Post by eternalnewbee on 2008-10-17
> **SILLAT said:**
> hey thnx for trying but the system says 
"libflashsupport is already the newest version"
i jus dont kno y it cant see the plugin an its installed already !

Sorry I can't be of more help to you, but I'm sure someone here will be able to help you out.
Patience is a virtue.
Good luck.

---

### Post by NilsE on 2008-10-17
Sounds like you have a conflict.  Remove libflashsupport, flashplugin-nonfree, and the .deb flash you installed.

Then install the .deb file from Adobe and you should be good to go.

---

### Post by kansasnoob on 2008-10-17
I've tried both the .deb and the apt install, both worked OK. You have to restart Firefox when you're done.

---

### Post by SILLAT on 2008-10-17
hey guys thnx for the help but i have a new twist with my flash problems.
i have firefox 2 and firefox 3 installed on my PC firefox 2 see's the Flash Plugin but firefox 3 cant see  the flash plugin.
How could that be? How can i get firefox 3 to see the plugin firefox 2 and 3 have different profiles . . help please !

---

### Post by lswb on 2008-10-17
Exit from firefox. Try to find out where the installer put the binary. In a terminal,

locate libflashplayer.so

Assuming you found more than one, check their dates and sizes 

ls -l $(locate libflashplayer.so)

The binary for the latest flash 10 is 9974800 bytes and should have a recent date.
The binary for flash 9 is 8115888 bytes.

cd to the directory where the flash 9 binary was found. On my system it is in 
/usr/lib/flashplugin-nonfree/libflashplayer.so

Rename the flash9 binary to something that does not end in .so or move it to a safe place. 


sudo mv libflashplayer.so libflashplayer.so.version9

Copy the flash10 binary to this directory (or put a symlink to it in the directory)

sudo cp /path/to/flash10/libflashplayer.so .

Note that this will very likely interfere with package managers like apt-get or synaptic being able to manage future flash installations.


I'll add that I've been using the latest version 10 for a few days now and it is the best so far. Menus are displaying properly and no firefox crashes (yet) Neither of the version 10 release candidates worked as well as for me as the version 10 beta or version 9.

---

### Post by b0b138 on 2008-10-17
uninstall firefox 2 and 3 through synaptic. make sure flashplugin-nonfree is also uninstalled. In your home folder theres a hidden folder called .mozilla  Delete it. Then install firefox 3 then the flash plugin from the adobe site.

---

### Post by SILLAT on 2008-10-18
hey LSWB ! your little tip did the  trick . . i moved the libflashplayer.so file from the flashplugin-nonfree directory then extracted the flash player 10 .debs and copy the libflashplayer.so file  from the flash 10 i extracted to the flashplugin directory and it did the trick. 
big thnx to u man !!

---

### Post by JeppeM on 2008-10-18
I know that this is marked as solved, but i stumbled across this post via. google, and so may others :)

My problem was basically the same as OP, but the solution didn't work for me. When i had done the above steps (basically, i deleted all libflashplayer.so from my system, and downloaded the newest in a tar.gz package from the adobe site, and then put it in ~/.mozilla/plugins/). when starting firefox from the command line, i got errors like this:

```
~$ firefox
LoadPlugin: failed to initialize shared library /home/jeppe/.mozilla/plugins/libflashplayer.so [libplds4.so: cannot open shared object file: No such file or directory]
~$ firefox
LoadPlugin: failed to initialize shared library /home/jeppe/.mozilla/plugins/libflashplayer.so [libplc4.so: cannot open shared object file: No such file or directory]
~$ firefox
LoadPlugin: failed to initialize shared library /home/jeppe/.mozilla/plugins/libflashplayer.so [libnspr4.so: cannot open shared object file: No such file or directory]
```
I also got some of libnss3.so, libssl3.so and one more i can't rememeber. To solve this, i simply copied the .so.0d or .so.1d file to .so from the /usr/lib/ dir. For example, with the libplds4.so error, you would do:

```
~$ sudo updatedb
~$ locate libplds4.so
/usr/lib/libplds4.so.0d
/usr/lib/firefox/libplds4.so
/usr/lib/thunderbird/libplds4.so
```

It's the libplds4.so.0d we want. When we get the right file name, we just need to copy it to the same place, just without the .0d ending (it might be .1d as well).

```
~$ sudo cp /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
```

I did that for 6-7 different shared objects, and now flash player 10 is working like it should :) I have no idea why this happens, or if my way of doing it is the correct one, but at least it works. I would be nice if the shared objects in /usr/lib/firefox/ were somehow used, so users wouldn't have to do this from the command line... Not sure if it's a real bug though..

Hope that this helps others, who might have the same problem as me. The flash player version is 10.0 r12, i don't know if thats the same one you tried to install SILLAT?

---

### Post by redseventyseven on 2008-10-18
JeppeM's solution worked for me - in fact it's been documented before.

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

These instructions were written with the second release candidate in mind, but the same instructions will work for the final release. They have for me, anyway!

The website quoted above suggests making symbolic links rather than copying as JeppeM suggests; I prefer making symlinks myself, but I imagine they both work fine. Incidentally there was no need (in my case at least) to do lswb's trick first. I simply installed the deb file in the usual way without any tinkering.

In all, you need to make six symlinks:

```

sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so

sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so

```

The first three were all you needed to get the first release candidate working, so you may only need the last three. Jeppe's suggestion of running firefox using the terminal and opening a site that's supposed to have flash on it, and reading the terminal output to find out what's missing is a good one to see what you might have missed.

---

### Post by philinux on 2008-10-18
This is all very weird. I installed the deb from adobe. Have no symlinks and one file in the system.
/usr/lib/adobe-flashplugin/libflashplayer.so

And it works just fine. I'm baffled by the contortions some are having to go through.

---

### Post by JeppeM on 2008-10-18
I totally agree... It had /usr/lib/adobe-flashplugin/ligflashplayer.so as well, but for some reson it just didnt work... I guess there's something speicial about some of the setups, even though i have no idea at all what it could be.

redseventyseven - At least i'm not alone, nice to know :D But anyway, symlinks or copying doesnt matter i think, but i'd have the agree that symlinking seems to be the better options.

---

### Post by Sidster2143 on 2008-10-18
if you ask me i don't like firefox at all try google chrome its very fast but you can't put toolbars:)

---

### Post by lswb on 2008-10-18
> **JeppeM said:**
> I totally agree... It had /usr/lib/adobe-flashplugin/ligflashplayer.so as well, but for some reson it just didnt work... I guess there's something speicial about some of the setups, even though i have no idea at all what it could be.

redseventyseven - At least i'm not alone, nice to know :D But anyway, symlinks or copying doesnt matter i think, but i'd have the agree that symlinking seems to be the better options.

I think it has to do with previous installs of tarballs from Adobe's site. I remember several months ago I successfully installed the ver 10 beta when it was available in the backports or proposed repositories. When Adobe put the ver 10 RC1 tarball on their site, I tried installing it but had to go back to the beta because firefox kept crashing with RC1. After that I've never been able to successfully install flash either from ubuntu's repositories or from Adobe's sites without some manual intervention. Although I must admit, with Adobe's latest .deb, I didn't even try. I just extracted the binary and copied it to a location where I knew it would work.

---

### Post by kansasnoob on 2008-10-18
> **lswb said:**
> I think it has to do with previous installs of tarballs from Adobe's site. I remember several months ago I successfully installed the ver 10 beta when it was available in the backports or proposed repositories. When Adobe put the ver 10 RC1 tarball on their site, I tried installing it but had to go back to the beta because firefox kept crashing with RC1. After that I've never been able to successfully install flash either from ubuntu's repositories or from Adobe's sites without some manual intervention. Although I must admit, with Adobe's latest .deb, I didn't even try. I just extracted the binary and copied it to a location where I knew it would work.

If someone has installed a previous tar.gz or even a .deb it's wise to:

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

If it's not necessary it won't break anything, it'll just tell you "not found" or some such.

---

### Post by crjackson on 2008-10-18
> **philinux said:**
> This is all very weird. I installed the deb from adobe. Have no symlinks and one file in the system.
/usr/lib/adobe-flashplugin/libflashplayer.so

And it works just fine. I'm baffled by the contortions some are having to go through.

I have 2 systems with fresh installs of Hardy 32. Installing the .deb file from adobe works perfectly on my desktop.

On my laptop however, firefox can't find the plugin. I've tried coping it to various folders (symlinks) and it just won't find the plugin.

Flock however finds it just fine and it works well there. The only way I can get flash to work on my laptop while using firefox is to revert to synaptic install of flashplugin-nonfree.

This really sucks. I hope that this thing gets updated in Hardy and I can get a working install on my lappy. None of the usual fixes are working for me.

I even removed every stitch of firefox and deleted all the only folders. REBOOTED and did a fresh install of firefox.  No dice.

Anyone want to throw a suggestion...?

---

### Post by lswb on 2008-10-18
crjackson,  try this method. Start firefox and open "about:plugins". Note the filenames of the plugins you find there. In a terminal, use the command "locate someplugin.so" and see where they are. On my system I have found that 
/usr/lib/xulrunner-addons/plugins/
seems to be the main location for symlinks to firefox plugins and a few actual files as well. Some of these links point to other links and it can get somewhat confusing. If you haven't already tried the /usr/lib/xulrunner-addons/plugins/ directory, put a symlink to the libflashplayer.so there and see if that works. 

I think that the reasoning behind designing this complicated chain of symlinks was just a little _too_ clever.

---

### Post by crjackson on 2008-10-18
> **lswb said:**
> crjackson,  try this method. Start firefox and open "about:plugins". Note the filenames of the plugins you find there. In a terminal, use the command "locate someplugin.so" and see where they are. On my system I have found that 
/usr/lib/xulrunner-addons/plugins/
seems to be the main location for symlinks to firefox plugins and a few actual files as well. Some of these links point to other links and it can get somewhat confusing. If you haven't already tried the /usr/lib/xulrunner-addons/plugins/ directory, put a symlink to the libflashplayer.so there and see if that works. 

I think that the reasoning behind designing this complicated chain of symlinks was just a little _too_ clever.

Okay, I'll try that in a bit. I'm busy writing an English essay right this minute.

---

### Post by frito_x on 2008-10-21
[FONT="Times New Roman"][SIZE="4"][COLOR="SeaGreen"]Just registered to confirm that symlinking those libraries fixes flash player 10 for me (i also had trouble installing 9 and remember having to do it manually) maybe that's why the .deb package didn't take... i also had most of the plugins in the /usr/lib/xulrunner-addons/plugins folder so i did put another symlink there to go to the libflashplayer.so that the package installed...

thanks for the help... i would've never guessed the thing with the libs...

p.s.: they (adobe and mozilla) are really making us work hard for it, aren't they?... wonder why?[/COLOR][/SIZE][/FONT]

---

### Post by crjackson on 2008-10-23
> **redseventyseven said:**
> JeppeM's solution worked for me - in fact it's been documented before.

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

These instructions were written with the second release candidate in mind, but the same instructions will work for the final release. They have for me, anyway!

The website quoted above suggests making symbolic links rather than copying as JeppeM suggests; I prefer making symlinks myself, but I imagine they both work fine. Incidentally there was no need (in my case at least) to do lswb's trick first. I simply installed the deb file in the usual way without any tinkering.

In all, you need to make six symlinks:

```

sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so

sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so

```

The first three were all you needed to get the first release candidate working, so you may only need the last three. Jeppe's suggestion of running firefox using the terminal and opening a site that's supposed to have flash on it, and reading the terminal output to find out what's missing is a good one to see what you might have missed.

My systems needed the symlinks with the *4.so - strange, I didn't have to do this on my main system and they are all fresh installs with updates of 8.04.1

---

