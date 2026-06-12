---
title: "How do I disable &quot;double click with touchpad&quot; in Lubuntu 12.10"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by Delricko on 2012-12-23
Is it possible to disable the "double click with touchpad facility", and also is it possible to disable the touchpad whilst typing in Lubuntu 12.10?

---

### Post by Rex Bouwense on 2012-12-23
I think what you are looking for can be found here:
[https://help.ubuntu.com/community/Lubuntu/Mouse#Disable_touchpad_while_typing](https://help.ubuntu.com/community/Lubuntu/Mouse#Disable_touchpad_while_typing)

---

### Post by Delricko on 2012-12-23
> **Rex Bouwense said:**
> I think what you are looking for can be found here:
[https://help.ubuntu.com/community/Lubuntu/Mouse#Disable_touchpad_while_typing](https://help.ubuntu.com/community/Lubuntu/Mouse#Disable_touchpad_while_typing)


Thanks for your reply.
It seems that the feature that I most wish to do away with is "TapAndDragGesture".  The instruction page that you directed me to in this respect is very helpful, but it seems that the best that I can manage is to turn the feature off for the current session only.  After restart it's back on again.

---

### Post by NikTh on 2012-12-23
Hi , 
**below is an example to disable TabButton .. if this is what you mean.. with "double click" **, _I'm not sure if I understood correctly. _
you can try from terminal .. 
```
synclient
```read the list and locate the TapButton entries.. 
for example 
```
TapButton1=1
``` means that is enabled.. 
turn off the TapButton , with the command below 
```
synclient TapButton1=0
```see if is ok , maybe it needs to turn off all the TapButton entries.. e.g : 
```
synclient TapButton2=0
synclient TapButton3=0
```depends , see which is 1 (enabled) and set it to 0 (disabled). 

Now when you find the correct command , that serves your needs , add it to startup with the command below ( I assume TapButton1=0 is the correct) 

```
echo '@synclient TapButton1=0' | sudo tee -a /etc/xdg/lxsession/Lubuntu/autostart
```**About the while typing .. **
Try syndaemon 
e.g
```
syndaemon -i 2 -d
```will disable touchpad while typing and will re-eanble it after 2 seconds after finish the typing. 
See ```
man syndaemon
``` for more info. 
Add the command that serve your needs to startup , with the same procedure as above (for TapButton).

Thank you.

---

### Post by Delricko on 2012-12-25
> **NikTh said:**
> Hi , 
**below is an example to disable TabButton .. if this is what you mean.. with "double click" **, I'm not sure if I understood correctly......

Thanks for your reply.  "Double click" is an expression that I gleaned from a different operating system.  I now realise that TapAndDrag was the facility that I wished to disable.  Yours and Rex B's advice have helped me to do so.
Thanks for that.

However, the "disable the touchpad whilst typing" matter has been a disaster.  I now find that the touchpad is permanently disabled after I type no more than a couple of characters.  As a consequence I'm having to send this message from a different operating system.
Any advice that you may offer will be much appreciated.

---

### Post by Delricko on 2012-12-25
Further to my most recent post I am pleased to report that I have now resolved the disabled touchpad problem by editing the /etc/xdg/lxsession/Lubuntu/autostart file from a USB based operating system.
This looks like success.

I'll mark this item as "Solved" if all works well for the next day or two.

In the meantime I offer my thanks once more to Nik Th and Rex B for your help,
and send seasons greetings to all readers of this thread.

---

