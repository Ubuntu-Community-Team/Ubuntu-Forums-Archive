---
title: "[SOLVED] How to change computer name?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by ppttpp on 2008-06-04
How do I change computer name?

I remember when I was installing kubuntu that the wizard asked me what name you will give your computer (for network purposes) and now I want to change it because I found out there is a pc with a duplicate name on the same LAN.

BTW I am on KDE 4.

---

### Post by neurostu on 2008-06-04
Manually configure your network settings,
Select the General tab
then change the "Host Name"

---

### Post by FlyingPenguin542 on 2008-06-04
> **neurostu said:**
> Manually configure your network settings,
Select the General tab
then change the "Host Name"

...and then save your settings as a profile :)

---

### Post by Prospero2006 on 2008-06-04
The file /etc/hostname

defines this parameter.

---

### Post by ppttpp on 2008-06-04
> **neurostu said:**
> Manually configure your network settings,
Select the General tab
then change the "Host Name"

Beware I am on KDE 4 and there are only

System Settings --> Network settings

and this does not have a General tab neither a Host name

where do I find what you are referring to?

---

### Post by ppttpp on 2008-06-04
> **Prospero2006 said:**
> The file /etc/hostname

defines this parameter.

I will check this thanks .. but if Linux does not have a GUI for setting this then we are in trouble. ;)

---

### Post by Prospero2006 on 2008-06-04
Would you count a text editor like kate as a gui?

```

kate /etc/hostname

```

Change the name.

Save File

---

### Post by ginestre on 2008-06-04
My 3 Feisty computers are all  properly labelled in their respective   hostname files- yet neither the router, nor the Mac nor the  Feisty PCs pick up any of the names. I just get the IP number + a label saying UNKNOWN. Yet the mac and the router both pick each others names up, and both also pick up the name of the linksys slug fileserver. What else should I be checking, so that I can have friendlier names rather than UNKNOWN + IP denominating the ubuntu PCs??

TIA

---

### Post by ppttpp on 2008-06-04
> **Prospero2006 said:**
> Would you count a text editor like kate as a gui?

```

kate /etc/hostname

```

Change the name.

Save File

Thanks I will try that :)

But just the mere ability of doing that via the system settings is not available feels cumbersome to linux newcomers!

Then the newcomer opens the file browser searching for that file..
navigates to it ..
opens the file with Kate ..
clicks save ..
but discovers that he has no permission ..
closes the browser .. goes to run ..
types in kdesudo kate or konqueror or whatever ..
edits the file successfully!!

Yes it is a GUI!!! :---)

---

### Post by The Cog on 2008-06-04
[COLOR="Red"][SIZE="5"]**Noooooooo!!!**[/SIZE][/COLOR]

Don't just change /etc/hostname or you will not ba ble to sudo any more. You **must** change /etc/hosts to match at the same time (the 127.0.0.1 entry). Use the command ```
gksudo /etc/hostname /etc/hosts
```
o better still use the GUI tools that know they must change both files.

---

### Post by Prospero2006 on 2008-06-04
dang, I forgot. Just changing hostname will mess things up.


Sorry!

---

