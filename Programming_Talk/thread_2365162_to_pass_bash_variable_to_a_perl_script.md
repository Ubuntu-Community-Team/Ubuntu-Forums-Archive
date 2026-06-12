---
title: "to pass bash variable to a perl script"
date: 2017-07-03
forum: Programming Talk
---

### Post by Biscarri on 2017-07-03
Hi,

I run iteratively a bash script that uses the variable 'loopNumber' as iteration number, and increases its value every time the script is executed.  
This bash script calls a perl script where I need to use the current 'loopNumber' value.
In order to pass 'loopNumber' value to the perl script I have tried... 

1) to 'export' the variable 'loopNumber' within the bash script, in order to make it 'environment variable' and then refer to it in the perl script as '$ENV{'loopNumber'}

2) to pass '$loopNumber' as argument when calling the perl script and then refer to it in the perl script as '$ARG[0]'

But none of those attempts has worked, or I have not found the correct syntax.
 
Any hint on how to do it will be appreciated.
Thanks
Lluis

---

### Post by slickymaster on 2017-07-03
Thread moved to **Programming Talk** for a better fit

---

### Post by steeldriver on 2017-07-03
Yes either should work:

```

$ foo=bar ; perl -le 'print $ARGV[0]' $foo
bar

```

(note the array is called ARGV not ARG)

```

$ export foo=baz ; perl -le 'print $ENV{"foo"}'
baz

```

---

### Post by Biscarri on 2017-07-03
Thanks for helping, steeldriver!

With first option (ARGV) I try to pass the argument '$foo', in order to get in perl 'foo' current value at every bash script iteration...

in the bash script...

```

foo=1
./perlscript $foo
foo=foo+1
```


in the perl script...

```
print $ARGV[0]
1
```


Maybe it is not allowed to pass a variable name as a perlscript argument.

Second option (export) I understand it works like that...

in the bash script...

```
foo=1
export foo
```

in the perl script...

```
print $ENV{'foo'}
1
```

But either is working!

---

