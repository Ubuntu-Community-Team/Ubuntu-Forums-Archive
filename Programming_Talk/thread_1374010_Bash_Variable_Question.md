---
title: "Bash Variable Question"
date: 2010-01-06
forum: Programming Talk
---

### Post by samurailink3 on 2010-01-06
I've been trying to set a variable to a known host's IP address, but it keeps setting the variable as a blank string. Any ideas? :P

```

	read ipchoice
	case $ipchoice in
		1) set ipaddy "`host google.com | sed -rne 's/.*has address ([0-9]+\.[0-9]+\.[0-9]+\.[0-9]+)/\1/p' | head -n 1`";;
		#Other choices in progress.
		7) echo -n "IP Address: " && read ipaddy;;
	esac
	echo $ipaddy && sleep 10

```

---

### Post by The Secret on 2010-01-06
What does the following command return if launched right from the Terminal ?

```
host google.com | sed -rne 's/.*has address ([0-9]+\.[0-9]+\.[0-9]+\.[0-9]+)/\1/p' | head -n 1
```

---

### Post by samurailink3 on 2010-01-06
```
64.233.169.99
```
The IP address of Google.

---

### Post by The Secret on 2010-01-06
```
IP_ADDRESS="Unknown"

echo -n "Choose a number ( menu ):"  && read $IPCHOICE

case $IPCHOICE in
    1) $IP_ADDRESS=`host google.com | sed -rne 's/.*has address ([0-9]+\.[0-9]+\.[0-9]+\.[0-9]+)/\1/p' | head -n 1`
    #Other choices in progress.
    7) echo -n "IP Address: " && read $IP_ADDRESS
esac

echo "IP address:" $IP_ADDRESS
read

```Try it and let us know whether it works or not ( can't access my Linux box so not entirely sure whether the code is valid ).

---

### Post by samurailink3 on 2010-01-07
Did a wee bit of editing, got it working:
```

	IP_ADDRESS="Unknown"
	echo -n "Choose a number ( menu ):"
	read IPCHOICE
	case $IPCHOICE in
	    1) IP_ADDRESS=`host google.com | sed -rne 's/.*has address ([0-9]+\.[0-9]+\.[0-9]+\.[0-9]+)/\1/p' | head -n 1`;;
	    #Other choices in progress.
	    7) echo -n "IP Address: " && read IP_ADDRESS;;
	esac
	echo "Thanks for choosing: "$IP_ADDRESS && sleep 4

```

I was trying ```
set variable "`command string`"
``` instead of ```
variable=`command string`
```

Thanks for all the help! Code is working perfectly now!

---

