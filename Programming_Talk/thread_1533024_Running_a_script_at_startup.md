---
title: "Running a script at startup"
date: 2010-07-17
forum: Programming Talk
---

### Post by PaulM1985 on 2010-07-17
Hi

I have written a script (part of a thread posted today) that I want to run at startup.  I have tried adding it to System>Preferences>Startup Applications but in the command section I have tried both:

./path/to/script.sh

and

/path/to/script.sh

and neither seem to be executed.

I have already run chmod to make it executable and it runs fine from command line.  I have seen various methods of adding a startup script but I thought this would have been the standard way to do it.  Is there a standard way?

Paul

---

### Post by pastalavista on 2010-07-17
Have you tried ```
sh /path/to/script
or
bash /path/to/script
```

---

### Post by ju2wheels on 2010-07-17
Make sure that all application calls and file paths are absolute and not relative.

[Edit] Sorry answered to quick. Edit /etc/rc.local and execute your script from within that one.

---

### Post by PaulM1985 on 2010-07-17
> **pastalavista said:**
> Have you tried ```
sh /path/to/script
or
bash /path/to/script
```

This didn't seem to work.  By adding sh before it the sh kept getting removed on save.  By putting the whole thing in quotes it still didn't work.

@ju2wheels
Do I just add the absolute filepath call to my script in this file.

Paul

---

### Post by ju2wheels on 2010-07-17
> **PaulM1985 said:**
> 
@ju2wheels
Do I just add the absolute filepath call to my script in this file.

Paul

Yes, be sure to add the extension as well if your file has one...

---

### Post by soltanis on 2010-07-17
Add an entry to run the script into /etc/rc.local and make sure that file is set to executable. You can also tell the script to run by using the "[@reboot]("http://www.cyberciti.biz/faq/linux-execute-cron-job-after-system-reboot/")" directive of **cron** (use crontab -e to edit your crontab).

---

### Post by Zorgoth on 2010-07-17
What do you mean by "startup?"

If you want to run as user at login, Startup Applications is the best way and you should try to figure out why it doesn't work.

If you want to run as root at login, put in in an executable script called /etc/gdm/PostLogin/Default or /etc/gdm/PreSession/Default (in GNOME).

If you want to run it as root at boot, put it in rc.local.

---

### Post by PaulM1985 on 2010-07-18
> 
What do you mean by "startup?"

If you want to run as user at login, Startup Applications is the best way and you should try to figure out why it doesn't work.

If you want to run as root at login, put in in an executable script called /etc/gdm/PostLogin/Default or /etc/gdm/PreSession/Default (in GNOME).

If you want to run it as root at boot, put it in rc.local.


I want to run it at login.  The computer will automatically login onto my user, then I want my script to run which waits for an internet connection to become available and then start my media player program.

---

### Post by PaulM1985 on 2010-07-18
Ok.  I think I am getting nearer to why it is not working.  Below is a copy of my script:

```

NET_CONNECTED=0

function TestConnection {
	WGET="/usr/bin/wget"

	$WGET -q --tries=10 --timeout=5 http://www.google.com -O /tmp/index.google &> /dev/null
	if [ ! -s /tmp/index.google ];then
		let NET_CONNECTED=0
	else
		let NET_CONNECTED=1
	fi
}

# keep looping while waiting for internet to connect
while [ "$NET_CONNECTED" -ne 1 ]
do
	TestConnection
done

echo "Got connection"

# start mediaplayer
./Client-Xine/Client&

# keep polling for wiimote connection
while true;
do
	wminput -c ir_ptr
done

```

This works when I run ./startup.sh from terminal.  I thought that maybe startup applications would only run compiled executables, so I created the following executable file:

startupProg.c:
```


int main()
{
	system("./startup.sh");
	return 0;
}

```

which is just to call the script.  Running this at command line gave these errors:

```

paul@mediacenter:~$ ./startupProg
./startup.sh: 3: function: not found
./startup.sh: 11: let: not found
./startup.sh: 12: Syntax error: "}" unexpected

```

Is it possible that some things have not been defined and that is why this is not working at login?

Paul

---

### Post by PaulM1985 on 2010-07-18
@pastalavista
I didn't try bash, I just used sh.  Bash worked.

Thanks.
Paul

---

### Post by Zorgoth on 2010-07-18
Try making a simpler script and testing if you can run that, to help identify the problem; for example make a script which just starts firefox or something.

---

### Post by Zorgoth on 2010-07-18
I know you've solved your problem, but did you have #!/bin/bash at the beginning?

---

### Post by PaulM1985 on 2010-07-18
No I didn't.

I thought everything after a "#" was ignored and that it was a comment character.  This is the first time I have ever used scripting on linux so I don't know too much.  Just enough to get what I wanted done (with some help from the people on this forum).

---

### Post by lkjoel on 2010-07-18
> **PaulM1985 said:**
> Ok.  I think I am getting nearer to why it is not working.  Below is a copy of my script:

```

NET_CONNECTED=0

TestConnection**()** {
**# instead of function TestConnection**
    **#** WGET="/usr/bin/wget"

    **wget** -q --tries=10 --timeout=5 http://www.google.com -O /tmp/index.google &> /dev/null
    if [ ! -s /tmp/index.google ];then
        **export** NET_CONNECTED=0
    else
        **export** NET_CONNECTED=1
    fi
}

# keep looping while waiting for internet to connect
while [ "$NET_CONNECTED" -ne 1 ]
do
    TestConnection
done

echo "Got connection"

# start mediaplayer
./Client-Xine/Client&

# keep polling for wiimote connection
while true;
do
    wminput -c ir_ptr
done

```This works when I run ./startup.sh from terminal.  I thought that maybe startup applications would only run compiled executables, so I created the following executable file:

startupProg.c:
```


int main()
{
    system("./startup.sh");
    return 0;
}

```which is just to call the script.  Running this at command line gave these errors:

```

paul@mediacenter:~$ ./startupProg
./startup.sh: 3: function: not found
./startup.sh: 11: let: not found
./startup.sh: 12: Syntax error: "}" unexpected

```Is it possible that some things have not been defined and that is why this is not working at login?

Paul
Check the changes I did to your file.

---

