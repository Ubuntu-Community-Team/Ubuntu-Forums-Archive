---
title: "Startup script help"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by roodypoo on 2012-02-25
I would like to write a small script that searches for available network adapters, brings them down, runs macchanger on them then brings them up. I would like this script to run each time the computer is booted up.   Would someone point me in the right direction?

 Also, these commands require root privileges. Is there a way to run them at startup with root privileges.  

When I write other scripts, is there a way to pass the password to commands in a bash script?  

Thanks

---

### Post by The Cog on 2012-02-26
I think /etc/rc.local is probably the best place to call your script from. This runs with root privilege, and so any scripts that it calls should not be editable by normal users. These commands will set the right permissions and put the script in the /bin directory:
```
sudo chown root:root script
sudo chmod 744 script
sudo mv script /bin
```

---

### Post by Lars Noodén on 2012-02-26
[/usr/local/bin](http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html) or /usr/local/sbin might be an even better place for the script.

---

### Post by roodypoo on 2012-02-26
When you say "call the script" do you mean to amend rc.local with the path to the script? Or do I have to make a link?

Also, I can hardcode the interface aliases, but is there a place to read them from then feed them into the scrip as variables?

---

### Post by Lars Noodén on 2012-02-26
> **roodypoo said:**
> When you say "call the script" do you mean to amend rc.local with the path to the script? Or do I have to make a link?
I mean the former.  Put a line inside /etc/rc.local that calls your script.  Make sure it is before the line with 'exit 0'

> **roodypoo said:**
> 
Also, I can hardcode the interface aliases, but is there a place to read them from then feed them into the scrip as variables?

I'm sure it can be done but can you clarify a little more about what you are trying to do?  You can grab the script arguments with ${1}, ${2}, ${3}, and so on.  

```

#!/bin/sh

echo $# script arguments;
echo The first is "${1}";
echo The second is "${2}";

```

---

### Post by roodypoo on 2012-02-26
The script will look like this
```

#! /bin/bash

sudo ifconfig wlan0 down
sudo ifconfig wlan2 down
sudo macchanger -A wlan0
sudo macchanger -A wlan2
sleep 2
sudo ifconfig wlan0
sudo ifconfig wlan2

```But, what I'd like is for the script to find all available interfaces and feed them in as variables.

I would just add the path to the script in rc.local?

Here is rc.local at /etc/init.d/rc.local
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs $syslog $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start() {
    if [ -x /etc/rc.local ]; then
            [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
        /etc/rc.local
        ES=$?
        [ "$VERBOSE" != no ] && log_end_msg $ES
        return $ES
    fi
}

case "$1" in
    start)
    do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

/usr/bin/myscript.sh

```

---

### Post by roodypoo on 2012-02-27
So I got the script to run at startup, but it only changes the MAC of one of the interfaces.

---

### Post by Lars Noodén on 2012-02-28
> **roodypoo said:**
> 
Here is rc.local at /etc/init.d/rc.local


Sorry, I just noticed.  That's the systemv script for /etc/rc.local your actual changes should go in /etc/rc.local instead, right before the line "exit 0"

---

### Post by roodypoo on 2012-02-28
Thank you. I got the script to run, but it only changes one of the devices MACs. 

Is there a command that outputs the name of the device only, so that I may use those as variable?

Ifconfig -a lists all the available network devices with other information. All I want is the device name itself.

How can I make those variables for a script?

---

### Post by Lars Noodén on 2012-02-28
You could do something like this to get just the names of the devices:

```

 for i in $(/sbin/ifconfig -a | awk '/^[a-z]/{if ( $1 != "lo" ) print $1}')
 do echo $i; 
 done

```

Substitute what you want for **echo**.

---

