---
title: "How do I install Flash plugin for Firefox and Opera?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by RobHK on 2008-06-28
I was unable to view the video at the end of this page:
[http://blogs.independent.co.uk/independent/a_nice_green_leaf/index.html](http://blogs.independent.co.uk/independent/a_nice_green_leaf/index.html)  on either Firefox or Opera.

I have spent over an hour googling and trying to get it to work but am just getting more confused. Can someone help please?

---

### Post by ConMan318 on 2008-06-28
Try entering this in the command line:
```

sudo apt-get install flash-plugin-nonfree

```

Then try again.

---

### Post by brian_p on 2008-06-28
> **RobHK said:**
> I was unable to view the video at the end of this page:
[http://blogs.independent.co.uk/independent/a_nice_green_leaf/index.html](http://blogs.independent.co.uk/independent/a_nice_green_leaf/index.html)  on either Firefox or Opera.

It's never a good thing to refer to the position of an item on a page as a way of locating it. Different browsers render pages in different ways.

> I have spent over an hour googling and trying to get it to work but am just getting more confused. Can someone help please?

As ConMan318 but

```
apt-cache search flash
```

might throw up other things which might interest you.

---

### Post by swimm3r137@gmail.com on 2008-06-28
how do u install flash for konqueror browser?

---

### Post by whitethorn on 2008-06-28
Konqueror usually looks into the Firefox plugins.  So either you can get the flash-nonfree or download flash 9 from the adobe webpage and install it.  

For Opera you need the 9.50b version to be able to play flash. Firefox should work with the flash-nonfree out of the repositories

---

### Post by Ptero-4 on 2008-06-28
Just install it like you would for firefox, then add the firefox plugins path to the plugins list (not on a KDE now, so I'm going from memory). It should be on the "plugins" section of the "Configure konqueror" dialog. And the path is /usr/lib/firefox/plugins (IIRC).

---

### Post by Ptero-4 on 2008-06-28
> **whitethorn said:**
> Konqueror usually looks into the Firefox plugins.  So either you can get the flash-nonfree or download flash 9 from the adobe webpage and install it.  

For Opera you need the 9.50b version to be able to play flash. Firefox should work with the flash-nonfree out of the repositories

Actually, konqueror by default look in the netscape plugin paths, you need to add the firefox one manually (AFAIR, not on KDE ATM).

---

### Post by doorknob60 on 2008-06-28
My Konqueror looks in the Firefox paths on Debian, and it did in Kubuntu too. Should work no problem :)

---

### Post by markbuntu on 2008-06-28
The correct place to put flash in hardy is in 

usr/lib/flashplugin-nonfree

No matter where you got it from or what version, this is where the

libflashplayer.so

 should live.

You can go to Tools/Preferences/Advanced in Opera and highlight 

applicationx/shockwave....swf

and click edit and change the path to 

user/lib/flashplugin-nonfree

This will work for both i386 and amd64 versions of Opera. If you direct the search to firefox-addons in amd64 it will link to npwrapper.flashplayer.so and Opera9.50 does not need the wrapper to use flash on amd64 so it should be linked directly.

You can get flash10b from the adobe website and unpack the download and put libflashplayer.so the directory mentioned above. The installer will try to put it in the wrong place for Ubuntu and complicate any future updates.

---

### Post by RobHK on 2008-06-29
> **ConMan318 said:**
> Try entering this in the command line:
```

sudo apt-get install flash-plugin-nonfree

```

Then try again.

That's already installed, Brian, via Synaptic. But I did it anyway and got an error message:

 ```
$ sudo apt-get install flash-plugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flash-plugin-nonfree
```

---

### Post by netwurkpunk on 2008-06-29
Im having the same problem.

---

### Post by brian_p on 2008-06-29
> **RobHK said:**
> That's already installed, Brian, via Synaptic. But I did it anyway and got an error message:

 ```
$ sudo apt-get install flash-plugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flash-plugin-nonfree
```


flashplugin-nonfree

I only proof-read my own posts!

---

### Post by RobHK on 2008-07-01
> **brian_p said:**
> flashplugin-nonfree

I only proof-read my own posts!

Point taken :). But it was already installed, though.

---

### Post by gandaran on 2008-07-01
> **RobHK said:**
> Point taken :). But it was already installed, though.

if it's installed, should be working for both firefox and opera ( only opera 9.50), maybe you have something else also installed like swfdec and gnash flash.
or are you runnig firefox 2?

---

### Post by AJCF on 2008-07-03
> **markbuntu said:**
> The correct place to put flash in hardy is in 

usr/lib/flashplugin-nonfree

No matter where you got it from or what version, this is where the

libflashplayer.so

 should live.

You can go to Tools/Preferences/Advanced in Opera and highlight 

applicationx/shockwave....swf

and click edit and change the path to 

user/lib/flashplugin-nonfree

This will work for both i386 and amd64 versions of Opera. If you direct the search to firefox-addons in amd64 it will link to npwrapper.flashplayer.so and Opera9.50 does not need the wrapper to use flash on amd64 so it should be linked directly.

You can get flash10b from the adobe website and unpack the download and put libflashplayer.so the directory mentioned above. The installer will try to put it in the wrong place for Ubuntu and complicate any future updates.

Thank you, dear sir :D

---

### Post by WinterMadness on 2008-07-03
> **RobHK said:**
> I was unable to view the video at the end of this page:
[http://blogs.independent.co.uk/independent/a_nice_green_leaf/index.html](http://blogs.independent.co.uk/independent/a_nice_green_leaf/index.html)  on either Firefox or Opera.

I have spent over an hour googling and trying to get it to work but am just getting more confused. Can someone help please?


to get it working for opera all I did was copy the .so file into the opera folder. 

for firefox, it seems like it installs its self

---

### Post by aminesoft on 2008-07-03
```
sudo apt-get install flash-plugin
```
good luke :lolflag:

---

