---
title: "[SOLVED] suspend and hibernation problems"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Tom--d on 2008-05-29
I'm running 32bit Hardy. 

I used to be able to have suspend working. Perfectly!
But for some reason. It just doesn't come out of suspend. It hangs on a blank screen. Well, the screen doesn't even light up.

hibernation doesn't work either. 
It stops loading on boot and I have to power off and boot up again. 


The **both** used to work. 
Why have they stopped working?

Suspend is the one I need.
I never use hibernation so I dont mind if that does not work.

Please help me get suspend working again. 

Thanks,
Tom :)

---

### Post by logos34 on 2008-05-29
The most recent kernel update killed mine too (same prob as you but I can hibernate/resume).  

Maybe go back to the -16 kernel

---

### Post by Tom--d on 2008-05-29
Ah, I see.

Thank you :) 

I will let you know if it worked.

---

### Post by Tom--d on 2008-05-29
Yes. It worked :)

Thanks!

---

### Post by pfeels on 2008-05-29
People, same thing here, a recent update stopped my Suspend from working, can you instruct me on how to go back and use the previous kernel, I haven't got a clue what your talking about but I'm trying ...

---

### Post by logos34 on 2008-05-29
> **pfeels said:**
> People, same thing here, a recent update stopped my Suspend from working, can you instruct me on how to go back and use the previous kernel, I haven't got a clue what your talking about but I'm trying ...

Change the 'default' line in /boot/grub/menu.lst to boot the -16 kernel:

Desktop panel>System>admin>startup manager>boot options tab>default operating system kernel box

---

### Post by pfeels on 2008-05-29
> **logos34 said:**
> Change the 'default' line in /boot/grub/menu.lst to boot the -16 kernel:

Desktop panel>System>admin>startup manager>boot options tab>default operating system kernel box


Startup Manager is not under System>Administration ... I'll search and see if i can find it anywhere else or maybe it has to be turned on somewhere
 
Either way I appreciate the help ... I'm using Hardy

I found it in the repository and installed it System>Administration>Synaptic Package Manager

---

### Post by nutpants on 2008-05-29
i really have to ask as a new ubuntu user..

how is downgrading your kernal  a "bug solved" situation???

i know i may get flamed for this but..

is that not like throwing the baby out with the bath water??

nutz

---

### Post by pfeels on 2008-05-29
> **nutpants said:**
> i really have to ask as a new ubuntu user..

how is downgrading your kernal  a "bug solved" situation???

i know i may get flamed for this but..

is that not like throwing the baby out with the bath water??

nutz

Hey I've been using Ubuntu for about 4 months and I cringe when i ask questions but how else are we suppose to learn ...

---

### Post by pfeels on 2008-05-29
I tried it out and it worked, it still gives me a blank white screen after it comes back but it did that before and i just type in my password and it works fine ...

Now does this mean I should avoid updates on the Kernel and if so is the Kernel an important piece of software?

Again thanks for teaching ...

---

### Post by logos34 on 2008-05-29
> **pfeels said:**
> I tried it out and it worked, it still gives me a blank white screen after it comes back but it did that before and i just type in my password and it works fine ...

Now does this mean I should avoid updates on the Kernel and if so is the Kernel an important piece of software?

I wonder if that blank has anything to do with your graphics card splash screen...

If another update comes out (-18), accept it...it will be added to the others.  Try it--if it doesn't work, continue using the -16.  The default grub option is to keep all kernels:

> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

so it's not like it's going to delete the older ones.

Linux IS the kernel. tres important 

This is the way I'm doing things until I find a workaround or someone suggests a better alternative.  I simply must be able to suspend and hibernate.

---

### Post by pfeels on 2008-05-29
> **logos34 said:**
> I wonder if that blank has anything to do with your graphics card splash screen...

I simply must be able to suspend and hibernate.

I agree with you on the have to have suspend, thanks for your help and I'll research the splash screen, it doesn't happen every time but it's more than 50% of the time ... But isn't this what Linux is, over coming these minor issues and hoping they don't turn into major ones ... :)

---

### Post by Tom--d on 2008-05-30
```
sudo apt-get install startupmanager
```

Then go to System > Admin > StartUp-Manager

Default OS to > Ubuntu 8.04, kernel 2.6.24-16-generic

And your done :)

If you want to change on boot up.
When you see grub. Press ESC. it will show you the list of them

---

### Post by pfeels on 2008-05-30
Thanks Tom ...
Logas34 already gave me the same and it worked but always good to simplify it for others who will no doubt be checking ... in fact I'll do a search for other similar threads and copy your instructions ... thanks again guys

---

### Post by Tom--d on 2008-05-30
No problem :)

Glad I could help!

---

### Post by ercferret18 on 2008-05-30
does anyone know how to do this? i'm new to ubuntu

---

### Post by pfeels on 2008-05-30
> **ercferret18 said:**
> does anyone know how to do this? i'm new to ubuntu


Are you having this problem, your computer won't suspend since installing recent updates?

If so go to TERMIL
Applications>Accessories>Terminal

and input this command:


sudo apt-get install startupmanager



Then go to System > Administration > StartUp-Manager

where it says

Default OS to 

Click on the drop down arrow and change it to 

Ubuntu 8.04, kernel 2.6.24-16-generic

let me know if you get lost ...

---

### Post by ercferret18 on 2008-05-31
yup, i got it, but my question is will this be any different from using the -17 version

---

### Post by lordmyth on 2008-05-31
did somebody file a bug yet?
because this is pretty ridiculous...

---

### Post by philferrar on 2008-05-31
This worked a treat - many thanks. It might be useful to add a comment [for other novice users like myself] that after doing the changes you still need to re-load the system [which reports the usual disk check problem, again] then to another hibernate/close before being able to 'get back to normal'.

---

### Post by Delawaredave on 2008-05-31
I just did above - worked great - Sony PCV 550 wouldn't hibernate.

---

### Post by pfeels on 2008-05-31
Well the 17 version is an update so there is a difference somewhere but what it is i don't know ... and I'm not sure where to report the bug

---

### Post by pfeels on 2008-05-31
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/236272](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/236272)

It was reported ...

---

### Post by ercferret18 on 2008-05-31
ok it doesn't seem to be that much different... it just doesn't work as well when playing games but that can be solved by disabling compiz

---

### Post by nutpants on 2008-06-03
Ubuntu 8.04, kernel 2.6.24-18-generic  fixed my issues.

my xps 1210 suspends and hibernates fine now.

nutz

---

### Post by ercferret18 on 2008-06-03
> **nutpants said:**
> ubuntu 8.04, Kernel 2.6.24-18-generic  Fixed My Issues.

My Xps 1210 Suspends And Hibernates Fine Now.

Nutz

Are You Serious? It Still Doesn't Work For Me, Even With The -18 One, I Still Have To Use The -16 One. Whats Wrong With My Machine??

---

### Post by glennric on 2008-06-03
> **ercferret18 said:**
> Are You Serious? It Still Doesn't Work For Me, Even With The -18 One, I Still Have To Use The -16 One. Whats Wrong With My Machine??

Same here.  The 2.6.24-18-generic kernel breaks suspend and resume.

---

### Post by momaya on 2008-06-04
Thanks very much. We wasted hours after screen went blank after hibernation. Nothing seem to work; not even hard boot. Ultimately, I disconnected power as well as battery & on reconnect, the screen came back. Advise: DO NOT TRY HIBERNATION, IF NOT AN EXPERT.

---

### Post by logos34 on 2008-06-04
-18 update didn't solve the problem for me either (to be specific I'm using the x86_64 -rt kernel rather than generic--ubuntustudio here)

I guess I'm stuck on -16 release

---

### Post by ercferret18 on 2008-06-04
I dont really care about hibernate, dont even use it, all i want is suspend!!!

OMG hey my computer started from suspend, but after like 10 minutes lol, so if u wait for like 10 minutes it really does start... wierd.

---

### Post by pfeels on 2008-06-04
They are working on 19, their first attempt fixed the suspend but there were problems with other things, they are working on it and it's high priority, great bunch of guys ...

---

### Post by ercferret18 on 2008-06-04
ok thanks, all i wanted to know is that they are working on it!

---

### Post by ercferret18 on 2008-06-04
ok check that, it starts up in about 20 minutes for me, i just timed it

---

### Post by mbw163 on 2008-06-20
downgrading to -16 kernel did not work for me. :(

First time I tried it before it worked and didnt want to come out of stand by. Now when I changed hte Post_video to false it wouldnt even standby

---

### Post by praveenpious on 2008-06-21
I have installed the -19 kernel, but resume from hibernation still not working for me :(

---

### Post by Tom--d on 2008-06-21
I know suspend works with the -19 kernel. Have not checked Hibernation as I never use it.

-17 and -18 broke my suspend.

-16 -19 fixed it :D

What what -20 will do >.>

---

### Post by pfeels on 2008-06-21
Same with me, I only use Suspend ...

---

### Post by thanos_pc on 2008-06-22
For me is the opposite..with -19 works only hibarnation but not the suspend...

---

