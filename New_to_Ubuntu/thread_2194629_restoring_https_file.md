---
title: "restoring https file"
date: 2013-12-19
forum: New to Ubuntu
---

### Post by kristen2 on 2013-12-19
Hi.
I'm missing the **/usr/lib/apt/methods/https** file for my system, Ubuntu 12.04 64-bit
Could anyone attach it here for me, please? I need it badly

---

### Post by steeldriver on 2013-12-19
Is your apt system currently broken without it? if not, have you tried just installing/reinstalling the apt-transport-https package?

---

### Post by kristen2 on 2013-12-19
Yeah.  I can't download anything from the Ubuntu Software Center with a missing https file.

---

### Post by steeldriver on 2013-12-19
but can you run apt-get from the command line?

```
sudo apt-get install apt-transport-https
```

As far as I know, the standard repositories do not require https transport and so the package isn't installed by default - I assume you need it to install particular software from a 3rd party repository?

---

### Post by kristen2 on 2013-12-19
No, that's not what I need it for. I simply cannot download any software from the Ubuntu Software Center, which I think are all not third party. I don't know. I also can't run the sudo apt-get update command because it gives me an error that I'm missing https. I was able to do it originally, without the https I guess, but suddenly it's not allowing. This happened to me once before and somebody here attached an https file for me and it solved my apt problem. My system was a 32-bit then and now it's a 64-bit, so I can't use that same attachment

---

### Post by kristen2 on 2013-12-19
Sorry. [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install apt-transport-https[/FONT][/COLOR] worked fine
Thank you :)

---

### Post by steeldriver on 2013-12-19
OK that's all good!

---

