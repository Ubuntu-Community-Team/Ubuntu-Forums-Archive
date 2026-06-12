---
title: "Can Bash Understand Exit Signals?"
date: 2005-12-22
forum: Programming Talk
---

### Post by xtacocorex on 2005-12-22
Is it possible for bash to do something automatically when a program exits without having to create a wrapper script to call a program?

I know about the exit signals, but I'd like to have the command line spit out text when a command exits, most likely based on it's exit status, sorta like having it talk back to you.

I know it sounds like a lame idea for it to talk back, but I need something to do while I'm on semester break besides playing Halo. Otherwise I'd attempt to figure out how to get FORTRAN to accept command line arguments, which is pretty much near impossible from the research I've already done.

Any help given will be credited in the final result.

---

### Post by darth_vector on 2005-12-22
i dont know about automating it, but if you echo $? you will get the exit status of the last command executed. as you said, a simple wrapper script could do this for you.

perhaps it can be done. i might have a look around.

---

### Post by Jengu on 2005-12-23
You could have some sort of daemon running in the terminal, that works like top, monitoring active processes, and when it notices one isn't in the list anymore, it prints out it's name.

---

### Post by Gandalf on 2005-12-23
as darth_vector said it's $?

for example adding a function as the following below
```

check_errs()
{
  if [ "${1}" -ne "0" ]; then
    echo -e "ERROR # ${1} : ${2}"
    exit ${1}
  fi
}

```

and you want to check after a faulty apt-get command
```

sudo apt-get install fedora
check_errs $? "There was an error Installing fedora."

```

will stop the script and print the error number in addition to the error message

Hope that Helps

---

### Post by LordHunter317 on 2005-12-23
If you want to respond to a child process exiting, look at trap (help trap).

---

### Post by xtacocorex on 2005-12-27
Thanks for all the responses, will definately have to try them out when I get back home from work.

---

