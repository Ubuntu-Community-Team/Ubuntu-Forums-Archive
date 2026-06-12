---
title: "Function call in gnome-terminal command"
date: 2009-08-10
forum: Programming Talk
---

### Post by kaibob on 2009-08-10
Is it possible to use a function in connection with the gnome-terminal command in a shell script? For example:

```
#!/bin/bash

greeting ()
{
echo "hello"
}

gnome-terminal --command="greeting"

```

If I run this shell script, I get an error message that states "There was an error creating the child process for this terminal."

I understand there are other ways to do this, such as the following:

```
gnome-terminal -x bash -c "echo hello ; bash"
```

BTW, I googled for about an hour on this topic but found nothing, and I know little about the use of functions in shell scripts, but I thought I would ask.

Thanks for the help.

---

### Post by jpkotta on 2009-08-10
The function is defined in the script's shell (the one that's spawned from the shebang line).  Functions aren't inherited, so the shell started by gnome-terminal won't have it defined.  You could have the terminal run a script instead.

---

### Post by kaibob on 2009-08-10
> **jpkotta said:**
> The function is defined in the script's shell (the one that's spawned from the shebang line).  Functions aren't inherited, so the shell started by gnome-terminal won't have it defined.  You could have the terminal run a script instead.

Thanks for the response. I understand now why the function didn't work.

---

### Post by jpkotta on 2009-08-10
Ah, but I spoke too soon.  You can export functions just like variables.
```
export -f greeting
```

---

### Post by kaibob on 2009-08-10
> **jpkotta said:**
> Ah, but I spoke too soon.  You can export functions just like variables.
```
export -f greeting
```

I modified my original test script with the export commmand, but it still doesn't seem to work.

```
#!/bin/bash

greeting ()
{
echo "hello"
}

export -f greeting

gnome-terminal --command="greeting"
```

---

### Post by benj1 on 2009-08-10
you could just add 'echo "hello"' to your ~/.bashrc and that would run automatically when you started any terminal.

---

### Post by jpkotta on 2009-08-10
> **kaibob said:**
> I modified my original test script with the export commmand, but it still doesn't seem to work.

It's probably trying to exec() the shell function, which can't be done.  Try 
```
gnome-terminal --command="bash -c greeting"
```
Some way or another, you have to start a shell in the terminal.

---

### Post by kaibob on 2009-08-10
> **jpkotta said:**
> It's probably trying to exec() the shell function, which can't be done.  Try 
```
gnome-terminal --command="bash -c greeting"
```
Some way or another, you have to start a shell in the terminal.

I played around with various alternatives, and the following worked. The second bash command appears only to be necessary to keep the terminal window open, as I substituted read for bash and that also worked.

Thanks for the help.

```
#!/bin/bash

greeting ()
{
echo "hello"
}

export -f greeting

gnome-terminal --execute bash -c "greeting ; bash"
```

---

