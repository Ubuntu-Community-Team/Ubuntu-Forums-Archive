---
title: "Having problem with launchers in 11.10"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by siriusbg on 2011-12-18
Hi. I installed the gnome-panel package in order to create a desktop screenshot. After that I type the ```
gnome-desktop-item-edit ~/Desktop/ --create-new
``` command and I come up with this 
```
gnome-desktop-item-edit: file:///home/user/Desktop does not have a .desktop or .directory suffix

```
Any hints?

---

### Post by Jacobonbuntu on 2011-12-18
I believe you forget to rename the title "Desktop" in the command, to the name of the "Desktop" in your language (I see you're from Sofia) your. I tried, and I get the same message if I do not change it. :)

---

### Post by siriusbg on 2011-12-18
Thank you very much! I didn't even notice that there is another name (in Bulgarian) instead of the usual "desktop". Now it works without any problems!

---

### Post by Jacobonbuntu on 2011-12-18
...glad it worked!
have a good time,
Jacob

---

### Post by yoramdavid on 2011-12-24
> **Jacobonbuntu said:**
> I believe you forget to rename the title "Desktop" in the command, to the name of the "Desktop" in your language (I see you're from Sofia) your. I tried, and I get the same message if I do not change it. :)


If I may, I have the exact same problem.
So I tried renaming "Desktop" with the translated name in Portuguese... but it did not work. That is, I think, because that "Desktop" in Portuguese is composed of 3 separate words, and has an accent "Área de Trabalho".
And it is trying to deal with 3 separate names instead of one... how do I deal with spaces in names? And with accents?

There is the error returned:

```
gnome-desktop-item-edit --create-new ~/Área de trabalho
gnome-desktop-item-edit: file:///home/yoram/%C3%81rea does not have a .desktop or .directory suffix
gnome-desktop-item-edit: file:///home/yoram/de does not have a .desktop or .directory suffix
gnome-desktop-item-edit: file:///home/yoram/trabalho does not have a .desktop or .directory suffix


```

Thanks for any help.

Yoram

---

### Post by Jacobonbuntu on 2011-12-24
....concerning the spaces; it should work if you put the name with spaces between "" in your command, so that is: "Área de Trabalho". I hope the special accent is no problem, but I believe not....

---

### Post by yoramdavid on 2011-12-24
> **Jacobonbuntu said:**
> ....concerning the spaces; it should work if you put the name with spaces between "" in your command, so that is: "Área de Trabalho". I hope the special accent is no problem, but I believe not....

Thank you Jacobonbuntu for the (qiuck) reply!

That works now, the accent is not an issue then.

Regards,

Yoram

---

### Post by Jacobonbuntu on 2011-12-24
> **yoramdavid said:**
> Thank you Jacobonbuntu for the (qiuck) reply!

That works now, the accent is not an issue then.

Regards,

Yoram


you're welcome!
have a good time,
Jacob

---

