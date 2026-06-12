---
title: "Binding capslock key to a shell script."
date: 2012-02-18
forum: New to Ubuntu
---

### Post by slotlocker on 2012-02-18
Hello everyone! A linux newbie here! I own a netbook which doesn't have any indicator leds. So I decided to write a small shell script that would notify me when the capslock key is pressed. The script  goes something like this:

#!/bin/bash
state=$(xset -q | grep Caps | awk '{print $4}')
if [ "$state" = "on" ]
then
notify-send "Caplock :ON"
fi

Now I want to bind the script to the capslock key so that it gets executed everytime I press the key. But the keyboard shortcuts setting expects a key combination. Is it possible to bind just the capslock key??

Thanks in advance! :)

---

### Post by Krytarik on 2012-02-18
Please see this guide:

[http://www.webupd8.org/2011/01/get-caps-num-scroll-lock-keys-notifyosd.html](http://www.webupd8.org/2011/01/get-caps-num-scroll-lock-keys-notifyosd.html)

If you are not using Compiz as the window manager, at least the Indicator method should work (also includes notifications).

If you want to stick with your own script, I've pimped it up a bit :P ; simply remove the OFF part I've added if you only want a notification for the ON state:
```
#!/bin/bash
state=$(xset -q | grep Caps | awk '{print $4}')
if [ "$state" = "on" ]
then
    notify-send -i keyboard "Caps Lock" "ON"
else
    notify-send -i keyboard "Caps Lock" "OFF"
fi
```Regards.

---

### Post by slotlocker on 2012-02-19
Hey! Thanks! I have mutter as my window manager! I have the indicator-keylock on my Ubuntu install :) Was looking for something that would work on my newly installed fedora. I rewrote the script!

#!/bin/bash

loop()
{
	
	while [ "$(xset -q | grep Caps | awk '{print $4}')" = "off" ]
	do
	continue
	done
loop2
}

loop2()
{
	notify-send --hint=int:transient:1 "Capslock:On"
	while [ "$(xset -q | grep Caps | awk '{print $4}')" = "on" ]
	do
	continue
	done
	notify-send --hint=int:transient:1 "Capslock:Off"
loop
}

loop

Not the most efficient of ways but given that it uses around 60kb(indicator-keylock uses 1.4mb),pretty reasonable :)



Ah! Just as I was about to  make it a background process I realized it was eating away 4% of the cpu(4gb). Thats pathetic! I guess the only option left is to build from source the indicator-keylock!

---

### Post by JKyleOKC on 2012-02-19
If you insert "sleep 1" lines in front of each "continue" in your rewritten script, it will use a lot less CPU. If you don't mind a 2-second delay in response, make it "sleep 2" for even less CPU usage...

---

### Post by HermanAB on 2012-02-19
Howdy,

No need to re-invent the wheel - xbindkeys is the program for that.

---

### Post by slotlocker on 2012-02-20
JKyleOKC: Hey! that did the trick! Consumes a LOT less memory(and CPU). I will stick with this! :) 

HermanAB : That is one amazing program out there! But for unknown reasons part of the script doesn't run! 

#!/bin/bash
state=$(xset -q | grep Caps | awk '{print $4}')
if [ "$state" = "on" ]
then
notify-send --hint=int:transient:1 "Caplock :ON"
else
notify-send --hint=int:transient:1 "Caplock :OFF"
fi

I used xbindkeys to bind this code to the capslock key! But only the second part of the code works,i.e.I get only the "off" notification. I tried running it in verbose mode,,,there weren't any errors. 

Nevertheless, will be using this for many other scripts! :)


Lastly ,I found these forums to be more friendly and responsive when compared to the other ones out there!( I was infact ridiculed in few of them...you guys have been very patient) Thanks!:)

---

### Post by JKyleOKC on 2012-02-20
When you bound the script to the CapsLock key, did it still actually function to turn on the lock? I would expect that binding a key to a program would remove the key's original function; however it's been a long time since I made any use of it so I could be way off base here. If it never turned on the lock, then of course the first half of the script could never execute.

If you never want to turn it on at all, this would be a way to disable it (if my guess is correct).

The "sleep" lines cause the program to relinquish all resources for the number of seconds you tell it to sleep. The longer it sleeps, the less resources you will use over time. It's often needed inside of scripts, since the script lines execute much faster than one can physically type in a command...

---

