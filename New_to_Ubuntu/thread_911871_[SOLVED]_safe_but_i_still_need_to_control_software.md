---
title: "[SOLVED] safe but i still need to control software access internet"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by npnutn7 on 2008-09-06
I read here a lot about how linux is more secure than windows. but i don`t feel good without controlling the software that access the internet. i have to know what`s going on in my pc..

I installed firestarter and not bad for keeping my pc stealth, but i still missing the Comodo firewall in windows with all the rules and security defence.

in breif,
how can i allow with permission , make rules as Comodo firewall?

---

### Post by Elfy on 2008-09-06
There is a community page for firestarter and for the default ufw, they should help you. 

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)
[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by hyper_ch on 2008-09-06
> **npnutn7 said:**
> I read here a lot about how linux is more secure than windows.
It is

> **npnutn7 said:**
> but i don`t feel good without controlling the software that access the internet.
What do you mean by that?

> **npnutn7 said:**
> I installed firestarter and not bad for keeping my pc stealth, but i still missing the Comodo firewall in windows with all the rules and security defence.
(1) firestarter is no firewall
(2) firestarter is sort of outdated
(3) very likely you don't even need to bother about the firewall... well, now tht you installed firestarter you changed the default settings... but mostly there's no need to think about a firewall when you don't have services running.

---

### Post by npnutn7 on 2008-09-06
the reason i installed firestarter because my pc did not pass the online Shield firewall test, after installing it i just edited to block ping and stealth all ports.

i don`t trust what the software do, maybe because i am used to windows, i  need to know when and why a software connect to internet without my permission. because i can not trust them. 

ok, do i have to worry about my privacy using any program? i am afraid there might be a bad script or code inside a software that  keep the developer updated on what`s going on in my pc .

---

### Post by anjilslaire on 2008-09-06
use a hardware firewall like a decent router. 

All of this is open source, so if you're *really* concerned about what its doing, learn to understand the code & check the source code yourself.

---

### Post by hyper_ch on 2008-09-06
what test did it fail?
The only reliable test IMHO would be to do a full nmap check from another computer. I don't trust online tests, and grc often reports wrong things.

And software does not just connect to the internet without your permission. There's no adware, no nagware, no spyware integrated if you use your brains and isntall software from trusted resources only.

---

### Post by brian_p on 2008-09-06
> **npnutn7 said:**
> the reason i installed firestarter because my pc did not pass the online Shield firewall test, after installing it i just edited to block ping and stealth all ports.

Many people do the same as you. Useless, but they do it.

> i don`t trust what the software do, maybe because i am used to windows, i  need to know when and why a software connect to internet without my permission. because i can not trust them.

I won't attempt to argue with you and provide evidence of Ubuntu's soundness because if you are convinced that any of its software is malign it will get neither of us anywhere.

> ok, do i have to worry about my privacy using any program? i am afraid there might be a bad script or code inside a software that  keep the developer updated on what`s going on in my pc .

No, you do not have to worry. Do you find that a satisfactory response?

---

### Post by cariboo on 2008-09-06
If you really must have a firewall and want something that is more configurable try [Aron's Iptables Firewall]("http://rocky.molphys.leidenuniv.nl/") it is available in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it. Basic configuration is done during installation, but there is a lot more to configure after it is installed.

BTW configuration after installation is done from the command line. 

Jim

---

### Post by men28 on 2008-09-06
I read now a book about Linux Ubuntu named Beginning Ubuntu Linux from Keir Thomas. In this book is recommended to use iptables firewall and configure it with Firestarter program.
They recommend Enable ICMP filtering in Firestarter too ( Edit -> Perferences ). When I have done this I had problems with number of web sites ( Yahoo email for example ). When I enabled MS Traceroute checkbox these problems stopped appear.
There was some information about SSH vulnerabilities in Linux in news these days. I think if I not open SSH ports these news are not relevant for my computer (I don't sure).

---

### Post by hyper_ch on 2008-09-06
I don't say there is no use at all for configurating iptables on linux but in most cases there's no need to... especially not when you are behind a router (integrated in your modem) anyway.

---

### Post by npnutn7 on 2008-09-07
Excuse my ignorance, but from what i experienced "advanced user" with windows since v3.1, made me suspect any software whatsoever beacuse i always like to feel that i am in control of what`s going on. 

I am newbie to linux in general, tried three different distro in one week and picked ubuntu as my favourite. still i can not read linux code, so can not decide if it`s good or bad. i trust ubuntu but i don`t trust myself downloading any software.

thank you for ur reply, 
oh by the way ubunut didn`t pass grc test until i Enabled ICMP filtering in firestarter.

---

### Post by hyper_ch on 2008-09-07
have a read here:

[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by npnutn7 on 2008-09-07
thanks, that answered it all.

---

