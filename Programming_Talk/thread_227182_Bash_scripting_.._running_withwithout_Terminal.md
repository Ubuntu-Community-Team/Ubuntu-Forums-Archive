---
title: "Bash scripting .. running with/without Terminal"
date: 2006-08-01
forum: Programming Talk
---

### Post by sefs on 2006-08-01
Hi all.

Background
----------
I use TrueCrypt and wanted an easier way to mound the drive without typing the long command each time.  I initally then set up a bash one liner script that launched in the terminal from a desktop icon.  I later discovered zenity and am trying to get a gui like dialog box.  

Problem
--------
The script works fine if in the desktop icon i specify "Run in terminal". It does not if i uncheck this box.  I would prefer not to see the terminal window at all.  What the problem is, is that when I dont specify to run in terminal, then if i enter an incorrect password the script does not loop at all.  When ran in the terminal, then on entering an incorrect password then it loops as expected.

Can any of you Gurus tell me whats wrong with the script?

Thanks.

P.S. I am new to this so any help is appreciated.

The script is as follows
```

#!/bin/sh
# /mnt/hd2/data/tc/lhd3.sh

COUNTER=0
TCSTATUS="Incorrect password or not a TrueCrypt volume."
DIALOGTEXT="Enter your password."
while [[ $COUNTER < 3 ]] && [[ $TCSTATUS == "Incorrect password"* ]] ; do
	GETPASSWD=`zenity --title "Password" --entry --hide-text --text "$DIALOGTEXT"`
	if [[ ${#GETPASSWD} != 0 ]] ; then
		TCSTATUS=`truecrypt /mnt/hd2/datadrive/datadrive /mnt/hd3 -p$GETPASSWD --password-tries 1`
		DIALOGTEXT=$TCSTATUS
		let COUNTER=COUNTER+1 
	else
		let COUNTER=3 
	fi
done

```

---

### Post by sefs on 2006-08-01
Ok ... I see now that when not running in terminal that the script varibles lose their settings ... like going out of focus.  I am assuming the Terminal window acts as a container for the script which maintains the environment and variable declarations.

In that case if running a bash script without a terminal window what are the extra steps to be taken to keep the envionment and variables intact until the script is exited.

Thanks.

---

