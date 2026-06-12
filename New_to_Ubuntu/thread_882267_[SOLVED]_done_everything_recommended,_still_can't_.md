---
title: "[SOLVED] done everything recommended, still can't get cairo dock to open"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by huntwell on 2008-08-06
I have gone to every thread and checked out every how to possible to get cairo-dock installed and working properly, but it still won't open. I get this message now: [COLOR="Red"]cairo-dock: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory
[/COLOR]

Does anyone have any suggestion on how to get this problem fixed? Like I said, I have done everything that all of the threads suggest and as far as I can tell, I installed it exactly as recommended. Does anyone have any idea as to how to fix this?

Thanks,
Huntwell

---

### Post by spiderbatdad on 2008-08-06
how did you install cairo-dock? Did you download the .deb packages and plugins?

You can probably create the symlink manually and solve the problem.

perhaps...```
sudo ln -s /usr/lib/libdbus-glib-1.so.2 /usr/lib/libdbus-glib-1.so.1

```
You'll need to look in /usr/lib to see which libdbus-glib you are actually linking.

---

### Post by huntwell on 2008-08-06
> **spiderbatdad said:**
> how did you install cairo-dock? Did you download the .deb packages and plugins?

You can probably create the symlink manually and solve the problem.

perhaps...```
sudo ln -s /usr/lib/libdbus-glib-1.so.2 /usr/lib/libdbus-glib-1.so.1

```
You'll need to look in /usr/lib to see which libdbus-glib you are actually linking.

I tried the code you recommended, but nothing happened. Also, I am sorry that I am not understanding what you mean by which libdbus-glib I am using. What do I need to be looking at/for? 

I downloaded using the deb files if this helps at all.

Thanks.

---

### Post by sharks on 2008-08-06
look for libdbus-glib-dev

---

### Post by huntwell on 2008-08-06
> **sharks said:**
> look for libdbus-glib-dev

Sharks,

Thanks for the help. I do not see a file by that name in the /usr/lib file. 

I also looked in synaptic and found that there are several unchecked packages: libdbus-1-dev , libdbus-glib-1-dev , libdbus-qt-1-dev , etc. Should these packages be checked?

Thanks again,
Huntwell

---

### Post by eightmillion on 2008-08-06
The package you need is **libdbus-glib-1-2**
> sudo apt-get install libdbus-glib-1-2

---

### Post by huntwell on 2008-08-06
> **eightmillion said:**
> The package you need is **libdbus-glib-1-2**

Thanks for the suggestion, but when I used that in the terminal, this is what I got back: [COLOR="Red"]libdbus-glib-1-2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/COLOR]

I am not sure why I am still having problems. Any other suggestions?

Thanks for your time.

---

### Post by eightmillion on 2008-08-06
Try this...
> sudo apt-get install --reinstall libdbus-glib-1-2
then try restarting cairo-dock.

---

### Post by nkri on 2008-08-06
Instead of the .deb, try using the repo.  Add this to your sources.list:

For Hardy:
```
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
```

For Gutsy:
```
http://repository.cairo-dock.org/ubuntu gutsy cairo-dock
```

It will install the dependencies for you, and should work just fine:).

Good luck!
-nkri

---

### Post by spiderbatdad on 2008-08-07
> **huntwell said:**
> I tried the code you recommended, but nothing happened. Also, I am sorry that I am not understanding what you mean by which libdbus-glib I am using. What do I need to be looking at/for? 

I downloaded using the deb files if this helps at all.

Thanks.

I was trying to suggest you see which libdbus-glib you had in /usr/lib and link to it. For example if you see:libdbus-glib-1.so.2.1.0 then your link would be;
```
sudo ln -s /usr/lib/libdbus-glib-1.so.2 /usr/lib/libdbus-glib-1.so.2.1.0
```

---

### Post by huntwell on 2008-08-07
> **nkri said:**
> Instead of the .deb, try using the repo.  Add this to your sources.list:

For Hardy:
```
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock
```

For Gutsy:
```
http://repository.cairo-dock.org/ubuntu gutsy cairo-dock
```

It will install the dependencies for you, and should work just fine:).

Good luck!
-nkri

I added the above repository to 'Software Sources' but I had it added before and I still couldn't get it to run. I am using hardy 64 bit with AMD64 processor. I am wondering if this is why I am having so many problems.

What would you all recommend as the best way to download cairo-dock? I have been to a lot of different web sites and probably read all of the threads for cairo dock and cannot seem to find a download system that works.

Maybe I should give up on cairo dock, but I would like a dock on ubuntu and found that Kiba-Dock caused problems with my screensaver and simdock doesn't work right either. 

Well, thanks everyone for all of your help.

---

### Post by huntwell on 2008-08-07
> **spiderbatdad said:**
> I was trying to suggest you see which libdbus-glib you had in /usr/lib and link to it. For example if you see:libdbus-glib-1.so.2.1.0 then your link would be;
```
sudo ln -s /usr/lib/libdbus-glib-1.so.2 /usr/lib/libdbus-glib-1.so.2.1.0
```

OK, so I must have been a bonehead somewhere before because I used the repository suggestion from the ubuntu wiki and it has worked perfectly. 

Thanks all,
Huntwell

---

