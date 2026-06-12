---
title: "Changing boot order"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by vicke4 on 2012-08-01
Hi friends I'm using a dual boot system with Ubuntu 12.04 & windows 7.everytime on startup Ubuntu is starting default.i want to change this with windows 7 and i want to edit the timeout seconds.how to do this?

---

### Post by levlaz on 2012-08-01
Do you see the grub bootloader when you turn the computer on?

---

### Post by robbie 348 on 2012-08-01
Just go to menu-admin-startup manager. You can do all you need to there.

---

### Post by vicke4 on 2012-08-01
Sorry guys I'm using 11.10.

@levlaz 
yes it is a grub loader

@robbi348
sorry it is 11.10.

---

### Post by drmrgd on 2012-08-01
You can manually edit your /etc/default/grub file to change the timeout and default OS.  However, there are a couple nice tools to do it graphically, like Startup-Manager and Grub Customizer.  

You can get Grub Customizer by adding this PPA:

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
```

and then running:

```
sudo apt-get update && sudo apt-get install grub-customizer
```

I believe (but might be wrong about this), that Startup-Manager is in the 11.10 repos, but has since been taken out for 12.04.  

Also, if you chose to go the manual route, here is a nice little tutorial on how to change the Default OS and Timeout:

[http://www.psychocats.net/ubuntu/bootmenu](http://www.psychocats.net/ubuntu/bootmenu)

Hope that helps!

---

### Post by vicke4 on 2012-08-01
Thanks for your help drmrgd(sorry i don't know your name).
i did it by editing grub
it is easy.

---

### Post by raja.genupula on 2012-08-01
We are very much glad that , you have solved with your issue . So now please mark the thread as solved .

---

### Post by vicke4 on 2012-08-01
Done:-)

---

