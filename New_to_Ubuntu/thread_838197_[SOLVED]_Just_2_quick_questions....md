---
title: "[SOLVED] Just 2 quick questions..."
date: 2008-06-23
forum: New to Ubuntu
---

### Post by linuxisfree on 2008-06-23
Hi all,

Just wanna know if you have anything that can help me regarding the ff:

1. Those who know Window$ know that <ctrl>+<esc> button combination (or the windows button ---- Super button to us) accesses the Start Menu, is there any equivalent here in Ubuntu that'll allow me to access either the Applications, Places, or System Menu?

2. Here in 8.04, there are SOME times when i play a video that my screen suddenly goes blank (no video, no audio), and i can't do anything, so i have to restart my Comp. It only happens sometimes, though... Any ideas as to why it happens? (I use VLC, but it has happened in whatever player i use: Totem, Kaffeine, etc...)

Thanks so much!!!

---

### Post by AndThenWhat on 2008-06-23
> **linuxisfree said:**
> Hi all,

Just wanna know if you have anything that can help me regarding the ff:

1. Those who know Window$ know that <ctrl>+<esc> button combination (or the windows button ---- Super button to us) accesses the Start Menu, is there any equivalent here in Ubuntu that'll allow me to access either the Applications, Places, or System Menu?

2. Here in 8.04, there are SOME times when i play a video that my screen suddenly goes blank (no video, no audio), and i can't do anything, so i have to restart my Comp. It only happens sometimes, though... Any ideas as to why it happens? (I use VLC, but it has happened in whatever player i use: Totem, Kaffeine, etc...)

Thanks so much!!!

1. Alt+F1
2. Sounds like a possible kernel lockup. You would need an error message to get help. A way you can get an error message would be to launch totem or vlc from a terminal window and leave the terminal in the foreground until the program crashes. Then make note of the resulting error message.

---

### Post by DGortze380 on 2008-06-23
> **AndThenWhat said:**
> 1. Alt+F1
2. Sounds like a possible kernel lockup. You would need an error message to get help. A way you can get an error message would be to launch totem or vlc from a terminal window and leave the terminal in the foreground until the program crashes. Then make note of the resulting error message.

Error messages should also be logged. Not sure which one, I can find out if you'd like. Check /var/logs/messages (there are other logs you can look through too. A useful command for this is:

```
 tail /var/logs/messages 
```

---

### Post by linuxisfree on 2008-06-23
Hey Thanks you two!!!

1. alt+F1 ??? ](*,)
2. this is what i get when i tail the log
<code>migs@Migs-Laptop:~$ tail /var/log/messages
Jun 23 21:15:29 Migs-Laptop kernel: [   52.340323] NET: Registered protocol family 17
Jun 23 21:15:34 Migs-Laptop dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Jun 23 21:15:34 Migs-Laptop dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1 
Jun 23 21:15:34 Migs-Laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Jun 23 21:15:34 Migs-Laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Jun 23 21:15:34 Migs-Laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Jun 23 21:15:34 Migs-Laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Jun 23 21:34:46 Migs-Laptop -- MARK --
Jun 23 21:54:46 Migs-Laptop -- MARK --
Jun 23 22:04:26 Migs-Laptop kernel: [  625.412265] gedit[7729]: segfault at 00000094 eip 0806d9cd esp bfb03990 error 4
migs@Migs-Laptop:~$ 
</code>
ps: No error message in vlc yet

By the way, is saw your sig Dan, have pretty much the same major, good luck! (Graduated last year!):D

---

### Post by DGortze380 on 2008-06-23
thanks linuxisfree, can't wait to get out and use it, lmao.
There are other logs in /var/log that may hold an error message about vlc. try complete removal through synaptic and reinstall.

---

### Post by linuxisfree on 2008-06-24
> **DGortze380 said:**
> thanks linuxisfree, can't wait to get out and use it, lmao.
There are other logs in /var/log that may hold an error message about vlc. try complete removal through synaptic and reinstall.

You mean VLC? Alright then, will try that... will post what happens (if the "blackout" happens again, i'll post about it.)

Thanks!

---

### Post by hyper_ch on 2008-06-24
(1) It is adviced to use a descriptive thread title that reflects the content/inquiry/problem within instead of using a generic title like "noob here" or "need help".

(2) It is also adviced to split up unrelated questions into several threads so that each one may be answered individually.

---

### Post by linuxisfree on 2008-06-24
> **hyper_ch said:**
> (1) It is adviced to use a descriptive thread title that reflects the content/inquiry/problem within instead of using a generic title like "noob here" or "need help".

(2) It is also adviced to split up unrelated questions into several threads so that each one may be answered individually.

Points noted. Thanks. BTW, is there anyway that one can change the thread title? (just asking...:D)

---

### Post by DGortze380 on 2008-06-24
> **DGortze380 said:**
> thanks linuxisfree, can't wait to get out and use it, lmao.
There are other logs in /var/log that may hold an error message about vlc. try complete removal through synaptic and reinstall.

Yup, remove and reinstall vlc through synaptic, sorry for being vague before. Any luck with that?? I know on my first install of ubuntu (back with 6.10 i think) I had to compile from source to get it to work.

---

### Post by linuxisfree on 2008-06-25
> **DGortze380 said:**
> Yup, remove and reinstall vlc through synaptic, sorry for being vague before. Any luck with that?? I know on my first install of ubuntu (back with 6.10 i think) I had to compile from source to get it to work.

I did reinstall it and, so far, it hasn't mucked up yet, so... THANK GOD!!!:)
Let's hope that it never does, but, in case, i will definitely post (so i won't mark it as solved just yet, may wait til the weekend...).

Thanks again, all of you!

---

### Post by Canis familiaris on 2008-06-25
If error still persists, try updating through Automatic Updates. Many a time, it solves (or rarely worsens?) the problem.

---

### Post by linuxisfree on 2008-06-27
Hey everyone! Just an update, it seems that the problem also occurs sometimes when i restart / shutdown (especially after a major update)... anyone got an idea as to what the problem could be?

EDIT: Could have been a kernel problem... just updated again recently, and its ok now!:D

---

