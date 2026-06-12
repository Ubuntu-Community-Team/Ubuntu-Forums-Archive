---
title: "internet is freaky!"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Adolphian on 2008-06-11
i dont know how else to say this.  half of my internet works.  half of it doesnt.  some site work some sites dont.  and when i open update manager half of the downloads are failed.  ive rebooted my computer and the router.  router seems fine.

any help.... please!

firefox 2 and 3 and epiphany all do this.  its like it refuses to view certain sites.

---

### Post by Adolphian on 2008-06-11
also, i posted the previous on my cell phone.

only the quick replys in threads are working.

in all forums i can get into.

---

### Post by kpkeerthi on 2008-06-11
Try disabling IPv6. [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

You must **reboot **after making the changes

---

### Post by Adolphian on 2008-06-11
update manager also stalls, and several things fait, or just say hit, and say zero bytes

---

### Post by Adolphian on 2008-06-11
im sorry kp, its still not working.

---

### Post by Adolphian on 2008-06-11
windows is working perfectly fine......

guys, dont make me go back...

---

### Post by Adolphian on 2008-06-11
sigh, vista here i come.

---

### Post by natman on 2008-06-11
Have you tried using a live CD to see if the live ubuntu works on the PC, if not there could a be a hardware compatibility problem with ubuntu, if the live works perhaps a reinstall ( separate partitions ? )

---

### Post by kpkeerthi on 2008-06-11
It could be that the repository mirror you are using is down. What happens when you run the update from command line and post the output here?
```
sudo aptitude update
```

---

### Post by kpkeerthi on 2008-06-11
It could also be that Ubuntu is not using a proper DNS server. What is the output of ```
cat /etc/resolv.conf
```?

---

