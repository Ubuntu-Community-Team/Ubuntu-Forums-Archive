---
title: "Is it normal for ubuntu to be this slow?"
date: 2017-11-07
forum: New to Ubuntu
---

### Post by pukiking- on 2017-11-07
As I've recorded on this video:

[https://youtu.be/3Mukw8K4faQ](https://youtu.be/3Mukw8K4faQ)

My laptop is running pretty slowly on Ubuntu. It works well on windows, but this takes just so long to startup. 
Specifications:
**Notebook:** [Asus K550VX-DM028D]("https://www.notebookcheck.net/Asus-K550VX-DM028D.184706.0.html")
**Processor:** [Intel Core i7]("https://www.notebookcheck.net/Intel-Core-i7-Notebook-Processor-Clarksfield.21025.0.html") 6700HQ
**Graphics Adapter:** [NVIDIA GeForce GTX 950M]("https://www.notebookcheck.net/NVIDIA-GeForce-GTX-950M.138026.0.html") 4096 MB


I'm totally new to Ubuntu, I've had tons of problems with Nvidia driver and wifi, but thankfully got help here and got them fixed. I'm just wondering if you guys have any idea is this about the hardware or something else?

---

### Post by Autodave on 2017-11-07
Fill us in: what Nvidia driver did you end up installing and where did you get the driver from?

---

### Post by vasa1 on 2017-11-07
I'm getting: This video is unavailable.

---

### Post by HermanAB on 2017-11-07
Slow to start up?

It is a laptop computer.  Don't shut it down.  Close the lid and let it go to suspend.  

Restart from suspend should take < 5 seconds, same as on Windows.

---

### Post by yetimon_64 on 2017-11-07
> **vasa1 said:**
> I'm getting: This video is unavailable.

+1, same problem trying to view it here.

---

### Post by pukiking- on 2017-11-08
My bad, didn't notice that video was set on private. Here's the link now [https://youtu.be/3Mukw8K4faQ](https://youtu.be/3Mukw8K4faQ)

For a nvidia driver I've followed the instructions on this thread. 

[https://ubuntuforums.org/showthread.php?t=2375751&highlight=Nvidia+driver](https://ubuntuforums.org/showthread.php?t=2375751&highlight=Nvidia+driver)

As you can see on that thread, now I have this driver

[http://us.download.nvidia.com/XFree8..._64-384.90.run]("http://us.download.nvidia.com/XFree8..._64-384.90.run")

---

### Post by littlefoot505 on 2017-12-01
I'd suggest making sure that your hard drive isn't full on either partition. You also could do what Herman said and just keep the lid shut (although in my experience with both Windows and Ubuntu, that can make my computer be slow). If all else fails, you could try reinstalling Ubuntu, as there could be something wrong with it. My computer usually performs pretty well in both systems, and it's not quite as powerful as yours (here are the specs of mine: [https://support.hp.com/us-en/document/c05157231](https://support.hp.com/us-en/document/c05157231) )

---

### Post by RobGoss on 2017-12-02
I viewed the video and it's hard to tell if anything is really slow seems to load OK for me

---

### Post by Perfect Storm on 2017-12-02
> **RobGoss said:**
> I viewed the video and it's hard to tell if anything is really slow seems to load OK for me

+1
It seems okay for a cold boot. Not as fast as mine (see my signature).

---

### Post by RobGoss on 2017-12-02
I think it's safe to say that some starting up problems may be caused by other programs trying to load-up at startup, In my case I always disable the ones I don't think will impact my system. You can look at the ones you have by accessing your **startup applications **

How is the performance once your machine is fully started?

---

### Post by VMC on 2017-12-02
What's the output of "systemd-analyze blame" ?

---

### Post by Douglas_White on 2017-12-04
If Windows is set for fastboot it is basically coming back from hibernate.

Ubuntu is coming up from zero.

This might account for it.

All the Best,
D. White

---

### Post by shintaomonk on 2017-12-07
If it's too slow, you could always try lubuntu, which works faster

---

### Post by RobGoss on 2017-12-07
Try disabling fast startup, and let us know how the system boots in many cases it will cause the system to boot up slower

---

