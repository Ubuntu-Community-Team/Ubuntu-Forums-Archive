---
title: "HOWTO: Make your own Automatix (ish, but not really)"
date: 2006-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by funkenstein on 2006-04-04
Hi there, I've written myself a little script that'll allow me to automatically install the stuff that I use most often... Kind of like my own automatix, only less fancy and with fewer things in it. 
Also, I moved away from the zenity thing... because I don't need it? 
Oh yea, I took everything in the file from [http://easylinux.info](http://easylinux.info), ubuntu brerezy part. It should work well enough on dapper too, IF YOU MODIFY IT ACCORDING TO THE DAPPER WIKI, on the same page. It doesn't really matter where you get the howto's from, really, so long as you can do everything in a shell. I suppose it'll work just as well on kubuntu, again, modifying the contents to fit your needs.

The script is about 100000000 miles from perfect, but what it does, is let n00bs such as myself download and customise it to their liking. I think that having an "easy to understand" shellscript is better for learning and modifying than other similar solutions using zenity. It's prettier, but it involves some sort of kjnowledge and programming and I'm lazy... I suppose this is kind of like a shell script howto, with the added bonus that instead of echoing "'ello, wurld" you get to install software.

On a final note: Instructions.
first, read easylinux.info, figure it out for yourselves a little
then, compare what I've written and try to understand why and how I did things and stuff and how you would modify it to work on your system/for your taste.
finally, chmod +x it, and sudo uberscript.txt it, and cross your single finger you didn't do any typos... although it wouldn't break your system too bad if you did... hopefully.... depending on how drunk/stoned/tired/excited/in-a-hurry/misc/other you were at the time, I suppose... :rolleyes: 
(note that it doesn't matter what name/extension you give it, so long as you chmod +x it... ) 


Anyway, since this is a forum and people ask questions in it, I'll start it off (cuz I'm a noob too, don't you know!:p ):

a. how can you echo linebreaks into a new file?
right now I do it line by line, but I'm sure there's a better way than this:

```
echo "[Desktop Entry]" > /usr/share/applications/dvdrip.desktop
echo "Name=dvd::rip" >> /usr/share/applications/dvdrip.desktop
echo "Comment=dvd::rip" >> /usr/share/applications/dvdrip.desktop
echo "Exec=dvdrip" >> /usr/share/applications/dvdrip.desktop
echo "Icon=/usr/share/perl5/Video/DVDRip/icon.xpm" >> /usr/share/applications/dvdrip.desktop
echo "Terminal=false" >> /usr/share/applications/dvdrip.desktop
echo "Type=Application" >> /usr/share/applications/dvdrip.desktop
echo "Categories=Application;AudioVideo;" >> /usr/share/applications/dvdrip.desktop
```

b. how can I insert text at a specific point in a file? I haven't installed some of the thigns I wanted to in this script because it involves me finding a specific line in a file and changing it...

---

### Post by wheelspin on 2006-04-14
[QUOTE=funkenstein]

Anyway, since this is a forum and people ask questions in it, I'll start it off (cuz I'm a noob too, don't you know!:p ):

a. how can you echo linebreaks into a new file?
right now I do it line by line, but I'm sure there's a better way than this:

```
echo "[Desktop Entry]" > /usr/share/applications/dvdrip.desktop
echo "Name=dvd::rip" >> /usr/share/applications/dvdrip.desktop
echo "Comment=dvd::rip" >> /usr/share/applications/dvdrip.desktop
echo "Exec=dvdrip" >> /usr/share/applications/dvdrip.desktop
echo "Icon=/usr/share/perl5/Video/DVDRip/icon.xpm" >> /usr/share/applications/dvdrip.desktop
echo "Terminal=false" >> /usr/share/applications/dvdrip.desktop
echo "Type=Application" >> /usr/share/applications/dvdrip.desktop
echo "Categories=Application;AudioVideo;" >> /usr/share/applications/dvdrip.desktop
```

b. how can I insert text at a specific point in a file? I haven't installed some of the thigns I wanted to in this script because it involves me finding a specific line in a file and changing it...[/QUOTE]

A.
A backslash escaped n denotes a newline, example: \n
also unless you are root you need sudo permission to write to restricted access file locations. So the above code should look like this:

```
sudo sh -c 'echo -e "[Desktop Entry]\nName=dvd::rip\nComment=dvd::rip\nExec=dvdrip\nIcon=/usr/share/perl5/Video/DVDRip/icon.xpm\nTerminal=false\nType=Application\nCategories=Application;AudioVideo;" > /usr/share/applications/dvdrip.desktop'
```

B.
There are several ways to insert text into a file: echo, sed, awk, head, tail, cut, paste, diff, etc. if what you want to enter is constant it's pretty easy if it's more random it could be quite difficult. Let me know exactly what you are trying to do and maybe I can help.

---

### Post by jtibau on 2006-05-10
hi,
I'm sort of working on the same thing, I want to install ubuntu on some of my friends machines and use an Automatix like script but use my own repositories.
For what I've seen in a couple of scripts, what most people do to edit files is like a sources.list is write their own sources.list and then make the script backup the original file from the machine it is being run at. Then copy the file they provide, use it, and after being done with it, replace the original file back...
Of course that wouldn't exactly work nicely with a different conf file, but I'm assuming that the line you want to add is one to sources.list
If not the commands listed in the other post could be better.

---

### Post by starscalling on 2006-12-10
o.O awesome project ^_^

---

### Post by jusmurph on 2007-06-27
I take it there is nothing else like this that is current and a bit more polished?

---

### Post by compiledkernel on 2007-06-28
I use apt-mirror, and apt-proxy for the purposes of updating mutiple machines over a wide variety of times. 

Both are very good ways of doing this. 

[http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/)
[http://apt-proxy.sourceforge.net/](http://apt-proxy.sourceforge.net/)

---

