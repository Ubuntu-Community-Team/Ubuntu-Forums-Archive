---
title: "Xpress 1150 (I think it's also called 200m) Ridiculously Slow"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Mr_KnowNothing on 2008-07-01
Hello All,

I'm 100% new to Linux and have just done a complete switch over!
Then, i have a Insipron 1501 with  ATI Xpress 1150 which seems to be installed, if i do fglrxinfo i get:
Display: 0.0   Screen: 0
OpenGL Vendor String: ATI Technologies Inc.
OpenGL Renderer string: ATI Radeon Xpress Series
OpenGL Version String: 2.1.7412 Release

In other words it seems to be installed but i guess it isnt...
In glxgears i get around 1050 and it keeps sort of blinking

Other programs that i used to run under windows are really slow under linux (even if compiled for linux - no wine or anything)

So pleeeease, can anybody help me

Many Thanks

---

### Post by Mr_KnowNothing on 2008-07-01
I have tried following this: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29)

But when i am installing the *.debs i get:
Error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

then i tried:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#libGL_error](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#libGL_error)

The permissions for libGL.so.1.2 are fine, but when i do:
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
It comes:
ln: creating symbolic link '/usr/lib/libGL.so.1': File Exists

so my guess as i cannot intall the debs yet is that there is something wrong could someone please tell me what to do

Any help is much welcome

---

### Post by Mr_KnowNothing on 2008-07-02
In my attempts to fix the problem i think i just made it worst...

I tried to uninstall fglrx to install it again, so i went to the synaptic and got rid of anything that appeared in a search for fglrx.

I tried to install again, following [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) using the method 1

Now guess what?!
Every time i restart my laptop it doesn't recognize my video card and i have to use it 800x600! That's really annoying
Also, the System=>Adm=>Hardware drivers disappeared (but i'm sure this wouldnt help me much anyway)

So, pleaaaseee what should i do? is there anyway to just start a clean install of my ati drivers?

fglrxinfo now shows the 2.1 mesa 7.0.3-rc2

Also, if i try to re-install ubuntu i'll have to re-install all my programs, right?

Many Thanks

---

### Post by meindian523 on 2008-07-02
Yours is ATi Radeon Xpress 200 all right.I'm getting around 1370 fps.I think what you do is go to Hardware Drivers Manager and reinstall fglrx from there.

If you reinstall Ubuntu,you will have to reinstall all your programs,but if they're all debs,then you can archive them to some external storage by backing up /var/cache/apt/archives,that basically is all your updates.If you downloaded something else off the net and not from the repos,you should add that to the archive too.

---

### Post by Mr_KnowNothing on 2008-07-02
Hello,

I managed to put back the Hardware Drivers Manager (that's System->adm>Hardware Drivers, right?) and tried to put the fglrx back but unfortunately when i re started it gave me the same screen saying it had to run in lower graphics mode...

The funny things is that i even got an icon saying "Proprietary drivers are being used to make this computer work properly" when it finished to load...

btw even so, fglrxinfo still says i've got mesa and not the ATI driver

Any clue?

Thanks

---

### Post by meindian523 on 2008-07-02
The path's correct,and I have no clue what else can you do.Is the enabled box ticked in System>>Adm>>Hardware Drivers?

---

### Post by meindian523 on 2008-07-02
Also check whether you have all these packages installed:

xorg-driver-fglrx
jockey-common
jockey-gtk
linux-restricted-modules-2.6.24-16-generic
linux-restricted-modules-2.6.24-18-generic
linux-restricted-modules-2.6.24-19-generic
xserver-xorg-video-ati

---

### Post by Mr_KnowNothing on 2008-07-02
Yes...
And the status is "in use"...

Yeahh i have no clue what to try now too, and also i cant reinstall ubuntu now as i havent got some of the programs i use (and need to use today) here (and no, i cant just download)...

This is really frustrating...

---

### Post by meindian523 on 2008-07-02
Check for the packages I mentioned above.

---

### Post by Frem on 2008-07-14
> **meindian523 said:**
> Yours is ATi Radeon Xpress 200 all right.

Just a clarification, the Xpress 200m is *not* the same card as the Xpress 1150. The Xpress 1150 is based off the Xpress 200m, but according to ATi, there should be a 30% performance increase.

---

### Post by meindian523 on 2008-07-14
Oh,thanks.I based that statement off my fglrxinfo,which was the same as the OP's.

---

