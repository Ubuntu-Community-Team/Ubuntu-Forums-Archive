---
title: "g++ / -std=c++0x ?"
date: 2010-03-01
forum: Programming Talk
---

### Post by fade2gray on 2010-03-01
Ubuntu 8.04.1 server edition.

I am seeing this when running a configuration file prior to compiling...
> checking if g++ supports C++0x features with -std=c++0x... [COLOR="Red"]no[/COLOR]
But I would rather see...
> checking if g++ supports C++0x features with -std=c++0x... [COLOR="SeaGreen"]yes[/COLOR]

Any advice please?

---

### Post by Simon17 on 2010-03-01
Get a newer version of GCC?

---

### Post by ssam on 2010-03-01
[http://packages.ubuntu.com/search?keywords=gcc](http://packages.ubuntu.com/search?keywords=gcc) shows the GCC/G++ versions in ubuntu releases.

[http://gcc.gnu.org/projects/cxx0x.html](http://gcc.gnu.org/projects/cxx0x.html) shows that GCC 4.3 has only basic c++0x support, there is more in 4.4, and will be more still in 4.5. so you should probably upgrade to karmic which has 4.4.

---

### Post by fade2gray on 2010-03-02
Thanks for your replies.

I have been considering upgrading to Karmic since it's first release but have avoided doing so for fear of messing up my mail server, it took so long to get right first time round.

---

### Post by ssam on 2010-03-02
an alternative would be to build GCC 4.4 from source. but this can be quite a task.

or you could try installing karmic in a virtual machine.

---

### Post by fade2gray on 2010-03-02
> **ssam said:**
> or you could try installing karmic in a virtual machine.
Bingo :KS You just kicked me out of my senile stupor.
See - I knew fade2gray would be an apt nick. ;)

---

