---
title: "Lubuntu 16.04 is slow when using Chrome browser with 2 or 3 tabs"
date: 2017-02-20
forum: New to Ubuntu
---

### Post by brspradeep on 2017-02-20
Hello all,
I have been using Ubuntu 10.04 LTS and later upgraded to 12.04. Currently I have installed 16.04.1 LTS (Lubuntu) freshly as it can run on lesser resources. 
This is a dual boot system with Windows as the other OS.

My Desktop system is 
CPU: AMD Athlon 64 2800+
RAM: 1 GB RAM
Hard Disk: 80 GB 
It seems to have inbuilt VIA Graphics. And I have dual boot system with Windows XP.
My monitor resolution is set to 1280 x 800(as per xrandr).

With 16.04, I noticed considerable performance degradation while using Chrome browser(generally 2 - 3 tabs) or other applications like sound applications or opening document using LibreOffice(occasionally).
This was not the case when I was using 10.04 earlier. Even though with Ubuntu 12.04 there was slow response, but I thought this was because I am using Ubuntu which is resource hungry.
Hence my decision to go for Lubuntu 16.04.

The boot and shutdown times seems to be Ok. Though I havent timed, the boot and shutdown time of 16.04 is less than 12.04.

I also use Rapidsvn to checkout svn repositories and/or commit the changes.
Whenever I am actively browsing chrome or trying to do commit with Rapidsvn(occasionally) I notice that the CPU touches 100% for few seconds or there are bursts of 100%. 
This i see from the "Resource Monitors" in the Panel. So much so, that sometimes the characters typed get jumbled or dont get typed at all!

When I see the task manager, it seems that Chrome and Xorg seem to be taking much CPU(5- 7% generally. But can go upto 30-50%).
If I try to scroll up and down in a page in Chrome, the CPU usage shoots to 96% with Xorg taking around 49%. This is again momentary. It again falls to single digit values within short time.
The Memory shows around 558 MB of 928 MB used(I have 1 GB RAM).

I am sort of a novice when it comes to Ubuntu or any OS for that matter and any help in improving the performance really helps.
I can assure that I will try to google if there are suggestions and will try to implement.

Thanks,
Srinivasa Pradeep

---

### Post by lysander6662 on 2017-02-20
I am no way as experienced as other users here but I would guess it's something to do with your RAM. As far as I understand, Ubuntu needs 2GB minimum to run well. It may be worth your trying another derivative of Ubuntu like Xubuntu, which is configured for systems with lower specs. I know it says 512BM RAM in the system requirements, but, from reading around, it seems that 2GB minimum is far more realistic. I find that even 'recommended' system requirements can be quite optimistic and not apply in all cases, so it can be worth shooting above them.

[http://askubuntu.com/questions/316560/can-ubuntu-run-on-512mb-ram?noredirect=1&lq=1](http://askubuntu.com/questions/316560/can-ubuntu-run-on-512mb-ram?noredirect=1&lq=1) 

[http://askubuntu.com/questions/333795/what-are-the-system-requirements-for-each-flavour-of-ubuntu-desktop](http://askubuntu.com/questions/333795/what-are-the-system-requirements-for-each-flavour-of-ubuntu-desktop)

---

### Post by cmcanulty on 2017-02-20
The poster already said he switched to Lubuntu.

---

### Post by lysander6662 on 2017-02-20
Ah indeed. Apologies, would be interested to see further comment on this.

---

### Post by mastablasta on 2017-02-20
> **brspradeep said:**
>  
It seems to have inbuilt VIA Graphics. And I have dual boot system with Windows XP.


via support is a hit or miss. it is quite possible that CPU is doing the rendering rather then GPU.

you say it is a desktop system, so upgrading should be possible. depending on your slot get a cheap used GPU card. if you need AGP slot support i can suggest ATI radeon 9600 or 9800 (if you can find a used one). If you can find a Radeon HD3650 AGP model it is even better. the 9200 or lower might bring you to same issue as the GPU is not so well supported (not all features are enabled).  
There is an nvidia model with legacy drivers support. 6000 something... can't say for sure.

if you have PCIe slot your choice is bigger. as well as using a newish GPU like GT 620 (entry) or maybe even GT730 (load proprietary drivers). a couple of low end AMD cards should also have descent opensoruce driver support.
if you go with used then nVidias will serve you well with proprietary drivers as well as AMD radeon HD 36xxx, 4xxx, 5xxx, and maybe even 6xxx. though be advised that 5xxx and 6xxx should work better with 16.10 and later 17.04 than with 16.04. new kernel expands suport. of course an option is also to wait for 16.04.3 release which will also land you with updated kernel.

another option is also to troubleshoot the VIA chip. perhaps there is a kernel switch or some workarroudn that enables better support for it. you need make and model and search google for known issues and possible solutions. still it would benefit you to get a newer card. but for such an old machine a used one might be necessary and they shouldn't cost you that much.

if you are in upgrade mode i would suggest if possible to upgrade ram to at least 2 GB. it will help you keep things smooth. although or browsing you should get away with 1 GB.

among other i have an old:
AMD64 3800+
Radeon 9200 128MB
1 GB RAM
Kubuntu with all effects turned off.

works relatively well for browsing. can't do many games as chip does not have hardware acceleration support. or at least it did until it fell silent and became a hardware donor :-)

---

### Post by Impavidus on 2017-02-20
> **brspradeep said:**
> 
If I try to scroll up and down in a page in Chrome, the CPU usage shoots to 96% with Xorg taking around 49%. This is again momentary. It again falls to single digit values within short time.
The Memory shows around 558 MB of 928 MB used(I have 1 GB RAM).Chrome is known for using a lot of memory, but that doesn't seem your main issue here. Xorg taking 49% of your CPU time points at the graphics card, so ...

> **mastablasta said:**
> via support is a hit or miss. it is quite possible that CPU is doing the rendering rather then GPU.

Fully agree with that.

---

### Post by brspradeep on 2017-02-20
> **mastablasta said:**
> via support is a hit or miss. it is quite possible that CPU is doing the rendering rather then GPU.

you say it is a desktop system, so upgrading should be possible. depending on your slot get a cheap used GPU card. if you need AGP slot support i can suggest ATI radeon 9600 or 9800 (if you can find a used one). If you can find a Radeon HD3650 AGP model it is even better. the 9200 or lower might bring you to same issue as the GPU is not so well supported (not all features are enabled).  
There is an nvidia model with legacy drivers support. 6000 something... can't say for sure.  


Thank you for the inputs. Actually I am not thinking of upgrading the desktop at this point of time.
Is there something that can be done to better support the rendering?

Thanks,
Srinivasa Pradeep

---

### Post by mastablasta on 2017-02-21
please post your hardware:

```
lshw -sanitize
```

if it was working before perhaps a feature needs to be turned on. then again it is also possible that there is no good support for the chip available anymore.

a descent used graphics card would be your best option. perhaps you can get one somewhere for free (repair shop?!), or nearly free.

---

### Post by HermanAB on 2017-02-22
Chrome has several options regarding background rendering that you can turn off, which will make it much faster.

---

### Post by brspradeep on 2017-02-23
> **HermanAB said:**
> Chrome has several options regarding background rendering that you can turn off, which will make it much faster.

Hmm. I am not sure about the options. I need to look deeper. Please let me know if you know any options.

Thanks,
Srinivasa Pradeep

> **mastablasta said:**
> please post your hardware:

```
lshw -sanitize
```


I did the following. I installed the openchrome drivers from synaptic package manager. 
After reboot, the response seems to be somewhat better. The CPU is not hitting 100% during scroll in Chrome.(It is 80+ though)

> **mastablasta said:**
> 
if it was working before perhaps a feature needs to be turned on. then again it is also possible that there is no good support for the chip available anymore.

a descent used graphics card would be your best option. perhaps you can get one somewhere for free (repair shop?!), or nearly free.


Do you have any inputs on fixing the jumbling of characters?
When I start typing in the address bar of chrome or leafpad or even on terminal and CPU is 100%, the characters get jumbled.
For eg: If I type HELLO, I may see EHLOL or any other combination other than the original order(HELLO).
This happens always when CPU stays at 100% for some time (for eg: few seconds)

Thanks,
Srinivasa Pradeep

---

### Post by vasa1 on 2017-02-23
> **brspradeep said:**
> ...

Do you have any inputs on fixing the jumbling of characters?
When I start typing in the address bar of chrome or leafpad or even on terminal and CPU is 100%, the characters get jumbled.
For eg: If I type HELLO, I may see EHLOL or any other combination other than the original order(HELLO).
This happens always when CPU stays at 100% for some time (for eg: few seconds)

Thanks,
Srinivasa Pradeep
Please do not start new questions totally unrelated to the original topic in the existing thread. You are encouraged to start separate threads for separate topics.

---

