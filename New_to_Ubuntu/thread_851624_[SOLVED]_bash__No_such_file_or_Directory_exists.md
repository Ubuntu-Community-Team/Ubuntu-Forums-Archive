---
title: "[SOLVED] bash : No such file or Directory exists"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2008-07-06
Hi
I'm trying some commands but get this error message :
bash : ./configure: No such file or Directory exists

I have same error message under my user and under root.

How do I fix that ?

Thanks

---

### Post by iaculallad on 2008-07-06
Be sure that you're inside the directory of where you're configure script resides before issuing the command:

Do the **ls** command first to check if the configure script is present in that directory

```
./configure
```

then:

```
sudo make install
```

But don't forget to install the build-essential files first before compiling your application:

```
sudo apt-get install build-essential
```

---

### Post by Pierrot Lafouine on 2008-07-06
ok,
I tried but look like configure script is not there.
I'm trying to update firefox 2.0 to 3.0 I just downloaded from web site.
Could it be possible that there is no configure/make/install script ?  and use a different method for installing the upgrade ?

Thanks

---

### Post by iaculallad on 2008-07-06
Lets try this:

Create a backup of your current Firefox profile:

```
cp -r ~/.mozilla/firefox/ ~/my_firefox_profile_backup
```

Get and extract the Firefox version:

```
wget -P ~ ftp://ftp.mozilla.org/pub/firefox/releases/3.0b4/linux-i686/en-US/firefox-3.0b4.tar.bz2 && tar xjf ~/firefox-3.0b4.tar.bz2 -C ~
```

Execute Firefox:

```
~/firefox/firefox
```

---

### Post by Pierrot Lafouine on 2008-07-07
hummmm
What should be the output of the command ~/firefox/firefox ?
Right now it just start old firefox version 2.0
Thanks

---

### Post by Titan8990 on 2008-07-07
Firefox does not need to be compiled. It is ready to execute and use as soon as you download it. All you need to do is configure you menus to hit firefox 3 instead of FF2.

---

### Post by Pierrot Lafouine on 2008-07-07
ok thanks,
but then I need to understand the command I did to get FF3 :

```
wget -P ~ ftp://ftp.mozilla.org/pub/firefox/releases/3.0b4/linux-i686/en-US/firefox-3.0b4.tar.bz2 && tar xjf ~/firefox-3.0b4.tar.bz2 -C ~
```

I understand wget in the command
But I dont understand &&, is it kind of a concatenation ?

tar is to uncompress, right ?
then were is the target folder of the command ?
Do I have to do all these command under root or with sudo ?

Thanks

---

### Post by Titan8990 on 2008-07-07
wget downloads the package

tar -x extracts a tar achive (similar to zip). -j flag uncompresses.

see: man tar

It does all this in your home directory show as "~" at the very end of the line.

And yes, && is a concatenation.

---

### Post by Pierrot Lafouine on 2008-07-07
Ok thanks,
There is a weird behavior on my computer, so I`ll ask question from begining (assuming the error is a 12-24 type)

were is home ?
We are 2 users using this computer (pl and mfl).
Is firefox, after tar command should be located  '/home/pl/firefox' ?
If so, what should be the command to launch FF3 ?
I'm assuming doing this should work :
```
cd home
cd pl
cd firefox
firefox
```

But it start FF2

---

### Post by Pierrot Lafouine on 2008-07-07
up

---

### Post by The Cog on 2008-07-07
The && bit in the script says to only do the second half if the first half worked.

FF 3.0b4 is old. There is a proper release version 3.0 out now.

Firefox is strange. If you launch firefox while another firefox is already open, it tells the already running instance to open a new window. So if you already have FF2 running, the FF3 launcher will simply give you a new FF2 window. Close all open FF2 windows before launching FF3 and you should see the new version running.

---

### Post by Pierrot Lafouine on 2008-07-07
> **The Cog said:**
> The && bit in the script says to only do the second half if the first half worked.

ok good to know

> FF 3.0b4 is old. There is a proper release version 3.0 out now

Ok, how do I get it ?
I must admit I'm still confuse with all these different ways to install software under Linux.

> Firefox is strange. If you launch firefox while another firefox is already open, it tells the already running instance to open a new window. So if you already have FF2 running, the FF3 launcher will simply give you a new FF2 window. Close all open FF2 windows before launching FF3 and you should see the new version running.

Ok, you fix the damn thing, FF3 now starts
:guitar:

---

### Post by The Cog on 2008-07-07
Download from a link on this page:
[http://www.mozilla.com/](http://www.mozilla.com/)
You will be offered a .tar.bz2 file, which is a compressed tar archive (much like a .zip file). Unzip it and it creates a firefox directory. Just put that entire directory wherever you want to keep it. No installer or anything complicated - just a directory full of all the files of the program. I copied mine to /opt/firefox, but is's your choice. /usr/local might be another good place for it.

---

### Post by Pierrot Lafouine on 2008-07-07
Thank you, it worked
Is this means there is no 'registry' or something similar to that under Linux ?

---

### Post by The Cog on 2008-07-07
Not a monolithic thing like windows. Most system config is held in the /etc/ directory. Mostly in textual configuration files.

---

