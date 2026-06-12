---
title: "multiple commands as argument to gnome-terminal - and &quot;error creating the child pr..."
date: 2009-10-03
forum: Programming Talk
---

### Post by sdaau on 2009-10-03
Hi all, 

I quite like the possibility to use gnome-terminal to spawn a terminal window, and run a bash script in it. While running something like:
```

gnome-terminal -e "/path/to/myscript.sh"

```works fine, I was wandering how is it possible to pass a series of bash commands, say
```

echo AAA
read

```directly as an argument to gnome-terminal. 

One of the biggest problems is that even on its own, 
```

gnome-terminal -e "read"

```will cause the infamous message "There was an error creating the child process for this terminal"; and without the read command, the newly spawned terminal window will execute without any feedback and close itself. 

Finally, I managed to find [#457846 - gnome-terminal.wrapper: problem with a particular command - Debian Bug report logs]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=457846")
[quote=http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=457846]
xterm supports both:
  1. xterm -e command with separate arguments
  2. xterm -e 'command line'

It appears to do this by first trying:
  a. execvp(argv[0], argv)
then if there is a single argument:
  b. execl(shell, basename(shell), '-c', argv[0], NULL)
else
  c. execl(shell, basename(shell), NULL)
But I think (c) isn't really important.

gnome-terminal -e behaves like (b) and gnome-terminal -x behaves like
(a).  I think that the wrapper should translate -e to -e only where
there is exactly one argument following and 'which' cannot find a
command by that name; otherwise it should translate it to -x.
[/quote]

Which pointed to me a possible solution - that is, pass the multiline set of commands as arguments to 'bash', which is itself the argument to gnome-terminal: 
```

gnome-terminal -e "bash -c 'echo AAA; read'"

```so also this works: 
```

$ gnome-terminal -e "bash -c 'echo AAA
> read'
> "

```However, I cannot find a proper document here variant; for instance the following:
```

gnome-terminal -e "bash -c <<EOF
set -x # debug output
echo AAA
read
EOF "

```just shows a new terminal and exits. So, if anyone knows if a document-here type syntax would be possible, please post :) 

Thanks, 
Cheers...

---

