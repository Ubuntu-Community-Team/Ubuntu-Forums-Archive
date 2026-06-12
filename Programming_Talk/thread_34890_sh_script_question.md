---
title: "sh script question"
date: 2005-05-16
forum: Programming Talk
---

### Post by Gandalf on 2005-05-16
hey guys,

i just have a simple question,

if i type in a script

sudo apt-get install proftpd >> log 2>&1

the installation will be logged in the file log, but the user will not see the question about installing proftpd as standalone or inetd Version, so how can i hide the apt-get actions from the user but display the proftpd question?

thanks in advance

---

### Post by JonahRowley on 2005-05-16
First off, why would you want to do this?  It seems like a useless thing to do.

Find out where the question is printed.  Is it on stdout?  stderr?  If it's stderr, you're going to have to not log errors in order to show the question.  This might also be configurable through apt.  Apt might even be able to write to the tty directly, skipping stdout and stderr entirely.

---

### Post by Gandalf on 2005-05-16
i don't actually know what really the difference between tty, stdout and stderr

i want to do it like this because the script will install VHCS and will have a lot of output and i don't want to write crap on the screen just the label of the step

---

### Post by JonahRowley on 2005-05-16
Since it sounds like you don't really want an interactive prompt anyway, why not **apt-get -y install proftpd**?  That might be more what you're looking for than a way to display the prompt.

---

### Post by Gandalf on 2005-05-16
[QUOTE=JonahRowley]Since it sounds like you don't really want an interactive prompt anyway, why not **apt-get -y install proftpd**?  That might be more what you're looking for than a way to display the prompt.[/QUOTE]
 I have already this option also --force-yes too
but this will not skip the question of standalone VS inetd

---

### Post by odyniec on 2005-05-17
I guess what you're trying to do could be accomplished by filtering the output of apt-get and redirecting it to either the log file or tty, depending on what it prints.

For example, consider the following script that prints several messages and asks the user to answer a question:
```
#!/bin/sh
echo "something"
echo "something else"

echo "AN IMPORTANT QUESTION"
read answer

echo "something"
echo "something else"
```

You can check each line of its output for the string "AN IMPORTANT QUESTION", and if there's a match, redirect the output to /dev/tty instead of the log file. This way, the question will be displayed to the user, while the rest of the messages will go to the log file.

```
out=log;
./script.sh | while read line; do 
  if [ "$line" = 'AN IMPORTANT QUESTION' ]; then 
    out=/dev/tty; 
  else 
    out=log; 
  fi; 
  echo "$line" >> $out;
done
```

---

### Post by Gandalf on 2005-05-18
thank you for this explination, but how to evaluate pre-configuring of the proftpd package? because it's not text ^o)

---

### Post by Finchwizard on 2005-05-19
Gandalf, have you managed to update the VHCS install script so it uses VHCS 2.4 Final ?

I sent you some PM's, but I thought I'd post here as well, just incase you don't check them that often or you have heaps :D

Cheers mate, keep up the great work.

---

