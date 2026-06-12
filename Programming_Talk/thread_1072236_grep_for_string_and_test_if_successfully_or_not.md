---
title: "grep for string and test if successfully or not"
date: 2009-02-17
forum: Programming Talk
---

### Post by b-boy on 2009-02-17
Hi guys I am using grep in a bash script to look for a string and i would like to check if the string was found

so my script goes a little some thing like this !!!

```

grep bboy /var/log/messages
echo $?

```

so assumed that since the string bboy was not in /var/log/messages I would get the value higher than 0 but wether or not the string is in /var/log/messages I still get the valure 0

why?

---

### Post by albandy on 2009-02-17
MSG=$(grep bboy /var/log/messages)

if [ "$MSG" == "" ]
then
echo "No results"
fi

---

### Post by b-boy on 2009-02-17
> **albandy said:**
> MSG=$(grep bboy /var/log/messages)

if [ "$MSG" == "" ]
then
echo "No results"
fi

thanks

---

### Post by Yuzem on 2009-02-17
You can use the "-m 1" flag that exits at the first match:

```
if ! [[ $(grep -m 1 bboy /var/log/messages) ]]; then
    echo no results
fi
```

---

### Post by lavinog on 2009-02-17
i use something like this:
```

grep -q "string" filename&&{
echo "string found"
other commands
...
}

```

---

### Post by glotz on 2009-02-17
I suppose you get 0 in both cases because that's the [exit code](http://en.wikipedia.org/wiki/Exit_code) for having successfully run the command. You could use this instead```
if grep -m1 bboy /var/log/messages>/dev/null
then
echo It\'s there.
else
echo Not there.
fi
```

---

