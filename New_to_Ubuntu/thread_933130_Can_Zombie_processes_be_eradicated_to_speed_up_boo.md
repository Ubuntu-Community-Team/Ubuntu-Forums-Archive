---
title: "Can Zombie processes be eradicated to speed up boot time?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by the8thstar on 2008-09-29
Hello,

I'm looking for a way to get rid of zombie processes that appear in bootchart when I turn on my computer. How can I do that?

Aside from that, I was wondering if removing these could speed up the boot time, or if this is a completely unrelated issue. Any ideas?

---

### Post by uberdonkey5 on 2008-09-29
not sure if I can help, but how come you get zombie processes when you boot up??? What processes have been started then terminated whilst booting?

so, you type 'top' and can see zombies? (or 'ps -aux' ps stands for process status)

find the PID number and type e.g. 'kill 3421'
alternatively if you know the process name due to past experience you can use 'killall process-name' (inserting the real process name)
Also, you could put this into a script if you wanted it to happen at start up.

zombies don't do anything anyway, so no worries

---

### Post by uberdonkey5 on 2008-09-29
PS as far as I am aware, eradicating zombie processes will not affect boot up time cos the processes don't use system resources - they are not running

---

