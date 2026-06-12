---
title: "The '&gt;' command"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by alphaniner on 2008-07-21
I was looking at another thread where someone was unable to use their mouse and needed to gather some debug info in order for the community to help him out.  Since in a gnome virtual terminal you need the mouse to copy text (I think), the '>' command can come in handy.  If you use the command

```
dmesg > /home/****/dmesg.file
```

the output of dmesg will be saved to the file *dmesg.file*.  It will overwrite anything that was already there, however.  If you replace the '>' with '>>' the output will be appended to the file rather than overwrite it.

You can use this handy little feller with any command that returns output to the screen.  You can then save the file to a floppy or a network share, etc.  Or you could open the file with a gui app (like gedit) to copy and then paste it onto a post in these fine forums, all without a mouse even.  Seriously, it's how I made this thread.  Call me a geek, but I think it is a pretty nifty tool.

---

### Post by Bachstelze on 2008-07-21
It's called "Redirections", and is not actually a comma,d. You can learn more about it here :

[http://www.gnu.org/software/bash/manual/html_node/Redirections.html#Redirections](http://www.gnu.org/software/bash/manual/html_node/Redirections.html#Redirections)

---

### Post by Joeb454 on 2008-07-21
I often use it to get peoples sources.list, I tell them to run ```
cat /etc/apt/sources.lst > ~/Desktop/sources.txt
``` and to then upload the "sources.txt" file on their desktop :)

It stops really long posts ;)

---

### Post by Joeb454 on 2008-07-21
I often use it to get peoples sources.list, I tell them to run ```
cat /etc/apt/sources.lst > ~/Desktop/sources.txt
``` and to then upload the "sources.txt" file on their desktop :)

It stops really long posts ;)

---

### Post by Tomosaur on 2008-07-21
^^ Doesn't stop double posts though, does it? :P

Another useful little tool is the 'pipe':
```

cat /etc/timezone | espeak

```

The pipe takes the output of the command on the left, and uses it as the input for the command on the right.

---

### Post by nick_h on 2008-07-21
> often use it to get peoples sources.list, I tell them to run
```
cat /etc/apt/sources.lst > ~/Desktop/sources.txt
```
Why not just use a copy command?
```
cp /etc/apt/sources.list ~/Desktop/sources.txt
```

> cat /etc/timezone | espeak
You could also use:
```
espeak < /etc/timezone
```

I often use the pipe for this sort of thing though - especially when I have just viewed the file with a cat command.

---

### Post by drubin on 2008-07-22
> **nick_h said:**
> Why not just use a copy command?
```
cp /etc/apt/sources.list ~/Desktop/sources.txt
```

Great question? answers?

---

### Post by Bachstelze on 2008-07-22
> **Joeb454 said:**
> I often use it to get peoples sources.list, I tell them to run ```
cat /etc/apt/sources.lst > ~/Desktop/sources.txt
``` and to then upload the "sources.txt" file on their desktop :)

:confused:

This is.. err... unusual. What's wrong with [FONT="Courier New"]cp[/FONT] ?

---

### Post by The Cog on 2008-07-22
In that instance yes, cp woud work. But not for other commands like netstat, lshw, ifconfig etc. Piping output to a file is a very common thing to do. So much so that it is more natural to think of **cat > file** than it is to thing of **cp**, at least when you would normally want to view the source file.

---

### Post by bab1 on 2008-07-22
The command > is for redirecting [COLOR="Magenta"]stdout[/COLOR] to a file.  The distinction here would be that cp does not default to stdout.  The examples Cog referred to are all directed to stdout ([COLOR="Magenta"]the display[/COLOR])by default.

---

