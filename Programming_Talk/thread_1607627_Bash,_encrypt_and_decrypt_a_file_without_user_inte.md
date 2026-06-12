---
title: "Bash, encrypt and decrypt a file without user interaction?"
date: 2010-10-28
forum: Programming Talk
---

### Post by tacticalbread on 2010-10-28
To teach myself Bash, I'm attempting to write a simple, silly text-based [SIZE="1"](obviously lol)[/SIZE] RPG type thing in Bash; essentially to prove to myself that it's possible to create something like that in a language definitely not designed for such a thing.

So I'd like to be able to encrypt and decrypt a file without any user interaction, behind the scenes. Is it possible to send the passcode as an argument to the encrypting program? Or is it possible to send text to a program running in the background with the '&' argument?

Thanks in advance. (:

---

### Post by trent.josephsen on 2010-10-28
How are you encrypting the file?  I'm not aware of any options to automate gpg, but it's got a monster man page that I have read less than half of.

---

### Post by MadCow108 on 2010-10-28
you could make gpg use gpg-agent with an key without passphrase.
But from a security standpoint this makes little sense.

and yes you can send data to a backgrounded process.
There are many many ways (google IPC)
One easy way would be an named pipe:
```

mkfifo mypipe;
read_data <mypipe &
sleep 5;
echo "data" > mypipe;

```
I guess exec could also be used
[http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/x13082.html](http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/x13082.html)

---

