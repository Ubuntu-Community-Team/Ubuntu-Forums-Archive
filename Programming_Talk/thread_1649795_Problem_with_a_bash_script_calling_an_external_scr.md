---
title: "Problem with a bash script calling an external script"
date: 2010-12-20
forum: Programming Talk
---

### Post by Hex on 2010-12-20
Hey, guys,

I'm new at scripting in bash, so I need your experienced help.

I'm recording a stream from an IP camera. Since the format is weird, I use a perl script (which I didn't write or understand completely) to convert it to normal mjpeg . Of course, I don't want one huge mjpeg file, so I'd like to separate it into 15 minute long segments.

What's the best way to start and stop the perl script every 15 minutes? I can't seem to find information on controlling external scripts.

---

### Post by roccivic on 2010-12-20
record the whole thing, then split it later?

---

### Post by Hex on 2010-12-20
> **roccivic said:**
> record the whole thing, then split it later?

Not a good idea, because it'll be recording constantly. A one day file can get close to 15GB, and a one month recording will be close to 500GB. Add to that that fps is not constant and you can imagine how hard it'll be to find a certain moment in time.

If I have a bash script to restart the perl script every 15 minutes (thus creating a new file name of the type yymmddhhmm.mjpeg), it'll be much easier to find and also delete files.

I didn't expect it to be so hard to control external scripts, so I'm relying on the experienced users here :)

---

### Post by Freelance Physicist on 2010-12-20
Does the perl script have options for running a certain length of time?  If it does, you could just create a simple bash script like this:

```

#!/bin/bash

while :   # while(true) infinite loop
do
    filename=$(date +%y%m%d%H%M).mjpeg
    recordmjpeg --time 15m --output $filename
done

```

In this case, the program is recordmjpeg (replace this with the name of the actual program, --time is a command-line option to record for a certain amount of time (replace with actual option from documentation) and --output specifies the name of the file to save.

This script is an infinite loop that repeatedly runs the recordmjpeg program for 15 minutes at a time (assuming the recordmjpeg program has this kind of option).

---

### Post by Hex on 2010-12-21
> **Freelance Physicist said:**
> Does the perl script have options for running a certain length of time?  If it does, you could just create a simple bash script like this:

```

#!/bin/bash

while :   # while(true) infinite loop
do
    filename=$(date +%y%m%d%H%M).mjpeg
    recordmjpeg --time 15m --output $filename
done

```

In this case, the program is recordmjpeg (replace this with the name of the actual program, --time is a command-line option to record for a certain amount of time (replace with actual option from documentation) and --output specifies the name of the file to save.

This script is an infinite loop that repeatedly runs the recordmjpeg program for 15 minutes at a time (assuming the recordmjpeg program has this kind of option).

Thanks for the thorough reply. However, the perl script doesn't have any options - it simply provides an infinite stream of data.

What I'm trying to do in the bash script is basically the following:

1. Start the perl script and save the output to a file in yymmddhhmm format.
2. Restart the perl script every 15 minutes and save the output to a file in yymmddhhmm format.

Is there a way to kill the perl script and then restart it from the bash script? I suppose I should use PID's, but it's a bit complicated for a newbie like me.

---

### Post by Freelance Physicist on 2010-12-21
You could use ```
pkill <program-name>
``` to kill the program by name instead of PID.

So, to modify the above program:
```

#!/bin/bash

while :   # while(true) infinite loop
do
    filename=$(date +%y%m%d%H%M).mjpeg
    recordmjpeg --output $filename &
    sleep 15m
    pkill recordmjpeg
done

```

The ampersand after the recordmjpeg command puts the program in the background and allows the script to move on to the next command.

---

### Post by Hex on 2010-12-21
> **Freelance Physicist said:**
> You could use ```
pkill <program-name>
``` to kill the program by name instead of PID.

Will try it and post back, thank you!

---

### Post by daqron on 2010-12-30
> **Hex said:**
> I'm recording a stream from an IP camera. ... I'd like to separate it into 15 minute long segments.

What's the best way to start and stop the perl script every 15 minutes? I can't seem to find information on controlling external scripts.
Is this something you want to run constantly? If so, maybe cron is a better option. You could have cron kill the script every 15 mins, then start it again.

---

### Post by Hex on 2011-01-02
> **daqron said:**
> Is this something you want to run constantly? If so, maybe cron is a better option. You could have cron kill the script every 15 mins, then start it again.

If I only checked this topic earlier - just figured that one myself today and it's working great. Thanks for the idea :)

Thanks to all for the support!

---

### Post by ziekfiguur on 2011-01-03
> **Freelance Physicist said:**
> You could use ```
pkill <program-name>
``` to kill the program by name instead of PID.
I don't know if that's a good idea, as not all output from the script is guaranteed to be flushed if you kill it like that.

I think it would be best to make te perl-script write to a (named) pipe, and use another script to read from that pipe and segment the data in 15-minute blocks.

---

### Post by Hex on 2011-01-03
> **ziekfiguur said:**
> I don't know if that's a good idea, as not all output from the script is guaranteed to be flushed if you kill it like that.

I think it would be best to make te perl-script write to a (named) pipe, and use another script to read from that pipe and segment the data in 15-minute blocks.

It's an mjpeg stream, so it doesn't seem to be a problem. Thanks for the idea though.

---

