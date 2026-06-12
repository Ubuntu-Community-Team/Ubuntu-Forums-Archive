---
title: "How to use internet explorer in Ubuntu"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by tiamat2009 on 2012-07-06
Hallo,

I want to switch to ubuntu. I don't play games or have any purchased programmes that I would miss, but as I'm a web designer I need to test sites in IE. How do I do this in Ubuntu, is this possible? How do others developing on Linux do this? I don't want to have to reboot just to check a site.

Also please note, the "M$ is evil" idiology doesn't interest my clients, so telling people to use another browser is not an option. Also  I don't want to have more than 1 computer so please don't suggest I buy a second computer.

Thanks for any tips. I know you can run virual OS but I have an OEM version of windows so I guess to do this I shall have to buy  anew copy of windows right? I don't think the windows DVD that came with my laptop will install inside virtual box, right?

---

### Post by MG&amp;TL on 2012-07-06
> **tiamat2009 said:**
> Hallo,

I want to switch to ubuntu. I don't play games or have any purchased programmes that I would miss, but as I'm a web designer I need to test sites in IE. How do I do this in Ubuntu, is this possible? How do others developing on Linux do this? I don't want to have to reboot just to check a site.

Also please note, the "M$ is evil" idiology doesn't interest my clients, so telling people to use another browser is not an option. Also  I don't want to have more than 1 computer so please don't suggest I buy a second computer.

Thanks for any tips. I know you can run virual OS but I have an OEM version of windows so I guess to do this I shall have to buy  anew copy of windows right? I don't think the windows DVD that came with my laptop will install inside virtual box, right?

Never fear, you can run IE on Ubuntu. [http://askubuntu.com/questions/64788/how-to-install-ms-internet-explorer-7-8-or-9](http://askubuntu.com/questions/64788/how-to-install-ms-internet-explorer-7-8-or-9)  I'm not sure how *well* it runs, but it definitely runs.

No, I don't think you can install windows (only repair) with an OEM DVD.

---

### Post by bobzxr on 2012-07-06
You could install PlayOnLinux from the software center, which is a front-end for wine.

"PlayOnLinux is a piece of software which allows you to easily install and use numerous games and apps designed to run with Microsoft® Windows®."

---

### Post by krustenBrot on 2012-07-06
Why don't you try your OEM cd with [Virtualbox]("https://www.virtualbox.org/") or [VMware Player?]("http://www.vmware.com/products/player/")

In my opinion this is the easiest and most convenient way. :)

---

### Post by codingman on 2012-07-06
I think you can run it somewhere in wine, I remember having it on my basic installation of wine, but I think I deleted it. 

Someone back me up on this! But try installing wine and browsing through the C: drive and looking for IE in there.

---

### Post by codingman on 2012-07-06
> **krustenBrot said:**
> Why don't you try your OEM cd with [Virtualbox]("https://www.virtualbox.org/") or [VMware Player?]("http://www.vmware.com/products/player/")

In my opinion this is the easiest and most convenient way. :)

With a VM you would have to have an OS in it, so it therefore still means that you have to use windows for IE.

---

### Post by krustenBrot on 2012-07-06
Yes and he doesn't have a problem with using Windows. Just with rebooting. Not a problem when using a VM.

---

### Post by codingman on 2012-07-06
> **krustenBrot said:**
> Yes and he doesn't have a problem with using Windows. Just with rebooting. Not a problem when using a VM.

That would be like wasting space just for a VM when you can easily run it inside of wine.

---

### Post by caffeinatedev on 2012-07-06
You can in fact install IE6 & 7 from PlayOnLinux with no problems, I don't think the WINE dev team has updated for IE9 yet.

---

### Post by vasa1 on 2012-07-06
> **codingman said:**
> That would be like wasting space just for a VM when you can easily run it inside of wine.
Do you know **for a fact** that IE 9 and IE 10 will work in Wine?

I know that IE 10 isn't yet released as "stable" but I'm assuming it will soon be.

---

### Post by sudodus on 2012-07-06
> **krustenBrot said:**
> Why don't you try your OEM cd with [Virtualbox]("https://www.virtualbox.org/") or [VMware Player?]("http://www.vmware.com/products/player/")

In my opinion this is the easiest and most convenient way. :)
+1

And I think you need to run Windows with IE to be really sure you are testing that your web pages work in Windows with IE. If your computer is powerful enough, Windows will run nicely in a virtual machine.

---

### Post by caffeinatedev on 2012-07-07
> **vasa1 said:**
> Do you know **for a fact** that IE 9 and IE 10 will work in Wine?

I know that IE 10 isn't yet released as "stable" but I'm assuming it will soon be.

Checkout [www.winehq.org](www.winehq.org) so you can find this kind of stuff out for yourself instead of having to wait for people to respond.

But for now it does look like IE9 will NOT run and IE10 hasn't even been tested yet.

---

### Post by vasa1 on 2012-07-07
> **caffeinatedev said:**
> Checkout [www.winehq.org](www.winehq.org) so you can find this kind of stuff out for yourself instead of having to wait for people to respond.

But for now it does look like IE9 will NOT run and IE10 hasn't even been tested yet.
I don't want to know. People suggesting the use of Wine should.

---

### Post by mastablasta on 2012-07-07
then ther eis running in wine and running and using all features. so even if you get it to run it might not use all the stuff explorer has.

---

### Post by vasa1 on 2012-07-07
> **mastablasta said:**
> then there is running in wine and running and using all features. so even if you get it to run it might not use all the stuff explorer has.
Exactly, as IE goes back to being "part of the OS", heavily integrated, I very much doubt Wine will be adequate.
If someone plans on earning a livelihood designing web pages, having access to the real thing would seem "essential", either via a dual boot or VM.

---

### Post by caffeinatedev on 2012-07-07
@vasa1 my mistake, I thought you were the OP

---

### Post by lykwydchykyn on 2012-07-07
I tried doing the "IE in Wine" approach for a while; unless things have changed massively in the last year or so it's a slow and horribly broken experience.

If you're testing things for the web, use a VM.  It's the only way to be sure that things will work and render right.

---

