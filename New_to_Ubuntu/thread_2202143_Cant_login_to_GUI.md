---
title: "Cant login to GUI"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by josh_eckert on 2014-01-27
I am having an issue with logging into my account on Xubuntu. I can log into the guest account without issues but when I log into my account the desktop image is displayed, the screen flashes black for a second and the desktop is displayed again only the cursor is then missing. I can get to the terminal ok using ctry alt F1.

I am guessing this is related to the screen resolution as this is a small netbook. It was previously working fine but was plugged into the TV prior to this issue which may have caused issues with the screen resolution. This is however just a guess.

Thanks In Advanced
Josh

---

### Post by joey8 on 2014-01-27
Reset the resolutiion with this command ```
xfconf-query -c displays -p /Default/Screen_0/Resolution -r
``` as per the man page here [http://docs.xfce.org/xfce/xfconf/xfconf-query](http://docs.xfce.org/xfce/xfconf/xfconf-query) or you can delete displays.xml located here ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml

---

