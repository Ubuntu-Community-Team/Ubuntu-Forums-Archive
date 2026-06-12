---
title: "Calling programs from scripts"
date: 2010-07-17
forum: Programming Talk
---

### Post by PaulM1985 on 2010-07-17
Hi

I want to create a script which will run on startup.  So I plan on putting it in System>Preferences>Startup Applications.

The aim of this script is to start up a media player and then start up the wminput service so I can connect my Wiimote.  The call to wminput should be in an infinite loop so that if wminput loses connection, it will restart so that I can reconnect.

In this I have two things. I want the script to call the media player to start it, then I want the call to wminput to be a blocking call so that in the while loop it waits for this to return before trying to start it.  I don't know if calls to scripts and other programs are blocking calls or not.

I was hoping to have something like:

```

# Start media player
./mediaplayer

# keep trying to register for wiimote
while true; do
    wminput -c ir_ptr
done

```

With the blocking problem, if all calls are non blocking then I could end up running infinite(ish) instances of wminput, and if they are blocking then I will only run my player and not get to register the remote.

Also, by adding scripts to startup applications, do they run sequencially, because my while loop could hold it in there.

I did a quick bit of googling and couldn't find anything obvious, plus I am quite new to bash.

Any help, tips, web links etc would be of great help.

Thanks

Paul

---

### Post by dv3500ea on 2010-07-17
You could run the media player in the background by appending ' &' to the line with the media player command (without the quotes). 
[FONT=monospace]wminput would still be blocking.[/FONT]

---

### Post by PaulM1985 on 2010-07-17
So what you are saying is that I would have:

```

# Start media player
./mediaplayer&

# keep trying to register for wiimote
while true; do
    wminput -c ir_ptr
done

```

?

---

### Post by PaulM1985 on 2010-07-17
Answer to my last question was yes.  Found out doing a simple test using this (if anyone wanted an example):

test1.sh:
```

# just say hello
echo "Hello"

```

test2.sh
```

# loop numbers 1 - 10
i="1"
while [ $i -lt 11 ]
do
	echo "i is " $i
	i=$[$i + 1]
done

```

runner.sh
```


# run test1
./test1.sh

# run test2 blocking
i="0"
while [ $i -lt 4 ]
do
	./test2.sh&
	i=$[$i + 1]
done

```

By having the & on the end of the calls to test2 they are non-blocking. Removing the & makes them blocking calls.

Thanks dv3500ea

Paul

---

### Post by trent.josephsen on 2010-07-17
Convention puts a space between the end of the line and the &

```
./test1.sh &
```

Syntactically it doesn't matter, but IMO it's easier to read when spaced out.

---

