---
title: "TV Tuner"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by jethier on 2008-08-02
What's the UBUNTU equivalent to Windows Media center.

---

### Post by JillSwift on 2008-08-02
Not sure it's *equivalent* or not, but you may want to look at [MythTV]("http://www.mythtv.org/"). In fact, I believe there's a "[Mythbuntu]("http://www.mythbuntu.org/")" out there...

---

### Post by OutOfReach on 2008-08-02
I used to have Windows XP Media Center, and from the looks (I haven't tested it out yet) Mythbuntu looks like a contender. There's also LinuxMCE but I also haven't tried that out.

---

### Post by jethier on 2008-08-02
Thank you. 

How do I check (before I go about installing Mythbuntu) if UBUNTU has detected my TV tuner card??

---

### Post by JillSwift on 2008-08-02
> **jethier said:**
> Thank you. 

How do I check (before I go about installing Mythbuntu) if UBUNTU has detected my TV tuner card??
Well, you can type the following into a terminal:
```
sudo lshw
```The device will be listed in there, I do believe, if it was detected.

```
sudo lshw -C multimedia
```This may make a much more brief and therefore more useful list.

---

