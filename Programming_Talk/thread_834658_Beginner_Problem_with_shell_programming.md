---
title: "Beginner Problem with shell programming"
date: 2008-06-19
forum: Programming Talk
---

### Post by shankhs on 2008-06-19
I am a newbie to shell programming...(and I guess I am posting at the right forum)
I wrote this program which uses echo with CSI(Command Sequence Introduction).This prog toggle the state of LEDs in keyboard.
here is my program:
```

#!/bin/bash
#testing \033[xq to toggle LEDs in keyboard

echo -e "\033[0q Turning all kbd -LED off"
echo "***Press ctrl+c to break"

while [ 1 ]
do

	echo -e "\033[1q Just look at the scroll key"
	sleep 1
	
	echo -e "\033[2q Just look at the Num key"
	sleep 1

	echo -e "\033[3q Just look at the caps key"
	sleep 1
done

```
and output is no blinking of LEDs:(
```

[0q Turning all kbd -LED lights off
* * * Press CTRL + C to stop
[1q Scroll On Other Off
[2q Num On Other Off
[3q Caps On Other Off
[1q Scroll On Other Off
[2q Num On Other Off
[3q Caps On Other Off

```

PLZ help me!!!!

---

### Post by HalPomeranz on 2008-06-19
Your problem is that those codes don't work in a typical X terminal window.  If you use Ctrl-Alt-F1 and run your program on the text console, the LEDs will light up like you expect (Ctrl-Alt-F7 to return to your X session).

---

### Post by reality1011 on 2008-06-20
> **HalPomeranz said:**
> Your problem is that those codes don't work in a typical X terminal window.  If you use Ctrl-Alt-F1 and run your program on the text console, the LEDs will light up like you expect (Ctrl-Alt-F7 to return to your X session).

FYI if you press Ctrl-Alt-F! then press CTRL-ALT-F7 to come back to normal screen

---

