---
title: "Synaptic Package Managerwant will open from the command line but not Gnome?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by glb48 on 2008-06-14
Synaptic Package Managerwant work click open and dosent do anything

---

### Post by the_doc on 2008-06-14
Can you open it from the command line?

---

### Post by rraj.be on 2008-06-14
Please give me some more info like what is actually happening and where it happened.

Befor that try this in terminal.

```
sudo apt-get install wine.
```

and post its contents to me.

---

### Post by glb48 on 2008-06-14
how do you open from comand line

---

### Post by rraj.be on 2008-06-14
```
Applications-->Accessories-->Terminal
```

and type 


```
sudo apt-get install wine
```

---

### Post by glb48 on 2008-06-14
Couldn't find package wine.

---

### Post by the_doc on 2008-06-14
Type..

sudo synaptic 

..from the command line and see if you can open Synaptic that way.

---

### Post by rraj.be on 2008-06-14
Then there is no problem with your synaptic package manager.

This may sometime be like that.

Just run an update and it should clear it.


Run this.

```
sudo apt-get update
```

---

### Post by glb48 on 2008-06-14
yes it opens what do i do now

---

### Post by Xerp on 2008-06-14
Cool. Now it opens you can manage packages :) I'd suggest installing something you find fun or like doing. For me, that is music and pictures!

---

### Post by glb48 on 2008-06-14
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by the_doc on 2008-06-14
What other apps do you have open?

---

### Post by glb48 on 2008-06-14
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by glb48 on 2008-06-14
terminal&foxfire

---

### Post by glb48 on 2008-06-14
Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

---

### Post by rraj.be on 2008-06-14
You have opened   apt and also some other pacake manager like SYNAPTIC.

You can open only one such package managers at a time.

Try closing all and open only one terminal.

---

### Post by glb48 on 2008-06-14
that worked

---

### Post by glb48 on 2008-06-14
thank you

---

### Post by the_doc on 2008-06-14
Yes, close everything and try opening it again.

---

### Post by glb48 on 2008-06-14
still want open

---

### Post by rraj.be on 2008-06-14
Had you run update.

```
sudo apt-get update.

```

If so then try this

```
sudo synaptic
```

---

### Post by the_doc on 2008-06-14
So it'll open from the command line but not Gnome?

---

### Post by glb48 on 2008-06-14
yes

---

### Post by glb48 on 2008-06-14
yes it'll open from the command line but not Gnome?

---

### Post by aysiu on 2008-06-14
Please stop telling people to use *sudo synaptic*. *sudo* is for terminal applications. *gksudo* or *kdesu* should be used for graphical applications. For example ```
gksudo synaptic
``` For more details, read [this](http://www.psychocats.net/ubuntu/graphicalsudo).

---

### Post by glb48 on 2008-06-14
Synaptic Package Managerwant
 will open from the command line but not Gnome?

---

### Post by glb48 on 2008-06-14
Synaptic Package Managerwant
will open from the command line but not Gnome?

---

### Post by glb48 on 2008-06-14
Synaptic Package Managerwant
will open from the command line but not Gnome?

---

### Post by wormser on 2008-06-14
Which command are you using?  Are there any error messages?

P.S.  Please use a descriptive title.  It helps when searching.

---

### Post by glb48 on 2008-06-14
i double click on Synaptic Package Managerwant but it want open

---

### Post by K.Mandla on 2008-06-14
Similar threads merged.

---

### Post by glb48 on 2008-06-14
help please

---

### Post by glb48 on 2008-06-14
what

---

### Post by wormser on 2008-06-14
> **glb48 said:**
> help please

We need more information.  We only know what you tell us.  Do Not bump the thread every couple minutes.

What is the command you are using?  Give us more details.

---

### Post by ad_267 on 2008-06-14
What happens if you run

```
gksudo synaptic
```

---

### Post by glb48 on 2008-06-14
dosent do any thing

---

### Post by ad_267 on 2008-06-14
Are you running it from the menu? If so can you right click on the menu and select edit menus. Browse to find the launcher for Synaptic Package Manager. Right click on this and select properties and post what it says here.

What command are you using to open it?

---

### Post by ad_267 on 2008-06-14
If you run the command "groups" does it say admin?

---

### Post by glb48 on 2008-06-14
type application, command gksu /usr/sbin/synaptic , comment install,remove,upgrade

---

### Post by ad_267 on 2008-06-14
OK this thread keeps growing from the top not the bottom haha. It would have been useful if you only had ONE thread.

So basically:

```
sudo synaptic
```
works.

But:
```
gksudo synaptic
```
Doesn't?

---

### Post by aysiu on 2008-06-14
> **glb48 said:**
> dosent do any thing
Can you be more specific?

In other words, does it just hang and not go to the next line? Or does it actually go to the next line?

```
username@ubuntu:~$ gksudo synaptic
username@ubuntu:~$
``` for example... is that what you see?

Can you post a screenshot?

---

### Post by glb48 on 2008-06-14
command "groups what are they

---

### Post by glb48 on 2008-06-14
username-desktop:~$ gksudo synaptic

---

### Post by aysiu on 2008-06-14
> **glb48 said:**
> username-desktop:~$ gksudo synaptic
So it doesn't go to the next line? It just hangs on that command?

No error message either?

---

### Post by glb48 on 2008-06-14
nothing else

---

### Post by ad_267 on 2008-06-14
But if you run "sudo synaptic" it does work?

---

### Post by glb48 on 2008-06-14
username
-desktop:~$ ~$ gksudo synaptic
bash: ~$: command not found
username desktop:~$

---

### Post by glb48 on 2008-06-14
no

---

