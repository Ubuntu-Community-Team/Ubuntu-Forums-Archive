---
title: "[SOLVED] How to install NVIDIA drivers?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by adileader on 2008-08-05
I am using Hardy 64 bits and can't figure out how to install the latest nvidia drivers. Thanks a million in advance. 

P.S: the file is saved to my desktop!

---

### Post by ConMan318 on 2008-08-05
What card is it?

And there are no drivers in System > Administration > Hardware Drivers?

---

### Post by cdtech on 2008-08-05
Did you look in "Synaptic Package Manager"? Do a search for "nvidia".

I have:
nvidia-glx-new
nvidia-kernel-common
nvidia-new-kernel-source
nvidia-settings

Hope this helps.......

---

### Post by ClockMan on 2008-08-05
try envy

 if that doesn't work, then you have to do what i did

install the kernel headers source code

Configure runlevel 2 to run without X and boot with run level 2

run the sh script that you downloaded from NVIDIA as root
follow the instructions on the screen

change the runlevel to anything else other than 1. You can do this using the init command

you should see the 3D NVIDIA logo now

login and you will see that the graphics drivers are working

---

### Post by kirsis on 2008-08-05
The package repositories don't have the latest drivers though.

You can use a tool like EnvyNG but even that doesnt always know about the latest drivers (Im not 100% sure how it works, having used it only once. Maybe there's a way to update it)

What you should do is download the drivers from nvidia, then in CLI:

```
sudo telinit 1
```, it should come up with a menu. Choose the root option.

Navigate to where you have the downloaded file.

```
./<exec file from nvidia that ends with .run>
```

Then follow on screen instructions. Make sure there are no warnings (it'll often times finish the procedure even if warnings come up but the drivers wont work), follow the on-screen instructions.

When you're done, do

```
telinit 3
```

---

### Post by kpkeerthi on 2008-08-05
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

I suggest you install the drivers off ubuntu repository as explained in the link above. If you install from the download off nvidia's website, you may have to re-install the drivers everytime you do kerbel upgrade.

---

### Post by adileader on 2008-08-06
I'm really sorry for not replying but I will now. Thanks for all you guys cause I installed it with Envy. So it is solved! :-D:-D:-D:-D I am really happy.

---

