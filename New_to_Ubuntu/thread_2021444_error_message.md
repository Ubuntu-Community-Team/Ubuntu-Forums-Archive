---
title: "error message"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-07-09
any idea how to fix. using 4.10 in 12.04 and get the following when i try to open help

Failed to execute command "xfbrowser4 /usr/share/xubuntu-docs/about/xubuntu-index.html".
Failed to execute child process "xfbrowser4" (No such file or directory)

---

### Post by Bigtime_Scrub on 2012-07-09
Xfce-utils including xfbrowser4 are deprecated in xfce 4.10. Xubuntu 12.04 is at xfce 4.8...

You can try exo-open instead.

[https://bugs.launchpad.net/ubuntu/+source/qimo-session/+bug/1002253](https://bugs.launchpad.net/ubuntu/+source/qimo-session/+bug/1002253)
[https://bugzilla.xfce.org/show_bug.cgi?id=8642](https://bugzilla.xfce.org/show_bug.cgi?id=8642)

---

### Post by rburkartjo on 2012-07-09
big tks that is what i thought from researching problem.

---

### Post by rburkartjo on 2012-07-09
cant get exo-open to work no big deal

---

### Post by Toz on 2012-07-09
xfbrowser4 was nothing more than a shell script. Even though its deprecated, you could create the shell script yourself and use it until the 4.10 packages are updated to include the patch. Here are the contents of the script file (/usr/bin/xfbrowser4) from 4.8:
```

#!/bin/sh

if [ "x$BROWSER" = "x" ]
then
  for b in exo-open midori iceweasel firefox epiphany galeon mozilla konqueror dillo
  do
    if which "$b" > /dev/null 2>&1
    then
      BROWSER=$b
      break;
    fi
  done
fi

if [ "x$BROWSER" = "x" ]
then
  echo " *** Error ***: xfbrowser4: Could not find browser to use."
  echo "                Please set the BROWSER variable."
  exit 1
fi

if [ ! "x$1" = "x" ]; then
  case $1 in
      *://*) URL=$1;;
      *) URL="file://$1" ;;
  esac
fi

case $BROWSER in
    firefox*)
	$BROWSER -a firefox -remote openurl\($URL,new-window\) || \
		$BROWSER $URL
	;;
    communicator*|netscape|mozilla*|phoenix*|firebird*)
	$BROWSER -remote openurl\($URL,new-window\) || \
		$BROWSER $URL    
	;;
    opera*)
    	$BROWSER -remote openURL\($URL,new-window\) || \
		$BROWSER $URL
	;;
	exo-open)
	    $BROWSER --launch WebBrowser $URL
	;;
    *)
    	$BROWSER $URL
	;;
esac

if [ $? -ne 0 ]; then
	xmessage -center -file - -title Error <<EOF
Unable to execute browser. 
Online help is not available.
EOF
	exit 1
fi

exit 0

```

---

### Post by rburkartjo on 2012-07-09
okay toz what did i do wrong. when i run the script all it does is open my default browser chromium.

---

### Post by rburkartjo on 2012-07-09
no big deal but still doesnt allow me to open  help  from the application menu

---

### Post by Toz on 2012-07-09
> **rburkartjo said:**
> okay toz what did i do wrong. when i run the script all it does is open my default browser chromium.

If you're running the script manually, you need to supply it a url:
```
xfbrowser4 http://www.ubuntuforums.org
```

> no big deal but still doesnt allow me to open help from the application menu 
If you're trying to run help from the application menu, make sure you have **xubuntu-docs** installed.

---

### Post by rburkartjo on 2012-07-09
toz tks i just added /usr/share/xubuntu-docs to my bookmarks and then set them to open with chromium.

---

