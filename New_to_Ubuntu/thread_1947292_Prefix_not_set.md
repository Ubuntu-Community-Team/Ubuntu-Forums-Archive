---
title: "Prefix not set"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by SilverlightX on 2012-03-26
I tried to use Wubi and downloaded the appropriate ISO image into the same folder, the installation run seemengly correctly, but after I restarted my computer, and tried to start Ubuntu, &quot;&quot;prefix&quot; is not set&quot; error message appeared. What can be the problem?

---

### Post by bcbc on 2012-03-26
See bug [lpbug]927157[/lpbug]. This error message is common on all Wubi installs every time you boot Ubuntu. It doesn't mean there is a problem. Just some false message due to a grub (mis)configuration. There's no known workaround at this time (but since it doesn't cause any problems, there doesn't seem to be any urgency to fix it).

---

### Post by SilverlightX on 2012-03-26
> **bcbc said:**
> See bug [lpbug]927157[/lpbug]. This error message is common on all Wubi installs every time you boot Ubuntu. It doesn't mean there is a problem. Just some false message due to a grub (mis)configuration. There's no known workaround at this time (but since it doesn't cause any problems, there doesn't seem to be any urgency to fix it).

 Thank you, but what should I do when this message appears? Should I simply wait until Ubuntu starts to boot?

---

### Post by bcbc on 2012-03-26
> **SilverlightX said:**
> Thank you, but what should I do when this message appears? Should I simply wait until Ubuntu starts to boot?

So nothing happens after that? There are some cases where there is a delay before the computer boots. But there could be other issues. What computer brand/model/graphic card do you have? Do you think it's booting with a blank screen or is it hanging? If it's hanging, how long have you waited? Any hard drive activity or not?

---

### Post by SilverlightX on 2012-03-27
> **bcbc said:**
> So nothing happens after that? There are some cases where there is a delay before the computer boots. But there could be other issues. What computer brand/model/graphic card do you have? Do you think it's booting with a blank screen or is it hanging? If it's hanging, how long have you waited? Any hard drive activity or not?

 I tried it another time, now it succeeded. I did the usual user error: I was not patient enough.  Thnak you again for your time and help.

---

