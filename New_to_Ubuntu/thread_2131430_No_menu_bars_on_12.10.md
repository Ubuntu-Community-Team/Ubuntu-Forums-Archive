---
title: "No menu bars on 12.10"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by SD402F on 2013-04-01
Hello and thanks for reading. I've tried looking at other threadswhich were fairly confusing, as I am brand new to the Linux experience after just getting a 32 gig USB that I wanted to install it on. I used an ISO that I down'd from the Ubuntu website, and the Universal USB Installer from pendrivelinux.com with a 4 gig persistent file. When I boot it, it loads to a popup asking me to try it via USB or install. I tried using "Install" once but it tried to write it to my computer's HDD. When I click to try via USB, I can view the desktop with 2 icons, "Install Ubuntu 12.10" and "Examples", yet none of the standard top/bottom bars. Thankfully I can get into system preferences via the change desktop background workaround and through that Firefox, but it is pretty well useless without those options. Any advice is greatly appreciated.
System Info:
Video card
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce 6150 LE] (rev a2)
I'm not 100% sure if this is the right place to post so apologies if that is incorrect!

---

### Post by Frogs Hair on 2013-04-01
Hello, SD402F

Unity has no bottom panel, but has a dock / launcher  on the left and a top panel when displaying properly  

To find out if you can run Unity use Ctrl + Att + t  open the terminal  and copy and paste the following command. 

```
/usr/lib/nux/unity_support_test -p
```

If  there is a yes in each category displayed enter the next command to reset the unity desktop.
```
setsid unity
```

---

