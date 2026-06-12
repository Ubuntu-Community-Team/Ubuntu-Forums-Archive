---
title: "Need New Password"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-04-24
Just installed 12.04 from scratch - all went OK.  Used gksudo nautilus to copy from backup copy of ./home to ./home on new 12.04 install.  Rebooted and pc boots to login screen (was initally configured to automatically log me in) and when I input my password it tells me it is wrong(?).  I'm guessing the quickest way back into my system is to configure a new passsword but how do I do that?  Thanks.

---

### Post by slickymaster on 2014-04-24
Just follow this tutorial: [How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by sudodus on 2014-04-24
This link should help you (unless you have encrypted home)

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Quarkrad on 2014-04-24
Not working but I think(!) I might know the possible cause.  Prior to this I had 14.04 on my machine so ./home was for a 14.04 machine.  I have now installed 12.04 and copied my backed up 14.04 ./home to my new 12.04 ./home.  I followed your link and did not get the graphics but I did get a root prompt.  I went through the password procedure and it looked like it acdepted it but when I logged in via the prompt (dadubuntu login: ) after I put in my new password I get:  **-bash: /home/dad/ .profile: Permission denied **

---

### Post by deadflowr on 2014-04-24
I actually wonder if it's a password problem or a permission problem when you moved the directory over with gksu.

---

### Post by Quarkrad on 2014-04-24
Will it be quicker to re-install from scratch?

---

### Post by deadflowr on 2014-04-24
> **Quarkrad said:**
> Will it be quicker to re-install from scratch?

Maybe not
Follow the procedure in the reset link and see what ownership of the directory is.
```
ls -la /home/username
```
I think the owner might now be root, instead of you.

You might just need to reset the ownership.
```
sudo chown -R you:you /home/username
```

replace username and you references with your stuff.

---

### Post by sudodus on 2014-04-24
I think using an old /home works better if you start with it as a home partition and install (letting the installer know that it should use the old /home)

---

### Post by Quarkrad on 2014-04-24
wow - the instructions from deadflowr worked.  Many many thanks to you all.

---

### Post by sudodus on 2014-04-24
Congratulations to both of you :KS

---

