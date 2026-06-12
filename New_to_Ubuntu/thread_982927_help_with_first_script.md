---
title: "help with first script"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by oz-sco on 2008-11-15
Can anyone help me with my first script file? 
I have an annoying issue with my wlan light flashing, and found this script which is supposed to switch it off.
So i copied the script into gedit:

#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
	for dir in /sys/class/leds/iwl-phy*X; do
		echo none > $dir/trigger
	done
fi


Saved the file as iwl-no-blink.bash, now i need to make this executable, something to do with chmod? and move it from my desktop to etc/network/if-up.d$ tried to copy and paste, but denied.

I'm a user of OS, i don't really bother with this under the bonnet kind of stuff, so assume i know nothing :)

cheers Oz

---

### Post by pofigster on 2008-11-15
to change permissions:
```
cd Desktop
chmod 777 iwl-no-blink.bash
```
Where you can change 777 based on what permissions you want to give it (777 is read/write/execute all).  The other (simpler) option for making it executable is to right click on the file, select Properties and under Permissions, select "Make Executable"

to copy the file (from command line):
```
sudo cp ~/Desktop/iwl-no-blink.bash /etc/network/if-up.d
```
PLEASE NOTE - the above code will rename the file to if-up.d - if, rather, if-up.d is a directory and you want your script inside that directory type:
```
sudo cp ~/Desktop/iwl-no-blink.bash /etc/network/if-up.d/iwl-no-blink.bash
```
because the cp command takes two parts - the first is the source file and the second is the destination file.

Hope this helps!

---

### Post by jmmL on 2008-11-15
Okay, well the first part is easy enough. To make the file executable you need to run this command:
```
sudo chmod +x ~/Desktop/iwl-no-blink.bash
```

That command assumes that the script is on your desktop.

Now, it sounds like you want to move the script to /etc/network/if-up.d

So, this command should work:
```
sudo mv ~/Desktop/iwl-no-blink.bash /etc/network/if-up.d/
```

I think it should retain its executable permissions after the move. If it doesn't work, then post the link to the thread/site where you're getting the info from, and maybe we'll be able to help you some more.

---

### Post by oz-sco on 2008-11-15
@ Pofigster JmmL, 

Nice one guys, that's it working :) my wlan light is fixed, and i've pleased to say i've run my first linux script file with your help :)

What wasn't obvious to me, was where and how to run the chmod command.. I was trying to put it in the script, but thanks guys, i now understand how its just changing the file, and what it does.

Nice one on file move, i keep forgetting the sudo command :(

cheers Oz

---

### Post by pofigster on 2008-11-15
Glad to hear it worked!

Everybody runs into little stumbling blocks that eventually become learning moments.  I know it's happened to me more times than I can remember.

---

### Post by oz-sco on 2008-11-15
yes indeed, still learning :)

Light sort of fixed.. its only flashing now when its moving data.. So its an improvement over constant flickering.. I could still do with it not flashing at all.
But now at least i have a little big of a clue how scripts work, which is the main thing 

cheers Oz

---

