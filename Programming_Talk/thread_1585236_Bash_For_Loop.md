---
title: "Bash For Loop"
date: 2010-09-30
forum: Programming Talk
---

### Post by utsavgupta on 2010-09-30
I'm on Lucid Lynx.. Bash: 4.1.5

```
for i in {1..50..1}
do
 echo "$i"
done
```

Is not working. It's producing {1..50..1}.

I didn't  even know that this method existed, I came to know about it recently from:

[http://www.cyberciti.biz/faq/bash-for-loop/](http://www.cyberciti.biz/faq/bash-for-loop/)

I was using (( ; ; )) ... However I want to why isn't it working.

---

### Post by utsavgupta on 2010-09-30
I'm on Lucid Lynx.. Bash: 4.1.5

```
for i in {1..50..1}
do
 echo "$i"
done
```

Is not working. It's producing {1..50..1}.

I didn't  even know that this method existed, I came to know about it  recently from:

[http://www.cyberciti.biz/faq/bash-for-loop/](http://www.cyberciti.biz/faq/bash-for-loop/)

I was using (( ; ; )) ... However I want to why isn't it working.

---

### Post by spjackson on 2010-09-30
I'd guess that it's not working because it's processed by /bin/sh not /bin/bash. If you are using it in a script, place the following line at the start of the script.
```

#!/bin/bash

```

---

### Post by utsavgupta on 2010-09-30
It didn't work!

---

### Post by spadewarrior on 2010-09-30
try

> #!/bin/bash
for i in {1..50}
do
 echo "$i"
done

Output:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50

---

### Post by s.fox on 2010-09-30
Threads merged. Please do not duplicate threads.

---

### Post by utsavgupta on 2010-09-30
Thanks... it worked!

---

### Post by spjackson on 2010-09-30
> **utsavgupta said:**
> Thanks... it worked!
...which is quite remarkable since it is exactly the same as I suggested to you, and you said that didn't work.

---

### Post by spadewarrior on 2010-10-02
edit:

Seems you're right... Am guessing the original poster used 

sh [FILE]

rather than 

./[FILE]

or, as you say, left out the bash declaration...

---

### Post by utsavgupta on 2010-10-03
I think that was causing an error since I used "sh filename".

Sorry [spjackson]("http://ubuntuforums.org/member.php?u=1128302")

---

