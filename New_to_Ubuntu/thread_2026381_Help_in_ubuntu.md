---
title: "Help in ubuntu"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by Priyank Kaushal on 2012-07-15
I have recently installed ubuntu 12.04 but it has not got synaptic manager in it. I have dual OS windows and ubuntu..I can run internet on windows by modem but don't know how to run on ubuntu.It doesn't connect.for synaptic to install I need internet.so help me in using modem on ubuntu also...

---

### Post by Kirk Schnable on 2012-07-15
What sort of modem is this?  (dialup, mobile broadband...?)

Is it USB or PCI?

Do you know the model of it?

Kirk

---

### Post by Shadius on 2012-07-15
Synaptic Package Manager doesn't come installed with Ubuntu. You'll have to install it yourself using the Ubuntu Software Center. However, you're saying that you can't access the internet. Open up the Terminal and try these commands:
```
ifconfig
```
```
dmesg | grep eth0
```

Post the results here by using the "#" symbol, paste the results in between the [CODE] tags.

---

### Post by 3rdalbum on 2012-07-15
I'm more than a little curious as to why you want Synaptic Package Manager, when you have no internet connection. Synaptic does almost nothing useful unless you have internet access.

It's like wanting Yahoo Messenger installed without internet, or someone with one eye buying a 3D TV.

---

### Post by Shadius on 2012-07-15
> **3rdalbum said:**
> I'm more than a little curious as to why you want Synaptic Package Manager, when you have no internet connection. Synaptic does almost nothing useful unless you have internet access.

It's like wanting Yahoo Messenger installed without internet, or someone with one eye buying a 3D TV.

Well, the user has internet connection in Windows, but not in Ubuntu. So that would be the problem to fix, and then the user can install Synaptic Package Manager.

---

### Post by Kirk Schnable on 2012-07-15
I think you both took this thread and took off running in the wrong direction.  As I understood the original poster's problem, he's asking for help in getting his modem to work so he can install things from Synaptic\Use the Internet.  I also doubt very much if dmesg for eth0 will be relevant because he's not using eth0, he's using some modem. 

Kirk

---

### Post by ub07 on 2012-07-15
> **Kirk Schnable said:**
> What sort of modem is this?  (dialup, mobile broadband...?)

Is it USB or PCI?

Do you know the model of it?

Kirk

I echo this. We need more information in order to help you. I have just been through setting up a dial-up modem and can help if it is a dial-up modem.

---

### Post by ranger1021994 on 2012-07-15
> **Priyank Kaushal said:**
> I have recently installed ubuntu 12.04 but it has not got synaptic manager in it. I have dual OS windows and ubuntu..I can run internet on windows by modem but don't know how to run on ubuntu.It doesn't connect.for synaptic to install I need internet.so help me in using modem on ubuntu also...

I had this problem before
Go to Network>Edit Connection
Select wired/wireless tab and click edit
Go to IPv4 settings and see
1: If it is Automatic[dhcp] then select manual and ask the settings from ISP [Call their Help centre]
2: If its manual then select Automatic[dhcp]
It should work one way or the other.

As long as Synaptic is concerned you can install it from Software Centre

---

### Post by Priyank Kaushal on 2012-07-19
Now my internet is working..i did some setting..and I need synaptic to download packages of omnet++ simulator...

---

### Post by ub07 on 2012-07-19
> **Priyank Kaushal said:**
> Now my internet is working..i did some setting..and I need synaptic to download packages of omnet++ simulator...

What setting did you change? I'm very interested because of my own situation.

---

