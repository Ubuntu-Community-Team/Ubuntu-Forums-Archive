---
title: "[SOLVED] user inputs and grep"
date: 2008-08-08
forum: Programming Talk
---

### Post by Ristar on 2008-08-08
hello, im trying to write something to check the validity of a user's input in bash...

how do i make the program reject alpha and special characters?

thanks.

---

### Post by mssever on 2008-08-08
> **Ristar said:**
> hello, im trying to write something to check the validity of a user's input in bash...

how do i make the program reject alpha and special characters?

thanks.
```
read input
if [[ $input =~ ^[0-9]*$ ]]; then
  # do something
else
  echo "Bad input"
  exit 1
fi
```

---

### Post by Ristar on 2008-08-08
> **mssever said:**
> ```
read input
if [[ $input =~ ^[0-9]*$ ]]; then
  # do something
else
  echo "Bad input"
  exit 1
fi
```


uh.... but if i press space or if no characters were entered, it'd be OK also.

is there a way to stop this?

---

### Post by ConMan318 on 2008-08-08
Just a small change:
```

read input
if [[ $input =~ ^[0-9]+$ ]]; then
  # do something
else
  echo "Bad input"
  exit 1
fi

```

The '*' means to match 0 or more times, so zero number entered does match.  The '+' means to match 1 or more times, so there has to be at least one digit entered to match.

---

### Post by Ristar on 2008-08-08
thx guys.... that really helped.

---

### Post by mssever on 2008-08-08
> **Ristar said:**
> uh.... but if i press space or if no characters were entered, it'd be OK also.

is there a way to stop this?
Just adjust the regular expression to allow the correct characters.

---

### Post by ghostdog74 on 2008-08-08
> **Ristar said:**
> hello, im trying to write something to check the validity of a user's input in bash...

how do i make the program reject alpha and special characters?

thanks.

read [this](http://tldp.org/LDP/abs/html/testbranch.html) page. There are examples on testing user input. Also, although regexp in bash can be used, its only supported in newer bash (which i think you will have it.)

---

