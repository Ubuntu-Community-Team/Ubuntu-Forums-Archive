---
title: "display settings only allow 4:3 resolution though I'm displayiong on a HD ready TV!"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by hamuel on 2013-01-20
I've been banging my head against this one for a while. Followed multiple forum threads encouraging me to modify xorg.conf files, usae xrandr commands etc. Nothing has worked. First time Ubuntu User wanting to squeeze some life out of a 3 year old laptop (Vista has become frustratingly slow).

I'm using Ubuntu 12.1 on a HP laptop connected to a HD Ready (720P) screen via a VGA cable. Don't have HDMI/DVI etc. The laptop is a HP with Intel® Core™2 Duo CPU T5670 @ 1.80GHz × 2. ATI radeon graphics card ("unknown" according to Ubuntu).

MS Windows Vista displays fine on the TV but only get two 4:3 options on unbuntu. This is a real pain as I want to use this as a media device, laptop lid down. I can make VLC correct dvd playback but when viewing online video I'm forced to view a letterbox across the middle.

Can anyone help. How can I get an appropriate 720P output from this Ubuntu install as I do on Windows? This is the only thing stopping me loving Ubuntu!!


Thanks

---

### Post by audiomick on 2013-01-20
I reckon your video drivers aren't what they should be.

Can you do
```
sudo lshw -c video
```

and post the output here so that people can see exactly what the machine thinks the video card is? Hopefully someone can then give you specific help.

---

### Post by hamuel on 2013-01-21
This was my thought. I looked on the software centre and there was an ATI pack of drivers etc. Installed it. Ubuntu is broken! I can't log in to it at all. It brings up some form of error that prevents graphics drivers from working and trys to load in a basic graphics mode. I can't remember the terminology, its a home machine and I'm in work now. There is a window but no mouse pointer. somtimes it lets me select OK to proceed but then I get to second window and none of the input works.

So a new problem, much worse. How would I roll back on that install? and get back to square one?

---

### Post by mastablasta on 2013-01-21
have a look here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

and after you remove the drivers please post the results of the command above so we can see what the system recognises.

it is quite possibel that AMD dropped support for your GPU in 12.10. use 12.04 version instead.

---

### Post by hamuel on 2013-01-21
thanks guys,

RE my last post how would I roll back on the package I installed from the software centre that is now preventing me from getting into Ubuntu the normal way. In safe mode the interface loads but the sidebar and links are not there and I cannot do anything!

Total novice here! Any advice would be appreciated.

---

### Post by audiomick on 2013-01-21
I think you can remove it in the safe mode via the software centre, same as  when you installed it. Not 100% sure, though.

---

### Post by ld114 on 2013-01-21
I had a similar issue when connecting my Samsung netbook to a Panasonic 42inch HDMI TV with VGA. Initially I just got 4:3 options too.

I now do the following:

1) Power off the netbook.
2) Connect the TV using VGA (and sound) cables.
3) Switch on the TV.
4) Activate the PC connect option on the TV (using the AV button on the remote)
5) Make sure the TV aspect is set to 16:9
6) Boot Ubuntu (I am using 12.04)
7) Use Displays (in System settings) to turn off the netbook display, and choose the appropriate setting for the TV.

We are now able to watch mp4 files played on the netbook, in glorious widescreen on the TV.

Hope this works for you.

---

### Post by hamuel on 2013-01-21
Thanks

> **audiomick said:**
> I think you can remove it in the safe mode via the software centre, same as  when you installed it. Not 100% sure, though.

Unfortunately I can't get to the software centre as the icon bar seems to be on my other screen which no longer works due to the driver issue. Any hot keys/script for loading it via the terminal or any other ways to get to it?

---

