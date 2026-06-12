---
title: "script for opening web page automatically several times"
date: 2008-07-23
forum: Programming Talk
---

### Post by Mia_tech on 2008-07-23
this is for testing and is in a save environment.. anyway I'm looking for command or script that would allow me to visit a web page like 5 times in a row, and then close, I tried lynx, and links, but they are text base browser and some things on the web page won't execute correctly like some java/html code.... so I decided to do something with firefox, and make it automatically and came with this little script it works, the only problem is that it waits for user input; like it waits for me to close the browser and then it moves to the next instruction...I would like to open pages x amount of times and each in a separate tab...I looked at firefox help but I couldn't find any commands for opening in different tabs, if anyone has a better idea, they are welcome...
here's the script...
```
A=0

while [ $A -le 5 ] ; do firefox http://website.com
count=`expr $A + 1`

done

killall firefox

exit
```

thanks

---

### Post by LaRoza on 2008-07-23
> **Mia_tech said:**
> this is for testing and is in a save environment.. anyway I'm looking for command or script that would allow me to visit a web page like 5 times in a row, and then close, I tried lynx, and links, but they are text base browser and some things on the web page won't execute correctly like some java/html code.... so I decided to do something with firefox, and make it automatically and came with this little script it works, the only problem is that it waits for user input; like it waits for me to close the browser and then it moves to the next instruction...I would like to open pages x amount of times and each in a separate tab...I looked at firefox help but I couldn't find any commands for opening in different tabs, if anyone has a better idea, they are welcome...
here's the script...

Run it in the background with a &.

---

### Post by Can+~ on 2008-07-23
Must be bash?

[PHP]#!/usr/bin/env python
import webbrowser

for i in xrange(5):
    webbrowser.open_new_tab("http://www.google.com")[/PHP]

---

### Post by Mia_tech on 2008-07-23
LaRosa, I'm not much of a programmer, so I will ask, isn't the "&" command to concatenate two or more commands... how could I insert that into my script?

thanks

---

### Post by LaRoza on 2008-07-23
> **Mia_tech said:**
> LaRosa, I'm not much of a programmer, so I will ask, isn't the "&" command to concatenate two or more commands... how could I insert that into my script?

thanks

Run this:

```

firefox &

```

And you'll see.

&& is what you are thinking. They are not the same.

---

### Post by thschiavo on 2008-07-23
I had some problems dealing with java when using twill in Python. Is there anyway to deal with java, like "send scrap" in Orkut site?

---

### Post by Mia_tech on 2008-07-23
I tried this ```
firefox & www.website.com
``` and didn't work it kept looping forever until it crashed.. not sure if it was the & or the piece of code I'm using...I'll keep searching

---

### Post by nanotube on 2008-07-23
> **Mia_tech said:**
> I tried this ```
firefox & www.website.com
``` and didn't work it kept looping forever until it crashed.. not sure if it was the & or the piece of code I'm using...I'll keep searching

& goes on the end of the line.
```
firefox www.website.com &
```

---

### Post by Portmanteaufu on 2008-07-24
The & tells the shell that the process can be run in the background. It will begin to execute whichever command you've given it, then immediately return control of the shell to you while the process is being finished behind the scenes.

---

### Post by Mia_tech on 2008-07-25
> **nanotube said:**
> & goes on the end of the line.
```
firefox www.website.com &
```

I just used it like that and is looping forever... I think there's something wrong with the while condition [ $A -le 5 ] or it could be the counter is not executing count=`expr $A + 1`

any help appreciated

thanks

---

### Post by dexter.deepak on 2008-07-25
try this :
```
A=0

while [ $A -le 5 ] ; do firefox http://website.com &
sleep 5
A=`expr $A + 1`
pkill firefox
done
exit
```

you just happenned to kill firefox out of the loop...meaning that it would be killed automatically, only when the loop finishes running..until then you had to manually kill firefox.
your variable 'count' was meaningless here, as you are using 'A' to control the loop.
i have added a 'sleep 5' so as to give some time to the browser to load the page.. afterall, thats why you made the script:)
you can vary the value 5 (depending on your internet speed)

---

### Post by Felson on 2008-07-25
or this.
```

#!/usr/bin/perl

use LWP::Simple qw(!head);
var $c;
var $URL = $1;

for($c=0;$c<5;$c++)
  {getprint $URL;}

```

then use in terminal.
```

./ProgName "http://www.yoursite.com"

```
replaceing "ProgName" with whatever you call the script, and "http://www.yoursite.com" is the site you wish to request. I think it should work with https on Ubuntu out of the box as well, but not sure.

---

### Post by Mia_tech on 2008-07-25
> **dexter.deepak said:**
> try this :
```
A=0

while [ $A -le 5 ] ; do firefox http://website.com &
sleep 5
A=`expr $A + 1`
pkill firefox
done
exit
```

you just happenned to kill firefox out of the loop...meaning that it would be killed automatically, only when the loop finishes running..until then you had to manually kill firefox.
your variable 'count' was meaningless here, as you are using 'A' to control the loop.
i have added a 'sleep 5' so as to give some time to the browser to load the page.. afterall, thats why you made the script:)
you can vary the value 5 (depending on your internet speed)

yes, I had realized that fact, and changed it.... anyway thanks for your addintions..

---

### Post by ghostdog74 on 2008-07-25
what are you trying to do actually? this is not normally one would do when browsing the web. Its even queer if you are doing an automated script.

---

