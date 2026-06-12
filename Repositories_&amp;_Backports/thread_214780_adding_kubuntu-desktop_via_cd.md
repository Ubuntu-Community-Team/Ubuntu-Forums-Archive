---
title: "adding kubuntu-desktop via cd"
date: 2006-07-13
forum: Repositories &amp; Backports
---

### Post by CRIKEY on 2006-07-13
hi

im trying to add kde to ubuntu by installing the kubuntu-desktop but im having trouble because i have dialup i have to do it with the cd (kubuntu cd) so i put the cd in my drive and it comes up with ubuntu cd found you can launch the repositry program now so i do that and reload it then search for kubuntu-desktop to my dismay nothing to do with kde is in there so i try using terminal with

apt-cdrom add
apt-get update
apt-get dist-upgrade / apt-get install kubuntu-desktop

and it dosent work shouldnt the kubuntu .debs at least show up in my repositry i checked sources.list and the cd is in there it says the exact same thing as the ubuntu one exept with kubuntu instead am i missing something? i have extra .debs in my repositry but they are just the extra ones from ubuntu (a bunch of stuff like linux-kernel-headers i dont think id ever use them) can anyone help me ive tried installing kubuntu and adding ubuntu to that but same thing happens btw they are both fresh installs thanks in advance for any help

---

### Post by Radioactive Fellow on 2006-07-13
If you have installed Ubuntu and want to add KDE desktop do the following:

1. Insert [COLOR="DarkOrange"]Kubuntu[/COLOR] Cd on your Cd rom drive.
2. sudo apt-cdrom add
3. sudo apt-get install kubuntu-desktop
4. Restart your session and choose KDE

If you have installed Kubuntu and want to add Gnome Desktop do the following:

1. Insert [COLOR="DarkOrange"]Ubuntu[/COLOR] Cd on your Cd rom drive.
2. sudo apt-cdrom add
3. sudo apt-get install ubuntu-desktop
4. Restart your session and choose Gnome

---

### Post by CRIKEY on 2006-07-13
thats exactly what i have been doing and then i get the error something like
no such package as kubuntu-desktop

---

### Post by az on 2006-07-13
Are you doing this with the kubuntu Destop cd?  You would need the alternate cd for that.

---

### Post by CRIKEY on 2006-07-14
ahhhh that must be it is there any way i can get the required packages out of the desktop cd then? as downloading is really not a option

---

