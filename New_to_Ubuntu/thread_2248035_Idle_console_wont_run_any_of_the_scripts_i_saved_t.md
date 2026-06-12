---
title: "Idle console wont run any of the scripts i saved to the python34 folder"
date: 2014-10-11
forum: New to Ubuntu
---

### Post by spangol on 2014-10-11
i named the file hello.py and its not hello.py.py i made sure of that then ill do idle.py hello.py and it wont run the script then i try $ hello.py doesnt work then i tryied python3 hello.py still doesnt work then i tried $ python3 hello.py doesnt work i made a path in the enviornment variables which is C:\Python34 and im not sure whats going on can some one explain please ? im brand new to python was just learning java and decided this is better for me as a first language so im clueless the code i was saving is this 

print ('hello world')

---

### Post by TheFu on 2014-10-12
Extensions do NOT matter in Linux at all.

There are 2 things necessary to make any script executable ...  

1) make the file permissions executable for the userid or group or everyone as desired. Learn about Linux file permissions for that. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
2) the first line of the script must contain a comment with a special format telling the shell which script language to be used.  This is normally something like:
```
#!/usr/bin/env python
``` on the first line, alone.

Without BOTH of those things ... a script won't run.

The name has NOTHING AT ALL to do with it.


Oh ... and be certain that MS-DOS CRLF are not used.  Just LF is needed for the script file for most scripting languages.

---

