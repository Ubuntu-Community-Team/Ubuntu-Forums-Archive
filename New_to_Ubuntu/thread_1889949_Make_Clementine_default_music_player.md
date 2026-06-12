---
title: "Make Clementine default music player"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by shashanksingh on 2011-12-02
Hi (Ubuntu 11.10, unity)

I have vlc as my default mp3 player, and on right click I get the option of open with clementine and open with other applications.

But when I click on other applications, it gives me "Recommended Applications" and "Other Applications"(on show other applications).

Since I couldnt find clementine on both the lists, I thought maybe there was an option to specify a command in one of the previous versions I used.
Why isnt it here?

And where do I find the settings for deciding the default applications for certain files?

---

### Post by Lisiano on 2011-12-02
To make a application default for a certain filetype, just right-click a file -> Properties -> Open With -> Pick a application -> Make default
This will make the selected application default for whatever extension you picked, for example if you set html files to be opened with Gedit, htm files will still open with Firefox. Vice-versa.

---

### Post by shashanksingh on 2011-12-02
> **Lisiano said:**
> To make a application default for a certain filetype, just right-click a file -> Properties -> Open With -> Pick a application -> Make default
This will make the selected application default for whatever extension you picked, for example if you set html files to be opened with Gedit, htm files will still open with Firefox. Vice-versa.

As I said, I do not find clementine in that list, I find it directly in the right click menu as the second option.

If I open it via that option, it does open with clementine, but it doesnt make it the default application for mp3.

The only options I get are Recommended, Show other and Find Online in the "Other applications" option. and clementine isnt present there

---

### Post by Lisiano on 2011-12-02
Tried installing Clementine, now I see what you mean. Also noticing the same for Handbrake on mp3 files. In previous versions you could add custom commands, I'll try to find how to add custom applications to the list, though this should get filled as a bug at nautilus.

---

### Post by shashanksingh on 2011-12-02
Is it that only certain apps that ubuntu recognizes can be made default?

Because on the "search on the net" option, it gives me a list of apps I can install and use...

I really miss that command option, Ill file a bug still.

---

### Post by Lisiano on 2011-12-02
Found a workaround.
First we make a copy of the Clementine.desktop file
```
cp /usr/share/app-install/desktop/clementine\:clementine.desktop ~/.local/share/applications/clementine.desktop
```
Now we modify the default application list and add Clementine as a default for mp3 files
```
gedit ~/.local/share/applications/mimeapps.list
```
Under the [Default Applications] line, add ```
audio/mp3=clementine.desktop
```
Clementine is now the default app for all mp3 files, Banshee or whatever you had before will still be in the Right-Click Open as the default but will dissapear later on. If you modified the default, just replace whatever was in there with clementine.desktop

Edit: Now to restore back Banshee.

---

### Post by shashanksingh on 2011-12-02
> **Lisiano said:**
> Found a workaround.
```
gedit ~/.local/share/applications/mimeapps.list
```
Under the [Default Applications] line, add [code]


I searched the entire root but I couldnt find the "mimeapps.list"
I also dont have the applications folder in ~/.local/share

Im using 11.10.
Probably something different in this version?

---

### Post by mc4man on 2011-12-03
By default ~/.local/share/applications doesn't exist, though it & mimeappsa.list get created fairly easily/quickly when you open something from the right click > 'open with > Other Application'  or right click > 'Properties >  open with'  menus

Just pick something from either of those 2 menus & it'll show up 
(or you can just create

The reason that clementine doesn't show up on the right click properties menu is because in it's .desktop, the Exec= line doesn't end with a %letter, with f or U possible choices.

If you wanted to see clementine on the Properties menu then edit either the clementine.desktop in /usr/share/applications or a copied one in ~/.local/share/applications

Ex. - 
 in a terminal, will ck for the applications folder, create if not there, -  copy & paste the complete code box as one command.
```
cd; mkdir -p .local/share/applications && \
cp /usr/share/applications/clementine.desktop ~/.local/share/applications && \
gedit  ~/.local/share/applications/clementine.desktop
```

Make the Exec= line look like this, (9th line down or so
```

Exec=clementine %U
```

You should be good to go, if not do a log out/in

---

### Post by cbowman57 on 2011-12-03
@mc4man, good to know, worked for me.
thanks

---

### Post by shashanksingh on 2011-12-03
Thank you Lisiano and mc4man.
The %U makes it work
:)

---

### Post by mc4man on 2011-12-03
Just to note - 
The requirement of having an Exec= line end in %letter to show up in the Properties context menu extends to any app that uses a .desktop

There are several others, as found I file bugs against, sometimes they are fixed, sometimes not. Gdebi is a recent example that will be fixed, so far clementine has not responded to bug report

[https://bugs.launchpad.net/ubuntu/+source/clementine/+bug/876527](https://bugs.launchpad.net/ubuntu/+source/clementine/+bug/876527)

---

### Post by shashanksingh on 2011-12-03
[https://bugs.launchpad.net/ubuntu/+source/clementine/+bug/899285](https://bugs.launchpad.net/ubuntu/+source/clementine/+bug/899285)

I had filed this as a nautilus bug before.

Just curious, what is the significance of that %<something>
Technically what does that mean?

---

### Post by gaisboy on 2011-12-05
A big fat, thank you!! It Works!!!!!!!!!!

---

### Post by sajjad.ir on 2012-01-02
Fantasticoooooo !!
Lisiano and mc4man, both of you > Thumbs Up - Like

---

### Post by apos on 2012-01-07
Better use [Ubuntu-Tweak]("http://ubuntu-tweak.com/") to change the filetype.

[ATTACH]210422[/ATTACH]

---

### Post by morishka on 2012-01-30
wow! thank you, people. that was my problem too.

---

### Post by rgreener25 on 2012-01-30
Thanks! This helped me alot

---

### Post by forger on 2012-05-26
The bug was reported upstream and fixed in debian/ubuntu:
[https://bugs.launchpad.net/ubuntu/+source/clementine/+bug/971998](https://bugs.launchpad.net/ubuntu/+source/clementine/+bug/971998)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=666966](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=666966)
[http://code.google.com/p/clementine-player/issues/detail?id=2848](http://code.google.com/p/clementine-player/issues/detail?id=2848)

---

