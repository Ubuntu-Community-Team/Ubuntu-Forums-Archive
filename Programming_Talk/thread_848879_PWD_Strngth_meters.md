---
title: "PWD Strngth meters"
date: 2008-07-03
forum: Programming Talk
---

### Post by Tux.Ice on 2008-07-03
anybody got any good ones?

---

### Post by ghostdog74 on 2008-07-03
why not try making your own?

---

### Post by slavik on 2008-07-03
> **ghostdog74 said:**
> why not try making your own?
step 1:
if it's in /etc/dictionaries-common/words it's a crap password :)

```

#!/bin/bash

TEXT=$(grep $1 /etc/dictionaries-common/words)
if [ -n $TEXT ] then
  echo "password is crap"
  exit 0
fi

```

---

### Post by ghostdog74 on 2008-07-03
> **slavik said:**
> step 1:
if it's in /etc/dictionaries-common/words it's a crap password :)

```

#!/bin/bash

TEXT=$(grep $1 /etc/dictionaries-common/words)
if [ -n $TEXT ] then
  echo "password is crap"
  exit 0
fi

```

well, that path may not exist in other platforms. See [here]("http://www.theargon.com/achilles/wordlists/") for some other dictionaries. 

let's add some more
```

passwd="$1"
for dict in /path_where_dicts_are/*
do
  grep "$1" "$dict" && echo "password is crap" && exit 
done
min_passwd_length=8
max_passwd_length=10
min_number_in_passwd=1

if [ "${#passwd}" -ge 8 && "${#passwd}" -le 10 ];then
  echo "good"
else
  echo "crap"
fi
# and so on

```

---

### Post by slavik on 2008-07-04
> **ghostdog74 said:**
> well, that path may not exist in other platforms. See [here]("http://www.theargon.com/achilles/wordlists/") for some other dictionaries. 

let's add some more
```

passwd="$1"
for dict in /path_where_dicts_are/*
do
  grep "$1" "$dict" && echo "password is crap" && exit 
done
min_passwd_length=8
max_passwd_length=10
min_number_in_passwd=1

if [ "${#passwd}" -ge 8 && "${#passwd}" -le 10 ];then
  echo "good"
else
  echo "crap"
fi
# and so on

```
for a 5 minute post and 5 lines of code, it isn't too bad :P

---

### Post by Tux.Ice on 2008-07-04
actually im making my own. JavaScript. JUst wanted to see what other people could come up with.

---

### Post by ghostdog74 on 2008-07-04
> **Tux.Ice said:**
> actually im making my own. JavaScript. JUst wanted to see what other people could come up with.

it doesn't matter. you can do regexp, string manipulation in Javascript too. Same concept.

---

### Post by drubin on 2008-07-04
Very little dictionary support though. unless you going to use ajax server side, but then you have the whole keep sending their password to a server script problem.

Post what you come up with, maybe people can comment on it maybe even improve on it a bit..

---

### Post by ghostdog74 on 2008-07-04
in that case , do password checking on server side.

---

### Post by drubin on 2008-07-04
Just a few links..
[http://www.geekwisdom.com/dyn/passwdmeter](http://www.geekwisdom.com/dyn/passwdmeter) 
[http://www.codeandcoffee.com/2007/06/27/how-to-make-a-password-strength-meter-like-google/](http://www.codeandcoffee.com/2007/06/27/how-to-make-a-password-strength-meter-like-google/) 

THis one looks rather interesting with only regex
[http://www.douglaskarr.com/2007/08/27/javascript-password-strength/](http://www.douglaskarr.com/2007/08/27/javascript-password-strength/)

---

### Post by drubin on 2008-07-04
> **ghostdog74 said:**
> in that case , do password checking on server side.

That was my point doing the password checking server side would involve sending it back and worth a few times (Ajax). (OP wanted jscript strength as a client side implementation)

---

### Post by cdenley on 2008-07-16
I just made a php script for a password strength meter. I was looking for ideas to improve it when I found this thread. I created dict.php to split a dictionary into thousands of files so passwords can be compared quicker. Suggestions or improvements welcome.

---

