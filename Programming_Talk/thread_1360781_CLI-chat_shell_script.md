---
title: "CLI-chat shell script"
date: 2009-12-21
forum: Programming Talk
---

### Post by shark1997 on 2009-12-21
Hi all,
Today I made a shell script that allows people on different virtual terminals (ttys) to chat with each other
```
#!/bin/bash
$t = ""
echo "CLI Chat version 0.5 beta"
echo "Joining chat room..."
echo "" > /chat.txt
clear
echo "`whoami` at `tty` joined chat room" > who.txt
cat /chat.txt who.txt > chat.txt
cat chat.txt > /chat.txt
cat /chat.txt
echo "------------------------------------------------------------"
while [ 1 -eq 1 ] ; do
read chat
while [ $chat -eq $t ] ; do
clear
cat /chat.txt
echo "-------------------------------------------------------------"
read chat
done
echo $chat > 1.txt
clear
echo "From `whoami` at `tty`-" > who.txt
cat /chat.txt who.txt 1.txt > chat.txt
cat chat.txt > /chat.txt
cat /chat.txt
echo "-----------------------------------------------------------"
done

```
To use it, run gksudo nautilus and create an empty file called chat.txt in the root directory (/) . rename the script to cli-chat. and copy the script into /bin. and run make it executable by running chmod +x /bin/cli-chat
Run it like 
```

cli-chat

```

At the prompt, type in whatever you want to show up on the chat room and press enter
To refresh the chat room, press enter without typing anything

A fun way to test it is to log in as another user on a different terminal and chat with yourself

:)Hope you like it!:)

---

### Post by nvteighen on 2009-12-21
You better fix that chat.txt being placed at the root directory. Why not better place it in /tmp?

---

### Post by dwhitney67 on 2009-12-21
Or just use the 'talk' utility that is commonly available with most Linux distros.

---

### Post by shark1997 on 2009-12-23
Okay, i changed some stuff
 ```
#!/bin/bash
trap 'goodbye' 2
cd
chmod 777 who.txt
chmod 777 1.txt
chmod 777 chat.txt
t=""
leave="exit"
#function to be called if user presses Control-C or types 'exit'
goodbye()
{
	echo "Leaving Chat Room" > 1.txt
	clear
	echo "`whoami` at `tty` is LEAVING chat room" > who.txt
	cat /tmp/chat.txt who.txt > chat.txt
	cat chat.txt > /tmp/chat.txt
	cat /tmp/chat.txt
	clear
	exit
}
#intro
echo "CLI Chat version 1.1"
echo "Chat logs are stored in /tmp/chat.txt"
echo "Type 'exit' to leave chat room"
echo "To refresh your copy of chat logs, press enter without typing anything"
echo "To clear chat logs, run cli-clear"
echo "Press enter when ready to begin"
read enter
clear
echo "`whoami` at `tty` joined chat room" > who.txt
cat /tmp/chat.txt who.txt > chat.txt
cat chat.txt > /tmp/chat.txt
cat /tmp/chat.txt
echo "------------------------------------------------------------"
#sort of endless loop
while [ 1 -eq 1 ] ; do
	#reads chat input
	read chat
	#if user does not type anything, refreshes chat log
	while [ $chat = $t ] ; do
		clear
		cat /tmp/chat.txt
		echo "-------------------------------------------------------------"
		read chat
	done
	#if user enters exit
	while [ $chat = $leave ] ; do
		goodbye 
	done
	#finish and repeat loop 1
	echo $chat > 1.txt
	clear
	echo "From `whoami` at `tty`-" > who.txt
	cat /tmp/chat.txt who.txt 1.txt > chat.txt
	cat chat.txt > /tmp/chat.txt
	cat /tmp/chat.txt
	echo "-----------------------------------------------------------"
done

```
and also another script that goes along with it
```
#!/bin/bash
echo "Do you really want to clear chat logs? (Y/Ctrl-C)"
read response
if [ $response="Y" ]
then echo "" > /tmp/chat.txt
echo "Chat logs cleared"
exit
fi
exit
```

---

