---
title: "ssh command"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by seyiisq on 2008-06-14
% ssh user@192.168.x.y
I was trying to use the above but i keep getting a connection refuse error
pls can someone help

---

### Post by Joeb454 on 2008-06-14
Does the other PC have SSH Server installed?

On Ubuntu you could run ```
sudo apt-get install openssh-server
```

---

### Post by dje on 2008-06-14
1. Do you have a firewall configured that is blocking the ip of the computer you're connecting from or denying connections to the other computer?

2. Have you installed openssh-server on the computer you are connecting TO?
```
sudo apt-get install openssh-server
```

3. If so is it started?
```
sudo /etc/init.d/ssh start
```

---

