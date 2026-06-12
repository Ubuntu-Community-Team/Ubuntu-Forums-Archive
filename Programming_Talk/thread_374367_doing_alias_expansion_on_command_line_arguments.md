---
title: "doing alias expansion on command line arguments"
date: 2007-03-02
forum: Programming Talk
---

### Post by medeski on 2007-03-02
I'm trying to write a script where one of the parameters is used in the script as a command, e.g.

```
#!/bin/bash
$1 $2
```


So if the first parameter is more, then the script should open $2 with more and so on.

The problem is that I'd like to be able to use aliases for the first parameter. So if I've aliased m to more, I'd like the following invocations to be equivalent:

% <script> more <file>
% <script> m <file>

But! I can't get it to work. This is what I've got:

```
#!/bin/bash 

shopt -s expand_aliases 
source ~/.bash_aliases 

$1 $2 
m $2
```

Calling this script with m as the first parameter gives me

./script: line 6: m: command not found
<$2 opens with more>

In other words, alias expansion happens in the second case but not in the first.

Any ideas on why, and how to get around it?

---

### Post by Mr. C. on 2007-03-02
eval $1 $2

Think about what order variable and alias expansion occurs.

---

### Post by medeski on 2007-03-02
Thanks.  I figured it was an order problem but couldn't find anything in the man page specifically on alias expansion in relation to parameter expansion.  Didn't notice there was an eval either  :)

---

