---
title: "Bluetooth Dun Help!"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by kevin11951 on 2008-05-15
very soon here i will be getting a blackberry perl 8130, and it says:

 ```
[SIZE="4"]Phone as Modem Capable[/SIZE]

Use the included USB cable to connect to laptops for a wireless modem, or choose to run this capability via Bluetooth with no USB cable requirement. 
```

also the company im getting it through is sprint (im using there unlimited everything plan), any help here?

---

### Post by asrai on 2008-05-15
I'd like to help you, but I have no idea what "bluetooth dun help" means or what you are trying to do!

Please also calm down - we are not paid support here, just nice people who  will help as best we can.

What do you want help with? You don't have the phone yet so you can't have tried to connect your phone to your computer.  

Do you want to use your phone as a modem? I think it would be a lot easier to set that up once you have the phone.  You can then set it up as a bluetooth connection, or as a usb connection if you do not have bluetooth on your computer.

If I've missed something, please let me know, but I really am having a lot of trouble understanding the issue.

---

### Post by niteshifter on 2008-05-15
Hi,

You've some options:
1. Get gnome-ppp (uses wvdial) and set it up, you can use the GUI to connect.
2. Use wvdial from the command line (after setting it up).
3. Look at this [page]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") at the section "Using mobile phone/GPRS/EDGE as Internet modem" (which has you setting up ppp and chat scripts - tedious).

With option #2, I recently posted how I set up with a RAZR V3 [here]("http://ubuntuforums.org/showthread.php?t=789041"), at post #3. This sets up connecting via bluetooth or USB. Never mind I've a V3 and you've a Blackberry, the basic process of setting up is the same. You'll need the correct parameters for connection from your wireless provider.

You can also create a couple of "dummy" setups with gnome-ppp, then edit it's generated wvdial.conf to be like I described in the URL above.

You could work on having a bit more patience - you'll need it with 1x EVDO  - broadband it isn't ;)

---

### Post by kevin11951 on 2008-05-16
> **asrai said:**
> 
Please also calm down - we are not paid support here, just nice people who  will help as best we can.

actually i was just posting over and over because it was going 2 and three pages down, ive been here for 2+ years i have an okay idea of how things work... i think :)

---

### Post by asrai on 2008-05-16
Fair enough, I didn't intend to be rude, I am sorry if it came across that way.  I just though that if everyone bumped their posts 3 times within a matter of an hour this place would be chaos!

It looks like niteshifter has given you some good information, post back if you don't have any luck.

---

### Post by tavella on 2008-05-17
Have you called Blackberry support and had them add the PAM (phone as modem) package to your account? The $99 unlimited plan does not include tethering. I believe its $15 extra a month. I have been able to sync my 8830 via Bluetooth only using Feisty. I keep receiving kernel panics when I call rfcomm in Hardy. I believe it's a problem with the 2.6.24 kernel. Here is a link to how I proceeded. I used Kubuntu at that time, but you should be able to substitute KPPP with gnome-ppp if you're using Ubuntu.

[http://blackberryforums.pinstack.com/showthread.php?t=59656]("http://blackberryforums.pinstack.com/showthread.php?t=59656")

> **kevin11951 said:**
> very soon here i will be getting a blackberry perl 8130, and it says:

 ```
[SIZE="4"]Phone as Modem Capable[/SIZE]

Use the included USB cable to connect to laptops for a wireless modem, or choose to run this capability via Bluetooth with no USB cable requirement. 
```

also the company im getting it through is sprint (im using there unlimited everything plan), any help here?

---

