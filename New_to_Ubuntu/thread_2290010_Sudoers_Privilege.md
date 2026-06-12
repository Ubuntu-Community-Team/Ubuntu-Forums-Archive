---
title: "Sudoers Privilege"
date: 2015-08-08
forum: New to Ubuntu
---

### Post by thekotaksamapah on 2015-08-08
I looking for thread, but I can't find it. So correct me If I am wrong. I really frustrated about this LOL.

I Try make user then I give privilege user same as root but when I use to make directory, something happened like this

 ```

stack@devstack-net:/home/devstack-net$ mkdir devstackmkdir: cannot create directory ‘devstack’: Permission denied
stack@devstack-net:/home/devstack-net$



```

I have give command like this in /etc/sudoers file, but it can't give effect.

```
[COLOR=#7A0874]**echo**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#FF0000]"stack ALL=(ALL) NOPASSWD: ALL"[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**>>**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**/**[/COLOR][COLOR=#000000]etc[/COLOR][COLOR=#000000]**/**[/COLOR][COLOR=#000000]sudoers[/COLOR]
```

Please guide me to the right way from this problem. :( :(

---

### Post by steeldriver on 2015-08-08
NOPASSWD does not mean NOSUDO - you still need to prefix your command with sudo in order to escalate your privileges

```

sudo mkdir somedir

```

---

