---
title: "Issue with a sh script calling festival text to speach"
date: 2010-12-18
forum: Programming Talk
---

### Post by HectorG on 2010-12-18
I have a script triggered when an incoming call is placed to my home. The script in turn is supposed to get the caller id name and number and pass it on to festival to speak out the name and number with the text to speech. 


The portion of the script with problem is shown below...

```


#!/bin/sh

#MESSAGE="$1"
NUMBER="$2"
NAME="$3"


echo "Incoming call from $NAME. $NUMBER" | festival --tts

```


If I double click on it I hear the voice however when the script runs everything befor and after it runs but I don't hear festival. I don't see anywhere that I can change permissions for festival not sure what is wrong.

Any clues or suggestions?

---

### Post by saulgoode on 2010-12-18
Try providing a fully qualified path to 'festival'; it may not be in the PATH that is active when the script is triggered.

---

### Post by HectorG on 2010-12-18
I tried this

echo "Incoming call from $NAME. $NUMBER" | /usr/bin/festival --tts

but it still didn't work. That was a good guess though I didn't think to try that before.

That same command does work from the command line.



In case it helps here is all the code I am running

for upstart to work
/etc/init/mgetty.conf

```

# mgetty using ttyS0
#
# This service maintains a mgetty on ttyS0 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/mgetty /dev/ttyS0

```


The mgetty.config file
```

issue-file /etc/issue.mgetty
debug 8 # Log everything to /var/log/mgetty/mg_ttyS0.log
speed 115200 # Buad rate to run modem at
rings 2 # Answer phone after 2 rings - Need 2 because caller id info is sent between 1st and 2nd ring
# The following tells mgetty that for ttyS0 turn caller id on and run say_callerid.sh
port ttyS0
  init-chat "" AT#CID=1 OK
  cnd-program /home/h/callerid/say_callerid.sh

```


say_callerid.sh
```

#!/bin/sh

#MESSAGE="$1"
NUMBER="$2"
NAME="$3"

INDB=$( cd /var/www/callerid ; php -f newcall.php -- "$NAME" "$NUMBER" )

if [ "$INDB" = "NEW" ] ; then
{
        NAME="$NAME"
}
else
{
        NAME="$INDB"
}
fi

LOGGED=$( cd /var/www/callerid ; php -f insertlog.php -- "$NAME" "$NUMBER" )

#Format the number
FNUM=$(echo $NUMBER | sed -e 's#[^0-9]*\([0-9]\{3\}\)[^0-9]*\([0-9]\{3\}\)[^0-9]*\([0-9]\{4\}\)#(\1) \2-\3#')

sudo -u h /home/h/callerid/alt-notify-send.sh  "Incoming Call" "$NAME $FNUM" "5450" "/home/h/callerid/phone.svg"

# Do here whatever you want with the caller ID info. To say the info out loud you must have festival installed

echo "Incoming call from $NAME. $NUMBER" | /usr/bin/festival --tts

exit 1 # So mgetty will NOT answer the phone!

```

---

### Post by HectorG on 2010-12-19
ok I figured out how to get it to work...

 I think that root for security reasons is not allowed to run festival.  What I did is run festival as a known user "username" and add the -H parameter so that it will use the home of that user rather than root since festival was already configured and / or working with that specific user. Here is what the command should look like.

echo "Incoming call from $NAME. $NUMBER" | su -u username -H festival --tts

---

