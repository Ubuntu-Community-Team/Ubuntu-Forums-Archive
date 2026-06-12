---
title: "User interrupt in bash script."
date: 2007-05-13
forum: Programming Talk
---

### Post by musther on 2007-05-13
I'm trying to write a script to perform a looping operation, until the user interrupts it with a key press.

The key press is relevant, so if the key is p I want one thing to happen, if it's s I want another, etc.

I'm not sure if this is the correct way to go about this, but imagine:

```

function loopingfunc{
ping google.com
}
loopingfunc&

```

I assume I can then execute other commands, such as reading user input with 'read' while the ping command is running.  My question then is how I can kill the function loopingfunc depending on the user input.

If this is the correct way to do things, then I would want to make 'read' only capture one key press, and not wait for an enter key press.

Thanks

---

### Post by Ramses de Norre on 2007-05-13
The variable $! holds the pid of the last job started in the background from the current shell.
So you could read the input and if the loop needs to be stopped you issue **kill $!**. If the script is more complex you'll need to store the pid of the loop in some other variable.

---

### Post by cwaldbieser on 2007-05-13
> **musther said:**
> 
If this is the correct way to do things, then I would want to make 'read' only capture one key press, and not wait for an enter key press.

Thanks

Try
```

read -n 1 keypress
echo $keypress

```

---

### Post by musther on 2007-05-13
Thank you both, that's exactly what I needed to know. :)

---

