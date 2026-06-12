---
title: "Can't get bash script to terminate"
date: 2015-11-23
forum: Programming Talk
---

### Post by EricDallal on 2015-11-23
I found a script online called memusg to find the peak memory utilization of a program. Unfortunately, the memusg script doesn't terminate when the program whose memory utilization it is measuring terminates. This requires me to press ctrl-C. The problem is that I am now writing a script which itself calls memusg and so I need memusg to terminate properly. I have tried calling exit, as well as a few variations, but I always get one of two results: either my modifications do nothing, or else they prevent the program that I want to run from running in the first place, in which memusg returns 0 for peak memory utilization.

Here is the memusg script:

```

#!/usr/bin/env bash
# memusg -- Measure memory usage of processes
# Usage: memusg COMMAND [ARGS]...
#
# Author: Jaeho Shin <netj@sparcs.org>
# Created: 2010-08-16
set -um

# check input
[ $# -gt 0 ] || { sed -n '2,/^#$/ s/^# //p' <"$0"; exit 1; }

# TODO support more options: peak, footprint, sampling rate, etc.

# detect operating system and prepare measurement
case `uname` in
    Darwin|*BSD) sizes() { /bin/ps -o rss= -g $1; } ;;
    Linux) sizes() { /bin/ps -o rss= -$1; } ;;
    *) echo "`uname`: unsupported operating system" >&2; exit 2 ;;
esac

# monitor the memory usage in the background.
pgid=`ps -o pgid= $$`
(
peak=0
while sizes=`sizes $pgid`
do
    set -- $sizes
    sample=$((${@/#/+}))
    let peak="sample > peak ? sample : peak"
    sleep 0.1
done
echo "memusg: peak=$peak" >&2
) &
monpid=$!


# run the given command
exec "$@"

```

I know that this has something to do with subprocesses, but I can't find the solution.

---

### Post by Habitual on 2015-11-23
looks like it was written for Mac|BSD...?

```
case `uname` in
    Darwin|*BSD) sizes() { /bin/ps -o rss= -g $1; } ;;
    Linux) sizes() { /bin/ps -o rss= -$1; } ;;
    *) echo "`uname`: unsupported operating system" >&2; exit 2 ;;
esac
```

---

### Post by EricDallal on 2015-11-23
It works either in Mac, BSD, or Linux. The lines above just determine whether or not to pass a -g flag. In Linux, it doesn't.

---

### Post by Holger_Gehrke on 2015-11-23
Thank you for posting this script. It is truly an elegant piece of work by somebody who knows shell scripting very well. I had a great time working out how it works.

I don't understand your problem with it , though. 
It does terminate. 
The fact that it makes it's output (from the sub-shell started for the code in parenthesis) to error output after the measured process finishes and after the new prompt has already been printed makes that kind of hard to see. There seems to be one mode of failure to it, though: for very small programs that are finished quicker than the script can do it's measurement, it will return 0. For an example try to get the memory usage of /bin/ls or /bin/tempfile.

---

### Post by matt_symes on 2015-11-23
Hi

The script does return to the command prompt but the trailing newline from the echo command is overwriting the command prompt as the function is run as a background process. Hit the return key and you'll see a new command prompt.

```

matthew-laptop:/home/matthew:2 % ./memusg.sh sleep 1
matthew-laptop:/home/matthew:2 % memusg: peak=700
<i hit the return key here on the blank line>
matthew-laptop:/home/matthew:2 %
```

If you remove the trailing new line from the echo command, the prompt is displayed but on the same line as the usage output.

Here was a quick test.

```
echo **-n** "memusg: peak=$peak" >&2
```

```
matthew-laptop:/home/matthew:2 % ./memusg.sh sleep 1
matthew-laptop:/home/matthew:2 % memusg: peak=680
matthew-laptop:/home/matthew:2 %
```

There's no new (blank) line the in test above.

You can achieve the same effect using printf with no newline.

```
printf "memusg: peak=$peak" >&2
```

Kind regards

---

