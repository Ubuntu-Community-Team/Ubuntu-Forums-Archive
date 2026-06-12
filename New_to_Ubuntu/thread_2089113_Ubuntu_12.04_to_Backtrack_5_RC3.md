---
title: "Ubuntu 12.04 to Backtrack 5 RC3"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by Paladin07 on 2012-11-28
Hello 
I just want to make mine ubuntu 12.04 version to Backtrack 5 RC3. But i don't know  the softwares of Backtrack so.. can you help me making mine ubuntu 12.04 as backtrack..
 Thanks

---

### Post by Cheesemill on 2012-11-28
If you want BackTrack then install BackTrack, if you want Ubuntu then install Ubuntu. There is no way to convert a 12.04 installation into BackTrack (which is based on Ubuntu 10.04).

Also a large number of the tools that you get with BackTrack are already available for 12.04, just search in the software centre for them.

Personally I run BackTrack in a VM that I can fire up whenever I need it.

---

### Post by Paladin07 on 2012-12-01
I just don't want to remove ubuntu due to its software centre facility which i get here..
just want to use those apps that are in backtrack so want to convert Ubuntu into backtrack..
If i use VM ware mine PC becomes too much slow.. the problem lies there so..Thanks for help...

---

### Post by haqking on 2012-12-01
> **Paladin07 said:**
> I just don't want to remove ubuntu due to its software centre facility which i get here..
just want to use those apps that are in backtrack so want to convert Ubuntu into backtrack..
If i use VM ware mine PC becomes too much slow.. the problem lies there so..Thanks for help...

You cannot convert Ubuntu 12.04 into Backtrack anymore than you can convert it to Suse 9 or Windows xp.

If you want the tools available in Backtrack then install them into Ubuntu or use Backtrack directly as it is meant to be used which is from a VM, USB flash drive, External HDD, Live DVD etc.

Peace

---

### Post by Paladin07 on 2012-12-01
> **haqking said:**
> You cannot convert Ubuntu 12.04 into Backtrack anymore than you can convert it to Suse 9 or Windows xp.

If you want the tools available in Backtrack then install them into Ubuntu or use Backtrack directly as it is meant to be used which is from a VM, USB flash drive, External HDD, Live DVD etc.

Peace


can we convert ubuntu to windows Xp ??? or are you saying about wine on ubuntu???? ok it means ubuntu and backtrack are used for their own purpose...
Thanks for information

---

### Post by haqking on 2012-12-01
> **Paladin07 said:**
> can we convert ubuntu to windows Xp ??? or are you saying about wine on ubuntu???? ok it means ubuntu and backtrack are used for their own purpose...
Thanks for information

I am saying Ubuntu is Ubuntu, you canont convert it to something else.

If you want the tools available in Backtrack then install them yourself and configure them in Ubuntu, or use Backtrack from a live DVD, USB, VM etc.  If you cant it is highly unlikely that you need Backtrack or will benefit from it, it is a security auditing toolbox built for purpose.

Ubuntu is Ubuntu.

---

### Post by Paladin07 on 2012-12-01
> **haqking said:**
> I am saying Ubuntu is Ubuntu, you canont convert it to something else.

If you want the tools available in Backtrack then install them yourself and configure them in Ubuntu, or use Backtrack from a live DVD, USB, VM etc.  If you cant it is highly unlikely that you need Backtrack or will benefit from it, it is a security auditing toolbox built for purpose.

Ubuntu is Ubuntu.

Oh yes.. I am also just saying about installing the application on Ubuntu..
i just want to get the list of applications that runs on backtrack and configure it  on  ubuntu

---

### Post by haqking on 2012-12-01
> **Paladin07 said:**
> Oh yes.. I am also just saying about installing the application on Ubuntu..
i just want to get the list of applications that runs on backtrack and configure it  on  ubuntu

not rc3 but still valid

[http://zitstif.no-ip.org/bt5/toolslist.txt](http://zitstif.no-ip.org/bt5/toolslist.txt)

Not all will necessarily work or compile correctly on your system though.

Backtrack exists so you dont have to and is built around a kernel fit for purpose.

or from a live DVD or VM of RC3 type 

```
dpkg --list 
```

I cant be bothered to start a VM to do it for you right now so use the link above for a rough overview

have fun getting them all to work, about the time you finish it will be Backtrack 9 ;-)

---

### Post by Paladin07 on 2012-12-01
> **haqking said:**
> not rc3 but still valid

[http://zitstif.no-ip.org/bt5/toolslist.txt](http://zitstif.no-ip.org/bt5/toolslist.txt)

Not all will necessarily work or compile correctly on your system though.

Backtrack exists so you dont have to and is built around a kernel fit for purpose.

or from a live DVD or VM of RC3 type 

```
dpkg --list 
```I cant be bothered to start a VM to do it for you right now so use the link above for a rough overview

have fun getting them all to work, about the time you finish it will be Backtrack 9 ;-)

Thanks Again For The Help.....  And Yes may Be not Backtrack 9 it may take Backtrack 15 if you take overview of mine Speed :P :D   
VM is working too slow in mine PC so I need to bother to add applications on mine Ubuntu... getting to know the facility to remove just by deleting  those VM's . Its mine Unfortunate that a PC with 2GB RAM also doesn't support it....

---

### Post by haqking on 2012-12-01
> **Paladin07 said:**
> Thanks Again For The Help.....  And Yes may Be not Backtrack 9 it may take Backtrack 15 if you take overview of mine Speed :P :D   
VM is working too slow in mine PC so I need to bother to add applications on mine Ubuntu... getting to know the facility to remove just by deleting  those VM's . Its mine Unfortunate that a PC with 2GB RAM also doesn't support it....

Just run it from a USB drive or Live DVD if you cant run a VM, that is what most people do, that is what it was designed for, though it can be installed it is a toolbox full of tools that is all, you use them when you need them.

---

### Post by Cheesemill on 2012-12-01
Is there anything stopping you just running BackTrack from the DVD when you need it?

---

### Post by Paladin07 on 2012-12-01
> **haqking said:**
> Just run it from a USB drive or Live DVD if you cant run a VM, that is what most people do, that is what it was designed for, though it can be installed it is a toolbox full of tools that is all, you use them when you need them.

Oh Yes .. just Remembered the option i forgot.. a simple one.... Thanks for reminding me....
Also a question about the link you gave [http://zitstif.no-ip.org/bt5/toolslist.txt](http://zitstif.no-ip.org/bt5/toolslist.txt) 
Is It your Website you hosted from your home??? How did you port forwarded it .. The Apache server's Port 80 didnot worked neither any other Port worked....

---

### Post by haqking on 2012-12-01
> **Paladin07 said:**
> Oh Yes .. just Remembered the option i forgot.. a simple one.... Thanks for reminding me....
Also a question about the link you gave [http://zitstif.no-ip.org/bt5/toolslist.txt](http://zitstif.no-ip.org/bt5/toolslist.txt) 
Is It your Website you hosted from your home??? How did you port forwarded it .. The Apache server's Port 80 didnot worked neither any other Port worked....

no its not mine, it was a one second google, if you want a comprehensive list then use the command dpkg as i said above in a running version of BT 5 RC3

Port forwarding will be done on your home router to your IP which is hosting port 80.

---

### Post by Paladin07 on 2012-12-01
> **Cheesemill said:**
> Is there anything stopping you just running BackTrack from the DVD when you need it?

Yes The DVD is Just too slow to get started and the USB boot wasnot working ... now got the other option to run it...

---

### Post by Paladin07 on 2012-12-01
> **haqking said:**
> no its not mine, it was a one second google, if you want a comprehensive list then use the command dpkg as i said above in a running version of BT 5 RC3

Port forwarding will be done on your home router to your IP which is hosting port 80.

ok.. thanks!!! the port forward didnot worked for mine router tried 80 and 8080 and 443 also but didnot worked...
in some post i found other ports like:76 but didnot worked too...

---

### Post by haqking on 2012-12-01
> **Paladin07 said:**
> ok.. thanks!!! the port forward didnot worked for mine router tried 80 and 8080 and 443 also but didnot worked...
in some post i found other ports like:76 but didnot worked too...

well the port is whatever port you have hosting the service, it can be port 34567 as long as you configure apache to use that port but default and standard is 80.

If apache is working correctly and you can see localhost then its simple matter of setting up the forwarding on your router,  how you do that will depend on your router, look in the manual.

To access it from outside your lan you will need a static IP or some type of dynamic DNS service.

If you cant get port forwarding working for a website, you might want to take a step back from using backtrack tools yet and up your skillset on some basic networking skills otherwise backtrack and its tools will frazzle your brain.


Peace

---

### Post by Paladin07 on 2012-12-01
> **haqking said:**
> well the port is whatever port you have hosting the service, it can be port 34567 as long as you configure apache to use that port but default and standard is 80.

If apache is working correctly and you can see localhost then its simple matter of setting up the forwarding on your router,  how you do that will depend on your router, look in the manual.

To access it from outside your lan you will need a static IP or some type of dynamic DNS service.

If you cant get port forwarding working for a website, you might want to take a step back from using backtrack tools yet and up your skillset on some basic networking skills otherwise backtrack and its tools will frazzle your brain.


Peace

yes configured the localhost to port 8080 and tried to acces from lan it worked but couldnot be seen from outside using WAN ip.. how to get into the localhost page from outside if mine ip may be 123.145.224.9 ... a simple example...

---

### Post by haqking on 2012-12-01
> **Paladin07 said:**
> yes configured the localhost to port 8080 and tried to acces from lan it worked but couldnot be seen from outside using WAN ip.. how to get into the localhost page from outside if mine ip may be 123.145.224.9 ... a simple example...

well if your routers WAN IP is x.x.x.x then type x.x.x.x:8080 to access that port which will forward to your LAN service if router setup correctly.

However it is likely that your WAN IP is dynamic so changes so you will need a static or dynamic DNS service.

---

### Post by Zill on 2012-12-01
> **haqking said:**
> ...If you cant get port forwarding working for a website, you might want to take a step back from using backtrack tools yet and up your skillset on some basic networking skills otherwise backtrack and its tools will frazzle your brain...
+1

Excellent advice!

Backtrack tools are for those who (a) *really* need them and (b) know *how* to use them. ;-)

---

