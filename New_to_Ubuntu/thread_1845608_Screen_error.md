---
title: "Screen error"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by Eleeist on 2011-09-17
Hi,

I want to use screen to run something in background. This is my command:

```
screen -S java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```I get this error:
> 
Error: Unknown option x1024MThe command runs ok if type without "screen -S"

I had no problems with screen and this commad on Debian.  Recently I switched to Ubuntu and now is what I get...

Would anyone be willing to help?

---

### Post by Old_Grey_Wolf on 2011-09-17
```
screen -S minecraft java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```

---

