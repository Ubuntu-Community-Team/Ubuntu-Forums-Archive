---
title: "Trouble with converting .rpm to .deb"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by jshaterian on 2008-08-21
I am trying to convert an .rpm file to .deb through alien. I have downloaded the .deb file, and am able to to find it through search command. But when I go to the terminal and attempt to install it through the command 'sudo alien package_file.rpm' I get the response "File not found." Do I need to download the file to specific location, as I it is currently on my desktop? Or do I need to access it through a certain way? Any help would be appreciated.

Thanks.

---

### Post by stchman on 2008-08-21
> **jshaterian said:**
> I am trying to convert an .rpm file to .deb through alien. I have downloaded the .deb file, and am able to to find it through search command. But when I go to the terminal and attempt to install it through the command 'sudo alien package_file.rpm' I get the response "File not found." Do I need to download the file to specific location, as I it is currently on my desktop? Or do I need to access it through a certain way? Any help would be appreciated.

Thanks.

If you have already downloaded the .deb file then double clicking on it will start the install process.

If you have a .rpm file to convert to a .deb file do the following:

```
sudo alien -d ~/Desktop/<.rpm package>
```

You said the package was on your desktop.

Remember just because you converted a package to .deb does not mean it will work on Ubuntu.

---

### Post by philinux on 2008-08-21
If you downloaded to the desktop just use

cd Desktop

first

---

### Post by kevmitch on 2008-08-21
It's probably a better idea to use fakeroot instead of sudo to run alien. fakeroot allows you to set the necessary ownership and permissions on things in the package without actually using super user privileges. You might have to install it
```
aptitude install fakeroot
```

It is unlikely however that that in itself will solve your problem. Try

```
fakeroot alien -v package_file.rpm
```

to get a more detailed idea of where this file not found message is coming from.

---

### Post by hvc123 on 2008-08-21
in your term type :-

cd Desktop

then your alien command.

remember you always start term in your home area i.e ~/

---

### Post by ibuclaw on 2008-08-21
What are you trying to install?

99% of the time, there is already a debian package for it...

Regards
Iain

---

### Post by jshaterian on 2008-08-21
Thanks Guys. Gonna try right now.

I'm trying install a specific version of scheme that my instructor has created for one of my classes.

---

### Post by Grateful Canuck on 2008-08-21
Here's what I use to convert a RPM file to a DEB file

alien --scripts *filename.rpm*

It always works for me. When you use the GDebi package installer, you can read the fine print on what the file contains and its intended purpose.

Hope this helps answer your question.

---

### Post by rockerphil on 2008-08-21
here's what works for me when converting .rpm to .deb format, but remember that you must CD to the directory that the .rpm file is in, as stated earlier. then simply run this

sudo alien -d -scripts <nameofrpmfile>

then once that's done simply install with dpkg

sudo dpkg -i <nameofpackage>

and that should install the debian package you converted from the .rpm package, hope it helps,

Phil

---

