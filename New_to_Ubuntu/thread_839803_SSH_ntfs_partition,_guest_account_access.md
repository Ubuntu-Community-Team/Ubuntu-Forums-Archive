---
title: "SSH ntfs partition, guest account access"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by whitethorn on 2008-06-24
Hi,

I have an ssh server running on my laptop.  On my computer I set up a guest account.  My problem is in my guest accounts home folder I set up a symlink to my ntfs partition because it's bigger than my ubuntu partition. A friend of mine logged into my computer and tried to access the folder, and he didn't have the proper permissions.  when I ll the folder it belonged to root:root   I tried using chown to change it, but I guess I wasn't able to figure out how. Ne1 know how to do this?

---

### Post by Mikecore on 2008-06-24
> **whitethorn said:**
> Hi,

I have an ssh server running on my laptop.  On my computer I set up a guest account.  My problem is in my guest accounts home folder I set up a symlink to my ntfs partition because it's bigger than my ubuntu partition. A friend of mine logged into my computer and tried to access the folder, and he didn't have the proper permissions.  when I ll the folder it belonged to root:root   I tried using chown to change it, but I guess I wasn't able to figure out how. Ne1 know how to do this?
  

I dont think you want to do that ( given anyone access to your ntfs partion from a linux partition. I don't think they have finalized ntfs write support. I know read works but as far as I know write doesn't if he tried to write to it. that could hose things up. ) but its been a while since I last checked on that issue I could be wrong.

---

