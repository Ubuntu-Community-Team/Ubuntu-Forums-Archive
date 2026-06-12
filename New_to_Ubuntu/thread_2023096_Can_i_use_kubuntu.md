---
title: "Can i use kubuntu ?"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by tahsin rahman on 2012-07-12
my desktop pc configaration :

1. processor : intel core 2 duo processor e7500 , 2.93 ghz , 3mb chache
.
2. 500gb hdd
.
3. 2gb ram
.
4. mainboard : intel dg41wv
.
i have no graphics card
.
this is my desktop pc configaration. can i use 64 bit kbuntu in my pc ? please help me
.
another question is
can use 64 bit ubuntu with kde ?

---

### Post by Shadius on 2012-07-12
I don't think you can run 64-bit Kubuntu but 32-bit, definitely.

---

### Post by robtygart on 2012-07-12
> **tahsin rahman said:**
> my desktop pc configaration :

1. processor : intel core 2 duo processor e7500 , 2.93 ghz , 3mb chache

2. 500gb hdd

3. 2gb ram

4. mainboard : intel dg41wv

i have no graphics card

this is my desktop pc configaration. can i use 64 bit kbuntu in my pc ? please help me

Yes and it will be beautiful. Lots of eye candy. My laptop is a little older and it runs it very nicely.

Edit: 
Did not see the 64 bit part, I am running 32bit.

---

### Post by tahsin rahman on 2012-07-12
> **Shadius said:**
> I don't think you can run 64-bit Kubuntu but 32-bit, definitely.

thank you . another question is , can use 64 bit ubuntu with kde interface ?

---

### Post by Shadius on 2012-07-12
> **tahsin rahman said:**
> thank you . another question is , can use 64 bit ubuntu with kde interface ?

Well, you only have 2 GB RAM and 64-bit will take advantage of 4 GB RAM if you had it. Yes, you can use Ubuntu with the KDE interface.

---

### Post by deadflowr on 2012-07-12
> **tahsin rahman said:**
> thank you . another question is , can use 64 bit ubuntu with kde interface ?

Now do you mean, can you run a KDE interface through your existing Ubuntu system? Yes just install kubuntu-desktop.

As for 64bit with 2GB ram, Shadius has a point in that, while your system should be able to run 64bit, you'd probably be better served running in 32bit(or if possible adding more ram). Running 64bit with that ram size, you'd need to keep a wary eye on the ram usage more then if you had 4GB or more. But 2GB is certainly doable, if you limit the number of open applications running at one time.

---

### Post by Shadius on 2012-07-12
> **deadflowr said:**
> Now do you mean, can you run a KDE interface through your existing Ubuntu system? Yes just install kubuntu-desktop.

As for 64bit with 2GB ram, Shadius has a point in that, while your system should be able to run 64bit, you'd probably be better served running in 32bit(or if possible adding more ram). Running 64bit with that ram size, you'd need to keep a wary eye on the ram usage more then if you had 4GB or more. But 2GB is certainly doable, if you limit the number of open applications running at one time.

Right, if you want to take full advantage of a 64-bit OS, install more RAM! Feed the beast! :) Since you said you had 2 GB of RAM, I suggested you stick with 32-bit even though your processor can clearly handle 64-bit. Yes, you can definitely have the KDE experience within Ubuntu. I recently tried doing LXDE on Ubuntu. LXDE was ugly, but Lubuntu was beautiful.  :lolflag: I should mention (correct me if I'm wrong) that when you install *kubuntu-desktop*, it may replace your Ubuntu loading screen with Kubuntu's loading screen. It did that for me when I installed *lubuntu-desktop*. I'm pretty sure there is a way to get back your Ubuntu loading screen though. Just something to look out for. :)

---

### Post by mastablasta on 2012-07-12
if the CPU is 64 bit then you can use 64 bit or 32 bit OS. it's just that it won't bring so much advantage if you don't have more ram to back it up.
 
on the other hand if CPU is 32 bit you can't use 64 bit OS. a simple test is to boot a live 64 bit system to see if the computer can run it. boot it from a CD or USB and select try it.
 
but bottom line 64bit or 32bit os doesn't have so much to do with RAM as it does with CPU.
 
by the way you PCU is 64 bit.:
Intel® 64
Yes
 
[http://ark.intel.com/products/36503/Intel-Core2-Duo-Processor-E7500-(3M-Cache-2_93-GHz-1066-MHz-FSB](http://ark.intel.com/products/36503/Intel-Core2-Duo-Processor-E7500-(3M-Cache-2_93-GHz-1066-MHz-FSB))
 
btw you do have a graphics card becuase without it you can't see anythign on monitor. it could be just a chip on motherboard or inside CPU (e.g. core i have it in CPU).
 
to see which one it is boot into the live OS and type this command into terminal (or copy and paste it in):
 
```
 
lshw

``` 
it will list all your hardware including graphics chip

---

### Post by Shadius on 2012-07-12
> **mastablasta said:**
> if the CPU is 64 bit then you can use 64 bit or 32 bit OS. it's just that it won't bring so much advantage if you don't have more ram to back it up.
 
on the other hand if CPU is 32 bit you can't use 64 bit OS. a simple test is to boot a live 64 bit system to see if the computer can run it.
 
but bottom line 64bit or 32bit os doesn't have so much to do with RAM as it does with CPU.

What you can do is test both 64-bit and 32-bit and see how they perform.

---

### Post by deadflowr on 2012-07-12
> **Shadius said:**
> I should mention (correct me if I'm wrong) that when you install *kubuntu-desktop*, it may replace your Ubuntu loading screen with Kubuntu's loading screen. It did that for me when I installed *lubuntu-desktop*. I'm pretty sure there is a way to get back your Ubuntu loading screen though. Just something to look out for. :)

Yes, the other desktop environments do do that when installed in Ubuntu, to fix it I find the easy solution is to uninstall the package plymouth-theme-whatevertheDEis-logo. It's very easy to do in synaptic(For the OP synaptic was the old package manager, which was replaced by the Ubuntu software centre, you can still install it, though.) Be warned, though I do this, and my systems haven't gone crazy from uninstalling this package, I do not know whether uninstalling it has any adverse effects on the overall DE. but thankfully, nothing wrong has happened yet.

---

### Post by Shadius on 2012-07-12
> **deadflowr said:**
> Yes, the other desktop environments do do that when installed in Ubuntu, to fix it I find the easy solution is to uninstall the package plymouth-theme-whatevertheDEis-logo. It's very easy to do in synaptic(For the OP synaptic was the old package manager, which was replaced by the Ubuntu software centre, you can still install it, though.) Be warned, though I do this, and my systems haven't gone crazy from uninstalling this package, I do not know whether uninstalling it has any adverse effects on the overall DE. but thankfully, nothing wrong has happened yet.

The code that was suggested to me to get back my Ubuntu loading screen is the following: 
```
sudo update-alternatives --config default.plymouth
```

---

### Post by tahsin rahman on 2012-07-12
one thing , if i use a huge amount of swap , can i use 64 bit ?

---

### Post by Shadius on 2012-07-12
> **tahsin rahman said:**
> one thing , if i use a huge amount of swap , can i use 64 bit ?

Swap depends on your RAM. Usually, it's recommended to use double the amount of RAM you have for your swap space. So you'd probably use 4 GB swap space. That still doesn't mean that your processor will be able to perform to its full potential with just 2 GB RAM.

---

### Post by deadflowr on 2012-07-12
> **Shadius said:**
> The code that was suggested to me to get back my Ubuntu loading screen is the following: 
```
sudo update-alternatives --config default.plymouth
```

+1. I've added this to my ever growing command lines I'll never memorize but may someday need list. Thanks.

> **Shadius said:**
> Swap depends on your RAM. Usually, it's recommended to use double the amount of RAM you have for your swap space. So you'd probably use 4 GB swap space. That still doesn't mean that your processor will be able to perform to its full potential with just 2 GB RAM.

+1. Swap size will be somewhat helpful, but it won't be fully helpful. At this point I'd just stick with 32bit, unless you've planned to upgrade various components. But just because you might be running 32bit instead of 64bit, that doesn't mean you can't download the 64bit version as well(in case you later on get a more advanced system setup)

---

### Post by Shadius on 2012-07-12
> **deadflowr said:**
> +1. I've added this to my ever growing command lines I'll never memorize but may someday need list. Thanks.



+1. Swap size will be somewhat helpful, but it won't be fully helpful. At this point I'd just stick with 32bit, unless you've planned to upgrade various components. But just because you might be running 32bit instead of 64bit, that doesn't mean you can't download the 64bit version as well(in case you later on get a more advanced system setup)

You're welcome. Do you happen to have that list on a wiki or something online? I find myself having to go through my old threads in trying to find these commands. That list would be great to include in my signature or even bookmark! Hmm...maybe a side project? ;)

---

### Post by mastablasta on 2012-07-12
> **tahsin rahman said:**
> one thing , if i use a huge amount of swap , can i use 64 bit ?
 
 
ok why would you use a 32bit OS if you have a 64 bit system and the OS you want to use works on it?
 
the only reason might be some specific obscure programme that can't work under 64bit. otherwise i see no reason. in fact they wanted to recomend the 64 bit version but then went back to recommending the 32bit because there are plenty old CPU's running Ubuntu that are 32bit only. still in a few years i tiwll probabyl be recommended version. 
 
again  - RAM doesn't matter in this case. 32bit support up to 3GB natively but also up to (i think) 64GB ram with PAE kernel.
 
64 bit or 32bit is connected with cpu not ram: [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by oldos2er on 2012-07-12
> **tahsin rahman said:**
> thank you . another question is , can use 64 bit ubuntu with kde interface ?

No offense to Shadius, but (s)he's mistaken. 64-bit Kubuntu will run perfectly fine on your Core 2 Duo with 2GB RAM. I ran it with that same configuration for quite awhile. CPU-intensive tasks will be noticeably faster; everyday tasks such as web surfing and email will not be much different.

If you have a laptop and are planning to use hibernate, you'll need a swap partition of at least 2GB, same as the amount of RAM. For a desktop system, I had a swap of 1GB, and it rarely was used.

---

### Post by Shadius on 2012-07-12
> **oldos2er said:**
> No offense to Shadius, but (s)he's mistaken. 64-bit Kubuntu will run perfectly fine on your Core 2 Duo with 2GB RAM. I ran it with that same configuration for quite awhile. CPU-intensive tasks will be noticeably faster; everyday tasks such as web surfing and email will not be much different.

If you have a laptop and are planning to use hibernate, you'll need a swap partition of at least 2GB, same as the amount of RAM. For a desktop system, I had a swap of 1GB, and it rarely was used.

None taken. At least, now I know better, and I'm a he. :)

---

