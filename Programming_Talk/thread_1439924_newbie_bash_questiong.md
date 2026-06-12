---
title: "newbie bash questiong"
date: 2010-03-26
forum: Programming Talk
---

### Post by MacHaddock on 2010-03-26
I'm trying to maka a script that launches firefox and then evolution

so far I've got 

```
#!/bin/bash

firefox

evolution
```But that doesn't work. It just starts firefox and then evolution as I close firefox.

I know that typing firefox -t in a terminal opens it as a seperate thread or whatever but I can't get that to work in the script.

How would you do it?

---

### Post by dwarfolo on 2010-03-26
Try adding an "&" at the end of each line
```
#!/bin/bash

firefox &

evolution &
```

---

### Post by snova on 2010-03-26
> **MacHaddock said:**
> I'm trying to maka a script that launches firefox and then evolution

so far I've got 

```
#!/bin/bash

firefox

evolution
```But that doesn't work. It just starts firefox and then evolution as I close firefox.

I know that typing firefox -t in a terminal opens it as a seperate thread or whatever but I can't get that to work in the script.

How would you do it?

Run firefox in the background:

```
firefox **&**
```

I am not certain what would happen if you ran both processes in the background though.

---

### Post by dwarfolo on 2010-03-26
Well, sending both the commands in background let you close the terminal without waiting for them to return. You can send several command in the background at a time, but obviously if you close the starting shell you loose the option to use bg, fg and ctrl+z to control the jobs.

---

### Post by MacHaddock on 2010-03-27
Well I don't know what those do anyway :D

The & was what I was looking for. Thanks a lot

now maybe there is a way to close the terminal as well with a command. I'm making a panel launcher that launches two programs by the way.

---

### Post by Barriehie on 2010-03-28
$$ is the PID of the running process so to kill your launching terminal we use kill and send the process a signal 9, which can't be blocked.  See the manpage of kill and it will tell you about the diff. signals.  Also can't kill it without detaching the programs you're spawning and still have them run so we use the terminal to launch an instance of bash and give it a command with the -c 'string' and run in the background.

```

#!/bin/bash
bash -c 'firefox &'
bash -c 'thunderbird &'
kill -s 9 $$

```

---

### Post by MacHaddock on 2010-03-28
That worked if I run it from the panel launcher which is what I want. Thanks!

can't say I understand why it doesn't work if i run it from a terminal though. but what the hey.

---

### Post by Barriehie on 2010-03-28
> **MacHaddock said:**
> That worked if I run it from the panel launcher which is what I want. Thanks!

can't say I understand why it doesn't work if i run it from a terminal though. but what the hey.

From an already open term:
```

bash -c *name_of_script* &
```

---

