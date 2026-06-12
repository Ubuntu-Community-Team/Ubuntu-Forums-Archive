---
title: "Changing panel icons.. help?"
date: 2007-10-09
forum: Programming Talk
---

### Post by DaveDH on 2007-10-09
When I move my laptop between work/home/work etc. I have to manually toggle the network proxy each time.

I wrote a script to do this and created an icon on the gnome panel to run it:

#!/bin/bash
# Toggle the status of the network proxy

if [ $(gconftool-2 -g /system/proxy/mode) = "none" ]; then 
	gconftool-2 -s -t string /system/proxy/mode auto
	echo "Proxy is now AUTO"
else
	gconftool-2 -s -t string /system/proxy/mode none
	echo "Proxy is now OFF"
fi
exit 0

BUT, I would ideally like the icon to indicate the status of the proxy.  

Is there any way from a script to change the icon that is shown on the panel?

---

### Post by DaveDH on 2007-10-16
Thought I'd post a slight update as the script above is not complete.  This one works well, and in leu of a change of icon I have changed the panel link to 'Run in Terminal' and updated the script to display it's setting for 3 seconds.

[FONT="Fixedsys"]#!/bin/bash
# Toggle the status of the network proxy

if [ $(gconftool-2 -g /system/proxy/mode) = "none" ]; then 
	gconftool-2 -s -t string /system/proxy/mode auto
	gconftool-2 -s -t bool /system/http_proxy/use_http_proxy true
	echo "Proxy is now AUTO"
else
	gconftool-2 -s -t string /system/proxy/mode none
	gconftool-2 -s -t bool /system/http_proxy/use_http_proxy false
	echo "Proxy is now OFF"
fi
TMOUT=3
read justapause
exit 0
[/FONT]

---

