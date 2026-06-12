---
title: "Non-GUI Options"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by CosmicFlux on 2008-04-28
Hi,

Does anyone know how to change font size/color/style etc on a non-GUI system? I know it can be done but I'm finding it hard to locate any specific info on this. 

I've read up on **setterm** but I'm not sure if that's just for Virtual Consoles running off the GUI. There must be a file that Linux uses to load the login console with default values for font size, type, color etc but I'm not sure how to find it. I've tried **sudo find / -name <every-keyword-I-can-think-of>** but to no avail.

Cosmic

---

### Post by mrgnash on 2008-04-28
> **CosmicFlux said:**
> Hi,

Does anyone know how to change font size/color/style etc on a non-GUI system? I know it can be done but I'm finding it hard to locate any specific info on this. 

I've read up on **setterm** but I'm not sure if that's just for Virtual Consoles running off the GUI. There must be a file that Linux uses to load the login console with default values for font size, type, color etc but I'm not sure how to find it. I've tried **sudo find / -name <every-keyword-I-can-think-of>** but to no avail.

Cosmic

I think that setterm might be what you are looking for.

```
man setterm
```

---

### Post by CosmicFlux on 2008-04-28
Hmm from what that says I would assume that:

**setterm -foreground white** would change the text to green, but it's not working. 

Using:

**setterm -bold on** I get bold text, but only until I execute a command and then it all reverts back to default. 

Cosmic

---

