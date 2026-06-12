---
title: "Shell Script, why doesn't this work?"
date: 2009-06-16
forum: Programming Talk
---

### Post by Arctic_Fox on 2009-06-16
I don't really have a problem, I'm just asking this because I'm curious.

Why doesn't the command:

echo "test" | read x
echo $x

Work for storing "test" in variable x?

---

### Post by unutbu on 2009-06-16
When you use a pipe, commands (in the second half of the pipe) are run in a subshell.

When you say```


echo "test" | read x
```

the "read x" is run in a subshell. The value of $x is only understood in that subshell.
When bash gets to the next line,

```
echo $x
```

bash has already forgotten about the value of $x in the subshell. As far as bash is concerned the $x in "echo $x" has nothing to do with the x in "read x".

One way around this is to put the "echo $x" in the subshell:

```
echo "test" | (read x; echo "$x")
```

See also [http://tldp.org/LDP/abs/html/gotchas.html](http://tldp.org/LDP/abs/html/gotchas.html). Search for the words "Piping echo".

---

### Post by Arctic_Fox on 2009-06-16
Oh ok, Thanks!

---

### Post by ghostdog74 on 2009-06-16
don't have to echo to read. another way
```

read x <<< "test"

```

---

