---
title: "Add to /etc/apt/sources.list"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by bgast1 on 2008-05-26
I'm trying to get this up in a terminal but I keep getting permission denied. What I actually want to do is add the following lines. I want to use a package called moblock. At least, I think I do.

deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main

---

### Post by iaculallad on 2008-05-26
Here is the [guide]("http://moblock-deb.sourceforge.net/") to successfully install your MoBlock.

Below is the walk through of the guide.

Open your /etc/apt/sources.list,

Code:

> sudo gedit /etc/apt/sources.list

and paste this at the very end-part of the file.

> deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main

Next thing to do is, input the following commands on your terminal: one at a time.

> gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg --export --armor 9072870B | sudo apt-key add -

Be sure that "Universe" is enabled on your "Software Sources"

Do the update:

Code:

> sudo aptitude update

Final Part is the installation process:

Code:
> 
sudo aptitude install moblock
sudo aptitude install mobloquer

---

### Post by amingv on 2008-05-26
You need to do
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksudo gedit /etc/apt/sources.list
```

Though editing sources.list works, it is also an easy way to break apt if you don't have a steady hand, adding repos from Synaptic is, in my opinion, much more secure:
```
System>Synaptic Package Manager>Settings>Repositories>New
```

and add the data like this:

```
Binary deb
URI: http://moblock-deb.sourceforge.net/debian
Distribution: hardy
Section: main
```

Of course, make sure you can trust whatever repo you add to the list, run
```
sudo apt-get update
```
to commit changes.

---

### Post by bgast1 on 2008-05-26
I was at that guide when I originally posted. I can't get past the part where it says to add those lines to /etc/apt/sources.list

Actually I don't really understand what I'm doing anyway, but I just keep plugging away trying to understand. :lolflag:

Edit:
Thanks iaculalla, it worked perfectly.

---

### Post by iaculallad on 2008-05-26
> **bgast1 said:**
> I was at that guide when I originally posted. I can't get past the part where it says to add those lines to /etc/apt/sources.list

Actually I don't really understand what I'm doing anyway, but I just keep plugging away trying to understand. :lolflag:

Edit:
Thanks iaculalla, it worked perfectly.

You're welcome. Glad to have help. Go Ubuntu

---

### Post by jre on 2008-05-28
> **bgast1 said:**
> I was at that guide when I originally posted. I can't get past the part where it says to add those lines to /etc/apt/sources.list

Actually I don't really understand what I'm doing anyway
The important point was the "gk**sudo** gedit /etc/apt/sources.list".
sudo does give you root (administrator) privileges for the following command. And you need those privileges to edit system files like sources.list.

sources.list is the file that tells your packaging software where it can find packages.

---

