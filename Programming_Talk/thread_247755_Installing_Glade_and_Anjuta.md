---
title: "Installing Glade and Anjuta"
date: 2006-08-31
forum: Programming Talk
---

### Post by Andy McCall on 2006-08-31
Hi Folks,

I have basically done a clean install of Ubuntu 6.06 and added a few other packages like Blender and ndiswrapper.

I don't really know how to use Ubuntu or its package management system yet, but I have noticed that there are multiple packages for Glade and Anjuta within Synaptic.

Do I simply select Glade and Anjuta with the Ubuntu symbols next to them from within Synaptic and the package managment will install the latest stable version along with the compilers needed?

Will Ubuntu integrate Glade and Anjuta so I can use Glade from within Anjuta so i won't have to do any other set-up after the installation?

Thanks,

Andy McCall

---

### Post by skymt on 2006-08-31
Yes, and yes. :D

EDIT: Compilers, no. You need to install build-essential for them.

---

### Post by Andy McCall on 2006-08-31
Thanks for the reply.

I installed Glade and Anjuta and build-essentials and they all installed and seem to run OK. However, when I complete the application wizard from within Anjuta I get a message:

Auto generating the Project: TemperatureConverter ...
./autogen.sh

**Error**: You must have `glib' installed.
You can get it from: [ftp://ftp.gtk.org/pub/gtk](ftp://ftp.gtk.org/pub/gtk)
Completed ... unsuccessful
Total time taken: 1 secs

This doesn't seem right to me!  I have done a quick Google, but nothing seems to jump out as a solution to me.

Can anyone help?

Thanks,

Andy McCall

---

### Post by TeleTommy on 2006-09-06
I have the same problem.. anybody knows what's going wrong?

---

### Post by skymt on 2006-09-06
Try this in a terminal:```
sudo aptitude install libglib2.0-dev libgtk2.0-dev
```

---

### Post by thialme on 2006-09-10
> **skymt said:**
> Try this in a terminal:```
sudo aptitude install libglib2.0-dev libgtk2.0-dev
```


I had the same problem the others, and I was glad to find the solution. So, in order that everybody knows, it works.

Thanks for your help. :mrgreen:

---

### Post by darkfame on 2007-05-01
Thanks, fixed my problem too. :)

---

### Post by vudoo_5 on 2007-05-26
> **darkfame said:**
> Thanks, fixed my problem too. :)

and mine, thanks

---

### Post by Black Spider on 2010-10-09
> **skymt said:**
> Try this in a terminal:```
sudo aptitude install libglib2.0-dev libgtk2.0-dev
```

Thanks, it works

---

### Post by Hicker on 2011-03-11
Works for me... thanks

---

### Post by josealejandro93 on 2011-07-18
Also worked for me. Thank You very much :)

---

