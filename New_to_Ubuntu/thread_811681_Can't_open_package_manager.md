---
title: "Can't open package manager"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by rogerzoom on 2008-05-29
I need help - I'm new to ubuntu and I must have made an error trying to install skype. When I try to open the Synaptic Package manager I get this message:
> E: Type '--14:31:46--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


What must I do?

---

### Post by Seisen on 2008-05-29
> **rogerzoom said:**
> I need help - I'm new to ubuntu and I must have made an error trying to install skype. When I try to open the Synaptic Package manager I get this message:


What must I do?

Post your source list

```
cat /etc/apt/sources.list
```

---

### Post by FuturePilot on 2008-05-29
Actually try
```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by rogerzoom on 2008-05-29
where do I post the source list?

---

### Post by FuturePilot on 2008-05-29
You can post it right here.

---

### Post by drs305 on 2008-05-29
You have this posted in the general forum as well. I suggested the solution on that forum. ;-)

[http://ubuntuforums.org/showthread.php?t=811616#5](http://ubuntuforums.org/showthread.php?t=811616#5)

If that doesn't work, continue to post in one thread or the other. If it does, please mark both solved.

---

### Post by rogerzoom on 2008-05-29
Thanks very much for your help. All sorted out.

---

