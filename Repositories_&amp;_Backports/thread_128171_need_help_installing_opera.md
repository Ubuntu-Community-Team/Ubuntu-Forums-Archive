---
title: "need help installing opera"
date: 2006-02-10
forum: Repositories &amp; Backports
---

### Post by Dauphinfay on 2006-02-10
root@rombus:/home/sinjin/downloads# dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.deb
(Reading database ... 64338 files and directories currently installed.)
Preparing to replace opera 8.51-20051114.5 (using opera_8.51-20051114.6-shared-qt_en_etch_i386.deb) ...
Unpacking replacement opera ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on xlib6g (>= 3.3.6) | xlibs; however:
  Package xlib6g is not installed.
  Package xlibs is not installed.
 opera depends on libqt3-mt (>= 3.3.4) | libqt3c102-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera





....so uh... i have googled my tail off and i con't find where to get these packages. can anyone point me in the right direction please? TIA:confused:

---

### Post by byen on 2006-02-10
How about 
sudo dpkg -i packagename.deb
sudo apt-get -f install

The first installs the programs and informs abt missing packages
The second command installs the missing packages and completes the installation.
I see this is your first post. Welcome to Ubuntu and Goodluck!

---

### Post by Dauphinfay on 2006-02-10
Thank you very much, byen. :D  I have been using linux on and off for the last two years (more on in the last year tho) and I never realized that that combination would be so effective. I have just been lazy all this time and 'su'ing everything.

thank you for the welcome. i have always used distros that focused on kde. but when i found out that gnome can be made to look much like my beloved osx i jumped on it. too bad the live cd is so terribly slow on my pc at work.

---

### Post by byen on 2006-02-12
Ok.. after I suggested the above, I got two private messages similar to the following question.
> I followed the instruction you had on installing Opera. It seems to have worked or at least it shows it as being installed. Now I can't find any link in any of the menu's to open it. As you probably know I am new to Linux and Ubuntu. Where can I find the link to open Opera?
So here is what someone with such issues might want to do.... 
(but before that... did you logout/restart after installation?)
To just see if Opera has been installed without any errors. You can just open the Terminal and type: opera
See if Opera starts up. If it does...all you need to do is add this to the menu
(Now I have no idea why you have to do this manually as mine seemed to add itself automatically). Now to add opera to your Applications menu all you have to do is:
Applications icon>Right Click>Edit Menus>Internet> New Entry (on right menu)
Name:Opera
Comment: This part is upto you
Command: opera (it is case sensitive so please remember...all small letters)
Icon: /usr/share/opera/images/opera_48x48.png

Thats it... that should add opera to the menu list. 
(You can also just run opera by doing <Alt><F2> and type opera >run)

See if this works. If it doesnt...Please let me know in this thread... 
Hope it helps.Goodluck guys!
~byen

---

### Post by bobap1950 on 2006-02-12
Thanks, it works great.

Bob :)

---

### Post by byen on 2006-02-12
You are Welcome! Glad to know things worked out!!! :-)

---

### Post by missmoondog on 2006-02-12
or, you can use automatix and goofy little things like this won't happen next time.

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

