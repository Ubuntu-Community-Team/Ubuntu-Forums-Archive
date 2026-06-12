---
title: "Venting, followed by a question."
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Rackham on 2008-05-19
Can someone tell me how to shut off the requirement for sudo and/or eliminate the seemingly millions of annoying prompts asking me for a password to "perform administrative tasks" (even though I'm logged in, as the administrator - or whatever it is in linux)

In a nutshell, if someone could tell me how to shut all this junk off, I'd be grateful - short of that, maybe just tell me how to edit the etc/hosts file without too much grief.

---

### Post by Cypher on 2008-05-19
"sudo" is there for your own protection..it can truely prevent you from doing something that you shouldn't, which might cause things to break or become unstable.

Short of that, if you wish to become "root" for a small period of time to perfom numerous tasks, you could
```

sudo su

```
and then once you've done everything you've wanted to do, return to a regular user with
```

exit

```

---

### Post by Rackham on 2008-05-19
Thanks...

tried that, and it is still giving me a "permission denied" notice.

---

### Post by aysiu on 2008-05-19
I believe it should be ```
sudo -i
```

---

### Post by aysiu on 2008-05-19
> **Rackham said:**
> Thanks...

tried that, and it is still giving me a "permission denied" notice.
You don't have permission to *sudo*?

---

### Post by signseeker on 2008-05-19
are you using the account created by the installer? or have you added a new user?

new users dont automatically get access to sudo. i believe they need to be part of the admin group.

---

### Post by Rackham on 2008-05-19
no, Frankly, I just don't know how to use it - so that's probably 95% of the problem.

---

### Post by aysiu on 2008-05-19
This will make sure you have proper *sudo* privileges:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Once that's in place, you can find out how to edit /etc/hosts with this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

If you want more information on *sudo* and root permissions in general (some of the backstory) read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Rackham on 2008-05-19
gracias...I'll look at that stuff shortly. thanks for the resources.

---

### Post by aysiu on 2008-05-19
If you get stuck at a certain point, let us know, and we'll try our best to help you out.

---

### Post by Paqman on 2008-05-19
> **Rackham said:**
> (even though I'm logged in, as the administrator - or whatever it is in linux)


You aren't logged in as an admin by default. That's an important security feature. One of the main reasons there's so much malware on Windows is that most people are running as an admin all the time. On Linux you temporarily take on admin powers when you want to do something that requires it.

---

### Post by Rackham on 2008-05-19
Cool, the gksudo nautilus worked. Many thanks for the assistance - now, I'm curious as to how to get windows to see the ubuntu machine on the network... I thought there was a pretty straight forward way to do this, but I'm not seeing anything that looks like it would facilitate that - smb is installed by default I'm guessing, and I can see and browse the Windows shares, just not vice versa.

---

