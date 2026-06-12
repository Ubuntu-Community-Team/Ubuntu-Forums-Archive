---
title: "failed to fetch packages while updating"
date: 2015-10-07
forum: New to Ubuntu
---

### Post by jing3 on 2015-10-07
Hello,

Today, I encounter a problem when I use "sudo apt-get update". At the end of update, I always receive below messages:

W: Failed to fetch [http://ppa.launchpad.net/kile/stable/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/kile/stable/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/kile/stable/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/kile/stable/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

I've tried to remove corrupted control files

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update

But, I still can't solve the problematic messages. Could anyone please tell me how to solve this problem?
I'll appreciate so much for your help. ;)

Best,
Jing

---

### Post by mc4man on 2015-10-08
Go 
```
software-properties-gtk
```
Click on Other tab, find that ppa in the list, highlight it & click Remove. Then close the window & click Reload

---

### Post by claracc on 2015-10-08
You have obtained the correct response since the forementioned ppas are not
in the pointed address: You will receive the following message:

```
Not Found

The requested URL /kile/stable/ubuntu/dists/vivid/main/binary-amd64/Packages was not found on this server.
```

if looking for them in web browser.

You can go to software updater and in the "other software" tab, disable these ppas. Reload sources and it is fixed.

---

### Post by jing3 on 2015-10-11
Thanks for your answer. It solved! :D

---

