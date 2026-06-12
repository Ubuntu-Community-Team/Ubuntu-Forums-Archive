---
title: "File deleted in terminal but still exists on GUI"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by GunGrave01 on 2012-05-21
Hello together, I need some help/advice. I have used terminal to remove my iTunes folder from my system with the "rv" command and I cannot find the file anymore if I am looking for it using the "dir -a" command in terminal. But when I am entering the folder where iTunes was installed  by using GUI, there is still the iTunes folder there. 
But why ?

Thanks in advance.

Dennis

---

### Post by acimi66 on 2012-05-21
Are you trying to delete the folder/ directory?

rm -r "folder name"= remove dir

rm -rf "folder name" = force removal of dir

I have come across this on occasion, I don't WHY it happens but I have found those two commands useful.

---

### Post by GunGrave01 on 2012-05-22
Hi, thanks for response. Using "rm -r iTunes" I am getting "this folder/directory does not exist",
"rm -rf iTunes" has no effect, but the folder is still available in my GUI. This is very strange.

Thanks anyways.

---

### Post by wojox on 2012-05-22
huh, what does the terminal list?
```
cd && ls -al
```

---

### Post by buzzingrobot on 2012-05-22
Not sure which GUI you're using, but look for an option to refresh its file listings.  Some programs need that before recognizing file system changes.

---

### Post by GunGrave01 on 2012-05-22
Hi togheter,
I've tried it with "cd && ls -al" and "ls -al", I couldn't find the iTunes folder in terminal. 
@buzzingrobot, would restart the pc be enought to refresh the GUI ? If yes, then it didn't help either.

Adios muchachos !

---

### Post by forrestcupp on 2012-05-22
Why don't you just delete it from the GUI? If you're using Nautilus, and for some reason it's not in your /home folder, you can open Nautilus with root privileges; just be very, very careful.
```
gksudo nautilus
```

---

### Post by acimi66 on 2012-05-22
This is probably a good example:

acimi66@Satellite-L650:~$ rm -f .idjc
rm: cannot remove `.idjc': Is a directory
acimi66@Satellite-L650:~$ rm -r idjc
rm: cannot remove `idjc': No such file or directory

I have deleted the program from the software center.

If I go to DASH and type IDJC the program is there and I can click on it and it opens.

I am using 12.04

P.s.
drwxrwxr-x   4 acimi66 acimi66   4096 Apr  6 19:12 .idjc

---

### Post by GunGrave01 on 2012-05-22
> **forrestcupp said:**
> Why don't you just delete it from the GUI? 


there is a principal involved :p

I haven't used Nautilus before, gonna try it out.

---

### Post by buzzingrobot on 2012-05-22
> **GunGrave01 said:**
> 
@buzzingrobot, would restart the pc be enought to refresh the GUI ? If yes, then it didn't help either.

Yes.  I don't know which application you are using, but if a file manager does not reflect file system changes in real time, typically there is a "Refresh" function available somewhere in its menu.

---

### Post by steeldriver on 2012-05-22
> **acimi66 said:**
> This is probably a good example:

acimi66@Satellite-L650:~$ rm -f .idjc
rm: cannot remove `.idjc': Is a directory
**acimi66@Satellite-L650:~$ rm -r idjc**
[B]rm: cannot remove `idjc': No such file or directory
[/B] 
I have deleted the program from the software center.

If I go to DASH and type IDJC the program is there and I can click on it and it opens.

I am using 12.04

P.s.
drwxrwxr-x   4 acimi66 acimi66   4096 Apr  6 19:12 **.idjc**

you left out the '.'

---

### Post by acimi66 on 2012-05-23
Yeah thanks, but that didn't help.

I will add it as a bug when I get a chance.

Cheers

---

### Post by acimi66 on 2012-05-24
This Helped.

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-completely-uninstallremove-a-packagesoftwareprogram](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-completely-uninstallremove-a-packagesoftwareprogram)

I was able to find the files and delete them.

---

