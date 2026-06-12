---
title: "Issues with find"
date: 2010-07-08
forum: Programming Talk
---

### Post by Azrael3000 on 2010-07-08
Hi!

I have got a weird issue with find that I can't seem to work out. Any help is greatly appreciated.

Consider the following code:
```

test='"Case1*"'
echo $test
echo '---'
find . -name $test -exec echo {} \; #-exec rm -f {} \; &> /dev/null
echo '---'
find . -name "Case1*" -exec echo {} \;

```

The output will then be:
```

"Case1*"
---
---
./Case1_windows_cygwin_gfortran.bat
./Case1_unix_gfortran.bat
./Case1_windows_ftn95.bat
./Case1.txt
./Case1_windows_cvf.bat
./Case1_unix_ifort.bat

```

But why? I mean clearly the second output should not be empty but rather the same as the third one.

Thanks in advance,
Arno

---

### Post by dwhitney67 on 2010-07-08
What's wrong with doing it like...
```

test='Case1*'
echo $test
echo '---'
find . -name "$test" -exec echo {} \; #-exec rm -f {} \; &> /dev/null
echo '---'
find . -name "Case1*" -exec echo {} \;

```

---

### Post by anomie on 2010-07-08
Right, you've got some superfluous double-quotes (") in your variable assignment. The previous poster's method - including double-quoting the variable at *expansion* time - seems more logical.

---

### Post by Azrael3000 on 2010-07-09
oh yeah. somehow this did not come to my mind. thanks lads. problem solved.

---

