---
title: "I need a script"
date: 2008-10-17
forum: Programming Talk
---

### Post by deejay_wonder on 2008-10-17
Hi all

I do not have that much experience in programming but I need a script with a counter which counts down from 2 min and execute a command and then again count down (a loop)

Maybe a script that work in windows and use "run" to execute the command which is a simple text string.

Can anybody help?

---

### Post by mobilediesel on 2008-10-17
> **deejay_wonder said:**
> Hi all

I do not have that much experience in programming but I need a script with a counter which counts down from 2 min and execute a command and then again count down (a loop)

Maybe a script that work in windows and use "run" to execute the command which is a simple text string.

Can anybody help?

You can start with something like:
```

:start
sleep 120
*command*
goto start

```
":start" is a label for the "goto" command at the end.
The 120 after "sleep" is the number of seconds to wait.
"*command*" is whatever you are wanting to run.

---

### Post by deejay_wonder on 2008-10-17
Can you be more specific? How do I create and execute the scipt and what format?

---

### Post by LaRoza on 2008-10-17
> **deejay_wonder said:**
> Can you be more specific? How do I create and execute the scipt and what format?

Can you be more specific? What OS is this for?

---

### Post by deejay_wonder on 2008-10-17
It has to be both but if you can show me how to do in linux that would be great.

---

### Post by Rich78 on 2008-10-17
For Linux:

vi scriptname
Press I to insert data.

Type the example shown to you above.

Press Escape
Type :wq 
This will save the file and quit out of vi

Now you need to make your script executable.

Type chmod 755 scriptname

Then you can run your script by typing ./scriptname

For Windows I would suggest writing a batch file.  (ie *.bat).

---

### Post by deejay_wonder on 2008-10-17
some of it works - but when I execute the scipt it says

```
laptop:/home/stiven/Skrivebord# ./script 
./script: line 1: :start: command not found

** (galeon:6999): WARNING **: I could not load the bookmarks file, will load the default bookmarks from /usr/share/galeon/default-bookmarks.xbel.

** (galeon:6999): CRITICAL **: radio_group_set_from_value: assertion `action != NULL' failed
./script: line 4: goto: command not found
```

I have typed the script exactly as shown above

---

### Post by kpkeerthi on 2008-10-17
Post your script here so we can take a look

---

### Post by deejay_wonder on 2008-10-17
:start
galeon [www.something.com](www.something.com)
sleep 120
goto start

---

### Post by tukuyomi on 2008-10-17
> **deejay_wonder said:**
> Hi all
I do not have that much experience in programming but I need a script with a counter which counts down from 2 min and execute a command and then again count down (a loop)
For Windows, I have no idea, maybe the example shown above, saved as script.bat
For linux, use cron (already installed w/ Ubuntu) from a terminal type the command and edit a new line that reads:
```
~$crontab -e
#       m       h       dom     mon     dow     command
        */2     *       *       *       *       /home/username/command-you-want-to-execute

```
command-you-want-to-execute can be a command or an _executable_ (very important!) script* of your choice
under m, */2 means every 2 minutes but  you can write */5 or whatever you want
Ok, after viewing your next post, you can write a line that reads
```
        */2     *       *       *       *       galeon www.something.com
```

Hope it helps you a bit :)

---

### Post by deejay_wonder on 2008-10-17
thanks a lot :D 

How do I run this script? After editing crontab nothing happens

---

### Post by tukuyomi on 2008-10-17
> **deejay_wonder said:**
> thanks a lot :D 

How do I run this script? After editing crontab nothing happensWell, it doesn't run :/ as this...
What I did is to create a script in my userhome, called test. I wrote inside
```
#!/bin/bash

DISPLAY=:0 iceape www.google.com

exit 0
```
(Change iceape with galeon)
I saved it in /home/tukuyomi/test, and made it executable ```
~$ chmod +x /home/tukuyomi/test
```
After that, I edited my crontab (crontab -e) to write a line that reads:
```
	*/2	*	*	*	*	/home/tukuyomi/bin/test
```(saved it with CTRL+O, then CTRL+X). Crontab said then: ```
crontab: installing new crontab
```and that was working :)
(You can view it working -or at least look for errors- issuing the command ```
tail -f /var/log/syslog
```(Hit CTRL+C to stop tail updating))

---

### Post by deejay_wonder on 2008-10-17
I did exactly what you showed me. 

My script look like this
```
#!/bin/bash

DISPLAY=:0 firefox

exit 0

```

and my crontab look like this

```
# m     h     dom       mon     dow        command
  */4   *      *         *       *         /home/stiven/test

```
but it does not open firefox. 
here is my syslog

```

root@stiven-laptop:/home/stiven# tail -f /var/log/syslog
Oct 17 16:30:13 stiven-laptop crontab[12865]: (root) END EDIT (root)
Oct 17 16:31:01 stiven-laptop /usr/sbin/cron[5755]: (root) RELOAD (crontabs/root)
Oct 17 16:32:01 stiven-laptop /USR/SBIN/CRON[13006]: (root) CMD (/home/stiven/Skrivebord/script)
Oct 17 16:38:38 stiven-laptop crontab[13518]: (root) BEGIN EDIT (root)
Oct 17 16:39:02 stiven-laptop crontab[13518]: (root) REPLACE (root)
Oct 17 16:39:02 stiven-laptop crontab[13518]: (root) END EDIT (root)
Oct 17 16:40:01 stiven-laptop /usr/sbin/cron[5755]: (root) RELOAD (crontabs/root)
Oct 17 16:40:02 stiven-laptop /USR/SBIN/CRON[13601]: (root) CMD (/home/stiven/test)
Oct 17 16:40:41 stiven-laptop crontab[13642]: (root) BEGIN EDIT (root)
Oct 17 16:41:44 stiven-laptop crontab[13642]: (root) END EDIT (root)

```

I want the test to be executed every 2. minute - is this the right way?

---

### Post by ratmandall on 2008-10-17
> **deejay_wonder said:**
> I did exactly what you showed me. 

My script look like this
```
#!/bin/bash

DISPLAY=:0 firefox

exit 0

```

and my crontab look like this

```
# m     h     dom       mon     dow        command
  */4   *      *         *       *         /home/stiven/test

```
but it does not open firefox. 
here is my syslog

```

root@stiven-laptop:/home/stiven# tail -f /var/log/syslog
Oct 17 16:30:13 stiven-laptop crontab[12865]: (root) END EDIT (root)
Oct 17 16:31:01 stiven-laptop /usr/sbin/cron[5755]: (root) RELOAD (crontabs/root)
Oct 17 16:32:01 stiven-laptop /USR/SBIN/CRON[13006]: (root) CMD (/home/stiven/Skrivebord/script)
Oct 17 16:38:38 stiven-laptop crontab[13518]: (root) BEGIN EDIT (root)
Oct 17 16:39:02 stiven-laptop crontab[13518]: (root) REPLACE (root)
Oct 17 16:39:02 stiven-laptop crontab[13518]: (root) END EDIT (root)
Oct 17 16:40:01 stiven-laptop /usr/sbin/cron[5755]: (root) RELOAD (crontabs/root)
Oct 17 16:40:02 stiven-laptop /USR/SBIN/CRON[13601]: (root) CMD (/home/stiven/test)
Oct 17 16:40:41 stiven-laptop crontab[13642]: (root) BEGIN EDIT (root)
Oct 17 16:41:44 stiven-laptop crontab[13642]: (root) END EDIT (root)

```

I want the test to be executed every 2. minute - is this the right way?

eh it launches firefox for me try this
[php]
#!/bin/bash

firefox

exit 0
[/php]

---

### Post by deejay_wonder on 2008-10-17
After I did all this I ran /home/stiven/test

firefox opened but only once and nothing more happened.

Is it possible to make a script like

firefox
sleep 120
firefox
sleep 120 
etc.

and so on - I know it's not a loop

or is it me who misunderstands something :P

---

### Post by tukuyomi on 2008-10-17
> **deejay_wonder said:**
> After I did all this I ran /home/stiven/test

firefox opened but only once and nothing more happened.

Is it possible to make a script like

firefox
sleep 120
firefox
sleep 120 
etc.

and so on - I know it's not a loop

or is it me who misunderstands something :P
You can but it's a bit tricky, huh :p
```
#!/bin/bash

while [ 1 ]; do
	firefox;
	sleep 120;
done

echo 0;
```


ratmandall: Your script won't run under cron like this because $DISPLAY is not set. You can run it with a terminal because echo $DISPLAY returns :0.0.
Or is it me who is missing something?

---

### Post by tukuyomi on 2008-10-17
```
Oct 17 16:40:02 stiven-laptop /USR/SBIN/CRON[13601]: (root) CMD (/home/stiven/test)
```Why does your script is running on a root crontab o_O?
crontab -e doesn't require sudo or super-user at all.

---

### Post by mssever on 2008-10-17
> **tukuyomi said:**
> ratmandall: Your script won't run under cron like this because $DISPLAY is not set. You can run it with a terminal because echo $DISPLAY returns :0.0.
Or is it me who is missing something?
Sample code (a simplification of tukuyomi's): ```
#!/bin/bash
while true; do
    firefox
    sleep 120
done
```Also, you *can* run it from crontab, but you need to set the display. Some programs can take the display as an argument. I do that in a script to restart xscreensaver whenever it dies. This script is called by cron: ```
#!/bin/bash

p xscreensaver scott >/dev/null 2>&1
status=$?
if [ $status -ne 0 ]; then
  p gnome-screensaver scott >/dev/null 2>&1
  status=$?
fi
[ $status -ne 0 ] && **xscreensaver -display :0.0 &**
```If you can't use a display argument directly, you should be able to set the environment variable $DISPLAY.

The other thing is that if you need your script to work in both Windows and Linux, you'll either have to write and maintain two separate scripts or use a cross-platform language such as Python, Ruby, etc.

---

### Post by deejay_wonder on 2008-10-17
thanks everybody - now it works as it should.

One last thing - how do I put in a function that shutdowns firefox

it should be something like

```
#!/bin/bash
while true; do
    firefox
    sleep 10
    kill firefox
    sleep 110
done 
```

---

### Post by mssever on 2008-10-17
```
#!/bin/bash
while true; do
    firefox &
    sleep 10
    killall firefox
    sleep 110
done 
```

---

