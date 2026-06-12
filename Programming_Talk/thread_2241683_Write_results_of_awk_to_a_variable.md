---
title: "Write results of awk to a variable"
date: 2014-08-27
forum: Programming Talk
---

### Post by graylinux on 2014-08-27
Hi

In a bin/bash, I can get an awk to echo out it's results to a file correctly:- 

```
echo $path | awk -F"/" '{print $NF}' >>  $HOME/Desktop/Test_Shortcut.desktop
```

but I want to use the results later in my script. I cannot figure out for the life of me how to get those results into a variable? I thought this would do it
```
variable=$($path | awk -F"/" '{print $NF}') 
echo $variable >> $HOME/Desktop/Test_Shortcut.desktop
```

but it does not seem to work? $variable produces nothing (or empty)?

Any pointers please?

---

### Post by papibe on 2014-08-27
Hi graylinux.

I think you forgot the 'echo':
```
variable=$(**echo** "$path" | awk -F"/" '{print $NF}')
```
Regards.

P.S.: BTW if you are trying to get the equivalent of the command 'basename', you may want to try internal bash parameter substitution instead of an external call for a program like awk:
```
variable=${path##*/}
```

---

### Post by graylinux on 2014-08-28
Brilliant!

Ahh... a schoolboy error! :o)

Thanks so much for that. I have been programming for years but never with unix-ish technologies... it's a whole different world!

Also, I used your bash substitution ... works a charm!

Thanks again!

---

