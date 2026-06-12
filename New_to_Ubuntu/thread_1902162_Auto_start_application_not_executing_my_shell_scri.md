---
title: "Auto start application not executing my shell script"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by audeshmukh on 2011-12-30
Hi,

I have created a shell script and changed the attributes to executable by giving 'chmod 755' to it.

Now, I can manually execute from terminal window and it works perfectly fine. 

When I add an entry for this script to the auto-start application, it does not start at the time of login. To confirm the auto-start thing works, I made an entry for 'XTERM' and as soon as I login, it opens the terminal window.

Why is my script not running on start-up then? Am I missing anything here?

Please advise. I am new to shell scripts and *nix environments.

Thanks,
-Abhijit

---

### Post by perperNorbi on 2011-12-30
Could you please show us the content of the file you are trying to execute? We also have to exclude permission problems, so please run
```
$ ls -l my_script_file
$ cat my_script_file
```in a terminal.

---

### Post by NilPointer on 2011-12-30
You need to use -e argument. That worked for me:

xterm -e sh "/home/nilptr/test.sh"

Using only xterm "/path/to/script.sh" won't work (it seems to think it's path to tty).

---

### Post by audeshmukh on 2011-12-30
> **NilPointer said:**
> You need to use -e argument. That worked for me:

xterm -e sh "/home/nilptr/test.sh"

Using only xterm "/path/to/script.sh" won't work (it seems to think it's path to tty).

Yes, this worked for me. :) Thanks a lot !!

---

