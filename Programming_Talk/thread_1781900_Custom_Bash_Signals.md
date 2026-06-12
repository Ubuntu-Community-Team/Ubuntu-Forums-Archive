---
title: "Custom Bash Signals?"
date: 2011-06-14
forum: Programming Talk
---

### Post by impulse338 on 2011-06-14
Hi All!

    So i'm working on a very simple streaming app using netcat to stream music from my laptop to my desktop that is hooked up to bigger speakers. I know there is definitely a better way to do this but i'd like to be able to get this to work.

My server comp is running this script: (Laptop)


#!/bin/bash

 for f in *.mp3

 do pv "${f%.mp3}.mp3"| nc 127.0.0.1 7895

 read -p "press enter to stream next song"

 done
#######################################

While my client is running this (Desktop)

#!/bin/bash

 while [ 1 ]

      do nc -l -vvv 7895 | mpg123 -

 done
#######################################

    what i would like to do is be able to skip a song on the server side by hitting a key on the keyboard... similar to when you hit page up when using mplayer to skip to next song (really just 10 minutes ahead in know)

    Does anyone have any suggestions or just a direction to point me in? any help is most appreciated :) thanks in advance

---

### Post by amauk on 2011-06-14
First off, there are far better ways to go about doing this. There's a fair few client/server streaming apps for linux

But I fully understand if this is just a little project to see if you can do it ;)

When you say
"skip a song on the server side by hitting a key on the keyboard"
Do you mean a key-press on the client (desktop) or server (laptop)?

---

### Post by impulse338 on 2011-06-14
Thanks for understanding :)

and i meant on the laptop

---

### Post by amauk on 2011-06-14
Ok, that makes things a lot easier (communication is only one way)

You'll probably need to split the server-side script in two

One script just takes a file argument and streams it```
#!/bin/bash

# stream_file.sh

if [ -n "$1" ] && [ -f "$1"]; then
	pv "$1"| nc 127.0.0.1 7895
fi
```(this script is not run directly, instead it's called from the second script)

The second script (we'll call it the stream_server) does all the management, and just sits in the background responding to triggers

The stream_server has a list of files, and fires off instances of stream_file in sequence
When one stream_file exits, the stream_server fires off another instance with the next file as an argument```
#!/bin/bash

# stream_server.sh

# Temp list for debugging only
# Proper file list can be fed into script later
FILE_LIST="foo.mp3
bar.mp3
baz.mp3"

# Change input separator to newline only
# Allows for easy handling of spaces in filenames
IFS=$'\n'

STREAM_PID=""

for FILE in $FILE_LIST; do

	# appending & means process is run in the background
	./stream_file.sh "$FILE" &

	Store PID of backgrounded stream_file.sh
	STREAM_PID=$!

	# halt execution until background stream_file.sh exits
	wait $STREAM_PID
done
```


Now, for getting stream_server to respond to user input, you'll probably have to use process signals
You can trap signals in Bash, and execute functions when a signal is received

Great resource for trapping and using signals in Bash
[http://www.kahealani.com/linux/bin/signals.txt](http://www.kahealani.com/linux/bin/signals.txt)


So, pick a signal for song skipping, and trap it in the stream_server
When signal received, fire off a function that kills $STREAM_PID
Result is that stream_server resumes executing the FILE_LIST loop, and next file is streamed


Problems:

stream_file blindly sends data to client as fast as it can. You'll find that stream_file sends the file to the client much quicker than the client plays it

So, skipping a song, while technically working, won't make for an instantaneous change on the client
(in fact, the client probably has the rest of the file, and the next two!, queued up in it's buffer)

So, some sort of bandwidth throttling may be needed on the server, to ensure that the server does not send the client 5 songs-worth of data before the first song has even got to the chorus

Never really used it, but check out the "tc" command-line program for specifying a max. kbps bandwidth

Anyway, good luck

---

### Post by impulse338 on 2011-06-14
Awesome. this is exactly what i was looking for. thank you for your help!!!

---

### Post by amauk on 2011-06-14
> **impulse338 said:**
> Awesome. this is exactly what i was looking for. thank you for your help!!!no probs

---

