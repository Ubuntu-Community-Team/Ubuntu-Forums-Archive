---
title: "lubuntu/ubuntu usb headphones"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by seal308 on 2013-01-09
Hello,

I have installed lubuntu onto my computer.
I can hear music using speakers connected to my computer using a green speaker jack.
However my USB headphones is not working.
I installed pulseAudio, however I can't seem to find a way to get the usb headphones working.
They are logitech headphones. 

Can someone please help

---

### Post by seal308 on 2013-01-09
Hello again.
I have made some progress.
I noticed that I had 3 output devices in pulse audio.
I realized the one for my headphones did not look like sound was coming through. However sound was coming through for another output device.
I figured out that it's because i had problem with the default output device.
In terminal I put the commands:
pacmd list-sinks to list all the sinks.
There were 3 indexes that represented 3 sinks.
Then i set the default link by putting in the following command:
pacmd set-default-sink 10

The problem I have now is that whenever I remove the usb headset then put the headset back into the computer. The index keeps changing. Therefore whenever I put in the headphone i have to reset the default sink in terminal.

[B]I know there is some sort of script out there. However I don't know how to use or make a script. Can someone help with this?

Also the sound is really bad in comparison to use when I was running ubuntu. It's all cracky and distorted, can someone help with this?[/B]

Thanks

---

### Post by seal308 on 2013-01-09
The figured out how to not have to go to terminal each time. 
I just had to press the green check box in volume control.
It wasn't working before, that's why I had to use the terminal.

However I am still looking for some sort of script that will automatically make the usb the default when I plug it in.

Also the sound is still really bad.

---

### Post by seal308 on 2013-01-09
Ok so I figured out how to fix the cracky/box sounding headphones.
All I had to do was reboot the computer.

However I am still looking for a script now or some other alternative.

Please help

---

### Post by seal308 on 2013-01-09
bump

---

### Post by Bölvaður on 2013-01-09
do you always do

```
pacmd set-default-sink 10
```or does that number vary?

A script is going to do exactly the same as you are doing already.


I don't know how to the syntax so here are the parts of the script you'll need.

execute  ```
pacmd list-sinks
```then match the output of that to a string (name of the headphone or something)
Store that number.

Then execute:
```
pacmd set-default-sink **<stored number>**
```


When you got that in a file make it executable and place the path to that file in a progran named "Startup Applications" (aka gnome-session-properties if you execute it from command line).
It's uglier, but you can also place a bash script instead of a path of an executable file in there.

---

### Post by seal308 on 2013-01-09
yes,

the number keeps changing.
So even if i write in the script with the number I match it too it will change every time so would i have to rewrite the script each time?

---

### Post by Bölvaður on 2013-01-11
> **seal308 said:**
> So even if i write in the script with the number I match it too it will change every time so would i have to rewrite the script each time?

no that's why you need this middle part where you check(or pull out) the number.

When you have it like that you never have to change the script.

I would have to know  BASH in order to make this script. I do not, but if you are interested in making it, it wont take more than a day to learn to do I assume.

---

### Post by dannyboy79 on 2013-01-11
look into udev rules, you can make a usb device being plugged in always be the same device based on unique identifiers of the lsusb info. just google it

---

