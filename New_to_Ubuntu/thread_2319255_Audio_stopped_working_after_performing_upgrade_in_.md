---
title: "Audio stopped working after performing upgrade in ubuntu 12.04"
date: 2016-04-02
forum: New to Ubuntu
---

### Post by Rubin_Porwal on 2016-04-02
[COLOR=#111111][FONT=Ubuntu]I have dell inspiron 15 3542 series laptop with ubuntu 12.04 as operating system.
Yesterday I had executed following commands from terminal
sudo apt-get update
sudo apt-get upgrade
The above mentioned processes were successfully executed but when I did reboot ,there was no sound from inbuilt speakers on laptop.
After that I tried executing above commands and did reboot multiple times but the issue still persists.
Also I am receiving following notification in Google chrome browser[INDENT]This computer will soon stop receiving Google Chrome updates because this Linux system will no longer be supported.
[/INDENT]
Looking forward for appropriate solution ASAP


[/FONT][/COLOR]

---

### Post by HermanAB on 2016-04-02
This may sound silly, but did you try increasing the volume?  

It tends to default to zero.

Try aumix or amixer and crank it up.

---

### Post by Impavidus on 2016-04-02
Maybe the sound was somehow muted? Try setting it with pulse audio volume controller and/or alsamixer (use arrow keys to select and adjust, **m** to (un)mute, escape to exit). In terminal:```
pavucontrol
alsamixer
```They should be integrated, but I have seen cases where this didn't work correctly. Also, I'm a but rusty on 12.04. It's a long time since I used it.

As for your chrome issue: it seems that google will drop support for 12.04. Your options are to switch to a different browser or move to a later version of Ubuntu. You can switch to 14.04 (upgrade or clean install) or, if you can wait a few weeks, directly to 16.04 (clean install).

---

### Post by RobGoss on 2016-04-02
Right click on the sound icon at the top of your screen to see if the correct sound device is high lighted

---

