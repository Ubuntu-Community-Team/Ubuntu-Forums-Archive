---
title: "Scripts ???"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by lucky.developer on 2008-05-01
I have been hearing this word "script" in ubnutu websites/forums. What does this mean... is it a shell script???:confused:  what language is it written...??:(:(

what is advantage of using scripts?:confused:

I have written this code thing that start with "ch" in the terminal for installing some fonts.... what does this "ch"has got to do with scripts.please explain

---

### Post by blithen on 2008-05-01
Scripts are bash scripts. They can do tedious tasks such as copying and changing the tags of an MP3 quickly while you sit back and watch them work.
Or they can be extremly simple such as
```
#!/bin/bash
cd /usr/local/games/etqw/
./etqw.x86
```
And that's it! It just makes commands that can take awhile easier.
But when you save the file make sure it's like  etwe.sh <<<it has to have the .sh at the end. And to make it executable you have to do the ol' chmod +x <file here>

---

### Post by mali2297 on 2008-05-01
See here:
[http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)

---

