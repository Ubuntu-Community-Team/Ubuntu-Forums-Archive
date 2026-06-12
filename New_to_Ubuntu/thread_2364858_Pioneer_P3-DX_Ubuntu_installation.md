---
title: "Pioneer P3-DX Ubuntu installation"
date: 2017-06-28
forum: New to Ubuntu
---

### Post by zameelshaki13 on 2017-06-28
Hi all,

The Pioneer P3-DX that my school ordered did not come with an operating system (whoever ordered it on behalf of the school did not check the OS box). 
I called customer support, who advised me to install either Ubuntu 12 or 16 on the computer of the robot from a bootable USB stick. Has anyone here ever done something like that before? I'm worried because I don't want to mess the robot up.


Thanks in advance,

Zameel

---

### Post by Bucky Ball on 2017-06-28
Welcome. No, never done anything like that, but will say forget 12.04. That goes EOL next month. Use 16.04 LTS which is supported until 2021. 

A rather important question: do you have any experience with Ubuntu and you know how to create a bootable USB installer?

PS: Are you sure you install an operating system on the actual robot? Sure you don't drive it with another device, i.e. a laptop? I get that impression when [I'm looking here]("http://www.mobilerobots.com/Software.aspx"). Seems it should have the Pioneer stuff already installed. If it has wireless, you'd communicate with it that way. Has it a screen or can attach to a screen? If so, then insert the USB stick and install. 

If you can post any links to info on this device, would be good, as I'm finding not much. You're not talking the **P**3-DX, a mobile mapping robot?

---

### Post by zameelshaki13 on 2017-06-29
Hey there Bucky,

Yes, I do have experience creating a bootable USB installer. And you're right, now that I checked, the 12.04 does have no support soon. Also, the robot can be run from my laptop AND use its onboard computer to run. It has both capabilities. I need a USB to serial converter in order to run the robot using my laptop, along with the Aria software that came along with an installation CD. The robot itself came with the option of having a pre installled CD. Whoever ordered it from my university (this is for a research project) did not order the OS or the USB to serial converter.  However, since this is a summer internship and I'm short on time, and I know ordering the converter might take a while, I wanted to install an OS for the onboard computer of the robot. 

[http://www.mobilerobots.com/ResearchRobots/PioneerP3DX.aspx](http://www.mobilerobots.com/ResearchRobots/PioneerP3DX.aspx)

That's the robot itself. It has three USB ports, I've used them all for a monitor, keyboard and the USB stick.

---

### Post by Bucky Ball on 2017-06-29
Yea. The one I was looking at. The P3-DX. You might like to change the title of your thread for clarity as you have the R3-DX, which don't think exists. ;)

Well, if you can plug a monitor in and a USB stick, guess it's a matter of installing the OS and seeing how you go. Is there something preventing this? Don't think I'd be using Ubuntu. Lot of things you would probably never use for something like this and just bloat you don't need. Xubuntu or Lubuntu might be a better choice.

(In an ideal world, you would go for a minimal install or a -core install and just install the bits you need for your project, but as you're squeezed for time and that would be a(nother) learning curve, go for the lightweight Xubuntu would be my advice. A basic, lightweight system.)

---

### Post by zameelshaki13 on 2017-06-29
Update: I've installed Ubuntu 16 on the robot itself. There are no issues so far.

---

### Post by zameelshaki13 on 2017-06-29
haha nice catch. It was pretty late at night when I made that post, but thanks none the less. I went with Ubuntu because there are a few interfaces that the robot have optimized for Ubuntu. I'll  let you know if I run into any more  issues.

---

### Post by Bucky Ball on 2017-06-29
To change thread title, edit first post and 'Go Advanced'. Good you got it installed and so far so good. ;)

(PS: All the Ubuntu flavours use the same Ubuntu kernel and I imagine that whatever has been optimised has been optimised for the Ubuntu kernel rather than any apps running in Ubuntu. All flavours also use the same repositories so anything that can be installed in Ubuntu (or any other flavour) can be installed in any other flavour. Flavour irrelevant. Same floorplan, different house design is all, if you know what I mean. ;))

---

### Post by zameelshaki13 on 2017-06-29
Hey Bucky,
Once again, thanks for helping me out, haha. I'll be sure to keep the fact that all flavors have the same kernels in mind.

---

### Post by Bucky Ball on 2017-06-29
All good. If you're happy, mark thread as solved to help others from Thread Tools at top right of page and post new thread for any new issues. Good luck with the project. Playing with robots and Linux sounds like fun!

---

