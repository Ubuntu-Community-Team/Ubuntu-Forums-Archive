---
title: "New server help"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by reinamarquez on 2012-06-14
I am trying to make an SSH connection to my iPhone 4s and many of the websites I have visited tell me that I need to access something called places and then create a new server. I am guessing this was for previous versions of Ubuntu since my version (12.04 beta) has nothing of the sort. I have searched every known place in the internet and have not found anything to guide me through my version of Ubuntu. I've been trying to do this for over 2 hours... Please help!!! :cry::cry::cry::cry::cry::cry:

---

### Post by newbie-user on 2012-06-14
Just open up a terminal and ssh from there. Hit the super (or windows) key, type "terminal" into the search box. It should bring up a few terminal applications for you to choose from. Alternatively, you could press alt+F2, then type "gnome-terminal" to start the terminal directly. Then you can ssh all you want.

---

### Post by reinamarquez on 2012-06-14
Then I guess I'm confused as to what an SSH connection is... I'm following the instructions on this site: [http://marcansoft.com/blog/2011/01/syncing-music-in-new-idevices-with-linux/](http://marcansoft.com/blog/2011/01/syncing-music-in-new-idevices-with-linux/) and so I don't know what to do anymore... I installed SBSetting and OpenSSH from Cydia and I am currently stuck :$ If you (or anyone) knows a thread that can help me with a problem I have syncing my iPhone 4 with Rythmbox then please do tell me. Thanks :)

---

### Post by drmrgd on 2012-06-14
I'll assume your iphone is jail broken (the only way you can ssh in, as far as I can tell).  For clarity sake, you did install OpenSSH on the iphone, correct?  

I've not done this to my phone.  However, there are instructions for how to SSH in to your phone here:

[http://www.simonblog.com/2009/05/17/how-to-use-ssh-to-transfer-file-on-iphone/](http://www.simonblog.com/2009/05/17/how-to-use-ssh-to-transfer-file-on-iphone/)

The main key is to have an SSH client installed on the phone and to know the IP Address of your phone.  SSH is built into Ubuntu.  So, once you know the address of the iPhone (follow the link I gave you to find out how), then you could just launch a terminal and run something like:

```
ssh admin@<ip.address.of.your.phone>
```

Then you should be asked for a password, which according to that website is "alpine" (no idea why or if that's specific to a certain generation phone or what).

Hope that helps at least a little.

---

### Post by reinamarquez on 2012-06-14
So I tried doing what you said, but when I type in the code it gives me this error

---

### Post by drmrgd on 2012-06-14
> **reinamarquez said:**
> So I tried doing what you said, but when I type in the code it gives me this error

You have an extra "<" character in there.  Try it like this:


```
ssh admin@192.168.1.117
```

---

### Post by reinamarquez on 2012-06-14
Tried it again and now it gave me THIS error...

---

### Post by drmrgd on 2012-06-14
It looks like a network configuration issue on either your OpenSSH setup on your iPhone, or a traffic issue on your router.  I'm not at all a networking expert.  It's also a little more difficult as your server in this case is an iPhone, and I'm not entirely sure what tools are available.  I would first try the usual stuff like pinging the IP address from your computer to make sure you can at least see it:

```
ping 192.168.1.117
```

Googling around, it looks like some others have gotten the same error as you, and only solutions I saw (which I'm skeptical about), is to reboot the phone, restart the Cydia SSH server, or to disconnect your phone from WiFi and reconnect.  You could also try those things.

---

### Post by reinamarquez on 2012-06-14
Tried the ping command... Gave me this (I'm guessing it's not a good thing...)

Also, I tried rebooting the iPhone, disconnecting and connecting to the wifi and restarting springboard... None of it worked

---

### Post by reinamarquez on 2012-06-14
> **drmrgd said:**
> It looks like a network configuration issue on either your OpenSSH setup on your iPhone, or a traffic issue on your router.  I'm not at all a networking expert.  It's also a little more difficult as your server in this case is an iPhone, and I'm not entirely sure what tools are available.  I would first try the usual stuff like pinging the IP address from your computer to make sure you can at least see it:

```
ping 192.168.1.117
```

Googling around, it looks like some others have gotten the same error as you, and only solutions I saw (which I'm skeptical about), is to reboot the phone, restart the Cydia SSH server, or to disconnect your phone from WiFi and reconnect.  You could also try those things.

   Okay, so I made a breakthrough and found the place where you can make a new connection. Turns out you have to open the home folder and then at the bar on the top you look under files or edit (I don't really remember right now). Then a new window appeared telling me to input the settings for the SSH connection. Thing is it gives me an error that looks like the attached picture.



 If you know of someone who you think is better at these types of problems, please do direct me to him, or if you know another forum that might be more helpful. 

The help you have provided is very much appreciated :D

---

### Post by CharlesA on 2012-06-14
Make sure both are on the same network. Generally if you cannot ping it, you won't be able to access it via other services either.

---

### Post by newbie-user on 2012-06-14
> **reinamarquez said:**
> Okay, so I made a breakthrough and found the place where you can make a new connection. Turns out you have to open the home folder and then at the bar on the top you look under files or edit (I don't really remember right now). Then a new window appeared telling me to input the settings for the SSH connection. Thing is it gives me an error that looks like the attached picture.



 If you know of someone who you think is better at these types of problems, please do direct me to him, or if you know another forum that might be more helpful. 

The help you have provided is very much appreciated :D

That's the same thing as using the terminal to ssh. That will work fine, but it seems that: 1) the phone isn't accepting ssh connections, maybe an issue with a firewall on your phone perhaps, or, 2) your computer and the phone aren't in the same subnet and you don't have static routing set up, or, 3) you don't have an ssh server running on your phone.

What is the ip address of your computer?

---

