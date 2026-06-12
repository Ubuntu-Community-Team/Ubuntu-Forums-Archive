---
title: "problem installing ubuntu 12.04.1 server"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by ckaustav on 2012-10-23
I am facing a problem installing Ubuntu 12.04.1 server edition in my laptop pre-installed with windows 7 ultimate.When it reaches the partition phase it is not showing the windows partitions already present but instead new partitions which if created will result into data loss.So, what should i do to keep windows 7 untouched.please suggest a solution asap.
plz mail me at: [email]cpukan@gmail.com[/email]

---

### Post by Cheesemill on 2012-10-23
Can you boot from a Ubuntu Desktop Live CD and then fire up Gparted.

Take a screenshot and post it here so we can see what your partition setup looks like.
You may already have 4 primary partitions on you drive which would cause this behaviour.

---

### Post by snowpine on 2012-10-23
Welcome to the forums!

I recommend:

1. Perform a full backup of all Windows partitions. This will eliminate any risk of data loss.

2. Carefully follow these directions step by step. If you have any problems/errors then post back with details and we will attempt to help!

[https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)

---

### Post by ckaustav on 2012-10-24
I am uploading the screenshot taken by gparted and also in win 7.\plz check it out and reply asap.

---

### Post by 2F4U on 2012-10-24
From the screenshot it shows that you already have 4 primary partitions. So you are out of luck in installing Ubuntu or any other Linux system because you can have at max 4 primary partitons.
Ubuntu is showing your currently configured partitions, it is just not using the Windows naming convention of C:, E: and so on.

---

### Post by Cheesemill on 2012-10-24
Also you have your drive set up as a dynamic disk which are only recognised by Windows. You will need to convert it to a normal disk layout as well as changing one of your primary partitions into an extended partition.

Another option that would be a lot quicker and easier than a dual boot would be to install VirtualBox in Windows and then just run Ubuntu Server as a VM.

---

### Post by ColeTurner on 2012-10-24
> **ckaustav said:**
> I am facing a problem installing Ubuntu 12.04.1 server edition in my laptop pre-installed with windows 7 ultimate.When it reaches the partition phase it is not showing the windows partitions already present but instead new partitions which if created will result into data loss.So, what should i do to keep windows 7 untouched.please suggest a solution asap.
plz mail me at: [EMAIL="cpukan@gmail.com"]cpukan@gmail.com[/EMAIL]

Perhaps the first problem is you are installing the **server** edition on your laptop. I think you should try the desktop version,

---

### Post by krishna.988 on 2012-10-24
Try out Wubi install..if the partitioning is confusing..Just insert the ubuntu cd the wubi installer will start..

---

### Post by Cheesemill on 2012-10-24
> **ColeTurner said:**
> Perhaps the first problem is you are installing the **server** edition on your laptop. I think you should try the desktop version,
That won't make a difference.

The problem is the layout of the OP's hard drive, this is still a problem no matter which version he is trying to install.

---

### Post by ckaustav on 2012-10-24
So what is the procedure i should follow to change the layout of my hard disk partition so that win 7 is recognized by ubuntu.plz provide a step-by-step procedure.
Also if i were to use virtual box what should be the min. sys. req. And how should i implement it. plz enlighten me. ASAP...

one more thing..the drives are being shown as simple volume and not primary partition..

---

### Post by ckaustav on 2012-10-24
> **2F4U said:**
> From the screenshot it shows that you already have 4 primary partitions. So you are out of luck in installing Ubuntu or any other Linux system because you can have at max 4 primary partitons.
Ubuntu is showing your currently configured partitions, it is just not using the Windows naming convention of C:, E: and so on.
so what should i do...

---

### Post by snowpine on 2012-10-24
Here are easy instructions (with screenshots) to install Ubuntu inside Windows keeping your current disk partitioning scheme. If you are not comfortable/experienced with disk partitioning and don't have a full backup of your Windows data, then this is the only course of action I can recommend:

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by krishna.988 on 2012-10-25
Or you can use Wubi installer if you want to dual boot

---

