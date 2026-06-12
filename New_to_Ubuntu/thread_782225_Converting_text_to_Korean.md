---
title: "Converting text to Korean?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by hopelessone on 2008-05-04
Hi,

is there a way to convert this?

> ÆÑ½º ¼Ö·ç¼Ç

it was in Korean...

Thanks

---

### Post by Delever on 2008-05-04
Can we have more information in what way this sequence of symbols was created?

---

### Post by Bigtime_Scrub on 2008-05-04
Try this:

It is AMI, an X input method server for Korean text input.

[http://packages.ubuntu.com/dapper/x11/ami](http://packages.ubuntu.com/dapper/x11/ami)

This site: [http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)

Will install a Chinese, Japanese, and Korean input guide on Ubuntu.

This is a quick way install Korean inputs: (make sure universe is enabled in /etc/apt/sources.list) 


Code:

sudo gedit /etc/apt/sources.list

double check if the universe and multiverse lines are uncommented (remove # in the front of the lines)

Code:

sudo apt-get update
sudo apt-get install scim uim scim-uim scim-gtk2-immodule scim-hangul scim-tables-ko

Do the following in a terminal one line at a time (copy and paste)
Code:

sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup

Then reboot and press CTRL-space to start inputting with Korean.

If I were you I'd go to System | Preferences | SCIM Input Method Setup and under IM Engines uncheck everything except Korean. Then figure out which korean input methods you don't use and uncheck those too.

---

### Post by hopelessone on 2008-05-04
> **Delever said:**
> Can we have more information in what way this sequence of symbols was created?


It was a scanner installed under wine...all Korean displays great except the menu items...

---

