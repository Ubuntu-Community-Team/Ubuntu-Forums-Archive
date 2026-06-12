---
title: "Disabling openssh-server from automatic startup"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by Kimomaru on 2013-04-10
Hi,
I would like to configure openssh-server to not start automatically on boot.  Am not looking to uninstall since I need it, but would like to control when it's on.  I've tried;

[B]update-rc.d -f ssh remove
[/B][B]update-rc.d -f sshd remove
[/B]
Does anyone know how to accomplish this?

---

### Post by r.stiltskin on 2013-04-11
In the file /etc/init/ssh.conf comment out (with #) the line that begins with "start on ..."

Then when you want to start sshd:
```
sudo service ssh start
```

---

### Post by Kimomaru on 2013-04-11
> **r.stiltskin said:**
> In the file /etc/init/ssh.conf comment out (with #) the line that begins with "start on ..."

Then when you want to start sshd:
```
sudo service ssh start
```

Perfect!  Thank you very much! :)

---

