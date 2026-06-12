---
title: "Grub problem"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2013-03-06
Despite installing image updates as they have come along , grub still boots from an earlier kernel . If I delete this old version ,  grub says there is no system installed and halts .  I have tried update-grub and sure enough it lists the later  versions so I know they are installed . The only way I can get  the updated Lubuntu to run is to edit the grub file on each boot and direct it to the later kernel , which it then picks up and runsO.K.            Is there any way I can permanently edit the grub to boot from the latest version ?

---

### Post by schragge on 2013-03-06
Please open terminal (**Ctrl**+**Alt**+**t**) and post here the output of the following commands (you can copy them from here and paste into terminal, one by one).
```
grep ^GRUB_DEFAULT /etc/default/grub
```
```
sed -n '/header ###$/,//p' /boot/grub/grub.cfg
```
```
grep -o '^menuentry *"[^"]*"' /boot/grub/grub.cfg
```

---

### Post by ex-wirecutter on 2013-03-06
Errrrrr....... bearing in mind this is the absolute beginners forum , I'm afraid I am not advanced enough to do this .  Thanks for the reply anyway .

---

### Post by cortman on 2013-03-06
You can change the order in grub.cfg. See [here]("http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order").

But have you *ever* successfully booted with the new kernel?

---

### Post by schragge on 2013-03-06
Oh sorry. Open a terminal window by pressing **Ctrl**+**Alt**+**t** and enter there the commands shown above. Copy the output of each command and post here in forum between these tags:
[noparse]```


```[/noparse]

---

### Post by QIII on 2013-03-06
ex-wirecutter --

In our efforts to help, we often ask people to enter commands in the terminal and post back the results.  There are many reasons we might do that, and these are a few:


There are many different desktop environments and knowing how to navigate through all of them would be difficult.  The terminal, however, is common to all.

Some functionality is best or most quickly achieved by using the terminal.

It is sometimes the best way for you to provide diagnostic information that will be helpful in solving your issue.  This is the case here.


I asked people to use the command line when I helped on Windows forums, too.

Schragge has given you cut & paste commands to make it easier.  Please don't take it as a sneer at a "newbie".  He's making a genuine attempt to help by gathering some information.

Thanks.

---

### Post by ex-wirecutter on 2013-03-06
Thanks for the replies , they are enough to keep me going for a while .    As regards booting the latest version , as I say if I edit the opening grub file to boot from the latest version it does so no problem , I am using it now .   Its just a nuisance having to do this every time I switch on .
Thanks again , I am switching off now .

---

