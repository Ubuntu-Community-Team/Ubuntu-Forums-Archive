---
title: "[SOLVED] Minor problem: Wireless LED does not work in ubuntu 8.04."
date: 2008-07-19
forum: New to Ubuntu
---

### Post by bhadotia on 2008-07-19
I think the problem is so trivial that I did not bother about it for the last three months I've been using hardy.
But I thought I should make a thread to see if someone else has the same problem and has hopefully solved it.
My wireless card is Intel PRO 3945 bg.
The LED used to work fine in 7.10 , wherein ubuntu used restricted drivers for the wireless.

---

### Post by bhadotia on 2008-07-20
The bug report regarding this issue is over [URL="https://bugs.launchpad.net/ubuntu/+bug/221633"]here.
[/URL]

---

### Post by JagDragon on 2008-07-20
I presume you are using the iwl3945 module/driver/thing. How to find this out is ```
lsmod | grep iwl3945
```

Do you know what module should run the LED? I know that on thinkpads it is thinkpad_acpi, but I don't know about Lenovo laptops. The issue could be fixed next kernel update, you never know...

---

### Post by bhadotia on 2008-07-20
> **JagDragon said:**
> I presume you are using the iwl3945 module/driver/thing. How to find this out is ```
lsmod | grep iwl3945
``` 
The above command gives the following output:
```
abhishek@ubuntu:~$ lsmod | grep iwl3945
iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945
```


> Do you know what module should run the LED?
I don't know about the module. I have hp 530 notebook.
Any suggestion?
Thank you for the reply.

---

### Post by beercz on 2008-08-20
I have the same problem on my Lenovo 3000 N200 laptop.

Any clues anyone?

---

### Post by bhadotia on 2008-11-13
Solved in ubuntu 8.10. But there is still a bug in this driver (iwl3945) [(see the release notes)]("http://www.ubuntu.com/getubuntu/releasenotes/810#Cannot%20reactivate%20Intel%203945/4965%20wireless%20if%20booting%20with%20killswitch%20enabled").

---

