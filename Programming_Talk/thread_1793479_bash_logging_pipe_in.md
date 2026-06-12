---
title: "bash logging pipe in"
date: 2011-06-29
forum: Programming Talk
---

### Post by ian dobson on 2011-06-29
Hi,

I'm not sure if this is the correct forum but here goes:-

I want to log the output from a programm to a log file, and am currectly using pipe redirection with 
program > logfile.log  2>&1 &

This works ok, but the program sometimes produces 1000's messages along the lines of "connection closed", this log can then get very large (3-6Mb). I've seen that linux has a tool "logger" that combines messages that are the same (last message repeated 5 times). But eveyrthing I've tried to get logger to log the pipein (from my program) to a log file (of my choice) just doesn't seem to work.

So is there a program that does what I want?

Regards
Ian Dobson

---

### Post by geirha on 2011-06-29
```
program 2>&1 | logger
```

You might want some options for the logger command. See **man logger**.

---

### Post by ian dobson on 2011-06-29
> **geirha said:**
> ```
program 2>&1 | logger
```

You might want some options for the logger command. See **man logger**.

I've already tried that/read the help text, it logs to the syslog and I want to log to a different file.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-06-30
Hi,

OK using logger -s it loggs to stderr as well as syslog, which is a start but it still dumps all messages to syslog which is not what I want.

Looks as if I have to write my own "mini logger". Afew 100 lines of c code should do it :D

Regards
Ian Dobson

---

### Post by ian dobson on 2011-07-01
Hi,

OK I gave up looking and wrote my own logger. I've fully tested the code but here it is

```
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

/*
 * logger -- read and log utility
 *
 *      Reads from an input and arranges to write the result stdout
 */
int
main()
{
        char  buf[2],line[1024],lastline[1024];
        int count = 1;
        /* log input line if appropriate */
        while (fgets(buf, sizeof(buf), stdin) != NULL) {
                strcat(line,buf);  /* Save the line */
                if ( strcmp("\n",buf ) == 0 )  { /* End of line */
                        if ( strcmp(lastline,line ) == 0 ) {  /* Line same as last */
                                count++;
                                memset(line, 0, sizeof(line)); /* Clean out variable */
                        } else {
                                if ( count != 1 ) {
                                        printf("last line repeated %d times\n",count );  /* Dump the number of repeats */
                                }
                                printf("%s",line);  /* Dump the line */
                                memcpy(lastline, line, sizeof(line));
                                memset(line, 0, sizeof(line)); /* Clean out variable */
                                count=1;
                        }
                }
        }
        if ( count != 1 ) {
                printf("%s",lastline);  /* Dump the line */
                printf("last line repeated %d times\n",count );  /* Dump the number of repeats */
        } else {
                printf("%s",line);  /* Dump the line */
        }
        exit(0);
}
```

All it does is read stdin, look at each line and suppress repeats. I've just tested it on a 13Mb log file and the output was only 3Kb, which is much easier to check.

The code is abit hacky but hay it mostly works.

Regards
Ian Dobson

---

### Post by emiller12345 on 2011-07-01
> **ian dobson said:**
> ```

```

if you know its just a few single items, you can grep -v them
```
program 2>&1 | grep -v "connection closed" | grep -v "another repeated match" > logfile.log &
```

---

### Post by ian dobson on 2011-07-01
Hi,

The program could and does repeat almost any message. It's not just connection refused. 

Using grep/shell scripts I'd need to "remember" what the last line was, if it's diffent dump it, if it's the same increment counter.

Regards
Ian Dobson

---

### Post by pafoo on 2011-07-01
I agree using the grep -v would be the best option. Because it seems you only have the "connection closed". Just put that into the grep argument. Once you run put that program in the background just run your tail -f logfile and make sure there isnt anything else showing up that you dont want.

Oops I missed your last post. If it is repeating multiple things, it would be easier to edit your first script and edit what it puts to output. Dont forget if you are running a certain command and dont want its output do > /dev/null 2>&1 IN the script, that will control what actually reaches stdout, stderr before you send it to a log

---

### Post by ian dobson on 2011-07-01
Hi,

As I don't actually know what messages could be repeated, a simple grep isn't enough, I need a state machine to remember what the last message was.

As the code only took me about 2hours to write, I'm happy with it.

Modifying the program that generates these logs would be the best solution, but it was written by an external company and they wanted 10K $ to "implement a complete logging solution", which my company won't pay.

The poor guy who has to control the logs is also happy, rather than scrolling through a 10Mb file, he only has to look at one page of text. We can also printout/attach the log to the batch records.

Regards
Ian Dobson

---

### Post by Arndt on 2011-07-01
> **ian dobson said:**
> Hi,

As I don't actually know what messages could be repeated, a simple grep isn't enough, I need a state machine to remember what the last message was.

As the code only took me about 2hours to write, I'm happy with it.

Modifying the program that generates these logs would be the best solution, but it was written by an external company and they wanted 10K $ to "implement a complete logging solution", which my company won't pay.

The poor guy who has to control the logs is also happy, rather than scrolling through a 10Mb file, he only has to look at one page of text. We can also printout/attach the log to the batch records.

Regards
Ian Dobson

I haven't looked too closely on your program and your requirements, but 'uniq' can also be used for suppressing adjacent identical lines.

---

### Post by ian dobson on 2011-07-01
> **Arndt said:**
> I haven't looked too closely on your program and your requirements, but 'uniq' can also be used for suppressing adjacent identical lines.

Hi,

Arndt,

Uniq almost does what I need, but as my boss has now given me the OK to spend abit of time working on the program/adding abit more code so that the output fit with the batchreport.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-07-02
Hi All,

Hacked around abit more yesterday and have added afew new functions, also fixed a small bug where the output buffer isn't flushed after each printf if the output is redirected to a file.

Regards
Ian Dobson

---

### Post by pafoo on 2011-07-03
Uniq never works properly until the text is sorted. So try using sort then pipe to Uniq.

---

### Post by ian dobson on 2011-07-04
> **pafoo said:**
> Uniq never works properly until the text is sorted. So try using sort then pipe to Uniq.

Sorting won't help me, I need the order that the messages are generated. I have a logger program based on the standard (sys)logger that does what I want.

Thanks anyway
Regards
Ian Dobson

---

### Post by geirha on 2011-07-04
Here's your logger command written in bash:
```

logger() {
    local prevline line count

    while IFS= read -r line; do
        if [[ $line = "$prevline" ]]; then
            ((count++))
        else
            if (( count > 0 )); then
                printf "last line repeated %d times\n" "$count"
            fi
            printf "%s\n" "$line"
            prevline=$line
            count=0
        fi
    done
    if (( count > 0 )); then
        printf "last line repeated %d times\n" "$count"
    fi
}

```

---

### Post by ian dobson on 2011-07-04
Hi geirha,

See my post #5, I've extended the c code abit and I'll dump it here when I'm finished.

Regards
Ian Dobson

---

