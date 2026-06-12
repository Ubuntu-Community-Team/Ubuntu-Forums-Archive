---
title: "PID File"
date: 2009-12-06
forum: Programming Talk
---

### Post by Chamillionaire2 on 2009-12-06
What's Up?

OK, So I've been trying to start some commands upon start up, I heard it's possible to use a PID file in the /var/run/ folder, But i cant find any advice on the net, I dont suppose you just put in bash code into the .pid file and plonk it in the run folder do ya?

Thanks Bye.

---

### Post by The Cog on 2009-12-06
With bash, the process id of the last launched subprocess is available as $! so you can launch something and then write its pid file like this:
> myprog &
echo $! > /var/run/myprog.pid

---

### Post by Chamillionaire2 on 2009-12-06
> **The Cog said:**
> With bash, the process id of the last launched subprocess is available as $! so you can launch something and then write its pid file like this:

Ah Ok, Does it matter if I try and use a script rather then some sort of program?

---

### Post by The Cog on 2009-12-06
I don't think so except that if script A launches script B, then script A can only record B's PID. If script B launches program C, script A cannot know that and can't report C's PID.

---

### Post by Chamillionaire2 on 2009-12-06
> **The Cog said:**
> I don't think so except that if script A launches script B, then script A can only record B's PID. If script B launches program C, script A cannot know that and can't report C's PID.

Ah ok thanks, I recorded the PID but it seems it gets executed as root.

---

### Post by Barriehie on 2009-12-08
I've got a boot daemon and I record it's pid like this, from within the script that I want the pid of:
```

#!/bin/bash

if [ -e /var/run/picsdaemond.pid ]
  then
    rm /var/run/picsdaemond.pid
  else
    touch /var/run/picsdaemond.pid
    echo $$ >> /var/run/picsdaemond.pid
fi

...
do whatever
...

```
Barrie

Edit: In retrospect the touch is superfluous.

---

### Post by Barriehie on 2009-12-08
> **Chamillionaire2 said:**
> Ah ok thanks, I recorded the PID but it seems it gets executed as root.

It has to be root to write to /var/run.

Barrie

---

