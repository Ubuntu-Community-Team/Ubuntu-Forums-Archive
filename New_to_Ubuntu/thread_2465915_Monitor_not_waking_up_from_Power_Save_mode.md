---
title: "Monitor not waking up from Power Save mode"
date: 2021-08-14
forum: New to Ubuntu
---

### Post by syed_b_huq on 2021-08-14
I have an older version of Ubuntu (11.x). After a long period of not using, I turned on my Ubuntu Desktop. It loaded all the way to the login screen. Eventually the Monitor went into sleep mode and I am unable to "wake up" the system. I have clicked on the keyboard and mouse many times but the Monitor does not wake up. The Desktop is running.

I turned the monitor ON/OFF, it says, going into Sleep mode and does not respond.

How to fix this ?

Tks
Syed
.ps Previously all was working but I had not logged in for a long long time. Trying to get back to Ubuntu.

---

### Post by ActionParsnip on 2021-08-15
Does the system have a make and model?
Does the monitor have a make and model? 
What is the output of
```

sudo lshw -C display

```
Thanks

---

### Post by syed_b_huq on 2021-08-16
System: Dell Optiplex 745
Monitor: Dell SE198WFPv

Since I can't get to a log in screen, not sure how to execute that lshw command

---

### Post by bobunderwood99 on 2021-08-16
Hold the power button (on the computer) down until it turns off or, unplug it from the power. Do you remember your username and password?

---

### Post by syed_b_huq on 2021-08-17
Hi,
I have done a full reboot (holding the power button down), the system started and I am able to log in. I have created the output of:
# sudo lshw -C display and attaching it here .

What I am afraid of, once the monitor goes into sleep mode, I will not be able to recover from it (that is the original problem).

Tks
Syed

---

### Post by syed_b_huq on 2021-08-17
Hi, I have added an attachment that shows the output of the Code you mentioned.

---

### Post by syed_b_huq on 2021-08-17
Hi everyone,
I think you can CLOSE this issue. After I have logged in once, the system does go into sleep mode from lack of activity but I am able to revive and move on.
I am going thru an upgrade to 18.04 now.
I have also replaced the system Batt on the motherboard.

I think the original issue was, I reached the log-in screen but did not log in and once it went into sleep, could not get it to wake up. But after a hard reboot and log-in. All seems to be fine.
I don't understand the reason for the original problem.

I am on my way and thanks for all the questions and support.

Syed

---

