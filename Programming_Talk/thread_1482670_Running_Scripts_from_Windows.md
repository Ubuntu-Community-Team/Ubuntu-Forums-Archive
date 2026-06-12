---
title: "Running Scripts from Windows"
date: 2010-05-13
forum: Programming Talk
---

### Post by carlo_navarro on 2010-05-13
Hi.

I am trying to start writing simple shell scripts (#/bin/bash files) in ubuntu. It seems to be working fine when I call it out from a terminal.

Problem is, I want the trigger of the script to come from a batch file from a windows terminal (through a network). I've tried accessing the linux box from the windows terminal and running the script. But since the system files are in the linux box, then Windows does not know how to interpret the commands.

Could anyone give a heads up on what subjects I should be reading on?

Thanks,
Carlo

---

### Post by Bachstelze on 2010-05-13
If you want to add networking capabilities to your script, you're probably better off using a more advanced language like Python instead of shell scripts.

---

### Post by carlo_navarro on 2010-05-13
Thanks.

Will have to read up and convert what I have.

Though is there a way for the windows machine just to trigger execution of the script on the linux box. The linux box already has all the parameters / files for it needs for it to run. 

Regards,
Carlo

---

### Post by soltanis on 2010-05-14
You could run an HTTP server on the Linux box with a CGI script set to trigger the linux script. Or if you want to go simpler, you could set the script to run when a netcat instance exited:

```

nc -l 9999 && ./myscript

```

Then all you need to do is connect/disconnect from port 9999 on the linux box to run the script (obviously you need to unfirewall the port).

---

### Post by hannaman on 2010-05-14
If you have ssh on both the Windows and Ubuntu machines, you could use ssh to execute the script.
```
ssh user@hostname "script_name"
```

---

### Post by carlo_navarro on 2010-05-14
These seem a bit alien to be, but at least its a start.

Thanks for the inputs.

---

