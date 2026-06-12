---
title: "My almost first script. What's wrong?"
date: 2009-03-16
forum: Programming Talk
---

### Post by muxecoid on 2009-03-16
```
#!/bin/bash

cd $HOME
cd Desktop

for (( i = 1; i >= 3; i++ ))
do

cp 'job.temp' "job_$i.qsub"


echo "./foo $i 5. 0. 133" > "job_$i.qsub"


done
```

Expected behaviour: 3 files that contain job.temp with an extra string at the end.
Observed: No new files. No error message. Absolutely nothing.
Question: What's wrong and what is the good way to do it?

---

### Post by sisco311 on 2009-03-16
```
#!/bin/bash

cd $HOME
cd Desktop

for (( i = 1; **i <= 3**; i++ ))
do

cp 'job.temp' "job_$i.qsub"


echo "./foo $i 5. 0. 133" > "job_$i.qsub"


done
```

---

### Post by heindsight on 2009-03-16
```
for (( i = 1; i >= 3; i++ ))
```
Look carefully at that.

You're saying let i be 1, then as long as i is greater or equal to 3, increment i...

Try changing it to:
```
for (( i = 1; i <= 3; i++ ))
```

---

### Post by namegame on 2009-03-16
Just as an explanation of what sisco posted. In your original script, your loop variable, i never is "greater than" 3, you were basically stating that you want the loop to execute while i >= 3, which never occurs because i is initialized as 1.

EDIT: I also reported this to be moved to Programming talk. :)

---

### Post by muxecoid on 2009-03-17
Thanks. It's just a typo. I expected the problem to be in misunderstanding how shell scripts work and did not check the condition.

How do you debug shell scripts? In C I would just put a breakpoint in the middle of the loop to see what happened, what about this?

---

### Post by heindsight on 2009-03-17
> **muxecoid said:**
> Thanks. It's just a typo. I expected the problem to be in misunderstanding how shell scripts work and did not check the condition.

How do you debug shell scripts? In C I would just put a breakpoint in the middle of the loop to see what happened, what about this?
Try the -x option to bash. In other words, run your script like:
```
bash -x ./script.sh
```

Or change your
```
#!/bin/bash
```
to
```
#!/bin/bash -x
```

Or add a line like:
```
set -x
```
at the beginning (just after #!/bin/bash)

---

### Post by Tuna-Fish on 2009-03-17
> **muxecoid said:**
> 
Expected behaviour: 3 files that contain job.temp with an extra string at the end.

I think there is another, somewhat subtler bug on this line:
```

echo "./foo $i 5. 0. 133" > "job_$i.qsub"

```

The redirecting operator > means replace the contents of the target file with the output of the previous.

To append text, use >> 

example:
```
$ echo "123" >test
$ cat test
123
$ echo "456" >test
$ cat test
456
$ echo "123" >>test
$ cat test
456
123
$

```

---

