---
title: "[SOLVED] shutdown script"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by NaF on 2008-05-26
Hello.
I would like my pc to shutdown after 120minutes - I wont really be touching a mouse or keyboard in this timeframe - So I wrote a little bashscript ```
 sudo shutdown -h 120 
``` Did the whole ```
 chmod u+x 
``` and loaded the script into the session-thiny of Ubuntu. Of course it does not work, because the shutdown command requires sudo and I don't enter a password. Hm, how do I go around this?

---

### Post by sam_delta on 2008-05-26
i believe that you have to call the whole script as sudo, and remove any sudo from the inside of the script
example, your script should look like

"shutdown -h 120"

and you should call it as "sudo script"

remember that you have to add a bash header to the script so it would look like this
> #!/bin/bash

shutdown -h 120

sam

---

### Post by kerry_s on 2008-05-26
disregard not fully awake yet. :)

---

### Post by NaF on 2008-05-26
> **sam_delta said:**
> i believe that you have to call the whole script as sudo, and remove any sudo from the inside of the script
example, your script should look like

"shutdown -h 120"

and you should call it as "sudo script"

remember that you have to add a bash header to the script so it would look like this


sam

But how do I call it as sudo on startup :)?

---

### Post by sam_delta on 2008-05-26
another solution which is much simplier and you dont even have to manually run the script is to direclty Put the command (without sudo) in /etc/rc.local above the exit 0
it will execute the command you typed at boot time and it will not need sudo since its still at boot time

you would add the line "shutdown -h 120" before the "exit 0" line in /etc/rc.local
sam

---

### Post by NaF on 2008-05-26
> **sam_delta said:**
> another solution which is much simplier and you dont even have to manually run the script is to direclty Put the command (without sudo) in /etc/rc.local above the exit 0
it will execute the command you typed at boot time and it will not need sudo since its still at boot time

you would add the line "shutdown -h 120" before the "exit 0" line in /etc/rc.local
sam

ahh that's pretty fancy, thanks a lot :)

---

### Post by starcannon on 2008-05-26
In a terminal type 
```

username@ubuntu:~$ sudo sh ./yourScript.sh

```

The script will now run.

I think if you want this script to run without super user required you might could:
```

username@ubuntu:~$ sudo chmod 777 ./yourScript.sh

```

GL

---

### Post by sam_delta on 2008-05-26
no problem, enjoy ubuntu

sam

---

