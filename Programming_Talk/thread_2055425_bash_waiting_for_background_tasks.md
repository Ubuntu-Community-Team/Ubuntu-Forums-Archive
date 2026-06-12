---
title: "bash waiting for background tasks"
date: 2012-09-09
forum: Programming Talk
---

### Post by frankdn on 2012-09-09
It's been a while (years!) since I did any shell programming... which makes me a novice again.

I run a startup script at login.  I've recently added a 'find' command:

   #!/bin/bash

   ...blah

   nohup find $HOME -iname wifiadapt -delete &

The command works but despite backgrounding the nohup, bash waits for 'find' to exit... which I don't want.  What have I forgotten?

---

### Post by iponeverything on 2012-09-09
> **frankdn said:**
> It's been a while (years!) since I did any shell programming... which makes me a novice again.

I run a startup script at login.  I've recently added a 'find' command:

   #!/bin/bash

   ...blah

   nohup find $HOME -iname wifiadapt -delete &

The command works but despite backgrounding the nohup, bash waits for 'find' to exit... which I don't want.  What have I forgotten?

perhaps add a "disown %1" after backgrounding.

---

### Post by frankdn on 2012-09-11
Thanks, but that didn't help.

---

### Post by ofnuts on 2012-09-12
> **frankdn said:**
> It's been a while (years!) since I did any shell programming... which makes me a novice again.

I run a startup script at login.  I've recently added a 'find' command:

   #!/bin/bash

   ...blah

   nohup find $HOME -iname wifiadapt -delete &

The command works but despite backgrounding the nohup, bash waits for 'find' to exit... which I don't want.  What have I forgotten?
Hmmm. Waiting for "find" or for "nohup"? How can bash tell that "find" is an executable?

---

