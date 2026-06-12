---
title: "Dangerous commands"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Pandiani on 2008-11-09
Hello, I have read about executing dangerous commands but I'd like to know more. 
For example if I'm working in some directory I created, say /home.../mydir
and execute this command: rm -rf *, does this means I'll erase everything on my computer, not just all files in my current working directory?
What is the difference between rm -rf / and rm -rf .?
Will second command remove only contents of my working directory?

Thank you very much for your help.

---

### Post by DrDagostino1 on 2008-11-09
rm -rf * will erase all the files in your current directory.
rm -rf /* and rm -rf / will erase everything on your computer.
I'm not sure what rm -rf . will do though.

---

### Post by kernelhaxor on 2008-11-09
> **DrDagostino1 said:**
> 
I'm not sure what rm -rf . will do though.

rm -rf . will erase the current directory and all the files and sub-directories inside the current directory

---

### Post by lukjad on 2008-11-09
I hear the ```
sudo rm -rf /
``` is disabled in Hardy and up. DON'T try it though. I ran this in Feisty for 2 secs and it destroyed my Compy.

---

### Post by jflaker on 2008-11-09
Since some troll had a newbie run a command while "trying to help", I put a warning in my signature..... understand WHAT you are doing and WHY....

You should always investigate any command before you execute it....plenty of resources on the internet.

---

### Post by Matthewthegreat on 2008-11-09
I have been wanting to see what this does first hand. If I run rm -rf / in a virtual machine if will only destroy the guest and not the host, Right?

---

### Post by jpeddicord on 2008-11-09
> **kernelhaxor said:**
> rm -rf . will erase the current directory and all the files and sub-directories inside the current directory

`rm -rf .` will actually fail with:
```
rm: cannot remove directory `.'
```

because that would leave you with a nonexistent working directory. :)

---

### Post by jpeddicord on 2008-11-09
> **Matthewthegreat said:**
> I have been wanting to see what this does first hand. If I run rm -rf / in a virtual machine if will only destroy the guest and not the host, Right?

Correct, providing you do not have anything on a shared resource between the host and guest. Be sure to detach the guest from any network connections before trying it. (I wouldn't recommend trying it at all, really. [Here's a video if you really want to see.]("http://www.youtube.com/watch?v=wWOjmvWPRvQ"))

---

### Post by pirattrev on 2008-11-09
if you are going to erase anything important, i think it'll ask for a password first. Just don't give it unless you're sure.

---

### Post by jpeddicord on 2008-11-09
> **pirattrev said:**
> if you are going to erase anything important, i think it'll ask for a password first. Just don't give it unless you're sure.

Not if you've run a command involving root privileges within the past 15 minutes. `sudo rm` will ask for your password because of the `sudo` bit to elevate privileges. But, it will remember your password for fifteen minutes afterwards, so it might not always ask.

In short, be wary of any commands you type in, folks. :)

---

### Post by Pandiani on 2008-11-10
Thank you guys for your help and explanations.
Since these commands are risky I'll not try to execute them. However, I cannot understand how I can destroy my files and folders that way. I think that most modern operating systems don't allow such easy deletions of system files. 
For example, system win XP can be formated only from bootable CD and appropriate menu. 

Thanks again

---

