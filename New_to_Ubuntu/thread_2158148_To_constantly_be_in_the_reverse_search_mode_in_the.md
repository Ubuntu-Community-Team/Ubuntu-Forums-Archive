---
title: "To constantly be in the reverse search mode in the terminal"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by ArindamSaha1507 on 2013-06-28
I am using the default terminal in ubuntu. I frequently work with the same commands over and over again. I came to know that Ctrl-R start the reverse search mode. Can I somehow always be in the Ctrl-R mode (So that it sort of auto-completes my commands always)?

Thanks in advance for the help...

---

### Post by dino99 on 2013-06-28
up & down arrows also select the latest commands

---

### Post by Kujua on 2013-06-28
If what you want is to avoid repetition, then why not write a simple shell script?

---

### Post by ArindamSaha1507 on 2013-06-28
Thanks!

---

### Post by stinkeye on 2013-06-28
Running these 2 commands will bind pageup to history-search-backward and pagedown to history-search-forward...
```
echo "\"\e[5~\": history-search-backward" >> ~/.inputrc
echo "\"\e[6~\": history-search-forward" >> ~/.inputrc
```
Type the first part of a command then use pageup and pagedown to cycle 
through previous commands.

---

### Post by ArindamSaha1507 on 2013-06-28
Thanks a lot! Exactly what I wanted.

Could you please tell how does it work?

---

### Post by stinkeye on 2013-06-28
> **ArindamSaha1507 said:**
> Thanks a lot! Exactly what I wanted.

Could you please tell how does it work?
[https://wiki.ubuntu.com/Spec/EnhancedBash](https://wiki.ubuntu.com/Spec/EnhancedBash)

---

### Post by ArindamSaha1507 on 2013-06-28
Thanks!

---

