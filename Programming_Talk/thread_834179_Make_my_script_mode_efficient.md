---
title: "Make my script mode efficient"
date: 2008-06-19
forum: Programming Talk
---

### Post by DAC1138 on 2008-06-19
This is my first (useful) BASH script I have written. I'm in the process of learning to write BASH scripts and wrote this for fun.

I don't have a specific question. I just wanted to know if there was any better way to write this program. Are there more efficient ways of doing some of the things I have done? Please feel free point them out.

I do know already that my "newline" isn't very efficient. My empty quotes, I mean. I tried using \n but the only thing that did was put a lone n in the sentence.

```

#!/bin/bash

script_name="DVcapture"

sudo modprobe raw1394
sudo modprobe dv1394

# Check of DVgrab is installed
if [ -e "/usr/bin/dvgrab" ]; then # test to see if DVgrab exists in /usr/bin
	echo " "	
	echo "DVgrab installed"
else
	echo " "		
	read -p "You do not have DVgrab installed. Install it now? (y/n)?"	
		if [ "$REPLY" = "yes" ]; then
			sudo apt-get install dvgrab
  		else
			cancel			
		fi
fi

# Changes permission for normal user access
sudo chmod a+rw /dev/raw1394 /dev/dv1394

echo " "
echo "=================================="
echo "Press C to start capturing video"
echo "Press Esc to stop capturing video"
echo "Press Q to quit dvgrab"
echo "=================================="
echo " "

# Run dvgrab with the following parameters
dvgrab --interactive --noavc --a --timecode --format raw


```

---

### Post by geirha on 2008-06-19
> **DAC1138 said:**
> 
I do know already that my "newline" isn't very efficient. My empty quotes, I mean. I tried using \n but the only thing that did was put a lone n in the sentence.


I doubt there's much difference in using \n instead of an empty echo (You don't need the space " " btw, just «echo»), but «echo -e» will accept \n as newline.

On the code itself:

You set script_name="DVcapture", which is fine and all, but you're not using it for anything, so why set it?

When you prompt the user if he wants to install dvgrab, you give the user the option of typing "y" or "n", but you check for "yes". Might confuse the user a bit ...

And in the else-clause, you are running the "cancel" command. This command cancels print jobs, you may want to do something like "exit 0" instead.

The following line raised some flags.
```
sudo chmod a+rw /dev/raw1394 /dev/dv1394
```
You are giving everyone write access to these devices. This might be harmless, but it's unnecessary. I looked through the udev-rules for these devices, and found this comment along with them (/etc/udev/rules.d/40-permissions.rules):
```

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",          GROUP="disk"
KERNEL=="dv1394*",          GROUP="video"
KERNEL=="video1394*",           GROUP="video"

```
So in this particular case it seems like a bad idea, so it's better to check if the user is a member of the needed groups, disk and video in this case.
Something like this maybe: 
[php]
if ! groups | grep -qw 'video' ; then
  echo "You need to be a member of the video group."
  exit 1
fi
if ! groups | grep -qw 'disk' ; then
  echo "You need to be a member of the disk group."
  exit 1
fi
[/php]

---

### Post by DAC1138 on 2008-06-19
> **geirha said:**
> 
The following line raised some flags.
```
sudo chmod a+rw /dev/raw1394 /dev/dv1394
```
You are giving everyone write access to these devices. This might be harmless, but it's unnecessary. I looked through the udev-rules for these devices, and found this comment along with them (/etc/udev/rules.d/40-permissions.rules):


That's actually one of the only methods to get kino/dvgrab working for a normal user. There's maybe one other way, but this is the most common solution people offer on the message boards for getting kino to capture for a normal user. Otherwise you'd have to run as a superuser. The other method would be the way you pointed out, but I figured if there's only one user on the machine, what difference does it make? I'll play around with adding users to groups within the script.

I didn't know cancel was the canceling print jobs. I was under the impression it canceled anything after that statement, just like "exit 0". Thanks for the input.

And for the script_name, I was taught by my friend to add it just in case. He said it never hurts, but can be useful if you need it later and forget to add it. It just becomes good habbit.

-edit-
I'm trying to capture the current user in the following statement:
```

sudo usermod -G disk `whois`

```

`whois` should be replaced by the command that gets the current user, but I don't know what command that is.

---

### Post by geirha on 2008-06-20
> **DAC1138 said:**
> 
-edit-
I'm trying to capture the current user in the following statement:
```

sudo usermod -G disk `whois`

```

`whois` should be replaced by the command that gets the current user, but I don't know what command that is.

You got the `whoami` command, but the variable $USER should contain the username already. It's also better to use the adduser and addgroup commands, which are a bit more friendly than the old `echo {user,group}{add,del,mod}` commands

```
sudo adduser $USER disk
```

---

### Post by DAC1138 on 2008-06-20
Ah, so $USER is already defined by default? Cool, I was never informed of this. None of the docs I've read covered $USERS (yet)

---

### Post by rikxik on 2008-06-20
> Ah, so $USER is already defined by default? Cool, I was never informed of this. None of the docs I've read covered $USERS (yet) 

Just run "set" command at the unix/linux prompt - it will give you very interesting information on various variables that are available to a user.

---

### Post by DAC1138 on 2008-06-20
Wow. I originally wrote this to be a basic DV capture program for people to use on Ubuntu and other linux distros having problems with kino. As I add onto the code I see more areas I could improve on. One area is checking if a user is in the disk/video group. I'm stuck at this and have not come up with anything from Google.

What I want to do now is check if the user is a member of the disk/video group. So far, I have

```

if grep $USER /etc/group != $USER; then

```

But I know this is off. I want it to do the following: If $USER is not found in the disk group of /etc/group, then..."

I'm going off the guide from the Linux Documentation Project and I can't find a section talking about grep and probing documents for text.

Can someone point me in the right direction of what I should be googling for or what I should look for? I don't want you guys to solve my problems for me, just point me in the right direction.

Thanks for all the help.

---

### Post by geirha on 2008-06-20
Parsing the output of the groups command is easier imo, but this regex should do the job. Do note that you need to log out and back in again for group-membership to be recognized.
[php]
if grep -q "^disk:.*\<$USER\>" /etc/group; then
  echo "member of the disk group"
else
  echo "not a member of the disk group"
fi
[/php]

---

### Post by DAC1138 on 2008-06-20
```
 if grep -q "^disk:.*\<$USER\>" /etc/group; then 
```

what does the ^ and the :.*\ do for that statement?

I can understand the statement does the following:
run grep with -quiet parameter, and scan /etc/group for (^ what's this?) the disk group...(what's the :.*\  ?)

---

### Post by geirha on 2008-06-20
> **DAC1138 said:**
> ```
 if grep -q "^disk:.*\<$USER\>" /etc/group; then 
```

what does the ^ and the :.*\ do for that statement?

I can understand the statement does the following:
run grep with -quiet parameter, and scan /etc/group for (^ what's this?) the disk group...(what's the :.*\  ?)

^ matches the start of the line ($ matches the end of the line), so for example "disk:" will match, but not "fdisk:".

disk: matches the literal "disk:"

. matches any character, and with the * behind it, .* matches zero or more characters.

Check out [http://www.regular-expressions.info/](http://www.regular-expressions.info/) for a nice tutorial on regular expressions.

---

