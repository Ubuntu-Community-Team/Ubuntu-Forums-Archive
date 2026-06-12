---
title: "s-video not working. PLEASE HELP!!!!!!"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Periswell on 2008-09-09
hello all.

my s-video is not working. everytime i plug it into the tv from my computer and press Fn F8 which is what i do to put it on the other screen. my tv just flickers and does nothing else. i have an intel video card. please help its urgent.

-josh

---

### Post by Periswell on 2008-09-09
bump

---

### Post by vikram on 2008-09-09
I would try with a lower screen resolution. Depends on what resolution the TV would expect, your card etc. 

also check logs for any error message

---

### Post by overdrank on 2008-09-09
Please do not bump your thread so quickly as once in 24 hrs will so patients. As suggested what is the model of the graphics card and have you tried the command  ```
gksu displayconfig-gtk
``` and set it up there.

---

### Post by Periswell on 2008-09-09
i tried what you said overdrunk and it detected the tv. it wont let me change the resolution from 800x600 and when i test it nothing new happens. the tv just flickers. it came up with an error in terminal though when i press test...

> on_button_test_config_clicked()
Failed to get preferred width, height, or rate - Assuming none. IndexError:  list index out of range
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 1038, in on_button_test_config_clicked
    (res, msg) = testX(self.xsetup,"/usr/share/displayconfig-gtk/servertestdialog-gtk")
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/displayconfigcommon.py", line 50, in testX
    xsetup.writeXorgConfig(config_filename)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 702, in writeXorgConfig
    self._syncXorgConfig()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 653, in _syncXorgConfig
    gfxcard._syncXorgConfig()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1470, in _syncXorgConfig
    self.screens[i]._syncXorgConfig(self.x_device[i])
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 2357, in _syncXorgConfig
    mode_list_line.extend([ mode_list[mode_index].getName() for mode_index in mode_indexes ])
IndexError: list index out of range


ps. overdrunk i nedd it very soon so i can't wait to let someone to notice it so i have to bump it to front page.

---

### Post by overdrank on 2008-09-10
Ok if the nvidia settings can not get the resolution you need then I am at a lost. :( I have not used a projector so I am on unfamiliar ground.

---

### Post by etnlIcarus on 2008-09-10
My guess is the video card is outputting an incompatible refresh rate for your television model. Unfortunately, I don't know how to fix that.

---

### Post by chronographer on 2008-09-10
Using nvidia-settings worked for me recently, it writes stuff to your org.conf for you!

type 'gksu nvidia-settings' and gui it up

---

### Post by Periswell on 2008-09-10
no i put it in the terminal but nothing happens.

---

### Post by overdrank on 2008-09-10
> **Periswell said:**
> no i put it in the terminal but nothing happens.

You may have to install nvidia-settings via synaptic manager.

---

