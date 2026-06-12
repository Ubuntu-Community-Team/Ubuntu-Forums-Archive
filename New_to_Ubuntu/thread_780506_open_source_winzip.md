---
title: "open source winzip"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by daberger on 2008-05-03
my winzip is expired and i have a lot of folders to unzip so i need to find a open sourcee version. any suggestions?

and this is in windows so i cant just apt-get

---

### Post by PeterJS on 2008-05-03
7 Zip opens just about everything, the only format I've ever run in to that it doesn't open is .ace

[http://www.7-zip.org/](http://www.7-zip.org/)

---

### Post by imT on 2008-05-03
[7-zip]("http://www.7-zip.org/") ?!

edit: late, d'oh !

---

### Post by lucky.developer on 2008-05-03
go for winrar(in windows) .. i don know if it is opensource !!!

in Ubuntu..you don have problem at all... you have archive manager to take care of unzipping

---

### Post by nowshining on 2008-05-03
> **PeterJS said:**
> 7 Zip opens just about everything, the only format I've ever run in to that it doesn't open is .ace

[http://www.7-zip.org/](http://www.7-zip.org/)

in the repos, 

unace

& or

uname-nonfree


after installing the program 7-zip should now be able to open up and extract .ace files. :)

---

### Post by agentjon on 2008-05-03
ive had a pretty good experiance with peazip as well:
[http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)

---

### Post by AndyCooll on 2008-05-03
Well File-Roller is already included as part of the default Ubuntu install. It's called Archive Manager in the menus (Applications > Accessories > Archive Manager), however it's menu icon is hidden by default so you'll need to go to System > Preferences > Main Menu and place a tick against its name to get it to display. You could additionally install unrar to open rar files (using File-Roller) if you need to.

:cool:

---

### Post by zvacet on 2008-05-04
```
sudo apt-get install p7zip p7zip-full
```

---

### Post by vishzilla on 2008-05-04
When I was using Windows, I liked AlZip @ [http://www.altools.net/](http://www.altools.net/)

---

### Post by daberger on 2008-05-09
wow thats alot thanks. but i already got 7zip

---

### Post by smm18951 on 2009-02-07
Not to contradict everybody here, but think 7zip is only for Windows and not any *nix OS...I fist found out about [7 zip right here]("http://www.mrbup.com/2009/01/01/7-zip-is-the-free-open-source-ms-windows-solution-for-for-file-compression-like-winzip-and-winrar") and they didn't mention 7zip running on Ubuntu...


what do you guys think??

ps I am about to install Ubuntu for the first time tomorrow (I hope)   wish me luck

---

### Post by wildman4god on 2009-02-07
> **smm18951 said:**
> Not to contradict everybody here, but think 7zip is only for Windows and not any *nix OS...I fist found out about [7 zip right here]("http://www.mrbup.com/2009/01/01/7-zip-is-the-free-open-source-ms-windows-solution-for-for-file-compression-like-winzip-and-winrar") and they didn't mention 7zip running on Ubuntu...


what do you guys think??

ps I am about to install Ubuntu for the first time tomorrow (I hope)   wish me luck

I haven't come across an archive file yet that ubuntu couldn't handle, but the offical 7 zip program that carries its own format is a windows only, though their are programs on mac that can handle it.

---

### Post by oldos2er on 2009-02-07
7zip is in the repositories as 'p7zip'.

---

