---
title: "Bash Scripting - Arguments and getopts"
date: 2009-08-21
forum: Programming Talk
---

### Post by pcman312 on 2009-08-21
I'm writing a bash script and I need to be able to parse various command line arguments. I know how to use getopts to get the various -abc type arguments, however I want to be able to get all of the arguments after all of the getopts arguments have been retrieved.

For instance:

```
q : some flag (quiet in this case)
a : requires one argument

./script -qa arg1 arg2 arg3 arg4
```

I want getopts to catch q and a with arg1, and then pass "arg2 arg3 arg4" to another parsing function to determine what to do with them (not just throw them away or output an error). The ordering of the arguments is also important if that happens to change your solution.

I was thinking of making a list of all of the arguments, then removing each argument as it's parsed by getopts, and then managing the list afterwards. But this also presents another problem of running the script thusly:

```
./script -q arg2 -a arg1 arg3 arg4
```

arg2 would be in the list, and in this particular example, I don't want any arguments to be in between the getopts arguments. So in this example, this should output an error.

Thanks in advance :popcorn:

---

### Post by geirha on 2009-08-21
That'll be very confusing to users that are used to gnu commands.

That said, the first example here might give you some ideas on how to handle that. [http://mywiki.wooledge.org/BashFAQ/035](http://mywiki.wooledge.org/BashFAQ/035)

---

### Post by pcman312 on 2009-08-21
Well, the script is going to be used by a grand total of 2 people: me and my coworker. So I'm not terribly concerned about "normal" gnu commands. It's there to help compile a number of eclipse projects (using maven) into one final result. We can do all of it regularly on the command line, but I want to streamline the compiling different projects at once. I'm thinking of simplifying it from what I had in mind though.

Thanks for the link, I'll take a look at it.

---

### Post by penguin007 on 2009-08-21
Advanced Bash Scripting Guide: the answer to life, the universe and everything.

[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)

---

### Post by quodlibetor on 2012-03-08
Years late, but I think I've figured this out:

I use the standard **getopts** loop with a **shift** at the end:
```
OPTIND=1
while getopts "vh" o ; do # set $o to the next passed option
  case "$o" in 
    v) # do stuff
       ;;
    h) print "$usage"
       exit
       ;;
  esac
done

shift $(($OPTIND - 1))
# $1 is now the first non-option argument, $2 the second, etc
```

It's that last line that does it: **$OPTIND** is set automatically by getopt to the index of the last option processed. **shift** removes arguments from the script, and, given a numeric arguement **arg**, it removes **arg** arguments from the script argument list.

Hence, shifting off the number of arguments that were actually options lets you treat the rest of the arguments as if they were the only ones.

---

