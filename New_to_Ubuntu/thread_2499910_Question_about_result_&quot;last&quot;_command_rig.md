---
title: "Question about result &quot;last&quot; command right after installation ubuntu"
date: 2024-08-15
forum: New to Ubuntu
---

### Post by bhubunt on 2024-08-15
Hi,
I just reinstalled ubuntu on a laptop of mine. But when I typed in the command last, right after having installed the ubuntu OS, I got the following return:

```
  $ last 
username        :1            :1             Thu Aug 15 05:20 still logged in 
reboot             system boot 5.15.0-67-generi Thu Aug 15 05:20 still  running
reboot             system boot 5.15.0-67-generi Thu Aug 15 05:17 still  running  
```

My question concerns the :1 and :1 after my username, which do not look right to me. In past successful installations it always said :0  and :0 after my user name, not :1.

I tried researching this matter on the forum but could not find an explanation of what the :0 and :1 mean respectively.

Any ideas?

---

### Post by currentshaft on 2024-08-15
What do the commands "w" and "who" return? Is there an external monitor in use?

---

### Post by bhubunt on 2024-09-01
Sorry for the late reply.

 I'm afraid I don't understand your question. What do you mean by 'external monitor'?   

And what does the :1 after my username mean? And what does the regular :0 stand for? 

I'd be grateful for a bit of a lengthy reply.


Thanks

---

### Post by bhubunt on 2024-09-04
Hi,
Perhaps someone else has time to answer my query? Currentshaft removed his reply.

---

### Post by grahammechanical on 2024-09-04
My completely uneducated guess is that :1 = the root user & :0 = a non-root user.

If I understand things correctly the Ubuntu install process is carried out as a root user.

Regards

---

