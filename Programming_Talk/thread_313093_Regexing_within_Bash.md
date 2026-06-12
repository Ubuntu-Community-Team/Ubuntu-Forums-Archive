---
title: "Regexing within Bash"
date: 2006-12-05
forum: Programming Talk
---

### Post by MattKemp on 2006-12-05
I'm playing around in bash scripting, and I'm looking to do some reasonably complex regexing on HTML I've grabbed with cURL that comes out something like this:

abc[1234]...(stuff I don't need)...def[1234]...(more stuff)...abc[123456]...def[123456]

and so on. Ideally, I'd like a list of unique numbers - preferably in a bash array so I can play around and run functions off them.

Is this doable within bash/awk, or will I need perl or python?

Ta for any help.

---

### Post by duff on 2006-12-05
If your just trying to extract information out of a file, you may be able to get away with using "egrep".  Check out its man page.

---

### Post by IYY on 2006-12-05
```
grep -o '...[[0-9]*]'
```

is a good starting point.
```

ilya@muddy:~$ grep -o '...[[0-9]*]' 
abc[1234]...(stuff I don't need)...def[1234]...(more stuff)...abc[123456]...def[123456]
abc[1234]
def[1234]
abc[123456]
def[123456]
```

---

### Post by MattKemp on 2006-12-05
> **IYY said:**
> ```
grep -o '...[[0-9]*]'
```

is a good starting point.
```

ilya@muddy:~$ grep -o '...[[0-9]*]' 
abc[1234]...(stuff I don't need)...def[1234]...(more stuff)...abc[123456]...def[123456]
abc[1234]
def[1234]
abc[123456]
def[123456]
```

That's fab, as it gives me a nice list of them, something like this:

```
matt@rustbucket:~/Desktop$ cat form.html |grep -o '...[[0-9]*]'
ype[13813]
ail[13813]
ine[13813]
veg[13813]
veg[13813]
rcb[13813]
sdr[13813]
ype[13780]
ail[13780]
ine[13780]
veg[13780]
veg[13780]
rcb[13780]
sdr[13780]

```
I can reduce that down by getting rid of the first/few characters or brackets and can get singular occurrences as the bits before are just repeated, but trying:
```
cat form.html |grep -o 'ype[[0-9]*]' |awk '/ype\[([0-9]*)\]/ {print $1}'

```

just gives me the same results. Can you point out where I'm going wrong? And, any idaa how I can get this into some kind of data structure within bash?

---

### Post by IYY on 2006-12-06
I'm don't know the answer to your program, but the 'uniq' command can be used to easily remove duplicates.

---

