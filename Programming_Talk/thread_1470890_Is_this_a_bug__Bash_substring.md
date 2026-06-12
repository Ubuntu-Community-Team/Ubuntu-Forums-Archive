---
title: "Is this a bug ? Bash substring"
date: 2010-05-03
forum: Programming Talk
---

### Post by dragos2 on 2010-05-03
I have this code:
```

number=12345*
echo ${5:1}

```which should ouput "*" but instead outputs all the variables I set.

What is wrong ?

---

### Post by dragos2 on 2010-05-03
I want to check if the 5th character of this string is '*'

```

#!/bin/bash
number=12345*
echo ${number:5:1} # does not work
echo ${number:(-1)} # does not work

```

and it returns a list of inputs I did in some other scripts and the .sh names of all the scripts I executed.

Why the script above does not work ?

---

### Post by john newbuntu on 2010-05-03
Try:
echo "${number:5:1}"

---

### Post by Portmanteaufu on 2010-05-03
If I'm understanding you correctly, you would like the result of
```

echo ${number:5:1}

```
to be an asterisk ('*') printed to the screen. If that's the case, you'll need to put the latter portion of that statement in double-quotes, like so:
```

echo "${number:5:1}"

```

Without the double quotes, bash interprets the statement as
```

echo *

```

Which means "print all of the file names in the current directory". Adding the double quotes makes it mean
```

echo "*"

```
which means "Print the character '*'". Hope that helps!

---

### Post by philinux on 2010-05-03
Threads merged. Please dont double post threads.

---

### Post by dragos2 on 2010-05-04
Thanks all, the double quoting is the correct solution.

Thank you

Ps: Sorry for double posting.

---

