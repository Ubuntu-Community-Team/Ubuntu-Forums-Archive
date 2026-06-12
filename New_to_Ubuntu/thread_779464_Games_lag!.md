---
title: "Games lag!"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by khr on 2008-05-02
I really want to play World of Padman(WoP), neverputt, BTRL, and all those wonderful games... The only problem is that it lags extremely! The frame rate is maybe about 1 frame per 3rd second! I'm not really sure why.
I have an ATi Mobility Radeon X1600 256MB, and i have no idea on how i can make it work or whatever i need to do...

How do i play games without lag?

Edit: I'm using Hardy Heron.

---

### Post by khr on 2008-05-02
I've found out that whenever i play a game it uses Mesa driver, so thats why its so sluggish. The weird thing is that fglrxinfo returns:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.1.7415 Release
```
There's no Mesa...

Please help!

---

### Post by JoshuaRL on 2008-05-02
First of all, OpenGL is an framework for games makers to take advantage of video cards.  Think DirectX except open and better.

Could you post the output of the following command run from the terminal?
```

glxgears

```

Make sure you don't move the window or mouse any.  Let it run for five cycles, then hit ESC to end the command.  Post the output here.  That is a general idea of what kind of FPS you are getting from your card.

---

### Post by khr on 2008-05-02
> **JoshuaRL said:**
> First of all, OpenGL is an framework for games makers to take advantage of video cards.  Think DirectX except open and better.

Could you post the output of the following command run from the terminal?
```

glxgears

```

Make sure you don't move the window or mouse any.  Let it run for five cycles, then hit ESC to end the command.  Post the output here.  That is a general idea of what kind of FPS you are getting from your card.

1155 frames in 5.0 seconds = 229.675 FPS
1120 frames in 5.1 seconds = 219.840 FPS
1080 frames in 5.0 seconds = 214.983 FPS
1100 frames in 5.0 seconds = 218.996 FPS
1080 frames in 5.0 seconds = 215.230 FPS

---

### Post by JoshuaRL on 2008-05-02
Yeah, that should be a little higher.  I'm not an expert on newer ATI cards, but here's mine from a Nvidia 8400GS:

```

13818 frames in 5.0 seconds = 2763.566 FPS
14648 frames in 5.0 seconds = 2929.543 FPS
14726 frames in 5.0 seconds = 2945.132 FPS
14719 frames in 5.0 seconds = 2943.740 FPS
14376 frames in 5.0 seconds = 2874.850 FPS

```

It seems like you have either the wrong driver or it's installed incorrectly.  How did you get it working exactly?

---

### Post by khr on 2008-05-02
> **JoshuaRL said:**
> Yeah, that should be a little higher.  I'm not an expert on newer ATI cards, but here's mine from a Nvidia 8400GS:

```

13818 frames in 5.0 seconds = 2763.566 FPS
14648 frames in 5.0 seconds = 2929.543 FPS
14726 frames in 5.0 seconds = 2945.132 FPS
14719 frames in 5.0 seconds = 2943.740 FPS
14376 frames in 5.0 seconds = 2874.850 FPS

```

It seems like you have either the wrong driver or it's installed incorrectly.  How did you get it working exactly?

I'm not sure.
I think i got it working by using:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by khr on 2008-05-02
I followed this guide manually and it speeded up the glxgears test!
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The results are:
```
22637 frames in 5.0 seconds = 4527.325 FPS
23743 frames in 5.0 seconds = 4748.532 FPS
23763 frames in 5.0 seconds = 4752.585 FPS
23749 frames in 5.0 seconds = 4749.783 FPS
23758 frames in 5.0 seconds = 4751.523 FPS
```

About doubled...
I'm soon going to sleep, 3:13 after midnight here.

Edit: I've tried playing World of Padman and it doesn't lag at all! The only problem is that it FLICKERS, its such a pain to my eyes everytime it FLICKERS!!!

---

### Post by JoshuaRL on 2008-05-03
Nah man, that more than doubled.  You went from under 300FPS to over 4500FPS.  That seems like you have the driver installed correctly.  Congratulations.

Now, any more info on the screen flickers?

---

### Post by lswest on 2008-05-03
> **khr said:**
> 

Edit: I've tried playing World of Padman and it doesn't lag at all! The only problem is that it FLICKERS, its such a pain to my eyes everytime it FLICKERS!!!

Are you playing with compiz enabled? that can cause flickering

---

