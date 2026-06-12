---
title: "How to see a list of recent Permissions"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by Wiking on 2011-09-17
Is there anyway to see recent permissions -that require a password- that you have allowed?

Perhaps a log that shows all the permissions that you have granted to programs.

I'm getting paranoid that I might have allowed permission to something malicious.

---

### Post by haqking on 2011-09-17
> **Wiking said:**
> Is there anyway to see recent permissions -that require a password- that you have allowed?

Perhaps a log that shows all the permissions that you have granted to programs.

I'm getting paranoid that I might have allowed permission to something malicious.


any use of sudo or elevated privelege should be in /var/log/auth.log

---

### Post by Wiking on 2011-09-17
Thanks, I looked at the log, but am not sure what I should be looking for.

What is the syntax that describes giving permission with a password?

---

### Post by haqking on 2011-09-17
> **Wiking said:**
> Thanks, I looked at the log, but am not sure what I should be looking for.

What is the syntax that describes giving permission with a password?


im not sure i understand what you mean ?

there should be entries for sudo which is when any sudo related task is carried out, also su tasks which is when root carries out a task, often then passing it onto sudo such as system services and the like, cronjobs etc.

everytime you enter your sudo credentials it should list as sudo in the log.

perhaps i am not understanding you quite though

---

### Post by Wiking on 2011-09-17
No, no you answered my question, it's me who doesn't understand too much...

So for example I'm guessing that this line that is in my log is when sudo or a higher privilege is required??

```
  sudo: Anon4 : TTY=pts/1 ; PWD=/home/Anon4 ; USER=root ; COMMAND=/usr/bin/apt-get install compiz-fusion-plugins-extra  
```

So whenever a password is required I should look for something similar to the line above, yes?

Well the first part, the last bit (COMMAND) I know is specific to whatever it is you're installing.

---

### Post by haqking on 2011-09-17
> **Wiking said:**
> No, no you answered my question, it's me who doesn't understand too much...

So for example I'm guessing that this line that is in my log is when sudo or a higher privilege is required??

```
  sudo: Anon4 : TTY=pts/1 ; PWD=/home/Anon4 ; USER=root ; COMMAND=/usr/bin/apt-get install compiz-fusion-plugins-extra  
```So whenever a password is required I should look for something similar to the line above, yes?

Well the first part, the last bit I know is specific to whatever it is you're installing.


yep it means you probably installed compiz and when you did you had to use the sudo command to do so ?

---

### Post by Wiking on 2011-09-17
Okay thanks. Just for an example could you perhaps give show me what something malicious would look like?

---

### Post by haqking on 2011-09-17
> **Wiking said:**
> Okay thanks.


no worries, dont get overly paranoid with the log though, there will be alot of stuff you probably wont recognise and panic about ;-)

peace

---

