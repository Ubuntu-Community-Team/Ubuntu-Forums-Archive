---
title: "Problems running shell script"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Sunfist on 2008-06-08
When I try to run a shell script I get an error saying command not found, or something like that. If a script wont run, how do you go about finding out why it wont.

---

### Post by easybake on 2008-06-08
It could be many things. If you post it, maybe someone might find the problem.

---

### Post by stchman on 2008-06-08
> **Sunfist said:**
> When I try to run a shell script I get an error saying command not found, or something like that. If a script wont run, how do you go about finding out why it wont.

Post the shell script.

---

### Post by Baelus on 2008-06-08
Are you having trouble actually running the script? I can't quite tell from your post. If that's the case then try this:

Make sure your script is executable.

Change to its directory and type:

```
chmod +x my_script.sh
```

Then run it with:

```
./my_script.sh
```

You need the full path to the script, or ./ if it's in the current directory, because the script isn't in your $PATH, so bash doesn't know about it.

- B

---

### Post by Barriehie on 2008-06-08
This thread address' the same issue and offers solutions.

[http://ubuntuforums.org/showthread.php?t=815115](http://ubuntuforums.org/showthread.php?t=815115)

Barrie

---

