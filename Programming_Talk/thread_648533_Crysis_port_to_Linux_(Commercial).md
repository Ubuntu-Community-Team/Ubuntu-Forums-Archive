---
title: "Crysis port to Linux (Commercial)"
date: 2007-12-23
forum: Programming Talk
---

### Post by diaz028 on 2007-12-23
I know this is far fetched but with the future release of Crysis Linux Server and SDK, what would the possibility be to run Crysis on Linux?

I know there could be several approaches to this:
- DX9 through emulation Wine/CEDEGA
- Create an OpenGL/AL code

I am particularely interested in the OpenGL/AL area. Again, this is far-fetched, but what forum should I be posting to, and what website would be best for programming/porting games to OpenGL / Linux ?

I am beginner (will read all the stickies) - but am interested in programming. Maybe this is way too big a project to start with, but I'll give it a shot. LOL. 

Thanks

-D

---

### Post by diaz028 on 2007-12-23
HLSL2GLSL or HLSL/GLSL is my answer... I'll try to figure it out.

-D

---

### Post by moma on 2007-12-24
Install Code::Blocks IDE.
[http://ubuntuforums.org/showthread.php?p=3627418&posted=1#post3627418](http://ubuntuforums.org/showthread.php?p=3627418&posted=1#post3627418)

And read the **note 5)**. It provides all the necessary guides to start with OpenGL programming.

Merry christmas
$ xsnow

---

### Post by Steveway on 2007-12-24
You will need the source-code to port it.
Ask the Crysis team for the source-code, if they give it to you, call us back.
Without it your helpless.

---

### Post by Lucas DaSilva on 2008-02-13
Hey, I would like to get involved with a linux port for crysis. Any further update. Any links.

---

### Post by liebertx on 2008-02-18
i dont think it would be very hard for the developers to make an opengl version for linux, because from what ive heard, they are porting to ps3.  i dont think it is likely that they will, because they are involved with microsoft.  or at least i saw their logo in some of the demos for crysis's development.  as long as they are involved, there will be no official port.  i heard that the alky project(even though its been discontinued) was able to get a native version of prey on osx and linux by using their dx10 converter.  now that they have released their source(alky) its possible that someone might continue to work on it and make a native port, but dont get your hopes up.

---

### Post by antisocialist on 2008-02-18
if there were a port of it nobody using a Linux box would be able to use it anyway as
1 Linux doesn't support dual nvidia 8800 gtx graphics cards
2 the nvidia and ati drivers are so bad it wouldnt be runnable

---

### Post by lackofcreativity on 2008-06-11
> **antisocialist said:**
> if there were a port of it nobody using a Linux box would be able to use it anyway as
1 Linux doesn't support dual nvidia 8800 gtx graphics cards
2 the nvidia and ati drivers are so bad it wouldnt be runnable
Actually, it does support SLi:
```
sudo nvidia-xconfig --sli=AFR
```

Also, my X1300 runs much faster in Ubuntu than it does in Windoze.

---

### Post by lackofcreativity on 2008-06-11
Sorry, double post :(.

---

### Post by |{urse on 2009-06-01
> **lackofcreativity said:**
> Actually, it does support SLi:
```
sudo nvidia-xconfig --sli=AFR
```Also, my X1300 runs much faster in Ubuntu than it does in Windoze.

+2 I have sli running nicely on this box. On the box in the other room my x1650 still kicks butt. Isnt the real problem with porting this game direct3d and not opengl?

---

