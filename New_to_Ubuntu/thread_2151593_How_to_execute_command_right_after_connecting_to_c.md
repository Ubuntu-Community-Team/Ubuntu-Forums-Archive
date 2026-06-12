---
title: "How to execute command right after connecting to comp via ssh?"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by LinuxUser666 on 2013-06-05
Hello fellow Linux users, I am running on Ubuntu 12.04 LTS and have a problem.
How to write a syntax in terminal that will execute the command right after I connect to targeted computer via ssh.
I tried it like this, this is just an example:
```
ssh user@#.#.#.# && killall process
```
But it did not kill the targeted process when it connected.
Question. What command to type in to do killall command right after me logging onto computer via ssh?

Thank you.

---

### Post by papibe on 2013-06-05
Hi LinuxUser666.

You can add a command at the end of your typical ssh command so that can be executed on the remote host.

The syntax would be like:
```
ssh user@remotehost command
```
For example, this would list the remote home directory:
```
ssh user@remotehost ls -CF
```
This would check if transmission is running on the remote server:
```
ssh user@remotehost 'ps aux | grep transmission'
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by LinuxUser666 on 2013-06-05
I tried this method of yours. I did ```
ssh user@host kilall watch
``` and what it did is ask the password to host, I entered it and it did ```
killall watch
``` and automatically logged me off from the host.
Any ideas/suggestions?

---

### Post by papibe on 2013-06-05
That is the to expected behavior. Did you check that the process was killed?

Do you need to stay connected?

Regards.

---

### Post by LinuxUser666 on 2013-06-05
Umm yes I am one hundred percent sure process was terminated, I did check.
Yes I do need to stay connected after executing the command.
Do you maybe have a solution for that? I would be at most grateful.

---

### Post by LinuxUser666 on 2013-06-05
I partially figured out what to do: 
```
ssh user@host command && ssh user@host
```

Logically it asked me password twice since I logged 1st time to execute the command and 2nd time to log to host.
Do you maybe know how to do it quicker to avoid double logging?

---

### Post by papibe on 2013-06-05
That would be a simple solution. If you create ssh paswordless keys, you may run that with no password interactions.

An alternative would be to use screen on the remote machine. To install it:
```
sudo apt-get install screen
```
Then in your local machine you would do something like:
```
ssh -t user@host  'killall watch; screen -S rsession'
```
A little tricky but it works.

Try it out, and let us know if it helps.
Regards.

---

### Post by LinuxUser666 on 2013-06-05
This last solution worked perfectly...it executed the command and it kept me logged on my remote host computer.
Must say it a complete success. 
My regards to you papibe for your assistance, you helped me a lot.

---

### Post by papibe on 2013-06-05
:D Glad I could help.

Please mark the thread as solved, when you have the chance ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).

Regards.

---

### Post by LinuxUser666 on 2013-06-05
Oh don't worry, I will mark it solved, and double don't worry, I know how. 
:D

---

