---
title: "Is there a config file for Suspend?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by RustyTrowel on 2008-05-05
Hey Everyone!

I was wondering if anyone knew whether there was a config file which could be edited to change what was awakened when a computer is brought out of suspend in Hardy Heron?

I have a problem with there being no sound after I suspend my computer for a while.  I posted a thread about this a while back but no real solution was found (although there were some helpful responses  by **hhpeter** and **certux**).

That thread is: 

[http://ubuntuforums.org/showthread.php?t=767772&highlight=suspend+sound]("http://ubuntuforums.org/showthread.php?t=767772&highlight=suspend+sound")

I don't really understand linux, so I'm probably on the wrong track with this idea.     

Any thoughts on how to solve this problem would be great!

---

### Post by mustang on 2008-05-05
> **RustyTrowel said:**
> Hey Everyone!

I was wondering if anyone knew whether there was a config file which could be edited to change what was awakened when a computer is brought out of suspend in Hardy Heron?

I have a problem with there being no sound after I suspend my computer for a while.  I posted a thread about this a while back but no real solution was found (although there were some helpful responses  by **hhpeter** and **certux**).

That thread is: 

[http://ubuntuforums.org/showthread.php?t=767772&highlight=suspend+sound]("http://ubuntuforums.org/showthread.php?t=767772&highlight=suspend+sound")

I don't really understand linux, so I'm probably on the wrong track with this idea.     

Any thoughts on how to solve this problem would be great!

Put what you need to before "done" in /etc/acpi/resume.sh

---

