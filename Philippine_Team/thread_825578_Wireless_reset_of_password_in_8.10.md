---
title: "Wireless reset of password in 8.10"
date: 2008-06-11
forum: Philippine Team
---

### Post by monsag on 2008-06-11
Magandang umaga/tanghali/hapon/gabi po sa inyong bumabasa nito :-)

I have been "playing" with Ubuntu since 6.10, and I "was" happy with 7.10 primarily because the Intel wireless card on my old Neo laptop was working quite well with my WRT54Gs at home and the one in my office, using WPA2. 

7.10 also finally allowed me to have my maximum screen resolution 1280x768, even after a reboot. I did find the "manual step" how to do this from one of the threads.

Now, this is my current problem. Am sure there will be more, but you folks are here for that reason, right? :-)

After upgrading to 8.04, I noticed that I aside from the fact that I have to retype my password after each reboot (dual-booting pa po ako), I also have "re-choose" the WPA2-Personal from the drop down list. I thought changing the kind of encryption both on my home-based WRT54G and on the "Manual network configuration" would help, so I tried WPA and WEP, but no dice.

Since I will be overseeing, very soon, more than a handful of new wireless desktops running on 8.10, I am inclined to just forgo the authentication, broadcast my ESIID and then just implement a mandatory MAC address rule, entering the individual MAC addresses of the desktps on the WRT54G I also use in school. Feedback? Input? Help?

Yes, this set-up is for a school lab.

I am not a developer, a coder or anything close to being an "expert" on anything related to computers. I am just an old guy who has been "playing" with computers for a long time, quite comfortable in using computers, read a lot about computers, and who happens to appreciate this wonderful tool. In short - I'd greatly appreciate the "layman terminologies" when possible from those who would be so kind enough to hand-hold this old guy in introducing FOSS and Ubuntu to this particular small corner of Quezon province.

Isang paunang pasasalamat po sa inyong may mga ginintuan at mala-Ubuntung puso :-)

Ka Ramon

direct email is also welcome - monsagullo at gmail.com

---

### Post by loell on 2008-06-11
hello,

try **wicd** as suggested in this thread

[http://ubuntuforums.org/showthread.php?t=773016]("http://ubuntuforums.org/showthread.php?t=773016&highlight=wireless+reenter+password")

---

### Post by monsag on 2008-06-11
> **loell said:**
> hello,

try **wicd** as suggested in this thread

[http://ubuntuforums.org/showthread.php?t=773016]("http://ubuntuforums.org/showthread.php?t=773016&highlight=wireless+reenter+password")
Maraming salamat po :-) I will try ASAP and will post my experience.

Stretching your kindness, any thoughts in my plan to just use mandatory MAC rule on my Linksys WRT54G viz a viz the 40 desktops that I will soon supervise? Instead of a password, my very limited understanding is, this approach will simplify the wireless connectivity?

---

### Post by loell on 2008-06-11
40 desktop with mac rule sa wireless router?  mukhang  mabusising  setup po yan. ;)

---

