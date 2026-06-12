---
title: "Gaming in virtual machines"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by Diabolic66 on 2012-05-10
Hey there guys,

I've liked Ubuntu in a long time, but one thing holding me back from changing is games.

Nowadays with Wine it's getting easier and easier to play on Ubuntu. But there are still several games that don't work.
Although I like to fiddle around with Ubuntu, it gets kind of frustrating if you spend lots of time trying to make a game work and it doesn't work, or works poorly.

The other alternative, which is guaranteed to work if you have the required hardware, is, as indicated in the title, using a Windows virtual machine.

My question, after babbling all this time, is if the performance degrades drastically or enough not to be worth doing the VM, in terms of games (assuming my hardware is nothing special).

I've worked a bit with VMs in my work, but the computer is far more powerful and it's in a Windows environment.

If anyone has already experienced the adventure, please advise.

Thanks :)

---

### Post by KF5EUB on 2012-05-10
I am using VM VirtualBox running Windows XP right now to play GOG games like Wing Commander and Quest for Glory. I'm still a rookie and haven't yet figured out how to run them directly on Ubuntu but as far as performance goes it isn't bad at all. Keep in mind these are older games.

Epi

---

### Post by ixtok on 2012-05-10
Your best bet is a dual boot with whatever windows you are now using. I think that virtual machines have less performance and will not use your video card to the best efficiency.

---

### Post by kdane4 on 2012-05-10
> **ixtok said:**
> Your best bet is a dual boot with whatever windows you are now using. I think that virtual machines have less performance and will not use your video card to the best efficiency.

+1
If there 1 thing windows is better than linux, that is running games. I too recommend a dual boot.

Cheers!

---

### Post by kellemes on 2012-05-10
> **kdane4 said:**
> +1
If there 1 thing windows is better than linux, that is running games.

Windows games you mean..

There are a lot of fantastic Linux games that won't work on Windows at all.. ;-)

---

### Post by QIII on 2012-05-10
> **kellemes said:**
> Windows games you mean..

There are a lot of fantastic Linux games that won't work on Windows at all.. ;-)

And since many game engines are being ported to Linux there may eventually be games aplenty that will run on both platforms.

Back on topic:

Game performance, especially for graphics heavy games, will be severely limited by the nature of virtualization.  Virtualized OSes are at the mercy of the virtual graphics capabilities supplied by the virtualization software.  These are usually quite limited and intended for simple, basic functionality.  Your OS in a VM is not directly running your graphics card (or anything else) but on a hardware abstraction layer that has to communicate back and forth with your physical hardware.  This is inefficient and resource intensive.

You may get away with sub-optimal performance on some games, and find others simply will not work at all.

Although I am not much of a gamer, I understand that gaming is important to many people.  So I would suggest, in that case, that you stick with Windows for the Windows specific games you are interested in playing.  There is no better place to play Windows games than Windows.

If you want to use Linux for more mundane computer tasks, virtualization would be fine.

If you want to have full performance, dual booting is the way to go.  Then you could also play the emerging Linux games.  (Alien Arena, for instance, has a Linux version.  I've toyed with it and it seems pretty good from the perspective of a farty old man who doesn't game much.)

---

### Post by jockyburns on 2012-05-10
I used to love playing Eve online, when I had Win XP on my machine (had to change to Ubuntu after a HDD failure) tried for over a week to get it to run in Wine, finally managed to get it running, only to find it was virtually (no pun intended) unplayable. By the time you started firing lasers/missiles/railguns, at an opponent, you were floating in your egg. 
TBQH, that's the only thing I miss about Windoze..... When I eventually get a new computer, I reckon I'll dual boot, just so I can continue playing Eve.:):):)

---

### Post by Diabolic66 on 2012-05-14
Thank you for all your answers :)

The main problem here is the lack of game porting like QIII said, because what I really wanted, was Linux with Windows games :P

With dual boot, I'll just boot Windows and stay in Windows, rebooting to play games is too troublesome haha, that was the main reason for wanting to know how the performance (game-wise) of VMs is in the present.

I guess Ill have a VM with Linux inside Windows and fiddle with it.

---

### Post by kellemes on 2012-05-14
Maybe this an option?
[https://help.ubuntu.com/community/Xen]("https://help.ubuntu.com/community/Xen")

---

### Post by forrestcupp on 2012-05-14
Yeah, like QIII said, you're using virtual hardware, which is insufficient. Also, virtualized DirectX is still kind of beta. Things are getting much, much better than they were a couple of years ago, but it's still not a good solution for gaming.

> **Diabolic66 said:**
> 
With dual boot, I'll just boot Windows and stay in Windows, rebooting to play games is too troublesome haha, that was the main reason for wanting to know how the performance (game-wise) of VMs is in the present.

I guess Ill have a VM with Linux inside Windows and fiddle with it.That's probably your best choice right now. I understand the sentiment that it's too much of a hassle to reboot, so why waste my time ever booting into Linux. But you can still have fun fooling around with Linux in a VM. Things are changing for the good, though. See below.

> **kellemes said:**
> Maybe this an option?
[https://help.ubuntu.com/community/Xen]("https://help.ubuntu.com/community/Xen")Xen is kind of ahead of the game right now in this area. They're making progress on creating VMs that allow real hardware to be passed through, which will make things considerably better for gaming in a VM. I don't think it's quite up to snuff yet, and I've seen other people that haven't had success getting that to work well in Ubuntu. Still, it's very exciting, and something to keep an eye on.

---

### Post by TheGuyWithTheFace on 2012-05-14
> **Diabolic66 said:**
> Thank you for all your answers :)

The main problem here is the lack of game porting like QIII said, because what I really wanted, was Linux with Windows games :P

With dual boot, I'll just boot Windows and stay in Windows, rebooting to play games is too troublesome haha, that was the main reason for wanting to know how the performance (game-wise) of VMs is in the present.

I guess Ill have a VM with Linux inside Windows and fiddle with it.

Wait a Minute, I'm no gamer, but I do dual boot Win7 and Precise, and it's really not much of a hassle to reboot. I for one am thrilled with Ubuntu's Boot and Shutdown times, and windows, well... At the very least, You can improve Window's boot time with this:

[https://www.soluto.com/](https://www.soluto.com/)

Besides, Is it really any faster to boot in a virtual machine?

---

### Post by Diabolic66 on 2012-05-15
@kellemes, @forrestcupp: I guess I'll look into it with more detail. Having two OSes running at the same time sounds amazing! Especially if the two of the act like virtual machines and can communicate between them :)

@TheGuyWithTheFace: It's kind of a hassle when you play, and then stop and go to regular using, and then play again. The rebooting is a big hassle because I usually play while on Skype hanging out with friends, maybe messenger and the browser open. I just can't stand the lack of synch between OSes while on "chill mode". On "technician mode", it's really insignificant to reboot :P

---

### Post by forrestcupp on 2012-05-15
> **TheGuyWithTheFace said:**
> 
Besides, Is it really any faster to boot in a virtual machine?

No. But it's much, *much* faster to restore a snapshot. That only takes 5-10 seconds.

---

### Post by TheGuyWithTheFace on 2012-05-15
> **forrestcupp said:**
> No. But it's much, *much* faster to restore a snapshot. That only takes 5-10 seconds.

Restoring a snapshot... What is that again? Is it akin to hibernating? 

And yeah, diabolic, It can be a hassle to close all open programs and actually shut down, but why not hibernate back and forth?

---

### Post by forrestcupp on 2012-05-15
> **TheGuyWithTheFace said:**
> Restoring a snapshot... What is that again? Is it akin to hibernating? Kind of like hibernating, only it saves the state of your OS to the VM file. It just restores image of that state back to your RAM so you don't have to go through the boot process. That's one of the best things about virtual machines.

> **TheGuyWithTheFace said:**
> And yeah, diabolic, It can be a hassle to close all open programs and actually shut down, but why not hibernate back and forth?How can you hibernate from a real installation of Windows to a real installation of Linux? I've never seen any way to boot back into Linux, other than to shut down Windows. Is that some Wubi feature, or something?

---

### Post by TheGuyWithTheFace on 2012-05-15
> **forrestcupp said:**
> 

How can you hibernate from a real installation of Windows to a real installation of Linux? I've never seen any way to boot back into Linux, other than to shut down Windows. Is that some Wubi feature, or something?

No, I'm dual booting windows 7 and Ubuntu 12.04, and whenever I hibernate, when I turn the computer back on, grub just shows as normal, and I can choose what os to use as usual. I just tested hibernating in both at once, and it seems to work well. Isn't this normal?

---

### Post by Diabolic66 on 2012-05-16
> **TheGuyWithTheFace said:**
> No, I'm dual booting windows 7 and Ubuntu 12.04, and whenever I hibernate, when I turn the computer back on, grub just shows as normal, and I can choose what os to use as usual. I just tested hibernating in both at once, and it seems to work well. Isn't this normal?

I didn't even know that was possible, but there's still the delay of waiting for it to resume, it may be faster, but I only use Windows 7 on my laptop and it takes some minutes to restore from hibernation.

Also, I sometimes get network problems from hibernating too much, easy to solve, but I just want to be a regular user at home and don't have to fiddle with it a lot to be able to relax.

---

### Post by forrestcupp on 2012-05-16
> **TheGuyWithTheFace said:**
> No, I'm dual booting windows 7 and Ubuntu 12.04, and whenever I hibernate, when I turn the computer back on, grub just shows as normal, and I can choose what os to use as usual. I just tested hibernating in both at once, and it seems to work well. Isn't this normal?That's weird. I've never had that happen before. But I probably have it set to suspend rather than hibernate.

> **Diabolic66 said:**
> I didn't even know that was possible, but there's still the delay of waiting for it to resume, it may be faster, but I only use Windows 7 on my laptop and it takes some minutes to restore from hibernation.Yeah, from my experience of when I did hibernate, restoring from hibernation takes much, much longer than restoring a VM snapshot, and sometimes even longer than a regular boot. Because of that, I never really saw the point of hibernating, unless you just need to save the state of things.

---

