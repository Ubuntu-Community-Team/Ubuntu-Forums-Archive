---
title: "Change graphic driver."
date: 2008-08-17
forum: New to Ubuntu
---

### Post by skymera on 2008-08-17
Hey

Previously you was able tochange the grahpics driver in Ubuntu by fiddling with Xorg.conf

But i noticed that is now different? Howdo i go about changing the driver?

Cheers :)

---

### Post by nicedude on 2008-08-17
For your Nvidia card you have 2 options 

1. install envyng-gtk which is a program called envy and its GUI GTK frontend and let it do it for you. After install it will be in Applications -> System Tools -> Envy-ng

2. Go to Nvidia's website and download the newest driver package and install it yourself. This is kinda complicated though for some as it requires you to unload the X windows environment and run the install from a pure ocmmand line environment which is tricky the first time you do it but there are links on Nvidia's site to their forum where people will describe what is required :-)

INSTALL ENVY-NG COMMAND
sudo apt-get install envyng-gtk 

If you are at all squeamish about the command line & learning new stuff then go with envy-ng and let it do your dirty work for you.

hope this helps you out

---

### Post by skymera on 2008-08-18
Sorry i should have said. This is for my laptop :)

It has integrated VIA chipset and i want to try Unichrome or Openchrome drivers, i think it's using Vesa at the moment and wish to change about.

Thanks for your reply though, detailed :wink:

---

### Post by skymera on 2008-08-19
Anyone know?

---

### Post by spyd3r on 2008-08-19
have you checked out this link: [https://help.ubuntu.com/comChrommunity/Unichrome](https://help.ubuntu.com/comChrommunity/Unichrome)

---

### Post by skymera on 2008-08-19
404 error

---

