---
title: "No cd in shell script"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Bill magee on 2008-05-06
I am running Hardy on an Acer laptop.

Wrote a small shell script to change to my LaTex director, but the thing won't work. Permission are set. I get the echo, but no directory change. Can anyone suggest why?

#!/bin/bash
cd /home/bill/Desktop/MakeBook
echo "MakeBook Directory"

I also tried #!/bin/sh

Cheers,
Bill

---

### Post by AusIV4 on 2008-05-06
CD is a shell command, not a program. When you write a script, you create a new shell, and all shell commands only exist for that shell. Once the script terminates, the changes are gone.

At one time I knew how to change directories through a script. I don't have time to find it right now, but if this hasn't been answered in a few hours I'll try and find it.

---

### Post by Bill magee on 2008-05-06
Thanks AusIV4. I see now. I can look it up now that I know the reason.

---

### Post by Bill magee on 2008-05-06
Found the answer on the unix forums, thnx Laxmi:

```
. ./myscript.sh
```

When you run the script in this manner, all the changes you make to env variables will remain after you exit the script.

---

### Post by TrenTech on 2009-02-13
This helps but I have a small issue. I open the current shell using . ./filename but within this script it opens another scipted using the bash command. . ./filename2 will not execute therefore I can't use the cd command in the second file. help me out

---

### Post by geirha on 2009-02-13
> **TrenTech said:**
> This helps but I have a small issue. I open the current shell using . ./filename but within this script it opens another scipted using the bash command. . ./filename2 will not execute therefore I can't use the cd command in the second file. help me out

Should be possible to do that, so what error message does it give you?

---

### Post by niteshifter on 2009-02-13
Hi,

Maybe this will clear things up:

firstscript.sh
```
#! /bin/bash
echo "the current directory is:"
pwd
cd ~/test
echo "after a cd the current directory is:"
pwd
echo "now sourcing secondscript.sh"
. ~/secondscript.sh
echo "now we exit from the first"

```

secondscript.sh
```
#! /bin/bash
echo "second script running, in directory"
pwd
cd test2
echo "now the current working directory is:"
pwd
echo "leaving second script"

```

Output from running firstscript, folders ~/test and ~/test/test2 exist:
> foo@bar:~$ ./firstscript.sh
the current directory is:
/home/dlk
after a cd the current directory is:
/home/dlk/test
now sourcing secondscript.sh
second script running, in directory
/home/dlk/test
now the current working directory is:
/home/dlk/test/test2
leaving second script
now we exit from the first
foo@bar:~$ 


In firstscript.sh note how secondscript.sh is sourced:
```
. [COLOR="Red"]~[/COLOR]/secondscript.sh
```
These two character have differenct meaning to a shell:
. = the current directory
~ = the path to the user's home folder

I've got a feeling that one of the next questions is "how can a I cd to a directory in a script and leave it there?"
Answer: You cannot.

---

### Post by geirha on 2009-02-13
> **niteshifter said:**
> 
I've got a feeling that one of the next questions is "how can a I cd to a directory in a script and leave it there?"
Answer: You cannot.

Sure you can.

/tmp/script1:
```

cd /usr/
. /tmp/script2

```

/tmp/script2:
```

cd /etc/

```

```

/tmp$ . script1
/etc$ 

```

---

### Post by niteshifter on 2009-02-14
Hi,

> Sure you can.

/tmp/script1:
Code:

cd /usr/
. /tmp/script2

/tmp/script2:
Code:

cd /etc/

Code:

/tmp$ . script1
/etc$



You are quite correct ... and I was hoping somebody would make the call on it.

Now let's go one more step after performing your steps: open another terminal ... and where are we? At /home/user_name, not /etc.

Different ways of interpreting the question, I took it as cd "the DOS way".

Between the two of us the point is made: the current working directory is specific to a process - not "global".

---

