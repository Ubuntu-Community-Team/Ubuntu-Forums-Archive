---
title: "[Ubuntu]New to it and love it but question where can I get drivers for my dell vostro"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by inimitablesikh on 2008-07-18
I have a Dell vostro 1000 laptops I am running ubuntu under vmware getting a full feel and then wil make it my primary os but first is there a tool that i can use to get drivers for my machine automaticall free or not i want one....also i am running ubuntu 8.x and one more thing where can i get the cool beryl theme and how do i apply it and all?

---

### Post by ad_267 on 2008-07-18
What drivers do you need? Most things should just work. Beryl has been merged with compiz and is now compiz-fusion. Read this to find out more: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

I'm not sure if you can run compiz-fusion under vmware though.

---

### Post by hansdown on 2008-07-18
There is a download site for drivers. Hope it helps. [http://support.dell.com/support/downloads/index.aspx?c=us&l=en&s=gen&~ck=gp](http://support.dell.com/support/downloads/index.aspx?c=us&l=en&s=gen&~ck=gp)

---

### Post by inimitablesikh on 2008-07-18
> **ad_267 said:**
> What drivers do you need? Most things should just work. Beryl has been merged with compiz and is now compiz-fusion. Read this to find out more: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

I'm not sure if you can run compiz-fusion under vmware though.

That isn't working I have an AMD Athlon 64x2 processor with integrated graphics which is ati radeon xpress 1150...and when I go to system preferences there is nothing that says restricted driver settings or anything like that

---

### Post by HDave on 2008-07-18
You cannot run 3d graphics inside VMWare.  All hardware devices inside virtual machines are faked by the VM software.

If you want compiz enabled, you'll have to install Ubuntu to your internal hard drive, an external hard drive, or a USB stick.  Or you can boot via the live CD which will not mess with your system.

Once you boot Ubuntu without the VM, you will have an option to enable your restricted graphics driver.

As far as drivers go, Linux already comes with almost every driver you'll need pre-loaded into the kernel.  How cool is that!  I am using a Dell XPS M1210 laptop and almost everything worked out of the box.  

The drivers available from Dell won't work as they are for windows not linux.  The only exception to all this is wifi drivers.

If you want to see how well your laptop is supported you should check out the Ubuntu laptop testing wiki....its awesome!

---

### Post by inimitablesikh on 2008-07-19
> **HDave said:**
> You cannot run 3d graphics inside VMWare.  All hardware devices inside virtual machines are faked by the VM software.

If you want compiz enabled, you'll have to install Ubuntu to your internal hard drive, an external hard drive, or a USB stick.  Or you can boot via the live CD which will not mess with your system.

Once you boot Ubuntu without the VM, you will have an option to enable your restricted graphics driver.

As far as drivers go, Linux already comes with almost every driver you'll need pre-loaded into the kernel.  How cool is that!  I am using a Dell XPS M1210 laptop and almost everything worked out of the box.  

The drivers available from Dell won't work as they are for windows not linux.  The only exception to all this is wifi drivers.

If you want to see how well your laptop is supported you should check out the Ubuntu laptop testing wiki....its awesome!

Thanks so much also, How do I log in as root or whatever....I want to install vmware tools

---

### Post by ad_267 on 2008-07-19
Read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) and [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by HDave on 2008-07-19
The installation of vmware tools is super easy.  Check it out:

[http://https://help.ubuntu.com/community/VMware/Tools]("http://https://help.ubuntu.com/community/VMware/Tools")

I ran Ubuntu inside a VM for 6 months before finally committing and installing it on a bootable USB key.  Six months after that I can't even remember the last time I booted Windows...

Also -- a fun way to thank people in the forums is to hit the "thank you" button on the post that really helped you.

---

