---
title: "Using cd \ properly"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by prj44 on 2014-06-15
I am having the most difficult time with the most banal of commands.  I am trying to install a package, which runs with an '.sh' file.  The files  have been downloaded to my 'downloads' folder and unzipped.  I open a terminal and enter cd /home/downloads.  The T responds 'no such directory.'  Well, there is ...

Sorry to raise such a fundamentally simple issue, but this has me wanting to throw things in frustration.  So:
- how do I get to the appropriate directory?

Thanks in advance.

---

### Post by deadflowr on 2014-06-15
I usually use ls to see the contents of a directory, usually to see how those contents are spelled.
I also use tab completion(start the beginning of the word and then hit the tab key and it will autofill the rest.

But for the record, downloads directory in Ubuntu is Downloads, not downloads
If you are in your home folder, which is the normal starting point, then simply run 
```
cd Downloads
```

---

### Post by DuckHook on 2014-06-15
> **deadflowr said:**
> ...downloads directory in Ubuntu is Downloads, not downloads...+1

Case is critical in Linux (unlike Windows). This is also a frequent item that trips up users with passwords, as they forget that a certain letter was capitalized when set up.

---

### Post by prj44 on 2014-06-16
Thank you.

(How painfully simple ... )

---

### Post by Impavidus on 2014-06-16
In addition, /home/ is not your home directory. Your home directory is /home/yourusername/ or ~/ for short, and you should be there by default when opening a terminal so you can skip that part.

---

