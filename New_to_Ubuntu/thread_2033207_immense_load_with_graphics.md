---
title: "immense load with graphics"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by npk1npk on 2012-07-25
[COLOR=#800000]I have a serious problem in my laptop.It [/COLOR][COLOR=#800000]appears that something
fundamental is going wrong whenever I start[/COLOR][COLOR=#800000] a browser or a
graphics program.Then the load surges (I see it when I run a top[/COLOR][COLOR=#800000]
command),and the laptop (Dell Precision-M4600) is practically[/COLOR][COLOR=#800000]
useless.I have recently upgraded to Ubuntu 12.1.I have the[/COLOR][COLOR=#800000] impression that the
graphics card does not get along with[/COLOR][COLOR=#800000] Ubuntu. For example,when I
go to youtube then the system slows down[/COLOR][COLOR=#800000] immensely.The same
happens when I compile with gcc and have a[/COLOR][COLOR=#800000] plotting program open.
The truth is that the problem appeared before[/COLOR][COLOR=#800000] I upgraded to the
latest Ubuntu version,but only shortly before.In[/COLOR][COLOR=#800000] the past
everything was fine.Any ideas on a "solution"[/COLOR][COLOR=#800000]?My laptop
is practically useless.Thanks very much.
PS, I looked for additional drivers in the hardware part of the
administration section,but nothing helpful came up,I only got that 
the ATI/AMD FGLRX graphics driver is proprietary and can not be installed.[/COLOR]

---

### Post by richpri on 2012-07-25
I am unaware of any Ubuntu 12.1 so I will assume that you meant Ubuntu 12.04.

If you are running UNITY as your front end [the default] then you may want to revert to Gnome.

To do this:
First use apt or synaptic to install gnome-session-fallback
Then restart the computer and [[before you sign on]] click the gear wheel in the upper right corner of the sign on window and select gnome classic. 

This solved a similar problem for me.  See this link for more details.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1027724](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1027724)

---

### Post by QIII on 2012-07-25
If you are using 12.10, you shouldn't be unless you are testing it.  Since it is in development, it would not surprise me at all that the proprietary driver will not work yet.

Assuming you are actually using 12.04:

The FirePro driver may have to be installed from the AMD website.  I am not certain if the fglrx driver will work.

Edit:  it appears that the proprietary fglrx driver in the repo will work with that card.  What leads you to believe it can't be installed?

---

### Post by npk1npk on 2012-07-31
Thanks a lot for your messages. I tried the first by switching to gnome, but unfortunately and after some "grace" period the problem came back. As I have a double boot system, I logged in to windows and surprisingly (?) the problem appears to be there as well. I only opened the browsers and they were slow. Looks like the problem is  more fundamental (?). Regarding the driver, the message I got was that installation of the card is not possible, if I recall well due to a proprietary reason. I also went to the website pointed to in the second message to download the driver, but I could only found ones that had to be purchased and no free one. In any case my knowledge of linux is limited. This problem appears to be quite nasty, but it apparently showed up only to a few people. Any suggestions highly welcome, thanks a lot again for your older messages.

---

### Post by npk1npk on 2012-12-05
A technician came and found that the fan had to be cleaned.This was causing a surge in the temperature,which in turn was slowing down the machine dramatically.So the fan is something that has to be checked.

---

### Post by Wim Sturkenboom on 2012-12-05
Thanks for the feedback; maybe you can mark the thread as solved using the thread tools just above the first post.

And yes, a colleague of mine had a similar issue with his windows laptop.

---

