---
title: "Trying to copy system stuff from old to new disk"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by tiggsy on 2008-10-21
Ive just done a brand new clean Hardy install on my disk sda, and I want to get all the changes i made to my old Hardy install onto the new one, without having to try and remember them all...

Someone said just copy the home folder over. I tried these:
```
tiggsy@tiggsys-desktop:~$ sudo cp /home /oldhome
[sudo] password for tiggsy: 
cp: omitting directory `/home'
tiggsy@tiggsys-desktop:~$ sudo cp /media/data/home /home
cp: omitting directory `/media/data/home'
tiggsy@tiggsys-desktop:~$ sudo cp /home/tiggsy /home/oldtiggsy
cp: omitting directory `/home/tiggsy'
tiggsy@tiggsys-desktop:~$ sudo cp /home/tiggsy /home/tiggsy/oldtiggsy
cp: omitting directory `/home/tiggsy'
tiggsy@tiggsys-desktop:~$ mkdir /home/tiggsy/oldtiggsy
tiggsy@tiggsys-desktop:~$ sudo cp /home/tiggsy/*.* /home/tiggsy/oldtiggsy
cp: cannot stat `/home/tiggsy/*.*': No such file or directory
tiggsy@tiggsys-desktop:~$ sudo cp /home/tiggsy/* /home/tiggsy/oldtiggsy
cp: omitting directory `/home/tiggsy/Desktop'
cp: omitting directory `/home/tiggsy/Documents'
cp: omitting directory `/home/tiggsy/Examples'
cp: omitting directory `/home/tiggsy/Music'
cp: omitting directory `/home/tiggsy/oldtiggsy'
cp: omitting directory `/home/tiggsy/Pictures'
cp: omitting directory `/home/tiggsy/Public'
cp: omitting directory `/home/tiggsy/Templates'
cp: omitting directory `/home/tiggsy/Videos'
tiggsy@tiggsys-desktop:~$ 

```

I wanted to back up what i have on the new disk first, which is why im starting there.

As you can see, i'm not getting very far.

otoh, surely all the data would be in there, not the systems? I don't want to duplicate the data, in any case. I just want the system stuff.

---

### Post by C.S.Cameron on 2008-10-21
This is what worked for me.
[http://ubuntuforums.org/showthread.php?t=919612](http://ubuntuforums.org/showthread.php?t=919612)

---

### Post by tiggsy on 2008-10-21
But when i try to cp, as you can see from the output above, it comes back that it copied "omitting directory `/media/data/home'" ie. it copies zilch

btw, that computer is definitely brilliant

---

### Post by Elfy on 2008-10-21
The configs specific to your user will be in the /home as .mozilla for instance, copy those. if you used a different user name the second install it will cause some issues.

Anything that you changed system wide - for example fstab are not in /home

To copy a directory you need to do so recursively - 

```
cp -r /original/path /new/path
```

---

### Post by C.S.Cameron on 2008-10-21
It might be best to boot from the live cd then copy home as it is probably in use if it on the disk you are booting from.

---

### Post by tiggsy on 2008-10-21
Thanks to you all for all your help. Ive copied all the hidden files in my home folder. Seems to be working ok. Now for the long process of reinstllng all the stuff i use...

Well, at least i now have firefox and thunderbird working as usual, and pidgin.

---

