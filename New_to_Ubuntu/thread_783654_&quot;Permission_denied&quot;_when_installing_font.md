---
title: "&quot;Permission denied&quot; when installing fonts"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by sellswor on 2008-05-05
When I try to drag a font (.ttf) into any of the font folders, I get a "permission denied" notice.  I'm pretty sure I am logged in as a user who has administrative permissions so why would this be?  Basically, how do I install fonts in Ubuntu?

---

### Post by PeterJS on 2008-05-05
> **sellswor said:**
> When I try to drag a font (.ttf) into any of the font folders, I get a "permission denied" notice.  I'm pretty sure I am logged in as a user who has administrative permissions so why would this be?  Basically, how do I install fonts in Ubuntu?

You many be logged in as an administrative user, but you only have administrative rights when you explicitly request them with sudo.*

If you want to install fonts system wide fonts, ie in /usr/share/fonts/truetype/, then you can launch the file browser with administrative privileges using:
```

gksudo nautilus /usr/share/fonts/truetype/

```
In the run dialog (alt+f2).

Or if you're the only user on the machine, a much easier option would be to install the fonts for only your user in $HOME/.fonts/. The dot in .fonts indicates that it's a hidden folder so you'll need to press ctrl+h to un-hide it.

*[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cartisdm on 2008-05-05
The above solution works (and is probably your better option) but for future reference just open nautilus with your terminal as

```
sudo nautilus
```

and then you'll be able to do whatever you need

---

### Post by Tatty on 2008-05-05
Your account has the rights to get "administrator" powers, but you do not have them switched on all the time.  This is a security measure in linux and I highly recommend you read this.[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

To achieve what you want to achieve you need to open a nautilus (file browser) window and give it superuser powers.  To do this open a terminal (Applicaitons->Accessories->Terminal)  then type: ```
gksu nautilus
```

A file browser will then open with the permissions to write to the folder you are trying to use.

---

### Post by glennric on 2008-05-05
> **cartisdm said:**
> The above solution works (and is probably your better option) but for future reference just open nautilus with your terminal as

```
sudo nautilus
```

and then you'll be able to do whatever you need

You should always use gksu for graphical applications like nautilus for proper security.

---

### Post by SunnyRabbiera on 2008-05-05
currently there is no easy way to do this on hardy thanks to changes made to the UI, there used to be a function to easily open the fonts directory in ubuntu but no more... for now.
Currently the best solution I have is to open a terminal and type in sudo nautilus and make your way to usr/share/fonts and copy your desired fonts into any one of the folders listed in the directory...

Why the easy font install feature was removed? I dont know, but it was a stupid move on the gnome development team (gnome is the UI so you know.)

---

### Post by glennric on 2008-05-05
The easiest way to install fonts is to copy them into the directory ~/.fonts
You have permission for that.  The fonts will only be available for your user though.

---

### Post by sellswor on 2008-05-06
Wow!  I'm impressed with all the responses.  Thank you all.  Problem fixed.  I guess I just need to read up on some basics instead of doing things by trial and error like I normally do.

---

### Post by PeterJS on 2008-05-06
Nah, Trial and error is the way to go. Without trial and error you won't know what to read about. And don't be afaird to ask, it gives the Beginners team and the Unanswered posts team something to do.

---

