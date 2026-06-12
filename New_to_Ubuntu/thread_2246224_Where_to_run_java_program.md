---
title: "Where to run java program?"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by Helveticus on 2014-09-29
Hi

I want to run a Java program with ant on a Ubuntu machine on Amazon EC2.

How can I upload my program via ssh and to which directory should I upload it?

In which directory should I run the program and to which directory should I save the logs from my program (my program automatically creates logs)?

Thank you very much.

---

### Post by mcduck on 2014-09-29
That really depends on the program in question, for example what kind of permissions it needs, do you need to rotate the logs automatically, does all the data fit on your root file system or do you have a separate S3 drive for the data and so on...

(For example I run a Perforce version control server on EC2/Ubuntu, and while it could be ran as any user directly from that user's home, I decided do set it up as a daemon, and used a separate s3 volume mounted at /perforce as it's repository root and set it to keep the log files in /var/log/perforce.)

What comes to moving files over SSH: [https://help.ubuntu.com/community/SSH/TransferFiles]("https://help.ubuntu.com/community/SSH/TransferFiles")

---

### Post by Helveticus on 2014-09-29
What do you mean with rotating the logs? The logs should just be stored in a single rotation and when the program ends I will copy it to my local machine.

The amount of data is less.

The programs are just simple client and server java programs.

In which directory should I run the programs and store the logs or does it no depend?

---

### Post by mcduck on 2014-09-29
rotating logs means that, for example, every day the previous day's log file is renamed, new log file is created, and oldest log file is deleted, for example to make sure you'll always have exactly one week's worth of log files, and that anything older than that is automatically removed (so you have enough logs to troubleshoot possible problems, but at the same time the logs don't end eating too much of your disk space). Common thing to do with any system logs or log files for various running services.

Anyway, since it sounds like you don't have any specific needs for your applications, and you are not planning on running them as constantly running daemons, just place them in your home directory and run from there. (but like i said, it really depends on what the programs are, what kid of permissions they need, and do you want to run them as your own user or something else)

---

