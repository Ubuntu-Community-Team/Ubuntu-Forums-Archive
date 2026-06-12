---
title: "[SOLVED] Connecting a bluetooth headset"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by RoyHobbs on 2008-09-30
Hi

I am trying to connect a pair of Nokia BH-501 Headphone to my pc via bluetooth.  The bluetooth device manger can see the headphones, however when I select them and press connect I get the following error

Couldn't display "obex://[00:0D:3C:A6:FC:93]/".
Error: Host down
Please select another viewer and try again.

My phone (Nokia N95 8 GB) is seen by by the blutooth device manager and comes up as a icon on the desktop.  I can view files on my phone (I use it as an mp3 player as well) and I can even play the files on my phone through my pc.  However I can't copy files from my pc to my phone via bluetooth.  When I copy them I get the following error:

There was an error copying the file into obex://[00:1E:3A:82:E1:6E]/E:/Sounds/Digital
Operation not supported by backend

Which I assume means I need to add some sort of bluetooth server?  Any help would be greatly appreciated

---

### Post by Delvien on 2008-09-30
> **RoyHobbs said:**
> Hi

I am trying to connect a pair of Nokia BH-501 Headphone to my pc via bluetooth.  The bluetooth device manger can see the headphones, however when I select them and press connect I get the following error

Couldn't display "obex://[00:0D:3C:A6:FC:93]/".
Error: Host down
Please select another viewer and try again.

My phone (Nokia N95 8 GB) is seen by by the blutooth device manager and comes up as a icon on the desktop.  I can view files on my phone (I use it as an mp3 player as well) and I can even play the files on my phone through my pc.  However I can't copy files from my pc to my phone via bluetooth.  When I copy them I get the following error:

There was an error copying the file into obex://[00:1E:3A:82:E1:6E]/E:/Sounds/Digital
Operation not supported by backend

Which I assume means I need to add some sort of bluetooth server?  Any help would be greatly appreciated

Try Blueman app, if not available by doing the command below in a terminal, google it.

```
sudo apt-get install blueman 
```

then run it with Alt F2 and "blueman" without quotes.

---

### Post by RoyHobbs on 2008-10-01
> **Delvien said:**
> Try Blueman app, if not available by doing the command below in a terminal, google it.

```
sudo apt-get install blueman 
```

then run it with Alt F2 and "blueman" without quotes.

Thanks for your help, this has fixed the N95 but not the headset.  Whenever I go to bond the headset blueman freezes up?  Should I use another bluetooth manager?

---

### Post by RoyHobbs on 2008-10-02
bump

---

### Post by syväpaahto on 2008-10-05
I have the same problem with Nokia BH-101 Headset. Problem seems to be caused by a known bug. So far I haven't seen any workarounds. Just have to wait for future kernel updates.

EDIT:typos

---

### Post by RoyHobbs on 2008-10-06
> **syväpaahto said:**
> I have the same problem with Nokia BH-101 Headset. Problem seems to be caused by a known bug. So far I haven't seen any workarounds. Just have to wait for future kernel updates.

EDIT:typos

No drama, thanks.  I'll wait for future updates and close this off.

---

