---
title: "Unsupported GPT Detected"
date: 2008-09-01
forum: Other OS Talk
---

### Post by Inhumane on 2008-09-01
So I'm trying to install Arch Linux again, but I'm encountering this problem when trying to partition my HD using their built in cfdisk (which is a required process during the installation:

    Warning!! Unsupported GPT Detected. Use GNU Parted.

Why is this? I remember being able to install Arch on this very same hard drive not too long ago just fine (though I just used auto partition at that time). Any way to fix this?

I posted this on the Arch forums but as I suspected, no reply for 3 days now.

---

### Post by mips on 2008-09-02
I google a bit on this for you but I'm none the wiser unfortunately. Sounds almost like a problem people experience when trying to install XP on a old Mac HD.

---

### Post by Inhumane on 2008-09-02
> **mips said:**
> I google a bit on this for you but I'm none the wiser unfortunately. Sounds almost like a problem people experience when trying to install XP on a old Mac HD.

Yup. I googled this before posting here as well and I got a few foreign forums and the rest were this Mac problem :(

You know, I just thought of something. A few months ago I was messing around with osx86 (aka installing Mac on your PC). This could definitely be the reason. But then how come I was able to install Vista over it, and even Vista didn't repartition it to the correct format?

And if this is the case, what could I do aside from wiping the partition? As I want to keep Windows for now

---

### Post by mips on 2008-09-02
> **Inhumane said:**
> 
You know, I just thought of something. A few months ago I was messing around with osx86 (aka installing Mac on your PC). This could definitely be the reason. But then how come I was able to install Vista over it, and even Vista didn't repartition it to the correct format?


I actually wanted to ask you that directly but did not want to implicate you in anything. Best bet would be to zero the drive with dd.

---

