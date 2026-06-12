---
title: "Question regarding power usage  On new kernels"
date: 2011-08-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by gunksta on 2011-08-25
I bought a new lenovo x220, because I really need a fast, portable machine. It came equipped with a i5 2520 processor and the 32GB 7200 RPM hard drive. I bought it for two basic reasons. It is super portable (under 4 pounds) and does not use ULV processors, yet gets good battery life.

+1 to Intel for that combination.

Anywho, I decided to install Oneiric on it, since I don't need it to be a primary just yet. I figured I'd start off with the new hotness and all. But, when all the testing and updating is done, I want to make sure I am getting the best battery life possible. I've seen the Phoronix articles on all the power regressions in the Linux kernel which bothers me. It doesn't seem like these bugs should have lasted this long. But, I digress.

I'm not a kernel expert and I want to get some help assessing what I should install / run on this thing to maximize battery life. I know the repos often contain outdated stuff and I want to make sure I don't do something stupid.

I have always installed laptop-mode and cpufrequtils on mobile systems. The latter seems quite reasonable but the former pulls in hal. It is my understanding that the point of many recent developments was to leave hal and remove it from everyone's system. Is something like laptop-mode still needed or should I put up with hal for the time being?

Is there some way I can use powertop to tell is laptop-mode is going to do me any good?

---

### Post by cariboo on 2011-08-25
The best way to test the power usage, is to use Oneiric. I have a Compaq Mini 1100, I get 2.5 to 3 hours of usage when running on the battery like I always have, except for a very short period during Natty testing. Powertop will help you fine tune battery usage.

Keep in mind that Phoronix and web sites like it, are in the business of selling advertising, so anything they can come up with to get more page views will be published. You'd be much better off getting your news from [lwn.net]("http://lwn.net/"), as they are subscriber supported, not by advertisers.

---

### Post by hugmenot on 2011-08-25
You don’t need either of those packages. Nowadays pm-utils takes care of lowering power usage while on battery. Check the directory /usr/lib/pm-utils/power.d to see what scripts are run.

The power-saving CPU features (C states, P states, etc) are enabled by default on the modern CPUs.

What you can do is to look at stuff you don’t necessarily need running all the time (daemons and services). Powertop can help there. For instance RF-killing my wireless makes a difference on my machine.

---

### Post by gunksta on 2011-08-25
> **cariboo907 said:**
> The best way to test the power usage, is to use Oneiric. I have a Compaq Mini 1100, I get 2.5 to 3 hours of usage when running on the battery like I always have, except for a very short period during Natty testing. Powertop will help you fine tune battery usage.

Keep in mind that Phoronix and web sites like it, are in the business of selling advertising, so anything they can come up with to get more page views will be published. You'd be much better off getting your news from [lwn.net]("http://lwn.net/"), as they are subscriber supported, not by advertisers.

Yes, Phoronix makes money from advertisers, not subscribers, but on the other hand, Michael has developed an interesting suite of tools and published them under a FOSS license. AFAIK, nothing else of this sort exists for Linux systems. The unending parade of Ubuntu v. "Distro of the Week" gets a bit old, but being able to perform performance tests using real applications that stress hardware / software in semi-realistic ways seems valuable. I'll admit I don't know enough about the kernel or systems testing to genuinely critique his work, but I've not seen anything on any other site of similar depth.

---

### Post by gunksta on 2011-08-25
> **hugmenot said:**
> You don’t need either of those packages. Nowadays pm-utils takes care of lowering power usage while on battery. Check the directory /usr/lib/pm-utils/power.d to see what scripts are run.

The power-saving CPU features (C states, P states, etc) are enabled by default on the modern CPUs.

What you can do is to look at stuff you don’t necessarily need running all the time (daemons and services). Powertop can help there. For instance RF-killing my wireless makes a difference on my machine.

I know that part of what laptop-mode does is to reduce write-backs to the hard-drive and agressively spins the hdd down when not needed. I'm going to take a look at pm-utils/power and see what all I can find there and I definitely intend to use powertop to help ID what needs tweaking.

---

### Post by aeronutt on 2011-08-28
On my laptop (Dell Vostro), 11.04 draws about 900mA on battery, and 11.10 alpha3 is drawing about 1400mA on battery, with as many settings that I know about the same (power options, screen brightness, etc).

I've looked at powertop on 11.10, and didnt' see anything obvious that was causing significant power increase.

I'm hoping 11.10 final release gets that power down to near what 11.04 was.

---

### Post by grandtoubab on 2011-08-28
Hello,
that is a concern
[https://bugs.launchpad.net/ubuntu/oneiric/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/oneiric/+source/linux/+bug/760131)

---

### Post by gunksta on 2011-08-29
Irony - I uninstalled laptop_mode and the thinkfan utility and my battery life, as shown in powertop improved considerably. Apparently the thinkfan kernel module doesn't work well with the X220. Using powertop, I was able to slow the fan down when on battery. Using thinkfan, I was stuck with the fan running wide open, which killed my battery life.

The larger issues surrounding linux power usage are a concern and they need to be dealt with but I'm nor sue that is going to happen in Oneiric ( or Fedora for that matter, since this problem is clearly upstream.)

--thanks

---

### Post by kvv_1986 on 2011-08-29
The problem is apparently an improperly configured BIOS in many systems. There is a workaround.

[www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1]("http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1")

---

### Post by gunksta on 2011-08-30
I've seen the hack and I understand that the problem you are referring to lies in what the BIOS reports on affected systems. But, here's the problem. Folks like you and I (and most of the people who are testing a alpha/beta linux distro) can apply the fix easily. I think it took me 10 minutes and 8 of it was spent reading the comments on the Phoronix article.

But, if a random noob buys a system, installs linux and get fantastically crappy battery life, the fact that the problem lies in this "BIOS thing" doesn't matter. The noob will blame Linux.

Unfortunately (or perhaps fortunately) Linux can not afford to be good. It has to be damned near perfect.

---

