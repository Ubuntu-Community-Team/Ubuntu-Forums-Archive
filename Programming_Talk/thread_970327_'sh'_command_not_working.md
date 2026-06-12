---
title: "'sh' command not working"
date: 2008-11-04
forum: Programming Talk
---

### Post by kulkarniniraj on 2008-11-04
this is a script (a.sh)

a=$1
i=1
i=$[ $i + 1 ]
echo $i	

rohan@rohan-desktop:~$ sh a.sh
a.sh: 3: 1: not found
1

rohan@rohan-desktop:~$ chmod +x a.sh
rohan@rohan-desktop:~$ ./a.sh
2

Can anyone tell me why same script gives error when tried to run with 'sh' command ???

I am using ubuntu 8.04 (64 bit version)

---

### Post by rjack on 2008-11-04
Probably it's feeded into bash when runned with ./a.sh, while sh should be dash.

So if you call "sh $script" you execute it with dash, else if you call "./$script" you execute it with bash.

Add the line```
#!/usr/bin/env sh
``` at the top of the code.

Now the script should always crash, regardless of the method of invocation :)

---

### Post by Bichromat on 2008-11-04
rjack explained why you have different behaviours. Now, the reason why your crashes: bash is smarter and understands what you're trying to do, but sh does not. When it sees something like ' 1 ' (notice the spaces), it understands it as a command, and fails when it tries to run it. If you remove the spaces :
```
i=$[$i+1]
```
you get another behaviour : sh understands this instruction as a string concatenation and your script prints
```
$[1+1]
```

If you want to do operations on numbers, use (( )) :
```
a=$1
i=1
i=$(($i + 1))
echo $i
```

---

### Post by geirha on 2008-11-05
If you want it to work in either shell, use expr for integer arithmetics.
```
i=1
i=`expr $i + 1`
echo $i
```

EDIT: The $(( )) syntax Bichromat showed is prettier though, so never mind this post.

---

