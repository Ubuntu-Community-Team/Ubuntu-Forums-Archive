---
title: "Problem with installation! - any idea's?"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by Accurax on 2008-07-04
Hi guys,

i previously installed Ubuntu 8.04 on my laptop, but it was a little sluggish, so, after some research I decided to install Xubuntu instead, as I am under the impression it should run a little smoother.

Now, the cd has no errors, and the partitioner loads correctly and the options proceed correctly.

however, once the installation starts it reached 15% (the same each time) and then freezes, the mouse locks up and it just sits there, I've left it for 20 minutes straight and no change.

Like I said, I have Ubuntu 8.04 installed, and I'm trying to replace this with Xubuntu 8.04.

Does anyone have any idea what might be causing this problem?

Cheers guys

Acc

---

### Post by bumanie on 2008-07-04
Does 8.04 still work? If so you can install xfce desktop (via synaptic) and at the options button at the login screen, you get given the choice (I think it is under 'choose session') which desktop to boot into - might be easier than a fresh install, when you are having difficulty. You then have the choice of gnome and xfce. Later, if you prefer xfce, you should be able to remove gnome via synaptic and boot straight into xfce - at  least I believe that's how it works. Check some documentation or wait for another answer to confirm or rebuke this as I have never actually done it - I like gnome.

---

### Post by akiratheoni on 2008-07-04
If you can still access your old Ubuntu install, fire up a terminal (Applications -> Accessories -> Terminal) and type:

```
sudo apt-get install xubuntu-desktop
```

Then after you type in your password (nothing will appear), it will download several hundred MB worth of files. After it's done, simply log out then click on Options at the login screen; choose "choose session" then select the Xfce option and hit okay and log in as normal. You should now have Xfce installed on your computer.

---

### Post by hyper_ch on 2008-07-04
use this to install a pure Xfce [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by Accurax on 2008-07-04
> **akiratheoni said:**
> If you can still access your old Ubuntu install, fire up a terminal (Applications -> Accessories -> Terminal) and type:

```
sudo apt-get install xubuntu-desktop
```

Then after you type in your password (nothing will appear), it will download several hundred MB worth of files. After it's done, simply log out then click on Options at the login screen; choose "choose session" then select the Xfce option and hit okay and log in as normal. You should now have Xfce installed on your computer.

Thanks guys really appreciate it... just one thing in referance to the above.

is that exactly the same as installing xubuntu from scratch?

---

### Post by brownknight on 2008-07-04
> **Accurax said:**
> Thanks guys really appreciate it... just one thing in referance to the above.

is that exactly the same as installing xubuntu from scratch?

No. Its not the same as installing Xubuntu from scratch since you will also have the Ubuntu components and programs installed. You will see them in your Xubuntu menu. So you will ge using up more space but I dont see any performance hit in my experience.

I had the same install problem before when installing Xubuntu. The reall culprit is the CD. You can try to burn it again in a clean CD. 

Dont forget to backup your data first. Good luck.

---

### Post by Accurax on 2008-07-05
> **akiratheoni said:**
> 
```
sudo apt-get install xubuntu-desktop
```


I get an error saying

```

E: Couldn't find package xubuntu-desktop

```

Anybody have any idea's?

---

### Post by Accurax on 2008-07-05
Seems to be working now.... how odd :)

---

