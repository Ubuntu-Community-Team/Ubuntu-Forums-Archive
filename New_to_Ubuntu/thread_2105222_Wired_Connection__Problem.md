---
title: "Wired Connection : Problem"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by 7Starphy on 2013-01-15
I am using a LAN connection for accessing the Internet , but 'wired connection ' is not getting detected in the Network Settings . It says Unmanaged but it is not detecting the presence of a wired cable . Ironically ,I am able to access the internet (which is how I am making this post ) . I remember messing up some configurations long time ago and I dont know how to reverse it back . Can anyone please help me out with this problem ?

---

### Post by Cheesehead on 2013-01-15
> **7Starphy said:**
> I remember messing up some configurations long time ago

That could mean a lot of things.
Most commonly, a user edits /etc/network/interfaces. If that's what you did, post what the file now contains.

Less commonly, a user uninstalls Network manager and replaces it with wicd. If you did that, then you must reverse the process.

Occasionally, a user will *really* haywire their system in some mysterious ways.

Can you give us any clues as to what you may have done?

---

### Post by 7Starphy on 2013-01-15
Yeah thanks,I figured out the problem and now things seem to work fine :)

---

