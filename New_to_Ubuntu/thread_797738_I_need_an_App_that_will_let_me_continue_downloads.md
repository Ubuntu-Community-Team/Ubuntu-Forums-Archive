---
title: "I need an App that will let me continue downloads"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by microsoft92sucks on 2008-05-17
I'm getting internet from WiFi and ot messes up alot for a minute or so (I'm pretty sure it's our phone screwing up the conection because there both on 2.4ghz) 
But anyway on firefox if your downloading something but it loses a conection for a minute or so you have to restart the hole download.
This gets really anoying when downloading a big file 
So is there anyway to keep what you have downloaded so far from a http or ftp server. Firefox plugin or stand alone App?

---

### Post by microsoft92sucks on 2008-05-17
Help
Please

---

### Post by herbster on 2008-05-17
You can use wget with the -c flag.

```
 wget -c http://www.site.com/file.mp3
```

as an example. If you don't use the -c flag, it will download the same file with a .1 extension numerically increasing.

And of course, if the host doesn't support resume, nothing you can do.

---

### Post by NightwishFan on 2008-05-17
Try kget. I am not sure if gwget can resume I know kget can.

---

### Post by ugm6hr on 2008-05-17
This works for me: DownThemAll Firefox addon
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)
[http://www.downthemall.net/](http://www.downthemall.net/)

---

### Post by SlappyPappy on 2008-05-17
Sweet! I was looking for something like that. 

In Windows I use an old program called NetVampire that was amazing at picking up where it left off after a dropped connection. It's the program I used to download Gutsy LiveCD on dialup.

Hope this addon works as well as NetVampire.  :)

---

### Post by microsoft92sucks on 2008-05-17
Thanks I've installed gwget and kget
I'm gonna try them both to see which one I like better
Hopefuly the'll let me continue a download next my internet screws up

Download Them All didn't seem to let me continue downloads after they where cut short...

---

### Post by nowshining on 2008-05-17
if u want u can get a firefox extension for gwget altho u'll have to do a lil manual labor - i use both the downthemall add-on and gwget. :)

rem. all .xpi file are actually zip files :)

right click on this and download to ur desktop:
[http://gnome.org/projects/gwget/FireGet-0.6.xpi](http://gnome.org/projects/gwget/FireGet-0.6.xpi)

Then open it up with ark or whatever unzip program u use and extract all contents,

in  the folder find a file with an extension called .rdf - and fix the max ver. & change it to whatever number u want that is higher than 3.0 or 2.0 or basically ur firefox version (i used ver. 4.00. - Save and re-package and if need be rename the extension .xpi and ctrl + o in ur browser and install. :)

edit: also any .jar file for firefox are zip files in disguise.

---

