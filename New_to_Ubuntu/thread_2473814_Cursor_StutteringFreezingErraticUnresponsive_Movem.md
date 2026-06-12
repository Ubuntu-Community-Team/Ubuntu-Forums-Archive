---
title: "Cursor Stuttering/Freezing/Erratic/Unresponsive Movement"
date: 2022-04-14
forum: New to Ubuntu
---

### Post by androy518 on 2022-04-14
Hello
I installed Ubuntu on a HP Pavilion 15t-cs200 laptop. Recently, I have been having issues with the cursor. After a while, the cursor movement becomes erratic and inconsistent.  When I reboot the laptop, sometimes, it starts with the erratic cursor movement and sometimes the cursor moves normally. I am using the trackpad on my laptop to move the cursor. When I run this command: "sudo systemctl suspend" then turn on the laptop again, the cursor starts moving normally again but starts stuttering again after a while. Sometimes, normal cursor movement returns. Do any of you know what could be causing this issue. Thank you.

---

### Post by Autodave on 2022-04-14
First, I would try another mouse.....either wired or wireless.  If problem continues, then I would be looking for an overheating condition.

---

### Post by androy518 on 2022-04-15
I just ran this command "xinput list" and this appeared: [https://imgur.com/a/AGbPeCQ](https://imgur.com/a/AGbPeCQ)
There appears to be two of the same touchpad driver installed. Could this be causing the issue that I am having? How can I solve this?

---

### Post by androy518 on 2022-04-15
> **androy518 said:**
> Hello
I installed Ubuntu on a HP Pavilion 15t-cs200 laptop. Recently, I have been having issues with the cursor. After a while, the cursor movement becomes erratic and inconsistent.  When I reboot the laptop, sometimes, it starts with the erratic cursor movement and sometimes the cursor moves normally. I am using the trackpad on my laptop to move the cursor. When I run this command: "sudo systemctl suspend" then turn on the laptop again, the cursor starts moving normally again but starts stuttering again after a while. Sometimes, normal cursor movement returns. Do any of you know what could be causing this issue. Thank you.

I have tried another mouse. The mouse works properly. It seems like an issue related to the trackpad.

---

### Post by ActionParsnip on 2022-04-16
If you run
```

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

```
Does it help? If so, we can make the option stick

---

