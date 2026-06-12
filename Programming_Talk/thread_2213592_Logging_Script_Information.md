---
title: "Logging Script Information"
date: 2014-03-27
forum: Programming Talk
---

### Post by Ackis on 2014-03-27
I have various scripts that are basically wrappers to add header information so it makes it easier to parse the output when I redirect the output to a file.

This is an example:

```
#!/bin/bash

echo ""
echo -e "*************************************************"
echo -e "*                                              *"
echo -e "*              Speed Test                      *"
echo -e "*              $(date +%r)                     *"
echo -e "*              $(date +%m-%d-%Y)                       *"
echo -e "*                                              *"
echo -e "*************************************************"
echo ""
/opt/speedtest/speedtest-cli
echo ""

```

Nothing special.  I basically run that script with something like:

```
scriptname >> foo.log
```

Is there a standard way to do this compared to what I'm doing?

---

### Post by Dave_L on 2014-03-28
I'm not sure what you mean by "makes it easier to parse the output".

My approach would probably be to provide separate functions for displaying header info and labels, and for displaying the content. That would reduce the need for duplicating code. It also might be easier to use a language like Perl, PHP or Python instead of a shell script.

---

### Post by Ackis on 2014-03-28
> **Dave_L said:**
> I'm not sure what you mean by "makes it easier to parse the output".

When I do a standard redirect into a log file information such as the date/time isn't generally included.  When I use that psuedo ascii art header it allows me to differentiate between executions of the script.

> **Dave_L said:**
> 
My approach would probably be to provide separate functions for displaying header info and labels, and for displaying the content. That would reduce the need for duplicating code. It also might be easier to use a language like Perl, PHP or Python instead of a shell script.

I didn't even think of that, and I should have.  Shows you what happens when you're looking at the smaller picture.

---

### Post by Bucky Ball on 2014-03-28
*Thread moved to **Programming Talk**.*

---

### Post by Vaphell on 2014-03-28
If the tool you use doesn't provide relevant header information in its own output then *wrapper_script >> log.txt* is as simple as it can get.

---

### Post by Ackis on 2014-05-21
I just wanted to follow up on the solution that I ended up using.

```

#!/bin/bash


WIDTH=49


if [[ -z $1 ]]; then
        echo "No argument supplied."
        exit 1
fi


printf "$1\n$(date +%r)\n$(date +%m-%d-%Y)" | boxes -d simple -p v1 -a c -s $WIDTH
echo ""

```

I threw it in a script so I can call it form other scripts and if I choose to update it at any point in time it'll update everything.

It aligns properly in my log files such as:

```

#!/bin/bash


logfile=/var/log/speedtest/speedtest.log
email=e-mail@foo.bar
exec > $logfile 2>&1


/opt/scripts/scriptheader.sh "Speedtest"


/opt/speedtest/speedtest-cli


if [[ -f ${logfile} ]]; then
        echo "Mailing log to ${email}"
        mail -s "Speedtest Log - $(date +%m-%d-%Y)" ${email} < ${logfile}
fi



```

However in e-mail/forum posts the *'s don't align when using different fonts (I know why, just can't remember the terminology).

```

*************************************************
*                                               *
*                   Speedtest                   *
*                  10:30:59 PM                  *
*                  05-20-2014                   *
*                                               *
*************************************************

```

*************************************************
*                                               *
*                   Speedtest                   *
*                  10:30:59 PM                  *
*                  05-20-2014                   *
*                                               *
*************************************************

---

### Post by ofnuts on 2014-05-21
Th terminology you are looking for is "monospaced" or "fixed-pitch" font.

---

