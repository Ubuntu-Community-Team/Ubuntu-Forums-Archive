---
title: "Whats wrong with my bash script?"
date: 2010-08-16
forum: Programming Talk
---

### Post by Zilioum on 2010-08-16
I'm currently writing a little program that converts my .mkv files to .mp4's. The program itself works reasonably well but I want to automate the whole process. I came along inotify and with it inotifywait. I created the following script, which is supposed to copy my little program into the directory where a new file has been created and then run it (not very elegant copying the program around, I know. I'll deal with that later).
I got the inotifywait syntax from [here]("http://manpages.ubuntu.com/manpages/jaunty/man1/inotifywait.1.html"). I used "example 2" as a basis for this script.
```

#!/bin/bash
while inotifywait -m -r -e create /media/mediadisk/files 
do
echo %w  #just for checking for the correct directory
cd /media/mediadisk/files && cp Converter %w && ./Converter %f
done

```

When I start the script though, I only get this for example:```

Setting up watches.  Beware: since -r was given, this may take a while!
Watches established.
/media/mediadisk/files/ CREATE logo.png
/media/mediadisk/files/ CREATE .giosave603NHV
/media/mediadisk/files/ CREATE test.mkv
^C

```

Only the while statement is executed, the rest not. I'm not sure if this would work, but having it executed would help a lot ;)
What am I doing wrong?

Cheers

---

### Post by soltanis on 2010-08-17
I think your problem is using the -m flag. From the page:

```

       **-m, --monitor**
              Instead of exiting  after  receiving  a  single  event,  execute
              indefinitely.   The default behaviour is to exit after the first
              event occurs.

```

But your while loop depends on the program exiting because it is waiting to collect the exit status:

```

while inotifywait -m -r -e create /media/mediadisk/files
# means, run inotifywait, wait until the program exits, then read the exit status

```

Since the program never exits, the loop body is never executed as well.

If you want to execute the loop body every time inotifywait sees a file get created then do this:

```

while inotifywait -r -e create /media/mediadisk/files
do
# ...
done

```

---

### Post by Zilioum on 2010-08-17
Yes, I think you're right, the stuff in "do" was never executed.
Thanks!

---

### Post by dwhitney67 on 2010-08-17
> **Zilioum said:**
> Yes, I think you're right, the stuff in "do" was never executed.
Thanks!

You marked your thread as solved, however when I attempted to run it, with Soltanis' suggestion, I could not get it to display anything worthwhile for %w or %f.  How did you get it to work?

I was able to use something like:
```

#!/bin/bash

while [ true ]
do
        file=`inotifywait -q -r -e create --format '%w%f' /path/to/some/dir`

        if [ -f $file ]   # only process a file, not a directory
        then
                echo $file
        fi
done

```

---

### Post by Zilioum on 2010-08-17
You're right, it still doesnt work. Thats because %w, %f etc. only work in the context of inotifywait.
I think the only way to get it to display things like %w is use it with --format (how you did it).
Personally I'm going to write a small c++ program that pipes the output of my inotifywait --format etc. command and then work with that to execute the commands.

---

### Post by soltanis on 2010-08-17
Sounds like a great job for an [awk]("http://www.softpanorama.org/Tools/awk.shtml") script.

---

### Post by Zilioum on 2010-08-17
Thanks for the input. Will have a closer look at it, sounds interesting.

---

