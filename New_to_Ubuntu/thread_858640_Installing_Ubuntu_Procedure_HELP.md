---
title: "Installing Ubuntu Procedure HELP"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by GeorgK51 on 2008-07-13
Hi,

I'm trying to install Ubuntu 8.04 unsucessfully with LiveCD.

[LIST]
[*]When I choose Option #2, Install Ubuntu, the LiveCD takes me to what I think is a command prompt with ubuntu@ubuntu:~$
[*]When I choose Option #1, Try Ubuntu Without any Change, a window appears asking me to confirm if I want to continue in Low Graphics, and after my confirmation, it hangs with *Starting Deferred Execution [OK] *Checking battery state [OK] *Running local boot scrips (etc/rc.local) [OK]
[/LIST] 

Tried Checking CD for Defects and no errors were found. Tried burning another CD and I still get the same results....

-George

---

### Post by ChameleonDave on 2008-07-13
It sounds like Ubuntu is having problems with your hardware.

We need info to see what is wrong.

Boot up with the live CD again.

Get to a command prompt, and log in with the user name "ubuntu", and the password "".

Do this command:

```

sudo lshw

```That will give you a list of the details of your system.  

Now, saving those results to a file so that you can show them to us is not actually difficult, but it might be a bit tricky to explain.  It may be easier to jot them down.

Alternatively, you can gather that information from any other operating system on the machine.  Or perhaps you already have it written down.  I'm interested in your video card in particular.

---

### Post by GeorgK51 on 2008-07-14
> **ChameleonDave said:**
> It sounds like Ubuntu is having problems with your hardware.

We need info to see what is wrong.

Boot up with the live CD again.

Get to a command prompt, and log in with the user name "ubuntu", and the password "".

Do this command:

```

sudo lshw

```That will give you a list of the details of your system.  

Now, saving those results to a file so that you can show them to us is not actually difficult, but it might be a bit tricky to explain.  It may be easier to jot them down.

Alternatively, you can gather that information from any other operating system on the machine.  Or perhaps you already have it written down.  I'm interested in your video card in particular.
The video card is an Nvidia 9600GT. I'm a TOTAL noob when
 it comes to linux. When you say the command prompt you mean "ubuntu@ubuntu:~$"? What is the command to log in then? Sorry for the questions and thanks for your patience!

---

### Post by z.s.tar.gz on 2008-07-14
Since you are using the liveCD, when you go into the command line, you aren't asked to log in... (At least, it shouldn't)

What Dave means is,

When you get into the command line, type in "sudo lshw" without the quotes.

It should ask you for a password, but just press enter. Then just post the output.

---

### Post by ChameleonDave on 2008-07-14
> **GeorgK51 said:**
> When you say the command prompt you mean "ubuntu@ubuntu:~$"? 
Don't worry about being a newbie.  We all were once.

Yes, that's the prompt.  Great!  If you see that, you can enter commands.

I gave the log-in details because in certain circumstances people have reported being faced with a log-in screen on the live CD.  But if it lets you access a command terminal without logging in, so much the better!

---

### Post by GeorgK51 on 2008-07-17
Ok here it goes:

ilesystem=ntfs label=New Volume state=clean
      *-volume:1
        description: Windows NTFS volume
        physical id:2
        bus info:scsi@1:0.0.0.2
        logical name: /dev/sde2
        version: 3.1
        serial: ...........
        size: 37018
        capacity: 37018
        capabilities: primary bootable ntfs initiated
        configuration: clustersize=4096 created=2008-07-09
ilesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true
state=dirty upgrade_on_mount=true
      *-serial UNCLAIMED
        description: SMBus
        product: 82801G (ICH7 Family) SMBus Controller
        vendor: Intel Corporation
        physical id: 1f.3
        bus info: pci@0000:001f.3
        version: 01
        width: 32 bits
        clock: 33mhz
        configuration: latency=0
ubuntu@ubuntu:~$

Don't know if it helps. I have a 80GB HD with two partitions and in one of them I have installed Windows Vista. What I want to do is install Ubuntu in the other partition (if I can get past this command prompt :-). Thanks. -George

---

### Post by seagullplayer77 on 2008-07-17
Maybe you could try using the alternate install CD instead of the live one. I'm not entirely sure that it'll solve your problem, and things aren't too intuitive when you use the alternate CD (read: not impossible to follow, but not impossible to get lost either), but it's worth a shot. Good luck!

---

### Post by cariboo on 2008-07-17
You could trying starting in safe graphics mode. At the menu hit F4 select safe graphics mode and hit enter. Choose the menu item you want ant hit enter again. This should get you running.

Jim

---

