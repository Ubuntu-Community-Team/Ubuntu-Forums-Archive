---
title: "Can't find sensors-applet"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Pacopag on 2008-06-29
Hi.  I just installed sensors-applet using Synaptic, but I can't seem to find it in any of the menus.  Does someone know where I can find it?

Thanks,

---

### Post by ad_267 on 2008-06-29
Right click on a panel and select "Add to panel" and select the sensors applet from there.

---

### Post by Pacopag on 2008-06-29
What do you mean by "panel"?  Sorry, I'm a goof.

---

### Post by Pacopag on 2008-06-29
I tried doing that in the bar across the top, but I don't see sensors-applet (or anything to that effect) in the list.

---

### Post by Pacopag on 2008-06-29
Sorry.  I'm a real goof.  I did find it.
Is there a way to get it in the menus at the top, for example in Applications>System Tools?

---

### Post by ad_267 on 2008-06-29
It's called hardware sensors monitor.

---

### Post by Pacopag on 2008-06-29
Ok.  I've got it in my top panel now, but when I click on it, nothing happens.  It is just reading the cpu temperature.  Can it read anything else?  e.g. fan speed, etc.

---

### Post by ad_267 on 2008-06-29
> **Pacopag said:**
> Sorry.  I'm a real goof.  I did find it.
Is there a way to get it in the menus at the top, for example in Applications>System Tools?

I don't think you can. An applet is something that is put on a panel. There is probably a better application that can do this. Just having a search of packages it looks like xsensors could do this.

To get it to read other stuff right click on it and select properties. What you are able to monitor depends on your hardware.

---

### Post by Pacopag on 2008-06-29
I installed xsensors, but when I try to run it, nothing happens.  But oh well, I'm happy enough for now with just the cpu temp.  Thanks, for your help.

---

### Post by ad_267 on 2008-06-29
> **Pacopag said:**
> I installed xsensors, but when I try to run it, nothing happens.  But oh well, I'm happy enough for now with just the cpu temp.  Thanks, for your help.

Ok yeah I just tried to run xsensors and got this message:
```
Error opening config file: /etc/sensors.conf
Use -c option to specify location of lm_sensors configuration file.

```

If you would rather use xsensors you will probably need to configure it. There might be some threads somewhere on how to do this.

Could you only get the cpu temp in the applet properties? Like I said it depends on your hardware but you should be able to get more than that.

---

### Post by ad_267 on 2008-06-29
I think I edited my post before after reading your reply about only getting the cpu temp so you might not have seen that.

> To get it to read other stuff right click on it and select properties. What you are able to monitor depends on your hardware.

---

### Post by philinux on 2008-06-29
[http://ge.ubuntuforums.com/showthread.php?t=833321](http://ge.ubuntuforums.com/showthread.php?t=833321)

It needs to detect your sensors first.

---

### Post by drs305 on 2008-06-29
You might be happier with gkrellm. It probably has what you want, is gui-based and doesn't take a lot of tinkering.

At one time I spent hours working to understand lm-sensors and how to get the most out of the configuration files but it probably wasn't worth the effort for me.

To install gkrellm:
```
sudo aptitude install gkrellm
```

It's in my Tools menu but I might have made a shortcut there myself. The startup command is "gkrellm".

---

