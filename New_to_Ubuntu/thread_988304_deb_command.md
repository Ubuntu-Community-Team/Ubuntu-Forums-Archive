---
title: "deb command"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2008-11-20
I see the "deb" command used all over in these forums.  However, I am still not sure of how to use it.

In trying to download a game, I was given this:

deb [http://trylegaldownloads.de/ubuntu](http://trylegaldownloads.de/ubuntu) hardy games 

However, entering that in the terminal doesn't work, nor does trying:

echo "deb [http://trylegaldownloads.de/ubuntu](http://trylegaldownloads.de/ubuntu) hardy games"

...which is the syntax that I gathered was correct based on posts in this forum.

I believe deb is used to retrieve packages (I tried apt-get instead of deb with the above string, but that didn't work, predictably), but I don't know exactly what it does, or how to use it - can someone help me figure it out?

Thanks!

~Nix

---

### Post by drs305 on 2008-11-20
> **Nixie Pixel said:**
> 
In trying to download a game, I was given this:

**[COLOR="Blue"]deb [http://trylegaldownloads.de/ubuntu](http://trylegaldownloads.de/ubuntu) hardy games [/COLOR]**

However, entering that in the terminal doesn't work, nor does trying:

~Nix

This line is intended to be added as is to your sources.list.
Backup and open sources.list for editing:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksudo gedit /etc/apt/sources.list

```

Add this line to the bottom of sources.list and save the file.
```

**deb http://trylegaldownloads.de/ubuntu hardy games**

```

When you open Synaptic or Software Sources, the new repository should be active and the packages listed and available for download. The repository should be listed under the 'Third Party' tab.

For more info on repositories, here is the community link:
[Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by tagbre on 2008-11-20
You're supposed to add that line to your sources.list file (you'll finde it under (/etc/apt).
Then you open a terminal and do sudo apt-get update and sudo apt-get install yourgame, or the same process with synaptic.

---

### Post by taurus on 2008-11-20
You need to add that repo to your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and add this line to the end of it.

```
deb http://trylegaldownloads.de/ubuntu hardy games
```
Save it and then run

```
sudo apt-get update
```
Now, try to see if you can install whatever game you want to from that site.

---

### Post by Nixie Pixel on 2008-11-21
Thanks, all three of you, I appreciate it!

---

