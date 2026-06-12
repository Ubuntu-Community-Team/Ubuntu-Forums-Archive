---
title: "Screen is dim when running on battery and Fan is always running . please help"
date: 2015-11-07
forum: New to Ubuntu
---

### Post by switchex on 2015-11-07
So, new to Ubuntu and new instal of 14.04 with 2  issues i hope you guys can help.

Firstly, my screen is full bright only when plugged in.  Once unplugged , the screen goes dim.  The dim buttons (function key + f9/f10) on the laptop don't seem to be working .

Secondly, the fan, regardless on power or battery is always running! and the laptop, overall, seems to be running hot.

any solutions to these 2 issues?

Thanks all.

---

### Post by TXLightMan on 2015-11-08
[LIST=1]
[*]on your laptop, go to System Settings > Brightness And Lock and then uncheck "Dim screen to save power" 
[*]for there's few solution that reported to work, it's vary depend on the system i guess. the most reported to work, try to add this line to your /etc/default/grub

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux" 
```

or try** mikewhatever** solution,
> try adding acpi_backlight=vendor as a boot option. To do that, open a terminal window, and run  gksu gedit /etc/default/grub

Locate this line: GRUB_CMDLINE_LINUX="".

Edit it to look like this: GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

Save the file, then, in a terminal, run sudo update-grub.
Reboot, and check if the brightness keys work. 
Source: [URL="http://askubuntu.com/questions/266046/brightness-function-keys-not-working"]http://askubuntu.com/questions/266046/brightness-function-keys-not-working

[/URL] 
[*]Check system monitor, if your laptop in heavy usage state i think it's normal. unless if it's always happen even when you're not doing anything. if not, Try to install latest update from software updater & propriate driver, most likely it was an issue with your kernel. 
[/LIST]

---

