---
title: "Getting connected"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by MrNewie on 2012-11-10
Hello I have down loaded & ran ubuntu. I am a baby & this is my first non commercial OS. I can not get the OS to recognize a wireless connection. I have to switch back to windows to access the inter net.

Any help would be great.

---

### Post by kenizl86 on 2012-11-10
Open Terminal (I don't know how to on Ubuntu, because I run Xubuntu), and type this in:

```
sudo lshw -class network
```

It will ask for your password. Put it in and post the output here (as a reply). It should tell you the type of wireless adapter you have. Depending on what it is, we should be able to get drivers for it.

---

### Post by grahammechanical on 2012-11-10
You can open the Dash - tap the Super (windows) key and type help and press enter. As a 'baby' it will benefit you to read the Ubuntu Desktop guide. It has a section on Network, web, email & chat.

When you installed Ubuntu did you have your machine connected to the internet? That is recommended. If you did that then an Internet connection would be set up automatically. Perhaps it was by a wired (ethernet) connection?

We are also assuming that you are using Ubuntu 12.04 but you do not tell us. This means that we may give you the wrong directions.

You should be able to see an icon for the Network Manager in the top panel over at the right. Click on it. do you see a list of wireless networks? Do you see your wireless network? Is Networking and Wireless Enabled?

Select your wireless network and click on it. Put in the wireless key or passphrase when you are asked to authenticate. This will work even when using the live DVD session.

Regards

---

