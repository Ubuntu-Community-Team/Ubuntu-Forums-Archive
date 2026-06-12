---
title: "nvidia questions"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by sendy on 2012-12-25
hi there! i just bought dell inspiron 14r 5420, im new in ubuntu and just installed 12.04 lts 64 bit :)
i have some questions:
- how to check whether my nvidia GeForce GT 630M is working or not?
- if my nvidia GeForce GT 630M is not working, how to make it working?

i am really new to ubuntu, i already read some posts in google and cant understand some codes, if you're going to post some code at least please explain it :)
i hope i can get well in ubuntu forum :D, ubuntu has a really nice desktop view

---

### Post by Pjotr123 on 2012-12-25
First make sure that it's running on the restricted driver from Nvidia itself:
[https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers](https://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-sure-all-hardware-is-working-properly-and-install-missing-drivers)

Then type this in a terminal:
```
gksudo nvidia-settings
```

Press Enter.

That should tell you how your card is doing. :)

If you want to measure performance (fps), then type this in a terminal:
```
sudo apt-get install mesa-utils
```

Press Enter. Your password remains entirely invidible, not even dots will show, this is normal. 

This installs some tools.

Now type this in a terminal:
```
glxgears
```

Press Enter. Wait a few minutes and see how high the fps is.

---

### Post by sendy on 2012-12-25
> 
Then type this in a terminal:
```
gksudo nvidia-settings
```Press Enter.
That should tell you how your card is doing. :)
err i typed it in terminal, it asked for password, i enter it correctly, but nothing happened. Btw what does the code above do?

> 
Now type this in a terminal:
```
glxgears
```Press Enter. Wait a few minutes and see how high the fps is.i know this sounds stupid but i dont know if this is normal or not :s , results :
```

299 frames in 5.0 seconds = 59.797 FPS
299 frames in 5.0 seconds = 59.608 FPS
299 frames in 5.0 seconds = 59.610 FPS
299 frames in 5.0 seconds = 59.609 FPS
299 frames in 5.0 seconds = 59.608 FPS

```

---

### Post by Pjotr123 on 2012-12-25
Apparently you don't have the restricted driver yet.... See the link in my previous message for the installation how-to.

---

### Post by sendy on 2012-12-25
> **Pjotr123 said:**
> Apparently you don't have the restricted driver yet.... See the link in my previous message for the installation how-to.
ermmm i read google how to check vga in ubuntu and i typed 
```

lspci | grep VGA

```output:
```

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev a1)

```there are 2 graphic card, then i tried to googling again and i checked system settings:
[[IMG]http://www2.picturepush.com/photo/a/11766335/640/11766335.png[/IMG]]("http://picturepush.com/public/11766335")

it seems ubuntu detects only intel :s,
then i read google about bumblebee, and yes im confused (cant understand the usage of it) , can you please explain what's the use of bumblebee nvidia(just the point why use it)

im really sorry for asking so much, but all of my life i have been using windows and never dealt with these things in ubuntu

---

### Post by monkeybrain2012 on 2012-12-25
Your laptop has Optimus. Unfortunately the nvidia card won't work with Linux out of the box.

Check out [http://bumblebee-project.org/](http://bumblebee-project.org/)

---

### Post by sendy on 2012-12-25
> **monkeybrain2012 said:**
> Your laptop has Optimus. Unfortunately the nvidia card won't work with Linux out of the box.

Check out [http://bumblebee-project.org/](http://bumblebee-project.org/)
i already read about bumblebee , but unfortunately im really dont understand 60% of what it says... can u please post what should i type and what should i do to make this nvidia running :(
windows made me stupid at computers.. i dont even know some of the settings. I think i will move to linux forever.. sriously im really sorry for my stupidness

---

### Post by Pjotr123 on 2012-12-25
In the terminal (use copy/paste to avoid errors):
```
sudo add-apt-repository ppa:bumblebee/stable
```

Press Enter. Your password won't show, not even dots, that's normal.

Then in the terminal (copy/paste):
```
sudo apt-get update && sudo apt-get install bumblebee bumblebee-nvidia
```

Press Enter again.

When this job is done, reboot your computer. All should be well now. :)

---

### Post by sendy on 2012-12-25
> **Pjotr123 said:**
> In the terminal (use copy/paste to avoid errors):
```
sudo add-apt-repository ppa:bumblebee/stable
```Press Enter. Your password won't show, not even dots, that's normal.

Then in the terminal (copy/paste):
```
sudo apt-get update && sudo apt-get install bumblebee bumblebee-nvidia
```Press Enter again.

When this job is done, reboot your computer. All should be well now. :)

hi there, in system settings still the same as before, but i read bumblebee documentation a bit and experimented a bit running
```

optirun glxgears

```
and yes it works! but system settings still using intel.

questions:

- why i must run optirun (sorry for this question, i already read bumblebee documentation and only follow the instructions, but it doesnt explain well 'why i must 
run optirun')

- do i must run optirun for everygame and apps?

---

