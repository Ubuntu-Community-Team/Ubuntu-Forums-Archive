---
title: "ctrl c does not kill shell script"
date: 2010-08-14
forum: Programming Talk
---

### Post by Mr_G on 2010-08-14
Hey,

I am using a  shell script as follows


ssh -v user@server less -F /var/log/maillog |grep domain 

to chech mail logs for a domain.

The script runs and displays the content but when I do a ctrl c to kill the script is still displays the content and does not exit.

Also any1 know of a good script to check mail logs as they are appended via ssh?

Thanks in advance
Mr G
amateurhosting.wordpress.com

---

### Post by Bachstelze on 2010-08-14
You don't want to do less | grep. Do

```
ssh -v user@server grep domain /var/log/maillog
```

---

### Post by Mr_G on 2010-08-14
Thank you ken.

The maillog file is gets appended with logs every minute hence I was using less with -F flag.

Any reason the script was not being killed?

---

### Post by Bachstelze on 2010-08-14
> **Mr_G said:**
> 
The maillog file is gets appended with logs every minute hence I was using less with -F flag.

Don't you mean tail?

---

### Post by soltanis on 2010-08-14
According to my manpage, the -F flag to **less** means "quit **less** if the result is less than one page". If you are trying to watch a log that is being appended by the minute, then this is probably not the command you want. Instead, I suggest you use **tail** and **watch** together, which will periodically print the last few lines out of the log file so you can see as it updates. On the server, create an executable script like this:

```

#!/bin/sh
grep domain /var/log/maillog | tail

```

Then do

```

ssh -v user@server 'watch -n 60 ~/script'

```

This will continually print out the last 10 lines from the file that match the grep pattern every 60 seconds.

---

### Post by Mr_G on 2010-08-14
Thanks for your reply guys, this is helping me a lot

The reason I used less with  the -F flag because as per the man page for less


F      Scroll forward, and keep trying to read when the end of file is reached.  Normally this command would be used when already at  the  end  of
              the  file.  It is a way to monitor the tail of a file which is growing while it is being viewed.  (The behavior is similar to the "tail -f"
              command.)

Its similar to tail -f and it searches the entire log file instead of searching for the last 10 lines

The only thing I could not understand is while using less in my script, the logs display took a very long time and hence I killed the script with crtl c and it seemed to be killed as it displayed my userprompt but as soon as I went to type something it continued to display the logs thus the script did not terminate, even after multiple crtl c's, at the end I had to kill ssh to terminate it.

hence I wanted to know y did the script not terminate.

Anyways thankx for all ur suggestions my issue is now resolved, just one more thing is it possible to mail the logs after the grep query via ssh, if yes then I would appreciate if you guys could post the code.

Thank you again

---

### Post by Bachstelze on 2010-08-15
> **Mr_G said:**
> 
The reason I used less with  the -F flag because as per the man page for less


F      Scroll forward, and keep trying to read when the end of file is reached.  Normally this command would be used when already at  the  end  of
              the  file.  It is a way to monitor the tail of a file which is growing while it is being viewed.  (The behavior is similar to the "tail -f"
              command.)

This is in the "commands" section of the man page, not in the "options" section. It's not a flag you pass on the command line, but a command you type while less is running.

> Anyways thankx for all ur suggestions my issue is now resolved, just one more thing is it possible to mail the logs after the grep query via ssh, if yes then I would appreciate if you guys could post the code.

To send the output of a command via email:

```
command | mail -s Subject foo@bar.org
```

---

