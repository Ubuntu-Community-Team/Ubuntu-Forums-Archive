---
title: "How do i backup??"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by NikS on 2008-06-29
Hi,

I have a limited internet connection, so when i update my system, is there a way to backup the updates for later re-installations???
That way i could create a disc or something n add to my repository!!
so next time i wont have to download all of them again!!

Is it possible??

---

### Post by aysiu on 2008-06-29
All the packages download to /var/cache/apt/archives/

---

### Post by NikS on 2008-06-29
So, does that mean I can copy them (Before restart) to some other destination n next time, to install them onto new ubuntu installation, copy them back to the download destination?????

---

### Post by NovaAesa on 2008-06-29
You could also try using APTonCD available from the repos. It pretty much does exactly what you desribed needing in your original post.

---

### Post by aysiu on 2008-06-29
> **NovaAesa said:**
> You could also try using APTonCD available from the repos. It pretty much does exactly what you desribed needing in your original post.
More info here:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by NikS on 2008-06-29
Thanks!!!
I had totally forgotten that i had that .deb package n i could use it!!!!

But i have not used it before,
So now what i can do is, I download or upgrade n update my system restart computer n some later time i creat a CD!!!
Is it correct??

---

### Post by NovaAesa on 2008-06-29
Yes, once you have either installed or updated a programme, you are then able to use APTonCD to ceate a CD. You can then add that CD as a repo source on another computer to avoid having to download again.

---

### Post by NikS on 2008-06-30
Ok..
I backed up my apts.

Now when I am reinstalling, APTonCD says it only restored them (To Cache!!??)!! but then what???
Do i have to click on EVERY .deb package to install all of them??
It'l take me months!!

Do I need to write a script??
How do I write a script to install them?? Never done before!!

---

### Post by Elfy on 2008-06-30
Just posted in your other thread 

> **forestpixie said:**
> If you have them in your cache the easiest way - also the easiest way to install if you know the name of a package is in the terminal

```
sudo apt-get install *package*
```

or if you know the name and path to the deb file you could use dpkg

```
 sudo dpkg -i /path/to/deb.deb
```

so for the compiz settings manager

```
sudo apt-get install compizconfig-settings-manager
```

You can also use search in the terminal if you have an idea what to search for, then you can use double click and middle button to paste

```
apt-cache search *package*
```

If you had a list of things to install

```
sudo apt-get install *package package1 package2 package3...*
```

There is no reason why you couldn't write a script - but I've never done it as there are only a maximum of 10 things I install on a clean install so i just write the command each time.

---

### Post by aysiu on 2008-06-30
I've never used AptonCD before, but if you have all the .deb files in the same folder, you can just *cd* into that folder and then install them all at once. For example, if they're all on your desktop, you'd paste in these [terminal](http://www.psychocats.net/ubuntu/terminal) commands: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by NikS on 2008-06-30
I actually tried something like that but many packages were not installed, probably because of the dependencies.

I wrote a script to execute, listed all the packages as they were listed in browser(alphabetically!!) and executed!!
I guess thats what the mistake was...

I have tried something just now,
The disk created using APTonCD, I added it to my software source n when a particular soft, like rhythmbox asked for GStreamer plugins i updated them placing the disc in the drive, worked fine...
Dint try for all the softs yet!!

---

