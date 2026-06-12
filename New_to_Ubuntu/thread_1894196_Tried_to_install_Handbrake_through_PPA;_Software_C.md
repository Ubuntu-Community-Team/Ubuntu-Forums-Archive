---
title: "Tried to install Handbrake through PPA; Software Center does not run now; error"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by diablo75 on 2011-12-12
So I tried to install Handbrake using the following three commands which I learned about from [this website]("http://www.webupd8.org/2011/01/handbrake-095-has-been-released-ubuntu.html"):

```
sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk
```

I've not managed to get it installed and now when I try to run the Ubuntu Software Center now via the Unity task bar a crash message appears in the upper right notification area that says:

> An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was: 'Error:  Opening the cache (E:Type 'ain' is not known on line 2 in source list /etc/apt/sources.list.d/stebbins-handbrake-releases-oneiric.list, E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.)'.  This usually means that your installed packages have unmet dependencies

How do I fix this?

---

### Post by gennatolls on 2011-12-12
Try the following:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Then try to install handbrake
```
sudo apt-get install handbrake-gtk
```

I followed the same instructions and it worked for me.
Good Luck

Edit: Heres the PPA I have:
deb [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu) oneiric main

---

### Post by beew on 2011-12-12
If you are using Ubuntu 11.10 you have to install with the snapshots ppa instead of the "releases" one,

so change the commands to
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk
```

---

### Post by diablo75 on 2011-12-12
[QUOTE=gennatolls;11531575]Try the following:

```
sudo apt-get update
```

Produces:

```
sudo apt-get update
E: Type 'ain' is not known on line 2 in source list /etc/apt/sources.list.d/stebbins-handbrake-releases-oneiric.list
E: The list of sources could not be read.
```

And that's it...

But to add to this, here is the full contents of that file:

```
deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu oneiric main
ain
```

Edit:  Figured that "ain" was suppose to be "main" but the previous line already ended with that word so I just backspaced "ain" away.  sudo apt-get update worked after that, but said it faield to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found.  E: Some index files failed to download.  They have been ignored, or old ones used instead.

---

### Post by diablo75 on 2011-12-12
> **beew said:**
> If you are using Ubuntu 11.10 you have to install with the snapshots ppa instead of the "releases" one,

so change the commands to
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk
```

Following the corrections I made above, this did the trick!  Thanks!

---

