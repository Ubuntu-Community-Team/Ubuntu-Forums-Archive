---
title: "Default Screen Resolution"
date: 2010-06-06
forum: Philippine Team
---

### Post by vaikz on 2010-06-06
Hi, I just finished install sa driver for my nvidia FX5200 and everything went fine.

question ay paano ba i-set sa xorg na ang screen resolution na gagamitin ko ay 1024x768? I'm using an old crt monitor.

Every start kasi lagi nalng 800x600, kahit palitan ko pa sa nvidia-settings, balik ulit siya sa dati.

kung gusto nyo sa xorg.conf ko, i will post, kung kailangan nyo.

---

### Post by nerdtron on 2010-06-06
Click mo ung "Save to X Configuration file" pagkatapos mong palitan ang screen resolution.
Kung may error na lumalabas try mo sundan ang steps sa thread na to: [http://ubuntuforums.org/showthread.php?t=1321327](http://ubuntuforums.org/showthread.php?t=1321327)

Ganito din kasi ang problem ko dati sa 9.10, sinundan ko lang ung nasa link. Goodluck!

---

### Post by vaikz on 2010-06-06
Thanks a lot nerdtron.
nasubukan ko na i-save sa x pro babalik ulit sa dati. subukan ko muna binigay mo link. babalik ako ulit kung ok ba o hindi.

---

### Post by loell on 2010-06-06
kailangan mo lang i-change ang settings with super user mode.

```
sudo nvidia-settings
```

---

### Post by vaikz on 2010-06-06
yup, i did open nvidia-settings w/ user mode. nothing changes. follow ko nga yung link na binigay ni nerdtron, same pa rin. And also found out na hindi lang ako ang may problema nito, meron then sa thread na yon. Pero wla ako nakita solusyon.

---

### Post by loell on 2010-06-07
are you sure? you said user mode, let me rephrase it nalang gumamit ka ng **sudo**?

or maybe you ran into this bug,

[http://www.uluga.ubuntuforums.org/showthread.php?t=1321327](http://www.uluga.ubuntuforums.org/showthread.php?t=1321327)

---

### Post by vaikz on 2010-06-07
im sorry, what i meant is using this > gksu nvidia-settings or super user mode. It did save the settings, nakikita ko sa xorg.conf. Pero wala pa rin. balik ulit sa dati.

Titingnan ko muna yung link na binigay mo.

Edit:
This is the same link that nerdtron gave.

---

### Post by aljoriz on 2010-06-07
SOLUTION: 

Go to Terminal 

type: sudo rm /etc/X11/xorg.conf

enter your sudo password

type: gksu nvidia-settings

enter password

click on X Server Settings adjust to your desired configuration
then click on Save to X configuration file 

on the empty box type:
/etc/X11/xorg.conf

press SAVE 

reboot and your resolution woes are fixed!!:guitar:

---

### Post by vaikz on 2010-06-07
Thanks for all the help guys.
@aljoriz & loell
I followed every step you've told me but unfortunately it did not fix my problem.
However, I was able to find a fix for this. All I do was change the resolution from the Preferences>Monitors. And the resolution stays even after a reboot. I was able to find this thread that help me.
[http://forums.linuxmint.com/viewtopic.php?f=59&t=19908#p138769]("http://forums.linuxmint.com/viewtopic.php?f=59&t=19908#p138769")

I will mark this as solve now.

---

