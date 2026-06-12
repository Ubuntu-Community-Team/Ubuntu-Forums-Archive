---
title: "DVD drive not working on dell laptop"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by thedon_1 on 2008-08-31
This is on behalf of a friend of mine who recently installed ubuntu.

He has a dell 620 laptop and it doesn't seem to have recognised his DVD drive, he can't use any media in the drive.

I asked him to get me the model number of his drive from hs windows partition and he says it's a HC-DT-ST-DVDROM.

Any ideas why it's not working?

Thanks

---

### Post by thedon_1 on 2008-08-31
Please, anyone?

---

### Post by gpilkay on 2008-08-31
I don't know enough about the system in question to really say anything useful, can you post the specs (memory, processor, etc) and if you also still have Windows on it?  And what version of Ubuntu are you using?  I myself had a computer that refused to know its CD was there under Kobuntu, normal Ubuntu worked well, though.

The single easiest quick-fix is to always make sure you have the latest non-beta Ubuntu release to try first.  That's 8.04.1, you can get it from the Live-CD download.

---

### Post by halitech on 2008-08-31
if he still has windows, does it work there? if it does, then what do you mean by it doesn't reconize any media?

---

### Post by unutbu on 2008-08-31
To help your friend, we will probably need to see the output of some terminal commands. Please post
```

sudo lshw -C disk
```

---

