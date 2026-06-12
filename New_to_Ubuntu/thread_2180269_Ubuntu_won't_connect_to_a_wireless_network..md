---
title: "Ubuntu won't connect to a wireless network."
date: 2013-10-12
forum: New to Ubuntu
---

### Post by rasti2 on 2013-10-12
I am having a problem with my laptop. It runs Ubuntu from a LiveUSB, I used LinuxLiveUSB Creator. After booting Ubuntu for the first 2 times the wireless connection was perfect, but now it tries to connect to a network and it says Disconnected - you are now offline. I am new to Ubuntu and not an expert in tech so if you could just explain it step by step I should be able to follow. Thanks for all the help.

---

### Post by Norm24 on 2013-10-12
Click on the network icon and then check "enable wireless".

---

### Post by grahammechanical on 2013-10-12
What do we need to make a wireless connection?

1) A wireless adapter in the machine that is under the control of Ubuntu. You have that because the wireless adapter in your machine is trying to connect to a wireless access point (network). So, we know that the wireless adapter is switched on and that Ubuntu has installed a driver for that wireless adapter.

2) A wireless access point in range. We know that you have that because Network Manager is trying to connect to it. But is it your router/hub? If the router/hub is switched off then Network Manager will try to connect to some other access point. If it fails to make the connection because it is a secure access point then we will get that error message.

3) A Network Manager that knows the correct pass phrase or wireless key for that network/access point/router/hub. Without that we will get a disconnected message.

You can click the Network Manager icon and from the menu you will see a list of networks in range. We can select Edit connections and see if we are connecting to the correct access point and if we have given the correct pass phrase.

There is another point to keep in mind regarding laptops. We need a connection (settings) for each wireless access point that we want to connect to. This is true also of desktop machines but as desktop machines are not portable one connection usually does what we want. But with laptops the connection settings we have for our home will not work if we use the machine somewhere else. We need to setup a connection for each wireless access point that we want to connect to, especially secure access points. May be this does not apply but I have no way of telling. But it will also be true if we use that USB memory stick Ubuntu in another machine with another access point to connect to.

Giving you step by step instructions is not possible because you do not tell us the version of Ubuntu that you are using. There are differences because improvements are made all the time.

Regards.

---

### Post by rasti2 on 2013-10-12
Thanks for your help but I figured it out it seems that I have accidentaly turned off WiFi and it isn't really obvious if it works or not so I was the problem.

---

### Post by Iowan on 2013-10-12
[Solved?]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)

---

