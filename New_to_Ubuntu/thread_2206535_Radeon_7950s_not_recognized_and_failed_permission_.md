---
title: "Radeon 7950s not recognized and failed permission to save /etc/X11/xorg.conf"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by ndunkz on 2014-02-19
[COLOR=#333333][FONT=UbuntuRegular]I have a gigabyte UD5 MB, and am running between 3-5 Sapphire, radeon 7950 GPUs off an AMD, CPU and 2 x corsair 750 RM PSUs -[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have some questions with this configuration and hoping someone here can help:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]1) what command is meant to be used when introducing a GPU, or multiple GPUs to Ubuntu? When I try and do this it wont recognize them, or the recognition is inconsistent.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]2) After reading a variety of forums, with many results, I tried different commands.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Atconfig --adapter=all --intitial -f[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Atconfig --adapter=all --intitial[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Atconfig --intitial[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The only command that shows the true amount of GPUs is Atconfig --adapter=all --intitial but when I do this command I get a failure message saying 'Writing to '/etc/X11/xorg.conf failed. Permission denied. However, if I run Atconfig --intitial, it recognizes only one GPU, but will update and save /etc/X11/xorg.conf correctly.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The question with regard to the above information is a) How can I delete ALL versions of /etc/X11/xorg.conf that have been written, and b) how can I rewrite /etc/X11/xorg.conf to recognize all GPUs in the machine currently?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thank you![/FONT][/COLOR]

---

### Post by QIII on 2014-02-19
Hi!

First off, you must elevate your privileges by using "sudo" or you will not be able to alter xorg.conf.

Second, check your spelling.  "atconfig" <> "aticonfig" and "intitial" <> "initial".

Third, aticonfig has been deprecated and the command to use is "amdconfig".

So:

```
sudo amdconfig --adapter=all --initial
```

amdconfig will create a backup of (rename) any xorg.conf it encounters, so there is no need to worry about removing what already exists unless you want to clean them up later.

Let us know if that works.

Cheers!

---

### Post by ndunkz on 2014-02-19
YES!  I got recognition of all three GPUs - thank you!!! Such a relief to see them all appear! THANK YOU!  Also, my command line spelling was better than the forum post!

---

