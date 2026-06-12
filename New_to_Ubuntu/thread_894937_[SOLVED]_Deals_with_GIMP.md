---
title: "[SOLVED] Deals with GIMP"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-08-19
Ya, I use to run windows and I had gimp on it. I would download photoshop brushes and put them in the brush folder of Gimps. Now on linux, I cant paste the brush files in the brush folder for gimp.

---

### Post by halitech on 2008-08-19
open Nautilus, press Ctrl - H on your keyboard (or go View - Show Hidden files) and look for a folder called .gimp-2.2(or 2.4 depending on your version) and then you will have folders in there for brushes, scripts, plugings, etc.

---

### Post by deadlySniper on 2008-08-19
I know where the folder is, I cant add the photoshop brushes into the Gimps brush folder. Also I cant seem to be able to change the permissions either

---

### Post by halitech on 2008-08-19
you don't need to change permissions, its in your /home folder so you have full read/write permissions

---

### Post by deadlySniper on 2008-08-19
The folder is located here

/usr/share/gimp/2.0/brushes

and I cant paste the files in there because the permissions dont allow me to

---

### Post by egalvan on 2008-08-19
> **deadlySniper said:**
> The folder is located here

/usr/share/gimp/2.0/brushes

and I cant paste the files in there because the permissions dont allow me to

Same on my system, so in a terminal use:

```


gksudo nautilus

```


this works for me under gnome
under kde, I have a 'rooted thunar' shortcut

ErnestG

---

### Post by deadlySniper on 2008-08-19
ok I got nautilus, what do I do now

---

### Post by halitech on 2008-08-19
if you are a single user (or the only one using gimp) just create a folder called .gimp-2.4 (or whatever version you are using and yes, the . in front of gimp is important) in your home folder (if its not there by default which would surprise me) and then put your scripts and brushes in the folders inside there.

---

### Post by deadlySniper on 2008-08-19
ok I added the files in there and they arent showing up on GIMP. I added brushes

---

### Post by halitech on 2008-08-19
go to File - Preferences - and then check the folders and see if /home/(username)/.gimp-2.4/brushes(scripts, etc) is listed, if not you may have to add them

---

### Post by deadlySniper on 2008-08-19
in nautilaus

---

### Post by deadlySniper on 2008-08-19
sweet its workin. Thanks you

---

### Post by halitech on 2008-08-19
no, in GIMP

---

### Post by paulmerchant on 2008-08-19
Be careful with "gksudo nautilus" as an alternative to customizing gimp in your user folder.

I'm lazy and "gksudo nautilus" all the time. The worse thing is that sometimes I use "gksudo nautilus" to delete custom installs and stuff, but then the files just end up living forever in /root/.local/share/Trash and they never show up in any trash can. And there are probably security issues and wacked things like settings being saved as root when you use "gksudo nautilus".

For Gimp brushes, just follow the instructions someone else gave:

Go to Places | Home Folder. Press Ctrl+H to show hidden folders, and then find your [home folder]/.gimp-2.4/brushes folder and throw in your brushes.

The other advantage to using your home folder rather than the /usr/share is that things like backups and software updates are easier (backups usually grab home folder and not usr/share, etc.).

On the other hand, "gksudo nautilus" can brute force almost anything you want to do.

---

### Post by egalvan on 2008-08-19
> **halitech said:**
>  just create a folder called .gimp-2.4 (or whatever version you are using and yes, the . in front of gimp is important) in your home folder (**if its not there by default which would surprise me)** and then put your scripts and brushes in the folders inside there.

Well surprise, surprise! :) It's not in my home either,

but it soon will be... you make good points.

Thanks!

:popcorn:

---

### Post by halitech on 2008-08-19
thats strange cause I have the .gimp-2.4 folder in my home folder and I didn't create it  so not sure why everyone else doesn't seem to have it. 

and as paul said, backups are usually of the /home folder so when you do backups, all those brusehs will be saved as well :)

---

