---
title: "CMS management system"
date: 2022-07-14
forum: New to Ubuntu
---

### Post by zapbrannigan on 2022-07-14
Hi,
Recently installed Ubuntu and setup Nginx for streaming services.
I would like to gain more experience with this awesome OS by installing some kind of CMS system that will enable me to install an intranet as well as some kind of media management system.

HAs anyone done something similar or can point me in the right direction?
Thanks :)

---

### Post by kingpenguin on 2022-07-14
Can you please describe what you mean a little more? I see that you have a reverse proxy for your streaming service but when I think of CMS I am thinking of a "Computer management system". If this is what you are talking about I would probably take a look into landscape from ubuntu [https://landscape.canonical.com/](https://landscape.canonical.com/) . There is always going to be more tools to do the job but it is really what you are needing from a CMS that will help us understand the issue better. If you have any other questions please let me know. Also when you are talking about "intranet" are you talking about subnets? The reason I ask is it can be defined as the following "An *intranet* is a computer network for sharing  information, easier communication, collaboration tools, operational  systems, and other computing services". The problem is that this can be done with just routers and switches. You can vlan the traffic with the router which should be able to solve this part of the question. Also the "media management system" part of the question is a little vuage as well. If you are just looking for a way to host video and play it back on other devices I would look into emby or plex. If you have any other questions please let me know.

---

### Post by zapbrannigan on 2022-07-14
Hi, Thank you for replying.
We have a few tvs which will be setup around the place which will be used to display videos and photos. I was thinking that a CMS would be used to manage those devices (raspberry Pis most likely) so that I can manage what content is played and when it is played. I dont know if it would be more efficient to stream content to multiple devices or to copy content over and have it played locally on each device. I would also like to install an intranet to be used as the internal web interface people can navigate to for collaboration, calendars, events, latest news etc..


Thank you!

---

### Post by grahammechanical on 2022-07-14
It seems to me that part of what you want is solved by setting up a kiosk system

[https://mir-server.io/docs/make-a-secure-ubuntu-web-kiosk?_ga=2.2680304.1143572614.1657817789-221267787.1648681486](https://mir-server.io/docs/make-a-secure-ubuntu-web-kiosk?_ga=2.2680304.1143572614.1657817789-221267787.1648681486)

[https://ubuntu.com/blog/mir-kiosk-uses-mir](https://ubuntu.com/blog/mir-kiosk-uses-mir)

Intranet  is a different situation. Every machine connected to that network would  be at risk of security breeches in just one of those machines in able  to connect to the World Wide Web (Internet).

Regards

---

### Post by zapbrannigan on 2022-07-15
Awesome. Thank you for the suggestion. Ill take a look at the kiosk system.

---

### Post by mIk3_08 on 2022-07-16
> **zapbrannigan said:**
> Hi,
Recently installed Ubuntu and setup Nginx for streaming services.
I would like to gain more experience with this awesome OS by installing some kind of CMS system that will enable me to install an intranet as well as some kind of media management system.

HAs anyone done something similar or can point me in the right direction?
Thanks :)
There are a lot of cms that can be use for media website, WordPress will also do and it would also be best when you use Drupal. These are the php platform but if you want another platform you can use django a Python/Django platform. And if you want java their are also theses OpenCms. So far these are the cms I've tried with great result so far. Actually there are many. Good Luck. Regards and cheers

---

### Post by mondelez on 2022-11-03
I would recommend WordPress for your tasks, I'm sure there is a solution there.

---

