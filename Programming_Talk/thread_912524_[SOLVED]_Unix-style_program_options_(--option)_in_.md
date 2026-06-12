---
title: "[SOLVED] Unix-style program options (--option) in Bash?"
date: 2008-09-06
forum: Programming Talk
---

### Post by jesushero on 2008-09-06
Hello, I'm writing a bash script and I want to implement some of the usual unix-style options, given to programs in the manner of:

```
program --option1 --option2
```

The obvious way is to use $1, $2 ... $34534 for any string arguments given, and predict all possible combinations of options and what to do. 

This is fine for 3-4 options. For a large number of options however it results in a huge script, most of which simply deals with all possible combinations of options.

Is there any smarter way of doing this in a Bash script? Like, just adding a single line of code regarding each option, no matter in what order options are given or if some are missing or something like that?

If not, is there a way in C/C++? I'm not that comfortable with C but I'd be willing to go that way if it's necessary.

---

### Post by weresheep on 2008-09-06
Hello,

Here is the method I use for program options for shell scripts...

```

for i in $* ; do
  case "$i" in
    -t ) RETAG=1 ;;
    -m ) MP3=1 ;; 
    -r ) REVERSE="-r" ;;
    . ) MUSICDIR=$(pwd) ;;
    * ) MUSICDIR="$i" ;;
  esac
done

```

The $* in the for loop expands to all the provided options.

The * ) in the switch (case) statement is like C's default case. It means anything else not explicitly handled.

Using a for loop combined with the case statement means you don't have to care about the order the options are passed in.

In your example, to handle "--option1 --option2" you could do...

```

for i in $* ; do
  case "$i" in
    --option1 ) echo "Doing option1 stuff" ;;
    --option2 ) echo "Doing option2 stuff" ;; 
    * ) echo "Hrmm, don't know $i option" ;;
  esac
done

```


Hope that helps.
-weresheep

---

### Post by slavik on 2008-09-06
cute, but wrong.

look up getopt. :)

---

### Post by ghostdog74 on 2008-09-06
getopts. Search the link on learning bash in my sig and you can find examples of using getopts.

---

### Post by mssever on 2008-09-07
getopts > getopt. The *s* makes all the difference.

---

### Post by jesushero on 2008-09-07
> **weresheep said:**
> Hello,

Here is the method I use for program options for shell scripts...

```

for i in $* ; do
  case "$i" in
    -t ) RETAG=1 ;;
    -m ) MP3=1 ;; 
    -r ) REVERSE="-r" ;;
    . ) MUSICDIR=$(pwd) ;;
    * ) MUSICDIR="$i" ;;
  esac
done

```

The $* in the for loop expands to all the provided options.

The * ) in the switch (case) statement is like C's default case. It means anything else not explicitly handled.

Using a for loop combined with the case statement means you don't have to care about the order the options are passed in.

In your example, to handle "--option1 --option2" you could do...

```

for i in $* ; do
  case "$i" in
    --option1 ) echo "Doing option1 stuff" ;;
    --option2 ) echo "Doing option2 stuff" ;; 
    * ) echo "Hrmm, don't know $i option" ;;
  esac
done

```


Hope that helps.
-weresheep

Worked great, thanks! I hadn't thought of doing it this way (apparently). Actually, it worked better than getopt or getopts for what I wanted to do, it's more flexible. Do you want to be credited in the distributed version? If so, let me know how would you like your name/nickname to appear.

---

### Post by jesushero on 2008-09-07
> **slavik said:**
> cute, but wrong.

look up getopt. :)

Thanks, but getopt and getopts didn't work that well for what I was trying to do, they were too specific and I wanted to be able to include both short/long options and one non-option argument. The simple script above worked a treat. I implemented the non-option argument in there, instead of doing it separately as I would have to do with getopt/getopts.

Thanks anyway, I'll keep that in mind for future use, I'm sure it will come in handy.

---

### Post by slavik on 2008-09-07
> **jesushero said:**
> Thanks, but getopt and getopts didn't work that well for what I was trying to do, they were too specific and I wanted to be able to include both short/long options and one non-option argument. The simple script above worked a treat. I implemented the non-option argument in there, instead of doing it separately as I would have to do with getopt/getopts.

Thanks anyway, I'll keep that in mind for future use, I'm sure it will come in handy.
getopt shifts the options out and you get left with your non-option argument (like a filename)

---

### Post by weresheep on 2008-09-08
> **jesushero said:**
> 
Worked great, thanks! I hadn't thought of doing it this way (apparently). Actually, it worked better than getopt or getopts for what I wanted to do, it's more flexible.


I've had a quick look at the getopt man page but never heard of getopts before. I'm sure I'll get around to reading up on them at some point, but I find the loop works well for me.

> **jesushero said:**
> Do you want to be credited in the distributed version? If so, let me know how would you like your name/nickname to appear.

Heh, thanks but thats okay. Just glad it helped.

-weresheep

---

### Post by ghostdog74 on 2008-09-08
> **weresheep said:**
> I've had a quick look at the getopt man page but never heard of getopts before. I'm sure I'll get around to reading up on them at some point, but I find the loop works well for me.



Heh, thanks but thats okay. Just glad it helped.

-weresheep

getopts is internal to bash. Its a bash builtin. As for the loop method, that's fine if you don't have option arguments. say if you have optio in -a and it takes in an argument, eg -a 10, then you can use OPTARG to get "10". in this case, its better to use getopts

---

### Post by weresheep on 2008-09-09
[quote=ghostdog74]
getopts is internal to bash. Its a bash builtin. As for the loop method, that's fine if you don't have option arguments. say if you have optio in -a and it takes in an argument, eg -a 10, then you can use OPTARG to get "10". in this case, its better to use getopts
[/quote]

Ah, thanks for explaining the use case for getopts, I'll do some reading up on it.

Thanks,
-weresheep

---

