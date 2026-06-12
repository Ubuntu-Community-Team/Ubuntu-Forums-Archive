---
title: "python3 script : &quot;no such file or directory&quot;"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by vmsda on 2013-05-16
1. I am trying to execute a python3 script which I have chmod'ed accordingly, but get the dreaded ": No such file or directory" console message. As with all other scripts, this one begins with the proverbial "#!/usr/bin/env python3" as the first line, and I submit "./myscript.py" from the terminal window. However, when I prefix the script name with "python3", everything runs smoothly. So the file is in fact there, only the shell refuses to "see" it.

2. Stranger still, if I change to another subdirectory, where I also have other python3 executable scripts, they all run ok even with or without prefixing them with "python3". So I moved my problem script to that other subdirectory, in order to better compare the "ls -l" outputs, and everything looks ok, so I do not seem to have done anything wrong with my chmod.

Anyone for that obvious hint? Thank you in advance.

---

### Post by spjackson on 2013-05-16
The symptoms you describe can arise if your script has DOS (/Windows) line-endings rather than Linux line endings. Python does not care about this, so it works when you explicitly put python3 in front of your command. However, it does matter for the #! syntax to find the right interpreter. If the file has DOS line endings, it will be looking for the program python3^M which is not found.

---

### Post by vmsda on 2013-05-16
Thanks. So, what chars should I be looking for, Carriage Returns? If I get rid of them, I should be in business ...

---

### Post by spjackson on 2013-05-17
Probably, yes. Any other character could mess it up, but the common case would be carriage returns. Also, many text editors have the option to read a Windows text file and save it with Linux line endings.

---

