---
title: "bash; seeking explanation"
date: 2006-04-26
forum: Programming Talk
---

### Post by vijayanand_sodadasi on 2006-04-26
Hello everybody,

I came across the following lines of code while I was reading nano-Howto.
```
( set -e 
tar -C /tmp -xzf ${SOURCES}/lxr-0.3.tar.gz 
LXR_SOURCES=/tmp/lxr-0.3 
) 
```

1. I assume that when the code is enclosed in ( ), we can enter the commands in multiple lines.  And when we complete it with a closing ), the entire block between ( ) gets executed.  Am I correct?

2.  what is this command?:confused:  ```
set -e
```  I undetstood the next two lines though:cool:

---

### Post by DoktorSeven on 2006-04-26
From **man bash**:

> 
       set [--abefhkmnptuvxBCHP] [-o option] [arg ...]
              -e      Exit immediately if a simple command (see SHELL  GRAMMAR
                      above) exits with a non-zero status.  The shell does not
                      exit if the command that fails is part  of  the  command
                      list  immediately  following  a  while or until keyword,
                      part of the test in an if statement, part of a && or  &#9474;&#9474;
                      list, or if the command&#8217;s return value is being inverted
                      via !.  A trap on ERR, if set, is  executed  before  the
                      shell exits.


---

