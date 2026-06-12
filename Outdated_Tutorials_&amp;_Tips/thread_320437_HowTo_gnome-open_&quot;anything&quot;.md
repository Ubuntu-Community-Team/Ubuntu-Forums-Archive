---
title: "HowTo gnome-open &quot;anything&quot;"
date: 2006-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by xyz on 2006-12-17
I was roaming the "ubuntu-fr.org" and found a post by [**BookeldOr**]("http://forum.ubuntu-fr.org/viewtopic.php?id=80904") that said _gnome-open "n'importequoi"_ meaining that with the "gnome-open" command line, you'll open lots of stuff from a terminal.
I find this very useful; it may depend on the way you approach your OS, I guess.

So I tried a bit...

I have a FAT 32 /dev/hda3 partition;so:
```
th@luser:~$ gnome-open /media/hda3
```

or my external HD:
```
gnome-open /media/usbdisk
```

Now I'd like to have a look at my photos:
```
gnome-open /home/th/photos
```

Need to read a .pdf?
```
gnome-open file_whatever.pdf
```
This will open the file with your preferred pdf reader.

How about:
```
gnome-open ubuntuforums.org
```
No need for [www..](www..).

Want to send an E-mail to your friends?
```
gnome-open mailto:yourfriend@hello.com
```
This will start the mail client you chose.

And so on...
I think this works with all mime types.

---

### Post by pavel_kbc on 2006-12-18
good tips . thanks :P

---

### Post by kalikiana on 2006-12-18
Incidently you can use 'exo-open' on Xubuntu in the very same way. ;)

---

### Post by ~LoKe on 2006-12-18
Not bad!

---

### Post by Klau3 on 2010-05-28
How can I add a file to a new mail? I have written a script that enables me to resize pictures to a certain custom MB size. Next step is, that I want to add the ZIPed images to a new mail message. I tried with gnome-open but couldn't find a way how to manage it. A tip would be nice.

Klau3

---

