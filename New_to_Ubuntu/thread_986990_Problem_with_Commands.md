---
title: "Problem with Commands"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Oliver.BS on 2008-11-19
Hey every one, I have a problem every time I try to type in a command I get "command not found" So if I typed in Sudo MV lines~/Desktop I get Command not Found 

Can any one help me out with this ? 

This is the same with all command by the way

---

### Post by hermes0710 on 2008-11-19
> **Oliver.BS said:**
> Hey every one, I have a problem every time I try to type in a command I get "command not found" So if I typed in Sudo MV lines~/Desktop I get Command not Found 

Can any one help me out with this ? 

This is the same with all command by the way

It is "sudo" not "Sudo" and "mv" not "MV" (commands in linux are case sensitive). If what you want to move is a file named "lines" then you should enter space between the file and the destination folder:
```
sudo mv lines ~/Desktop
```

Regards

---

### Post by Oliver.BS on 2008-11-19
Oh I see thank you very much

---

### Post by hermes0710 on 2008-11-19
> **Oliver.BS said:**
> Oh I see thank you very much

Welcome

---

