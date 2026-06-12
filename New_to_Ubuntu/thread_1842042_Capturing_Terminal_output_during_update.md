---
title: "Capturing Terminal output during update?"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-09-10
Hi,

As an example, I downloaded the Ubuntu Restricted Extras using the Terminal.
Although, my real question is: is there a way to log all of the stuff that scrolls in the terminal during the update process?  As the Restricted Extras was installing, it generated a ton of messages, but there was so much that alot of it (the top half) ultimately was lost.

So when you install software or whatever (I'm just using the Restricted Extras as an example) is there a way to capture what is in the terminal into a text file or something?

Thanks

I'm using 10.04 if it matters.

---

### Post by sanderd17 on 2011-09-10
you can send everything to a file by adding 
```

> file.txt

```
at the end of every command you which.

Waring. This will overwrite the file. If you prefer to append to the file, you should use
```

>> file.txt

```

So for example
```

sudo apt-get upgrade > file.txt

```
will send everything to the file.

The problem is that you don't see anything on the screen (also no error messages or questions). So I don't know if it's a good method.

You could also go in your terminal settings and set the scrolling settings to remember all lines instead of the standard (I think) 500 lines.

---

### Post by The Cog on 2011-09-10
script is a little utility that logs a terminal session to a file. Start with the command **script update-log.txt** and this starts a new sub-shell where everything will be logged to the file. Then run the update **sudo apt-get update** and then quit the script shell with **exit**. You can then view the file update-log.txt at your lesiure.

---

### Post by gmargo on 2011-09-11
To capture the output in a file but still see what's going on:
```

sudo apt-get update 2>&1 | tee Update.out
sudo apt-get -y dist-upgrade 2>&1 | tee Upgrade.out

```The "-y" argument says "yes" to all the questions to prevent an interactive mode.

---

