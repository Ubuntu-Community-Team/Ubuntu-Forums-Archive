---
title: "[SOLVED] Just a few 'Noob' questions..."
date: 2008-09-11
forum: New to Ubuntu
---

### Post by I wanted to leave on 2008-09-11
Hello everyone,
Have been looking at the site for a week or so & congratulations to all here for a great forum, with great info & genuine respondents.
I have been using different distro's for about a year now but Ubuntu in my opinion (8.04.1 Hardy) is the ants pants at the moment...
I have a couple of questions though if anyone can assist;
I seem to have lost the right click function of my mouse only on the desktop, though it works on the panels & everywhere else. ?
Having got things just as I like, I tried to create a custom iso via Remastersys, which seemed to go well until 99% when everything just froze?
All hardware is reliable, have compiz-emerald up and running (Hardy) and no issues.
Can anybody shed any light?
My thanks in advance

---

### Post by Gannon8 on 2008-09-11
Is there any icons on the desktop? Try going into the /home/*username*/Desktop folder and make an empty file. If it does not appear in the desktop, there is a chance that Nautilus has not been started. Type in nautilus in the terminal.

As for the ISO program, it is most likely the program's fault. Try a different program.

---

### Post by forger on 2008-09-11
> I seem to have lost the right click function of my mouse only on the desktop, though it works on the panels & everywhere else. ?

Try execute this in Applications > Accessories > Terminal:
```
killall -9 nautilus
nautilus
```

>Having got things just as I like, I tried to create a custom iso via Remastersys, which seemed to go well until 99% when everything just froze?

You might have a problem with free temporary space, post the reply of this command:
```
df -h
```

---

### Post by billgoldberg on 2008-09-11
If you are using conky it could be that it has disabled right clicking on the desktop.

The same is true if you are using the compiz fusion plugin called wallpapers.

---

### Post by I wanted to leave on 2008-09-11
Wow fast responses.. thank you!

Ok I got an error, something about Gnome-manager-desktop not found or started, sorry it was all so quick, what with wallpaper disappearing etc but alls good with the mouse now, back to normal.

Output as follows

bra10n@bra10n-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             7.4G  2.5G  4.6G  35% /
varrun                502M  108K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   44K  502M   1% /dev
devshm                502M   64K  502M   1% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2              29G  1.5G   26G   6% /home
gvfs-fuse-daemon      7.4G  2.5G  4.6G  35% /home/bra10n/.gvfs

---

