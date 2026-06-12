---
title: "Conky Problems"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by iSplicer on 2008-04-30
Hey all

I installed conky through synaptic as usual, but on Hardy Heron, when I start conky from alt+f2, it shows up as a separate window, rather than on the desktop where it should be... Could someone please help me fix this? Here is a screenshot:

[IMG]http://img149.imageshack.us/img149/8763/screenshot1sa9.png[/IMG]


Thanks in advance

---

### Post by Ek0nomik on 2008-05-01
The only thing I can think of is your conkyrc file being screwed up.

Could you post it?  (~/.conkyrc)

---

### Post by iSplicer on 2008-05-01
I cannot find it, even when viewing hidden files and folders!

---

### Post by Ek0nomik on 2008-05-01
> **iSplicer said:**
> I cannot find it, even when viewing hidden files and folders!

Try:

```
locate conky
```

If it doesn't find anything, try running this first, and then the above command:

```
updatedb
```

---

### Post by iSplicer on 2008-05-01
Thanks for your reply but neither of those worked.. I tried the first one.. nothing.

The second one gives an error:
> isplicer@isplicer-laptop:~$ updatedb
updatedb: can not open a temporary file for `/var/lib/mlocate/mlocate.db'

---

### Post by spiderbatdad on 2008-05-01
```
sudo updatedb
```

---

### Post by Ek0nomik on 2008-05-01
> **iSplicer said:**
> Thanks for your reply but neither of those worked.. I tried the first one.. nothing.

The second one gives an error:

Well this is odd. :)

I swear I'm not trying to be rude, seeing as how you have conky up and all, but make sure it's in:

```
sudo apt-get install conky
```

It says it's already installed right?

---

### Post by Ek0nomik on 2008-05-01
> **spiderbatdad said:**
> ```
sudo updatedb
```

I suppose that makes sense.  :/

---

### Post by iSplicer on 2008-05-01
> **Ek0nomik said:**
> Well this is odd. :)

I swear I'm not trying to be rude, seeing as how you have conky up and all, but make sure it's in:

```
sudo apt-get install conky
```

It says it's already installed right?

Thanks for the reply, but its already installed

```

isplicer@isplicer-laptop:~$ sudo apt-get install conky
Reading package lists... Done
Building dependency tree       
Reading state information... Done
conky is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
isplicer@isplicer-laptop:~$ 
```


Output of locate conky after sudo updatedb:

```
isplicer@isplicer-laptop:~$ locate conky
/etc/conky
/etc/conky/conky.conf
/usr/bin/conky
/usr/share/doc/conky
/usr/share/doc/conky/AUTHORS.gz
/usr/share/doc/conky/NEWS.Debian.gz
/usr/share/doc/conky/NEWS.gz
/usr/share/doc/conky/README.Debian
/usr/share/doc/conky/README.gz
/usr/share/doc/conky/TODO
/usr/share/doc/conky/changelog.Debian.gz
/usr/share/doc/conky/changelog.gz
/usr/share/doc/conky/config_settings.html
/usr/share/doc/conky/copyright
/usr/share/doc/conky/docs.html
/usr/share/doc/conky/examples
/usr/share/doc/conky/variables.html
/usr/share/doc/conky/examples/conky.conf.gz
/usr/share/man/man1/conky.1.gz
/usr/share/menu/conky
/var/cache/apt/archives/conky_1.5.1-1ubuntu1_i386.deb
/var/lib/dpkg/info/conky.conffiles
/var/lib/dpkg/info/conky.list
/var/lib/dpkg/info/conky.md5sums
/var/lib/dpkg/info/conky.postinst
/var/lib/dpkg/info/conky.postrm
isplicer@isplicer-laptop:~$ 


```



Thanks go to all that helped

---

### Post by Ek0nomik on 2008-05-01
Try the following:

```
cp /etc/conky/conky.conf ~/.conkyrc
```

Open the file:

```
gedit ~/.conkyrc
```

Search for:  "own_window"

Make sure it says "no".

---

### Post by iSplicer on 2008-05-01
> **Ek0nomik said:**
> Try the following:

```
cp /etc/conky/conky.conf ~/.conkyrc
```

Open the file:

```
gedit ~/.conkyrc
```

Search for:  "own_window"

Make sure it says "no".

That kinda fixed the problem (Thanks!) but theres a new one; the conky is really glitchy, everytime I drag my mouse over it it dissapears, it randomly flickers, etc

---

### Post by Ek0nomik on 2008-05-01
I'm not 100% sure on this, but try removing this line in your conkyrc file:

own_window_type override

OR replace it with:

own_window_type desktop

(the desktop is the default value, so if you remove override, it will just default to desktop.  produces the same effect)

---

### Post by spiderbatdad on 2008-05-01
you should visit  the .conkyrc thread to get some good ideas on .conkyrc files...you need think like "background yes" "double_buffer yes"...etc
Own_Window yes....and on and on...also visit conky website :P

[http://ubuntuforums.org/showthread.php?t=281865&highlight=.conkyrc](http://ubuntuforums.org/showthread.php?t=281865&highlight=.conkyrc)

---

### Post by iSplicer on 2008-05-01
> **Ek0nomik said:**
> I'm not 100% sure on this, but try removing this line in your conkyrc file:

own_window_type override

OR replace it with:

own_window_type desktop

(the desktop is the default value, so if you remove override, it will just default to desktop.  produces the same effect)

Replacing it with "desktop" doesnt help, its still really glitchy. Removing the line completely makes conky not appear at all..

---

### Post by Ek0nomik on 2008-05-01
> **iSplicer said:**
> Replacing it with "desktop" doesnt help, its still really glitchy. Removing the line completely makes conky not appear at all..

Well, my next suggestion was going to be what spiderbatdad said.  Check out some of the conkyrc files that people have posted and give them a whirl.  Then modify them from there.

---

### Post by iSplicer on 2008-05-01
Thanks guys, using one of the files there did the trick... seems that my config file was screwed over for some reason. 

Thanks guys for helping me solve another problem.. This is why I love ubuntu, if I had a similar problem in windows, I would never solve it

---

