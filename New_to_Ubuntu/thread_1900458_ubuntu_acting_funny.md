---
title: "ubuntu acting funny"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by krishnan t s k on 2011-12-26
Today i came across a very weird and irritating thing when i logged into ubuntu..... if i hover my mouse over anything(WITHOUT clicking it), that program or file or setting automatically opens.... Is it just me or is it happening to everyone using oneiric? the same also happens when i hover over maximize minimise or close!!!!! help please!!!!!

---

### Post by 2F4U on 2011-12-26
Did you install updates or other software? Could it be a hardware problem with the mouse?

---

### Post by krishnan t s k on 2011-12-26
No i havent installed any updates though security updates are installed automatically..... as far as hardware problems are concerned,i have been using the same mouse for just over a year and ever since i installed ubuntu on my comp....i dont think it's a hardware issue.... and i'm not sure its a bug too... and also, i havent installed any new programs for the past few weeks too!!!!

---

### Post by pygmalion7 on 2011-12-26
> **krishnan t s k said:**
> No i havent installed any updates though security updates are installed automatically..... as far as hardware problems are concerned,i have been using the same mouse for just over a year and ever since i installed ubuntu on my comp....i dont think it's a hardware issue.... and i'm not sure its a bug too... and also, i havent installed any new programs for the past few weeks too!!!!

I'd try a different mouse every time (assuming you have one !!)

---

### Post by jerrynewt on 2011-12-26
Go to System>Preferences>Mouse -- now go to the accessibility tab and make sure the "initiate click when stopping pointer movement" box is not checked.

---

### Post by The Cog on 2011-12-26
Could it be nautilus showing you previews? There's an option for previews in the nautilus settings somewhere. Scared the pants off me the first time it previewed a music file.

---

### Post by krishnan t s k on 2011-12-26
> **jerrynewt said:**
> Go to System>Preferences>Mouse -- now go to the accessibility tab and make sure the "initiate click when stopping pointer movement" box is not checked.

u mean system settings? if so, there is no accessiblity tab in mouse settings....what else to do??

---

### Post by krishnan t s k on 2011-12-26
> **The Cog said:**
> Could it be nautilus showing you previews? There's an option for previews in the nautilus settings somewhere. Scared the pants off me the first time it previewed a music file.

its not just nautilus where its happening.... its everywhere.....from launcher to system settings.... works even on maximise minimise and close buttons for all windows..... at times, its useful but at other times, its a bit irritating

---

### Post by The Cog on 2011-12-27
Ok. I would find that very inconvenient. My first move would be to try to find out if it's something in my personal setttings that's causing it. You can don this by renaming your home directory and making a new one with no settings in it (just for a while).

Log out from the GUI, then press Ctrl-Alt-F1 to get to a console. Log in (In the example, I'll assume your username is krishnan - substitute your actual username). Then use these commands to hide your real home directory and make an empty one:
```
sudo -i
cd /home
mv krishnan real-krishnan
mkdir krishnan
chown krishnan:krishnan krishnan
```
Then use Alt-F7 to switch back to the GUI and log in again. All your settings are gone, but see if your problem has gone too. Once you have found the answer, log out from the GUI again, Ctrl-Alt-F1 back to the console and undo your previous changes - remove the no-settings directory and rename your proper directory again **don't delete the wrong directory!**:
```
rm -rf krishnan
mv real-krishnan krishnan
```
and Alt-F7 back to the GUI.

What to do now depends on whether it's something in the settings in your directory that's causing the problem. If it's somethign in your settings, you can perhaps start deleting settings until it's fixed. If it's a system problem then I have no idea.

---

### Post by krishnan t s k on 2011-12-30
sorry for the late reply but i found the reason for it.... it was a feature my cousin accessed by mistake in the accessibility keyboard.... he himself came and disabled the feature.... thanks a ton for your suggestions and sorry if i wasted your time :) :)

---

### Post by The Cog on 2011-12-30
Haha! I didn't know there was such a feature. Thanks for letting people know what was really going on.

---

