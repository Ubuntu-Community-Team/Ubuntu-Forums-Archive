---
title: "Custom welcome screen"
date: 2009-06-01
forum: Programming Talk
---

### Post by saliljain on 2009-06-01
Hello everyone!
First of all, I'm relatively new to linux, so I'm kinda confused. I have customised a LiveCD based on Ubuntu 9.04 , without XWindows, now I have a PHP-CLI script called starts.php , I want this script to be run as soon as the system starts up every time. Also I want to run certain .sh scripts automatically as soon as the user gets logged on, please tell me how can i get this done?

Thanks in advance :)

~Salil

---

### Post by MichaelSammels on 2009-06-01
Try looking here:

System -> Preferences -> Startup Applications

Be careful. The script may require sudo privelages before it can be run. Hope this helps, though.

---

### Post by lisati on 2009-06-01
Another option is to look at System->Administration->Login Window which can let you do some customizations relating to what happens when the Login Window is displayed.

---

### Post by saliljain on 2009-06-01
Thanks for the prompt response,

But I dont have XWindows Installed, no Gnome or KDE...
can you tell me the packages that i have to install to get GNome (minimal) running? 
i tried apt-get install --no-install-recommends gnome it still wants about 450+Megs.. i cannot afford that much!
Please help :)

Thanks again
~Salil

---

