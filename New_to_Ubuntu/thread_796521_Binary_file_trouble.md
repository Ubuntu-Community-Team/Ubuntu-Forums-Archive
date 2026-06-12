---
title: "Binary file trouble"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Sheneron on 2008-05-16
I am having trouble installing a binary file.  I am new to Ubuntu so I do not know much; however, I have learned how to install the file and it doesn't work.  So far I have done two ways:

I edited the permissions so it will open as executable.  But when I open it an error pops up that says...  Couldn't open there is no application installed for this file type.

I tried to install using the terminal, but this error came up...  Cannot execute binary file type.

Any ideas?  Thanks.

---

### Post by Sheneron on 2008-05-16
Oh one other thing, there is a .cue file as well, so I don't know if I need to do anything with that or what.

---

### Post by Cypher on 2008-05-16
Please tell us what the file is and maybe we can help. Also do
```

file <file>

```
in the directory where the file is and tell us what it says..

---

### Post by H.Callahan on 2008-05-16
It sounds like a CD or DVD image file that needs to be burned to the appropriate medium.  Could you give us a little more detail?  Where did you get the file?  What is it supposed to do?  etc.

---

### Post by robalcorn on 2008-05-16
> **Sheneron said:**
> Oh one other thing, there is a .cue file as well, so I don't know if I need to do anything with that or what.

Sounds like you need to burn a cd image with the .cue

oh H.Callahan got it.

---

### Post by Sheneron on 2008-05-16
Is there anyway to do it without burning to a cd?  I know in windows I had poweriso, and I could have a virtual drive so I didn't have to burn everything to a cd.

---

### Post by robalcorn on 2008-05-16
I found this old thread that might help

[http://ubuntuforums.org/showthread.php?t=230412](http://ubuntuforums.org/showthread.php?t=230412)

---

### Post by Sheneron on 2008-05-16
Thanks everyone I have got it to work.  However, I now have a new problem entirely.  It says I need to be logged in as root while I am installing.  How do I do that, and what is it?

---

### Post by robalcorn on 2008-05-16
> **Sheneron said:**
> Thanks everyone I have got it to work.  However, I now have a new problem entirely.  It says I need to be logged in as root while I am installing.  How do I do that, and what is it?

root is the "superuser" or "administrator go to System/Administration/users and groups. From there select root and create a password.

than when ready to go back to original missions in terminal type su than your newly created password for root than go ahead.

---

### Post by Sheneron on 2008-05-16
Thanks everyone, problem solved.

---

