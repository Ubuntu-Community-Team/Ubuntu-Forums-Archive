---
title: "[SOLVED] Best place to install applications"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by leemajors on 2008-06-19
Hi there,

Using the Package Manager or the Add / Remove Applications wizard, installing applications is extremely easy.

However, I just downloaded a tar.gz file from songbird ([www.songbirdnest.com](www.songbirdnest.com)) and extracted it to my desktop. Within the folder that was extracted, was a program that ran songbird.

My question is, since I've now got a folder on my desktop which houses an application, where is the best place to put this folder? I don't want it sitting on my desktop. Is there a place in /home that I should be putting installed apps like this?

If someone could download and install that application as well and let me know if I need the whole folder or if there's just a couple of files in there I need that would be great too.

Thanks!

---

### Post by Duck2006 on 2008-06-19
Place it in your home folder. Thats where most of your other programs are click Ctrl+h key and you can see them.

---

### Post by leemajors on 2008-06-19
Awesome! What's convention -- should you put them in a subdirectory like /home/installs?

---

### Post by Duck2006 on 2008-06-19
You can.

---

### Post by leemajors on 2008-06-19
Well I know I *can* :) I guess I'm asking really what would *you* do if you were installing this application? I'm quite keen to do things the right way if you know what I mean...

---

### Post by mivo on 2008-06-19
I put the few manually, non-.deb installed applications to /home/username/programs. But anything is fine, pick any name you like best. There's no right or wrong way of doing this (you can put them in /bin, but I prefer the way that's easier to maintain). Don't worry too much, you'll reinstall often enough in the future. ;)

---

### Post by Duck2006 on 2008-06-19
I would make an home partition and store them in there.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you have to reinstall you still have your home partition with your stuff in there.

---

### Post by kansasnoob on 2008-06-19
Simply as a matter of preference I open my Home Folder and then File > Create Folder, and name the folder so you'll know what it is. Like I have one called OS Stuff. Not imaginative but I know what it is.

---

### Post by leemajors on 2008-06-19
Thanks everyone.

I had already created a separate home partition thanks to psychocats before I installed Ubuntu but thanks for that extra advice as well -- much appreciated :)

---

### Post by kansasnoob on 2008-06-19
Oh, and I suppose you know (I love this feature) you can just move a file from desktop to home and then when you open your home folder you can drag-n-drop any new files into their proper folders. Great for folks like me that can't remember folder names off the cuff.

---

### Post by ktrnka on 2008-06-19
I copied my songbird folder to /usr/share and then placed a symlink from
there to /bin so I could easily create an application launcher on my panel

```
sudo cp -R /home/yourusername/Desktop/Songbird /usr/share
```
```
cd /bin
```
```
sudo ln -s /usr/share/Songbird/songbird songbird
```

Then right-click on one of your panels and select "Add to Panel"
Select "Custom Application Launcher" and click add
Where it says "Name" put Songbird
Where it says "Command" put songbird
If you then click on the spring icon you can browse to usr/share/Songbird/chrome/icons/default
Once you click "Open" in that folder, you should then see the songbird egg.
Select it and then click ok

---

### Post by leemajors on 2008-06-20
> **kansasnoob said:**
> Oh, and I suppose you know (I love this feature) you can just move a file from desktop to home and then when you open your home folder you can drag-n-drop any new files into their proper folders. Great for folks like me that can't remember folder names off the cuff.

not sure what you mean?

---

