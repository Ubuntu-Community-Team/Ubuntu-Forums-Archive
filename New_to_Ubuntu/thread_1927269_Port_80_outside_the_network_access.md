---
title: "Port 80 outside the network access"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by jebaearnest on 2012-02-17
I am not able to access one Public DNS outside the network.
 But the same  Public DNS is working inside the network.

Port 80 works fine inside the network.Outside the network I am not able to acess the same.
But if i change to 8080 again, it works outside also

Do i need to change any settings ?

Sorry for posting so many times. I want to solve the issue.

Thanks for understanding.

---

### Post by CharlesA on 2012-02-17
Sounds like your ISP is blocking port 80.

---

### Post by jebaearnest on 2012-02-17
Is there a way to unblock it.
Actually that is amazon cloud ubuntu instance. I am not sure they will block.

If you pass the command to execute, i ll try  with that.

Thanks.

---

### Post by jebaearnest on 2012-02-17
Issue is fixed after executing "iptables -F -t nat" this command.
Thanks for your help.

---

