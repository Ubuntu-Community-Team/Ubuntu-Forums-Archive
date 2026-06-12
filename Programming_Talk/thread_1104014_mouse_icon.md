---
title: "mouse icon"
date: 2009-03-23
forum: Programming Talk
---

### Post by any.linux12 on 2009-03-23
Hi

How can I change the icon on my mouse during a command that takes some time to execute and then when its finish change again to the normal icon???

thanks

---

### Post by Zugzwang on 2009-03-23
> **any.linux12 said:**
> Hi

How can I change the icon on my mouse during a command that takes some time to execute and then when its finish change again to the normal icon???

thanks

It depends on what GUI framework/programming language you are using. Please tell us more.

---

### Post by any.linux12 on 2009-03-23
GUI-gnome 

And it's a #!/bin/sh script

---

### Post by Zugzwang on 2009-03-23
Try something like this:

```

`sleep 10` | zenity --progress --pulsate --auto-close

```

Needs "zenity" to be installed. Not precisely what you want, but close to it.

---

### Post by any.linux12 on 2009-03-23
> **Zugzwang said:**
> Try something like this:

```

`sleep 10` | zenity --progress --pulsate --auto-close

```

Needs "zenity" to be installed. Not precisely what you want, but close to it.

this is my script and I already have the zenity thing but I also want to change my mouse icon and the reason why I want my mouse to change is because the zenity bar does not pulsate, so, it starts it ends but you don't see anything and this script is not for me but for a simple user of my network

> #!/bin/sh

user=`whoami`


LOGFILE=`mktemp -t svn_checkout.XXXXXX`
ICONPATH="`dirname $0`/svn.xpm"
list=`ssh $user@192.168.1.3 "ls /esp-server/svn"`
URL=`zenity --entry --title="Subversion: Checkout" --text="$list

Enter repository folder according to the the aboves:" --entry-text="" --width=400 --window-icon="$ICONPATH" 2>&1`


while [ `svn checkout svn+ssh://$user@192.168.1.3/esp-server/svn/$URL &> $LOGFILE` ] ;
do 
	sleep 0.25
done | [COLOR="Blue"]zenity --progress --pulsate --auto-kill --text="Wait until the ok button is enable" --window-icon="`dirname $0`/svn.xpm"[/COLOR]
rm -f $LOGFILE



thanks

---

### Post by Zugzwang on 2009-03-23
You cannot globally change the mouse cursor. It is handled locally for every window by the X-Server. In order to get zenity pulsating, you need to feed it with input. Example:

```

yes | zenity --progress --pulsate --auto-close

```

---

### Post by any.linux12 on 2009-03-23
> **Zugzwang said:**
> You cannot globally change the mouse cursor. It is handled locally for every window by the X-Server. In order to get zenity pulsating, you need to feed it with input. Example:

```

yes | zenity --progress --pulsate --auto-close

```

I don't get the diference between your code and this 
> 
[COLOR="Blue"]done | zenity --progress --pulsate --auto-kill --text="Wait until the ok button is enable" --window-icon="`dirname $0`/svn.xpm"[/COLOR]

---

