---
title: "Program wont launch"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Mick8882003 on 2008-05-26
I installed tux guitar to use, successfully installed, but it wont launch, seems strange, just reinstalled ubuntu so yea.

---

### Post by tabithaboof on 2008-05-26
> **Mick8882003 said:**
> I installed tux guitar to use, successfully installed, but it wont launch, seems strange, just reinstalled ubuntu so yea.

Try launching from the command line using the command "tuxguitar" and post the output here.

---

### Post by Mick8882003 on 2008-05-26
damn:

/usr/bin/tuxguitar: 21: /usr/local/opt/java/jre/bin/java: not found

I see now, have to look up java!?

Thanks

---

### Post by tabithaboof on 2008-05-26
sudo apt-get install sun-java6-plugin

That should do it for you I think.

---

