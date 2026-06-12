---
title: "Bash programming: Value of a variable of a variable"
date: 2008-04-30
forum: Programming Talk
---

### Post by runder on 2008-04-30
I am running into a little bit of trouble with my bash script:

I need to access the value of a variable of a variable.
This is my sample.

```

HELLO_DIR="MyValue"

TARGET="HELLO"
TARGET_PATH="\$${TARGET}_DIR"

echo $TARGET_PATH

```

This prints: $HELLO_DIR

How can I get it to print "MyValue" without having to use $HELLO_DIR directly in my script.  In other words, having TARGET_PATH="$HELLO_DIR", I want to resolve the value of $HELLO_DIR so that TARGET_PATH prints the value of $HELLO_DIR (in this case, the string "MyValue") without assigning TARGET_PATH=$HELLO_DIR directly in the script.

---

### Post by runder on 2008-04-30
I think I found a partial answer.

Using eval.

In my case, I need to change the directory to HELLO_DIR's value

So I would do:

```

eval cd $TARGET_PATH

```

Echoing the value is another story though :)

---

### Post by stylishpants on 2008-04-30
```


HELLO_DIR="MyValue"

TARGET="HELLO"
TARGET_PATH="${TARGET}_DIR"

echo ${!TARGET_PATH}


```


More info:
```
man bash | less -p "indirect expansion"
```

---

