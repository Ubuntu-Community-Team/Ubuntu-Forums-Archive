---
title: "reinstalled 13.04 GUFW firewall no auto startup"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by atlus2 on 2013-10-24
After updating to 13.10 I went back to 13.04. I installed GUFW firewall but it appears off when I login so after turning it on then when i close settings manager is goes back to off .   Also I installed Unity Tweak Tools but cannot find it . Also I check the box Raring Ringtails in " software & updates" but dunno if I should.  After I installed 13.04 it didnt have that checked. photo attached.

---

### Post by whitesmith on 2013-10-24
Startup Applications is there for exactly one reason: to force software to auto-start when the machine comes up. I'm not a Unity person, so help for that will have to come from someone else.

---

### Post by atlus2 on 2013-10-24
ok thanks and I see that  iptables has ufw firewall so the "gufw configuration" I intsalled was just a tool to configure it so i removed that and then ran terminal command  "sudo ufw enable"   I think that was already set anywayzzz.  Now I uncheck the  box Raring Ringtails in software & updates. like it was before.

---

### Post by deadflowr on 2013-10-24
If I remember gufw always appears off when launched.
If you want to know if the policies you've set are enable and working running
```
sudo ufw status
```
in a terminal and it will show whatever you've done in gufw.

---

### Post by atlus2 on 2013-10-25
Thank you very much I will check that out...

---

### Post by atlus2 on 2013-10-25
I did that just now and its active,,,  tHanKs agAin

---

