---
title: "&quot;Opening ... &quot; tab every time I open something."
date: 2012-03-05
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2012-03-05
Everytime I opening anything, I get tab in the bottom bar telling me that its opening.  Is there a way to stop this, its annoying and it clutters up my bar. 11.10

---

### Post by Sonsum on 2012-03-05
What Window Manager are you using? Unity?

---

### Post by DarrenMR415 on 2012-03-05
Metacity...?

---

### Post by Sonsum on 2012-03-06
> **DarrenMR415 said:**
> Metacity...?

I meant more along the lines of desktop environment. All of the ones I can think of for standard Ubuntu are Unity, Gnome3-Classic, Gnome-Shell, Gnome-Shell w/ MGSE, and Cinnamon.

It sounds like you're talking about something with a bottom panel... So Gnome3-Classic? (I believe that that one allows a separate window manager, like metacity or compiz.)

---

### Post by mc4man on 2012-03-06
It's caused by this line that's found in the .desktops of many. (most) apps - 
> StartupNotify=true

It's been known starting with  gnome3 to cause the notify in the gnome classic panel to hang around longer than it should (isn't really needed in the 1st. place

---

### Post by DarrenMR415 on 2012-03-06
So is there a way to stop it?

---

### Post by mc4man on 2012-03-06
> **DarrenMR415 said:**
> So is there a way to stop it?
Well you could edit any of the .desktops of apps you use & set that line to false
Could be time consuming & updates to individual packages (or newly installed) would possibly revert to true

To do in bulk you could run this command (& repeat after any updated or freshly installed
don't worry about message "sed: couldn't edit /usr/share/applications/screensavers: not a regular file"
Copy & paste the _complete command _into a terminal

 ```
for i in $( ls /usr/share/applications ); do sudo sed 's/StartupNotify=true/StartupNotify=false/g' -i /usr/share/applications/$i; done
```

If you think it's causing you any issues then to revert

```
 for i in $( ls /usr/share/applications ); do sudo sed 's/StartupNotify=false/StartupNotify=true/g' -i /usr/share/applications/$i; done

```

Or if any issue in just some apps then locate that apps .desktop in /usr/share/applications, open in a root text editor and set back to true

---

