---
title: "Want to run a bunch of perl scripts -- .bat file for UNIX?"
date: 2007-06-22
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-06-22
I have a bunch of perl scripts that I want to execute, but not one at a time by hand.  Is there a way that I can list all the scripts that I want to run in a file and then just execute the file?  Similar to *.bat file for windows.

---

### Post by vambo on 2007-06-22
Put them in another perl script

---

### Post by robgr85 on 2007-06-22
> **SNYP40A1 said:**
> I have a bunch of perl scripts that I want to execute, but not one at a time by hand.  Is there a way that I can list all the scripts that I want to run in a file and then just execute the file?  Similar to *.bat file for windows.

create bash script, below is a link with example

[http://cheimes.de/opensource/misc/checkout.sh](http://cheimes.de/opensource/misc/checkout.sh)

Bash is very powerful scripting language for linux... nice to know the basics

the first line "#!/bin/bash" is important, it is not a comment so do not remove this

Robert

---

### Post by WW on 2007-06-22
robgr85's suggestion is good; I'll just add that, since all you want to do is run a bunch of commands, your script will be very simple, and won't necessarily need to be a *bash* script.  For example, consider this file called **myscript**

**myscript**
```

echo "Starting commands..."
perl program1.pl
perl program2.pl
perl program3.pl
echo "Done!"

```
You can run the commands in the file with the command
```

$ sh myscript

```
or
```

$ source myscript

```
If, as robgr85 suggested, you add the line **#!/bin/bash** at the beginning of **myscript**, and make the file executable, you can run the script as a command:
```

$ ./myscript

```

---

