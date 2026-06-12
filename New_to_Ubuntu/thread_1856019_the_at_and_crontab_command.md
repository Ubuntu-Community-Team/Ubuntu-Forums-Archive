---
title: "the at and crontab command"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by bresis87 on 2011-10-07
Hello.
I am trying to use the "at" and the "crontab" commands to execute a series of commands later. I have read in many posts how to use them but they seem not to work (or maybe is that I don know how to make them work). This is what a write in my shell

 user@laptop: at now + 1min
warning: commands will be executed using /bin/sh
at> echo "hello"
at> <EOT>
job 6 at Fri Oct  7 17:05:00 2011

then, nothing happens. If I type "atq" I see

7    Fri Oct  7 17:05:00 2011 a user

But then, when the clock turns 17:05, there is no output in the shell....

---

### Post by gmargo on 2011-10-07
> **bresis87 said:**
> there is no output in the shell....

Of course not.  Your current "shell" has no association with anything executed by the **cron** daemon.

Output from the **cron** daemon, which includes any non-redirected stdout or stderr, is emailed to you.  If you didn't get the email, it is because either you didn't check or you don't have an **MTA** (Message Transfer Agent aka Mail Server) installed.

Look for clues in the **/var/log/syslog** file.  It will tell you if the **cron** output was discarded.

---

### Post by bresis87 on 2011-10-10
Ok, thank you I solved this problem, I didn't know this commands was sending the output of the commands to my email. Would there be a way to see the output in a shell instead of receiving it in my mail?

---

### Post by Lars Noodén on 2011-10-10
Not to *your* shell but you could redirect output to a file:

echo "hello" > ~/output.txt
echo "world" >> ~/output.txt

---

### Post by gmargo on 2011-10-10
> **bresis87 said:**
> Would there be a way to see the output in a shell instead of receiving it in my mail?
Not output from the cron daemon.

Perhaps **at** is not the right tool for your task.  If you just want to "execute a series of commands later" (as you said in the original post), and have the output in your current shell, then you could background it with a delay.

This puts a subshell in the background, which will delay one hour, then run a script (or any command pipeline):
```

( sleep 3600 ; shell_script_with_commands.sh ) &

```

---

