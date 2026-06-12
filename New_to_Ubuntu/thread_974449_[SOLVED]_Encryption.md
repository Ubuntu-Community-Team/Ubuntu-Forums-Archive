---
title: "[SOLVED] Encryption?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-11-07
Is there a way to encrypt an entire Ubuntu installation not using the alternate CD? So for example, using truecrypt to encrypt? My problem is this. I am paranoid about my computer getting stolen and people being able to some how get my information. Now, I can easily use the Alternate CD to encrypt my installation ( which I have done for a while ), but I am also going to have it be a dual boot with Windows Vista Business. How would be the best way to go about encrypting both installations but also when booted into one of them, I would have access to the other?

---

### Post by jamesrfla on 2008-11-07
Try ecryptfs. I haven't used it myself but some people recommended it to me and it will encrypt your entire Ubuntu install. Let me know if it works.

---

### Post by Coreigh on 2008-11-07
I have not done the whole disk encryption but I think TrueCrypt can do this too. TrueCrypt can also access multiple encrypted containers so even if you encrypted each installation individually you would be able to mount and access the other.

---

### Post by Sylchat on 2008-11-07
For whole disk encryption you may want to try CompuSec ([http://www.ce-infosys.com/english/downloads/free_compusec/free_compusec_linux.html](http://www.ce-infosys.com/english/downloads/free_compusec/free_compusec_linux.html)) which is free and available for both Windows and Linux, although dual boot may not be supported.

I didn't try it myself though.

---

### Post by teddks on 2008-11-07
You can use the Alternate CD (which is surely the easiest way to do that, short of writing your own early userland). dm-crypt is fully compatible with [FreeOTFE](http://en.wikipedia.org/wiki/FreeOTFE). Just use a filesystem that's compatible with Windows, which include ReiserFS and ext2/3 (assuming the right drivers are installed).

---

### Post by slughappy1 on 2008-11-07
Ecryptfs is only for linux. So I don't see how I could use this to encrypt a Windows installation. CompuSec on the other hand, the linux version hasn't been updated since 2005. And all of the versions they say are supported are non debian based disros. Would it still work?

---

### Post by slughappy1 on 2008-11-07
The problem I am having is not with encrypting the Ubuntu installation. I have done that for a while now. But doesn't the Alternate CD use LUKS? Which LUKS can not be read by any Windows software that I know of.

---

### Post by teddks on 2008-11-07
> **slughappy1 said:**
> The problem I am having is not with encrypting the Ubuntu installation. I have done that for a while now. But doesn't the Alternate CD use LUKS? Which LUKS can not be read by any Windows software that I know of.

The key in that sentence is 'that I know of'.

That is not a true thing any more. Read this wikipedia article:

[http://en.wikipedia.org/wiki/FreeOTFE](http://en.wikipedia.org/wiki/FreeOTFE)

---

### Post by slughappy1 on 2008-11-18
Thank you teddks, I posted something earlier asking about the same question and no one knew about that. Thanks, it was EXACTLY what I was looking for.

---

### Post by hyper_ch on 2008-11-18
good to know... I also thought luks/dm-crypt can't be accessed from windows :)

---

