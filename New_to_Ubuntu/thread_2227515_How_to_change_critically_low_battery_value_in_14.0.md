---
title: "How to change critically low battery value in 14.04. (Unity)"
date: 2014-06-02
forum: New to Ubuntu
---

### Post by Beggo on 2014-06-02
Hey,
i would like to change this value to 9%, because my laptop turns off immediately at 7%. The default value (unknown) is to low.
Beggo

---

### Post by philinux on 2014-06-02
[http://askubuntu.com/questions/92794/how-to-change-critically-low-battery-value](http://askubuntu.com/questions/92794/how-to-change-critically-low-battery-value)

May still work in 14.04. I just watch the percentage on the indicator area.

---

### Post by Beggo on 2014-06-02
Hey, to set the value to 9 % I have tocopy/paste the following command in the terminal? Thats all? **         gsettings set org.gnome.settings-daemon.plugins.power percentage-critical 9**           What do I have to make, if I want to see, which critical value the system has saved?     Beggo

---

### Post by mcduck on 2014-06-02
> **Beggo said:**
> Hey, to set the value to 9 % I have tocopy/paste the following command in the terminal? Thats all? **         gsettings set org.gnome.settings-daemon.plugins.power percentage-critical 9**           What do I have to make, if I want to see, which critical value the system has saved?     Beggo
This should do it:
```
gsettings get org.gnome.settings-daemon.plugins.power percentage-critical
```
...or install *dconf-tools* and then use dconf-editor to check/change various settings like this.

---

### Post by Beggo on 2014-06-02
Hey,
thank you for the path ...
dconf-editor did it!!!
Thank you

but while starting dconf-editor the following message did appear:
**** (dconf-editor:5251): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends**

**** (dconf-editor:5251): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends**

... do I have to worry about it?

---

### Post by mcduck on 2014-06-02
I'm getting the same message, but since it's just a warning (and everything seems to work fine, at least based on my experience), it probably isn't anything to worry about.

---

### Post by philinux on 2014-06-03
Default seems to be set to 3%

---

