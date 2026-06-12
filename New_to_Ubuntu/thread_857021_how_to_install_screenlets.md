---
title: "how to install screenlets"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by lucky.developer on 2008-07-12
hi,

i want to install screenlets in my ubuntu

please guide me through that.
i have gone to compiz site which has the instructions to do so.. but it was not helpful... :(

please guide me step by step cos i am a total beginner in linux :)

thanks

---

### Post by nothingspecial on 2008-07-12
Acessories > Terminal

```
sudo apt-get install screenlets
```

:guitar:

---

### Post by nothingspecial on 2008-07-12
Oh yeah and make sure you`ve got all your repositories enabled -

System > Administration > Software Sources

Make sure all the boxes are ticked (multiverese, universe etc)

---

### Post by lucky.developer on 2008-07-12
i have installed screenlets... now.. how do i use it ?

please give step by step instructions

---

### Post by jimmy the saint on 2008-07-12
Applications>Accessories>Screenlets.  Then choose the ones you want by double clicking them.  You could also go to [http://www.screenlets.org/index.php/FAQ]("http://www.screenlets.org/index.php/FAQ") and read the faq/manual.  It is pretty comprehensive and you will learn a lot more than we could ever tell you in a forum post.

---

### Post by nothingspecial on 2008-07-12
Acessories > Screenlets

Click on one you want. Then click launch/add (top left)
If you want that sceenlet to appear everytime you log on tick the "auto-start at login" (bottom left)

Thats about it.

Oh, and to configure the sceenlet, (size, colour whatever) right click on it.

---

### Post by lucky.developer on 2008-07-12
hey... when i click App->Acce->Screenlets.... nothing happens,,, for some time,, the cursor shows that it is busy... but after a few seconds.. nothing happens.. 

please help

---

### Post by nothingspecial on 2008-07-12
Try opening a terminal and typing 

```
screenlets
```

That will tell you any errors.

---

### Post by jimmy the saint on 2008-07-12
What kind of video card do you have?  in order to use screenlets, you need to have compositing enabled.  Go to Settings>Preferences>Appearance and click the desktop effects tab (If memory serves) and try to set them to the bottom setting.  If you get wobbly windows (the windows act like rubber when you move them) you should be fine.  If nothing happens or you get an error, you may need to enable a restricted driver before you can use screenlets.

---

### Post by nothingspecial on 2008-07-12
You won`t get wobbly windows unless you enable them in compiz but the sdvice is good.

---

### Post by lucky.developer on 2008-07-12
all compiz effects work for me... i can experience the full compiz software plugins...

but i am not able to launch screenlets at all.. 

i opened the terminal and typed screenlets


the following comes in terminal window

> cat: /etc/screenlets/prefix: No such file or directory
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 29, in <module>
    from screenlets import utils,install
  File "/usr/lib/python2.5/site-packages/screenlets/install.py", line 33, in <module>
    DIR_USER		= screenlets.DIR_USER
AttributeError: 'module' object has no attribute 'DIR_USER'


---

### Post by jimmy the saint on 2008-07-12
before you followed nothingspeacial's instructions, did you try to install the software other ways?

---

### Post by nothingspecial on 2008-07-12
If you goto system > administration > synaptic package manager, and search for screenlets does it show it as installed? Box next to it is green.
If so try marking it for complete removal then mark it for installation and try again.

---

### Post by lucky.developer on 2008-07-12
i tried removing it and installing the screenlets again.. but it says the following after downloading and installing the screenlets package...



E: screenlets: subprocess post-installation script returned error exit status 1

---

### Post by nothingspecial on 2008-07-12
I`ve just removed screenlets and reinstalled and I can`t figure out what your problem is.

Try

```
sudo apt-get --purge screenlets
```

Then delete your .screenlets file. It`s in your home directory. You can find it by pressing ctrl+H.

Try reinstalling again. Even if it gives you errors try starting it from the terminal again.

---

### Post by ronaldo80 on 2008-07-13
when I go to synaptic package manager,and type "screenlets" in search meny,nothing comes up! Am I doing something wrong??? pls reply!!!
I am new with linux,not much expirienced!

---

