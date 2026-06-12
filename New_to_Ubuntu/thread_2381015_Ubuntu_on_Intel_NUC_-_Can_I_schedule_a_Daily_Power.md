---
title: "Ubuntu on Intel NUC - Can I schedule a Daily Power-On/Start-Up"
date: 2017-12-25
forum: New to Ubuntu
---

### Post by mpspot on 2017-12-25
[COLOR=#3D3D3D][FONT=intel-clear]Hi All,[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear] [/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]I just purchased an Intel NUC to be used with Ubuntu 16.04,[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]I have found a gui utility to schedule the machine to turn off each night,[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]However, I am trying to find a way to get the machine to auto power-on/Start up each morning.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]I have tried the Power - Scheduled Wake Up options in the BIOS, however it doesn't work. It will not power on.[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]Is this technically possible, ie, schedule a Non-Windows OS on Intel NUC to power-own each morning from either the BIOS or a GUI App (I dont want to manually run a script each day).

[/FONT][/COLOR]
[COLOR=#3D3D3D][FONT=intel-clear]Thanks.[/FONT][/COLOR]

---

### Post by leunam12 on 2017-12-25
If the BIOS allows it, it should power on, I don't see why it wouldn't.

---

### Post by mpspot on 2017-12-26
[LEFT][COLOR=#222222][FONT=Verdana]HI,
I confirmed with others on Intel forum that there is an issue with current BIOS on the Intel NUCs,
The other person was previously able to Auto-Power on but now cant so im waiting on a response from Intel.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]However, do you know of any good GUI Utilities to either Power On/Shutdown or preferabbly both?
Thanks,
[/FONT][/COLOR][/LEFT]

---

### Post by mpspot on 2017-12-26
Update,
I received an email from the member on Intel Forums, advising he re-tested and after allowing the pc to restart instead of forcing off, the power up option worked, though he is using Win10,
I will test on Ubuntu tonight.

Though, as for the Auto Shutdown-Gui utility, can anyone recommend anything,
I tried qShutdown and while it works if you do a once off, when trying to schedule in a daily shutdown it didn't seemt o shutdown even though I selected the Auto countdown on start up etc options.

---

### Post by leunam12 on 2017-12-27
Schedule the shutdown with cron like this:```
sudo visudo
```
then go to the end of the file and type:```
yourusername ALL=(ALL) NOPASSWD: /sbin/poweroff
```
save and exit, then ```
crontab -e
``` 
To define the time you can provide concrete values for minute (m), hour (h), day of month (dom), month (mon),
and day of week (dow) or use '*' in those fields. Example: To shutdown everyday at 11:00PM
```
0 23 * * * sudo /sbin/poweroff
```

---

### Post by mpspot on 2017-12-27
Thanks. I ll give it a try. 
Do u know od any good gui methods incase i neef others to do.

---

### Post by leunam12 on 2017-12-27
I don't know any GUI methods, I googled "cron GUI" and some options came up, but I haven't tried any of them.

---

### Post by mpspot on 2017-12-27
Ok thanks

---

