---
title: "Applications so slow."
date: 2013-04-14
forum: New to Ubuntu
---

### Post by Zerochilli on 2013-04-14
Hello,

I recently installed ubuntu 12.04 a few hours ago, While it was on the live USB it was speedy and I liked it, but when I installed it the applications took like 20 seconds to load up. I have no idea why it is, I check system monitor and everything seems fine, I (think) I have installed the graphics card driver on the restricted proprietary drivers it says It has been activated, Even though there is 4 of them and I can activate one?

Regarding the very sluggish slowness of the applications I changed to unity 2D, I also tweaked unity. Seems so slow though, Any help would be greatly appreciated, I moved to linux cause I hated windows being super slow and taking forever to load :confused:. I have installed preload I changed the swappiness, I've read and researched so much to try and fix it but nothing wants to work for me :/, I see lots of people saying they ran it fast on a 2GB netbook with 1.6ghz compared to my specs that is kinda low and I don't see how that is possible :-x.

PC Specs:

Ram: 3GB (275MB Reserved for hardware)
Processor: AMD Athlon(tm) II X2 215 Processor × 2 - 2.7ghz
Graphics: GeForce 9200/integrated/SSE2/3DNOW! 
Hard Drive: 320GB
OS: 32Bit

Is it my specs that could be causing this? Thanks in advance :)

---

### Post by ikt on 2013-04-14
I would install Lubuntu, if that is still slow then I think it is a hardware problem.

---

### Post by Zerochilli on 2013-04-14
Install lubuntu or just install the desktop for ubuntu is there any difference?

Also are my specs efficient enough to even run linux at a nice speed?

Thanks.

---

### Post by Impavidus on 2013-04-14
Those specs should be more than enough to run Ubuntu. There must be a problem with how Ubuntu interacts with your hardware.

---

### Post by zrdc28 on 2013-04-14
The first thing I would look at is that you have the correct video driver, That is one of the things that will slow down a machine the most.  
Go back to the apps manager and choose another driver.  Go to the dash and type in drivers and it will bring up the list again.
A quick check of the video can be done with "glxgears" at terminal.

---

### Post by deadflowr on 2013-04-14
Normally, when I install the nvidia drivers (not the open-source nouveau drivers) I have to run 

```
sudo nvidia-xconfig
```

Then reboot.

nvidia-xconfig generates an xorg.conf file, which the system reads, otherwise the system reads from another file which I don't think points to the nvidia driver but to the default nouveau driver.

after rebooting, if successful, I then open the nvidia-settings program and tweak to my liking, or at least as much to my liking as I can get.

You can tell if the driver is the one in use by running

```
sudo lshw -C display
```

It will list the current video driver in use.

To run these commands, open a terminal with ctrl + alt + T.

Your password will be typed invisible when prompted.

---

### Post by Zerochilli on 2013-04-15
@deadflowr The first command doesn't work currently running lubuntu.

@zrdc28 How would I come to that in Lubuntu 12.04. Complete noob here :P

Thanks :).

---

### Post by Zerochilli on 2013-04-15
> **jayzne said:**
> [IMG]http://s3.postimg.org/h5joiqxzn/solution.jpg[/IMG]

Was that necessary, It's not at all funny.


Does anyone have any idea, My specs can run it but they are refusing to co-operate and I really love ubuntu and unity :(

---

### Post by Locus Kiesselbachi on 2013-04-15
LOL (meme)! :lolflag:

In "Start"menu, choose "System tools", "Synaptic Package Manager". In there, search driver for your Nvidia videocard, there are few choices - its your only hope.
I swaped my Nvidia card for Radeon. ;)
Also you need to look [this]("http://www.youtube.com/watch?v=7MZs3MQO5eU")!

edit:
On the other hand, without videocard driver system should not be SO SLOW. It should make only anomalys in videogames. There must be something more!
In (L)ubuntu Ctrl+Alt+Delete, opens Task Manager, what is your CPU%, when idle-ing?

---

### Post by Zerochilli on 2013-04-15
In lubuntu it's between 15-20% and 500MB of ram.

but in ubuntu 12.04 while using unity 2D it seems a heck of alot more, and it shouldn't be like that, but I'll try the suggestions to see if I can get a updated Driver for my card and see if it fixes it.

To be fair I don't like lubuntu :P, It's fast but ugly I like speed and appearance but the speed I get on ubuntu is just ridiculous a toaster is faster >.<

---

### Post by Impavidus on 2013-04-15
Can you find out which program is using that much RAM and CPU? On my Xubuntu machine 400MB or RAM usage is typical, Lubuntu should be less, and the processor should stay below 5% when idling.

---

### Post by Zerochilli on 2013-04-15
Well the only one that had the multiples running and using a ton of memory was chromium, I guess that is part of the problem.

I did however switch back to ubuntu 12.04 and I installed a propiertary driver upon installion, Then I installed the current updated Nvidia driver aswell and the speed has increased dramatically, however can still feel a little sluggish at times. I guess more ram would fix this issue.

Thanks everyone for your help, If anyone else has any recommendations please post \\:D/

---

### Post by Ramfanatic on 2013-04-16
My Ubuntu is quite slow as well, but my specs are below yours - hopefully going through some of the suggestions will sort me though :)

---

### Post by Locus Kiesselbachi on 2013-04-16
> **Zerochilli said:**
> In lubuntu it's between 15-20% and 500MB of ram.

but in ubuntu 12.04 while using unity 2D it seems a heck of alot more, and it shouldn't be like that, but I'll try the suggestions to see if I can get a updated Driver for my card and see if it fixes it.

To be fair I don't like lubuntu :P, It's fast but ugly I like speed and appearance but the speed I get on ubuntu is just ridiculous a toaster is faster >.<
You can change your OS looks. Look [this thread]("http://ubuntuforums.org/showthread.php?t=2134087"), one posted hes pictures of (L)ubuntu - looks bretty to me.
I have quite fast PC, but I still use Lubuntu - I like how it fastly boots to OS. I hate PC lag and stutter.

---

### Post by Zerochilli on 2013-04-17
> **Locus Kiesselbachi said:**
> You can change your OS looks. Look [this thread]("http://ubuntuforums.org/showthread.php?t=2134087"), one posted hes pictures of (L)ubuntu - looks bretty to me.
I have quite fast PC, but I still use Lubuntu - I like how it fastly boots to OS. I hate PC lag and stutter.

Thanks alot for the thread :D. Your the same as me I hate lagg and slowness but I also like a decent looking desktop this is will help with both :)

---

### Post by Zerochilli on 2013-04-17
> **Ramfanatic said:**
> My Ubuntu is quite slow as well, but my specs are below yours - hopefully going through some of the suggestions will sort me though :)

I hope they do, If not just install lubuntu and pimp it up as the guy above pointed out.



Sorry double post.

---

