---
title: "start up folder in ubuntu"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by g-louis on 2008-09-10
Hi 
where do i put this script and how do i get it to run on start 
i need this to be able to get part of  port forword  working and to keep my ip static

And what do i name it             Thanks
#######################################################
	#! /bin/sh
	# . /etc/rc.d/init.d/functions	# uncomment/modify for your killproc
	case "$1" in
	    start)
		echo "Starting noip2."
		/usr/local/bin/noip2
	    ;;
	    stop)
		echo -n "Shutting down noip2."
		killproc -TERM /usr/local/bin/noip2
	    ;;
	    *)
		echo "Usage: $0 {start|stop}"
		exit 1
	esac
	exit 0
	#######################################################

---

### Post by iaculallad on 2008-09-10
Save it in /etc/init.d folder and be sure to give it an executable attribute.

---

### Post by WRDN on 2008-09-10
You need to save the script as [name].sh. Give it whatever name you want.

You first need to copy the script to /etc/init.d:

```
sudo cp [name].sh /etc/init.d
```

Now, make it executable:

```
sudo chmod +x /etc/init.d/[name].sh
```

To make the script run at startup:

```
sudo update-rc.d [name].sh defaults
```

If you want to run the script at login (rather than bootup), click System > Preferences > Sessions, and on the "Startup Programs" tab, click the "Add" button and add the script.

---

### Post by vanadium on 2008-09-10
An easier alternative might be to include your script in the script /etc/rc.local

---

### Post by t0p on 2008-09-10
If you prefer using a GUI to the command line, you can set programs to run on startup at **System > Preferences > Sessions > Startup Programs.**  You can add your script there.  You'll need to type in the full path to the script.

---

### Post by g-louis on 2008-09-10
Thanks alot for the quick reply

---

