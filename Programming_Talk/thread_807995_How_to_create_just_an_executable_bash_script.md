---
title: "How to create just an executable bash script"
date: 2008-05-26
forum: Programming Talk
---

### Post by GoCool on 2008-05-26
I am a newbie in scripting. I have this silly doubt.
Do I need to give both read and execute permissions for a script to make it executable. Can't I just give execute permissions to it (without read and write)?

Then how to make a script so that except for the admin no other user can see the script or modify the script but can only excecute it.

Any inputs on this would be highly appreciated.

---

### Post by sisco311 on 2008-05-26
Read this about permissions:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by GoCool on 2008-05-26
> **sisco311 said:**
> Read this about permissions:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Thank you sisco311. Yes I know about changing permissions.  But I cant make them execute the bash script, even after giving the execute permission. That is my issue. I even have to give the read permission too. That beats me.

---

### Post by dtmilano on 2008-05-26
bash (or any other interpreter) needs to read the script to execute it.

---

### Post by Tuna-Fish on 2008-05-26
When you make a bash script, and make it executable, you are not really executing it, you are invoking bash, and feeding the script to it in stdin.
The logic looks kinda like this:
# ./script.sh
if x bit set && first chars of file "#!" then run the command on first line <the script.

to make an executable that cannot be read, you need to make a real executable.

---

### Post by GoCool on 2008-05-27
> **Tuna-Fish said:**
> When you make a bash script, and make it executable, you are not really executing it, you are invoking bash, and feeding the script to it in stdin.
The logic looks kinda like this:
# ./script.sh
if x bit set && first chars of file "#!" then run the command on first line <the script.

to make an executable that cannot be read, you need to make a real executable.

Thank you that makes sense.

---

### Post by erjoalgo on 2010-08-30
the question was never answered. how to create a real executable from a bash script?

---

### Post by soltanis on 2010-08-30
You misunderstand the question. To create an executable bash script, you simply put the following line as the first line (indicates the appropriate interpreter) and set the permissions to read-execute.

```

#!/bin/bash

```

---

### Post by Bachstelze on 2010-08-30
> **Tuna-Fish said:**
> When you make a bash script, and make it executable, you are not really executing it, you are invoking bash, and feeding the script to it in stdin.


Wrong. You are passing the name of the file as an argument, not passing its contents on stdin.

*EDIT:* Meh, necromancy...

> **erjoalgo said:**
> the question was never answered. how to create a real executable from a bash script?

Define "real executable"?

---

### Post by erjoalgo on 2011-05-30
compiled machine binary code

---

