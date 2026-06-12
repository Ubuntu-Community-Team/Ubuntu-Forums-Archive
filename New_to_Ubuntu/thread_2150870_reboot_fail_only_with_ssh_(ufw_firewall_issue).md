---
title: "reboot fail only with ssh (ufw firewall issue?)"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by creepwood on 2013-06-02
I didn't have this issue before 13.04 (had 12.10). I'm not sure it started to happen then, I don't reboot that often.

Problem:
When I sudo reboot now from ssh or terminal the machine starts to reboot but halts with a screen saying:

```
Broadcast messagr from creepwood@Babel
          (/dev/pts/0) at 19:44 ...

The system is going down for maintenance NOW!
Skip stopping firewall: ufw (not enabled)
```

Just sits there, nothing happens, I try different keys like 'Y' or 'N' or esc, space, return etc. nothing happens until I press ctrl+alt+del

Then there's a screen with some [OK] and [FAIL] It's going by too quick to see what's failing. I tried the pause key, didn't help. I saw atleast two of them fails, and I think one of them was about not being able to stop all services before going down.

The weird part is, that if I do this in the gui, it works just fine. But since this is a server, I do most things by SSH.

---

### Post by Hekabe on 2013-06-02
Does init 6 work properly?

---

### Post by creepwood on 2013-06-02
Thank you for your answer, but I have no idea with init 6 is. I'm a newbie.

---

### Post by Hekabe on 2013-06-03
"init 6" is, I think, the command that reboot actually runs. Essentially, it's a reboot command. Also, you could try "shutdown -r now". Also, does it reboot after it gives you all the messages?

---

### Post by creepwood on 2013-06-04
Both sudo init 6 and sudo shutdown -r now doesn't give this error.

---

### Post by creepwood on 2013-06-22
Bump. I'm still having trouble with this :(

---

### Post by lothus2 on 2013-08-14
Just posting (had to create an account, heh) to say that I've got the same problem. I'm using version 13.04 as well. The machine usually runs headless and so being able to reboot/remotely manage it is important. reboot via SSH always fails with the stalled "Skip stopping firewall: ufw (not enabled)" screen until I hit Control-Alt-Del on the physical keyboard, at which point it continues. Shutdown often does the same thing, but not always. I assume the issue is connected and hope someone can offer assistance to both of us. :/

---

