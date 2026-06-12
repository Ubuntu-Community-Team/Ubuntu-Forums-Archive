---
title: "Do some commands on startup"
date: 2008-01-06
forum: Programming Talk
---

### Post by nukleuzN on 2008-01-06
I'm not sure if Im in the correct place at these forum to ask this question, but I want to run this command at start up:

```
$ sdptool browse 00:16:B8:1A:C0:80
```
Then i will get a respons like this (it's just a abridgement of the complete "answer"), IF my Cellphone has the Bluetooth turn on:
```
Service Name: Dial-up Networking
Service RecHandle: 0x10002
Service Class ID List:
  "Dialup Networking" (0x1103)
  "Generic Networking" (0x1201)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 2
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

```

Then i wanna check what "Channel" is set to, then run this command (gedit og nano?):
```
$ sudo gedit /etc/bluetooth/rfcomm.conf

```
The file rfcomm.conf will contain something like this:
```

#
# RFCOMM configuration file.
#

rfcomm0 {
	device 00:16:B8:1A:C0:80;
	channel 2;
	comment "BT DUN";
}
```
And then check if "channel" is set to (see line 7 in code-snippet above) the same as "Service Name: Dial-up Networking"-respons from my Cellphone. If not, the script should write to the file "rfcomm.conf", and change channel to the correct channel number.

At the end of the script this command should be runned:
```
$ sudo rfcomm bind rfcomm0
```
If the Cellphone does not respond, i will get this message in terminal "Failed to connect to SDP server on 00:16:B8:1A:C0:80: Host is down", but the code above should be runned anyway.

Does anyone know how i could do this? I'm new to linux.. :-\"

---

### Post by slavik on 2008-01-06
I suggest you look into Perl since it seems that you need to do some text processing

---

### Post by nukleuzN on 2008-01-07
Since I dont know Perl, i tried to do something i PHP.

[http://norskwebforum.no/pastebin/10269](http://norskwebforum.no/pastebin/10269)

But first, i need to run this on my startup. And second, how am i able to run sudo-commands in shell_exec? :(
This is probably_*** not ***_the best code that is written. But this is the first time i use Exceptions ;)

Thanx :)

---

### Post by meatpan on 2008-01-07
Is it correct that you want to run your script at system boot, as opposed to when you simply log in to a session?

If so, consider creating an init.d startup file.  Linux borrows the SvsV-Unix init process, and you can read more about it by running 'man update-rc.d'.  Essentially, a series of scripts are executed in a specified order by an 'init' process.  Ubuntu sets up the basic scripts and ordering for you, but you are able to modify this or add your own startup scripts.  

Try with a simple example script to verify the init process is doing what you think, and then add your desired components piece by piece.

---

### Post by slavik on 2008-01-07
if you know php, perl is not far away :) (except that there are real arrays and hashes instead of associative arrays)

but using php should suffice

---

### Post by nukleuzN on 2008-01-07
But this script works fine to me, the only thing I'm missing are how to run Sudo-commands (root previleges) with shell_exec in php?

And i think i will find out by my self how i will be able to start this by a Cron 1 minute after startup :)

EDIT: The only thing i need is to run the "private function StartConnection ()" in the destuctor as root :) The script remake the configuration file when needed... (if channels are  different)

---

### Post by slavik on 2008-01-07
if you run your script at boot up, then it will run as root. (no need for sudo)

---

### Post by nukleuzN on 2008-01-07
Hi again!

I have now updatet my code with the shebang line, found the correct "shebang line" when typing "which php" in terminal after installing "php5-cli".

After i have typed "crontab -e" in terminal, nano opens the file. And as I could see, I'm only able to run this with crontab at a designated time ?

How can i add "php -q /var/www/sysdoc/config.startup.php" to *boot up*? :)

---

### Post by ghostdog74 on 2008-01-07
here's one that does the parsing and editing
```

#!/bin/bash
sdptool browse 00:16:B8:1A:C0:80 | awk  '/Channel:/ { 
 bluetoothchannel=$2
 while ( ( getline line < "/etc/bluetooth/rfcomm.conf" ) > 0 ) {
    if ( line ~ /channel/ && line !~ /#/ ) {
      split(line,s)
      sub(";","",s[2])
      if ( s[2] != bluetoothchannel  ){
         print "  channel " bluetoothchannel ";" > "temp"
      }
    }
    else {
      print line > "temp"
    }
 }
 close("/etc/bluetooth/rfcomm.conf")
 }
 /Failed to connect/ { print $0 }'

```

I leave you to create the startup script. You can take references from the web by googling "How to create startup scripts ubuntu"

---

### Post by nukleuzN on 2008-01-07
> **slavik said:**
> if you run your script at boot up, then it will run as root. (no need for sudo)

I did this:

1: made a file named: bluetoothinit.sh
3: with this content:
#!/bin/bash
php -q /var/www/sysdoc/config.startup.php
2: saved it in /ect/rc6.d/

restarted, and nothing happend :(

Is there something wrong with the shell file?

---

### Post by amo-ej1 on 2008-01-07
why did you save it in rc6.d ? 6 is the runlevel to reboot  the system. Enter runlevel at your prompt to get to know the current runlevel. In my case this is 2. So I'd add the file to /etc/rc2.d/ also keep in mind that the file should start with SxxFILENAME where 'S' means that it should be started at  this runlevel (another option is K if you would want it killed) and xx illustrates the priority (S00aa.sh goes first, S99aa.sh goes last).

---

### Post by nukleuzN on 2008-01-07
Hmm, I have made the file:

[QUOTE=/ect/rc2.d/S28bluetoothinit]```
#! /bin/bash

#config rfcomm.conf and set up my cellphone channel.
php -q /var/www/sysdoc/config.startup.php
```[/QUOTE]

The the real "Bluetooth startup file" have the name S25bluetooth, so i think i had to name my a few number behind 25, so i called my file S28bluetoothinit. 

But it seems that the sh file want execute on bootup, but if i open terminal after boot and type: sudo sh /etc/rc2.d/S28bluetoothinit it works

but if i write sh /etc/rc2.d/S28bluetoothinit it works without sudo, i'll get this answere:
Can't create device: Operation not permitted
ERROR: $ ../../../etc/bluetooth/rfcomm.conf isnt writeable - Write to file ../..

Can it be that i dont have root permissions on the file S28bluetoothinit on bootup?

---

### Post by nukleuzN on 2008-01-07
Anyone?

---

### Post by evymetal on 2008-01-08
you could try putting it in rc.local - I *believe* this is run after everything else (right before you are given a shell as the computer boots) - this would make sure all the drivers are already loaded and set up correctly.

---

### Post by nukleuzN on 2008-01-11
I have tried, but it didnt work. 

```
$ sudo sh /etc/rc.local
```Works in terminal  :S

This is my rc.local file (saved under /etc/rc.local:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Config rfcomm.conf with correct Service Channel.
# And setup rfcomm0 ready to use with this channel.
php -q /var/www/sysdoc/config.startup.php

# Restart the bluetooth device!
/etc/init.d/bluetooth restart

exit 0
```

[http://norskwebforum.no/pastebin/10269](http://norskwebforum.no/pastebin/10269) (php-class)

---

