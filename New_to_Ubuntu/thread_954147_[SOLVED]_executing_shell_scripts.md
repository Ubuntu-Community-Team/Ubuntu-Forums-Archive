---
title: "[SOLVED] executing shell scripts"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by mike22 on 2008-10-20
How do you execute shell scripts? Thanks.

---

### Post by kerry_s on 2008-10-20
```
./file.sh
```

---

### Post by scragar on 2008-10-20
open a terminal(applications> accessoris>terminal), find the shell script(drag it into the terminal = easy way), and hit enter. If it complains about not having perms put this infront of it:```
chmod +x 
```so it looks like:```
chmod +x **SCRIPT**
```

and try to run it again(use up and down to scroll through last run commands)

---

### Post by blesbok on 2008-10-21
remember to have #!/bin/bash at the head of your script.

if you plan to execute your script (eg. wizzscrpt) regularly, edit .bashrc in your user home directory (i.e. /home/myname/.bashrc and insert this under #User specific aliases and functions:
alias wizzscrpt='cd /path/to/shellscriptcalledwizzscrpt'

hope this helps  :)

---

### Post by sazan on 2008-10-21
sh <path of file name>  (if current folder use ./<filename>)

---

### Post by hyper_ch on 2008-10-21
#!/bin/bash doesn't ahve to be the first line. If it is then it will use that shell... I think default shell would be dash. So if you don't say to use bin/bash it will use dash instead.

---

### Post by mike22 on 2008-10-21
Thanks for the help!

---

### Post by mike22 on 2008-10-28
I have a similar question in regards to php scripts. How do you run php scripts or how do you run it on the shell?

---

### Post by DGortze380 on 2008-10-28
> **hyper_ch said:**
> #!/bin/bash doesn't ahve to be the first line. If it is then it will use that shell... I think default shell would be dash. So if you don't say to use bin/bash it will use dash instead.

It really is better practice to include your shell at the top of the script. I've seen a number of really flaky errors that result from not specifying a shell.

---

