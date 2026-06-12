---
title: "while with &quot;lesser than&quot; not working"
date: 2010-12-21
forum: Programming Talk
---

### Post by lyngeled on 2010-12-21
Hi, I am trying an "while" with "lesser than" or "greater than" but this example I have found do not work, what's wrong?:  #!/bin/bash  num=1  while [$num -lt 5]; do num=$[$num + 1]; echo $num; done  Regards  Lars

---

### Post by unknownPoster on 2010-12-21
it's standard practice on this forum to surround your code with the code tags. Just for readability, I assume this is your program/script:

```

#!/bin/bash 
 num=1  
while [$num -lt 5];
do num=$[$num + 1]; 
echo $num; 
done


```

---

### Post by r-senior on 2010-12-21
Don't forget Bash is not as lenient with spacing as a typical programming language. The spaces inside the square brackets (and indeed the lack of spaces in the assignment) are significant.

```

$ cat test.sh
#!/bin/bash
n=1
while [ $n -le 5 ]; do 
    echo $((n++))
done

$ ./test.sh
1
2
3
4
5

```

What error message did you get?

---

### Post by lyngeled on 2010-12-22
Ok - that worked. Thanks!
I will continue on my script...

Lars

---

### Post by psusi on 2010-12-22
$[$num + 1] is nonsense, you want $(($num + 1)).

---

### Post by MadCow108 on 2010-12-22
> **psusi said:**
> $[$num + 1] is nonsense, you want $(($num + 1)).

its not nonsense, its just less portable.
For bash it works fine but it will fail in dash.

---

### Post by psusi on 2010-12-22
> **MadCow108 said:**
> its not nonsense, its just less portable.
For bash it works fine but it will fail in dash.

Weird.  I can't find any reference to $[ in the bash manual, but it does seem to work.

---

### Post by hakermania on 2010-12-22
Please mark the thread as Solved.

---

