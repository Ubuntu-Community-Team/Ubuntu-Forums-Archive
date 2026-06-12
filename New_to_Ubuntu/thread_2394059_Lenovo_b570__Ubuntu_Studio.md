---
title: "Lenovo b570 / Ubuntu Studio"
date: 2018-06-12
forum: New to Ubuntu
---

### Post by chrisbengtson7 on 2018-06-12
Hello Friends!

I installed Ubuntu Studio via pen drive. It booted well when alongside win 7. Then I installed Ubuntu on the entire disk and did away with win 7. 

Now it will not boot to linux. PXE-E61: Media test failure.

I have put at least 8 solid hrs in on this and would appreciate help. Let me know what data I can give you to assist. 

[http://paste.ubuntu.com/p/4ztXNHTwxV/](http://paste.ubuntu.com/p/4ztXNHTwxV/)

I have read and tried to understand this [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Best Regards, 
Chris

---

### Post by leunam12 on 2018-06-12
Seem like your computer is trying to boot from network and it doesn't find it. Disable boot from network (if you have that option) and try to configure your boot options in BIOS so that the hard drive is the first option and see what happens.

---

