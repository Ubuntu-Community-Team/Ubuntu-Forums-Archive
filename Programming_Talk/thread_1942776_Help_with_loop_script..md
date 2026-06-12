---
title: "Help with loop script."
date: 2012-03-18
forum: Programming Talk
---

### Post by stinkeye on 2012-03-18
I wrote a script to output my current desktop when using compiz virtual desktops to be used by conky.
```
#!/bin/bash

#set -x
###############################################################
##  Script to output the desktop number when running compiz  ##
##  with  4x1 virtual desktops and 1680x1050 resolution.     ##
###############################################################

# Use wmctrl -d | awk '{print $6}' to determine the coordinates for each virtual desktop if you use 2x2

sleep 3    ##Wait for conky to load
**while true; do**	
sleep 2



COORDINATE=$(wmctrl -d | awk '{print $6}')

if [ "$COORDINATE" == "0,0" ]; then
		echo 1 > ~/.desktop.txt

	elif [ "$COORDINATE" == "1680,0" ]; then
		echo 2 > ~/.desktop.txt

	elif [ "$COORDINATE" == "3360,0" ]; then
		echo 3 > ~/.desktop.txt

	elif [ "$COORDINATE" == "5040,0" ]; then
		echo 4 > ~/.desktop.txt
fi



done

```

I added the script to startup applications but found it remained running when
I logged out and started another instance upon login.

I fixed this by changing...
```
while true; do 
```

to 
```
while pidof conky; do
```

Just wondered if putting in startup applications is not the correct way to 
start this kind of script
or
is there something your supposed to add to the script so it exits when logging out.

---

