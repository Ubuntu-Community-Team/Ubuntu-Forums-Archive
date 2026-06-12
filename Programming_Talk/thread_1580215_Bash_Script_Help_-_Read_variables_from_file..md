---
title: "Bash Script Help - Read variables from file."
date: 2010-09-23
forum: Programming Talk
---

### Post by ShadowBlade72 on 2010-09-23
Now, I'll go ahead and start by saying that I've already read up a bit on array's and how to get them to read from a file. That isn't really the issue here.

What I have is a script that monitors a process on my system, a game server in this case, and if it's not running it will start it.

I have about five different game servers running on a box, and I've had to create a script for each one.

What I'm trying to do is get it down to one script that will adjust the variables and check every server.

```

#!/bin/bash
source /byond2/bin/byondsetup
DDVER="$(DreamDaemon --version)"

############DO NOT EDIT ABOVE THIS LINE############

SERVICE='dmg' #This is the name of the process your server is hosted under. You must use the name of the game your hosting. Ex. If your game is called dmg.dmb you'd enter dmg here. 
SERVERUSER='byondsrv' #This is the name of the user who the server is hosted under.
SERVERPATH='/home/byondsrv/dmu' #This is the path to your hosting folder. This should be the folder where your .dmb is contained.
PORT='6002' #This is the port you want to use to host DreamDaemon.

############DO NOT EDIT BELOW THIS LINE############

if ps -ef | grep -v grep | grep $SERVICE | grep $PORT > /dev/null
then
   exit
else
   echo "$(date):$SERVICE is not running!" >> $SERVERPATH/DreamCheck.log
   echo "$(date):Cheking logs and adding the person who crashed the server to hostban.txt if present." >> $SERVERPATH/DreamCheck.log
   USER="$(cat $SERVERPATH/$SERVICE.log | grep -A 6 -i 'Crashing' | grep -i 'Load()' | gawk -F'(' '{ print $1 }')"
      if [ -n "$USER" ]; 
      then
         cp -f /home/$SERVERUSER/.byond/cfg/hostban.txt /home/$SERVERUSER/.byond/cfg/hostban.old
         echo "$USER flags=4&message=Autoban for server crashing." >> /home/$SERVERUSER/.byond/cfg/hostban.txt
         echo "$(date):$USER added to ban list." >> $SERVERPATH/DreamCheck.log
      else
         echo "$(date):No user found... Continuing server startup." >> $SERVERPATH/DreamCheck.log
      fi
   if [ ! -d "$SERVERPATH/logs" ]; then
      echo "Logs folder not present, creating folder." >> $SERVERPATH/DreamCheck.log
      mkdir $SERVERPATH/logs
   fi
   echo "$(date):Moving current log to $SERVERPATH/logs" >> $SERVERPATH/DreamCheck.log
   mv $SERVERPATH/$SERVICE.log $SERVERPATH/logs/"$(date +%d%b%y:%H%M)".log
   echo "$(date):Deleting $SERVICE.dyn.rsc file from $SERVERPATH" >> $SERVERPATH/DreamCheck.log
   rm -f $SERVERPATH/$SERVICE.dyn.rsc
   echo "$(date):Starting $SERVICE now" >> $SERVERPATH/DreamCheck.log
   echo "$(date):Current Version: $DDVER" >> $SERVERPATH/DreamCheck.log
   DreamDaemon $SERVERPATH/$SERVICE.dmb $PORT -safe -logself &
      if ps -ef | grep -v grep | grep $SERVICE > /dev/null
      then
         echo "$(date):$SERVICE started successfully." >> $SERVERPATH/DreamCheck.log
         exit
      else
         echo "$(date):$SERVICE not started successfully!" >> $SERVERPATH/DreamCheck.log
         exit
      fi
fi

```

As you can see I have the variables set, and I have a different script for each version of the server.

What I want to do is have a config.ini file that it will pull the variables from for each server.

Here is an example of what I mean

```

Server1
SERVICE='dmg'
SERVERUSER='byondsrv'
SERVERPATH='/home/byondsrv/dmg'
PORT='6002'

Server2
SERVICE='dmg'
SERVERUSER='byondsrv'
SERVERPATH='/home/byondsrv/dmgsrv2'
PORT'6003'

Server3
SERVICE='dmg'
SERVERUSER='byondsrv'
SERVERPATH='/home/byondsrv/dmgserver3'
PORT'6004'

etc.

```

I'm not sure how to accomplish this. I found that I can get it to read one servers config by using an array such as.

```

#!/bin/bash

filename=config.ini
declare -a array1
array1=(`cat "$filename"`)

echo ${array1[@]}
echo ${array1[0]}
echo ${array1[1]}
echo ${array1[2]}
echo ${array1[3]}

```

Any help would be great. I'm not sure where to go from here, and I'd like to streamline the process of monitoring my game servers.

---

### Post by SaintDanBert on 2010-09-23
Without studying all of you post, my first thought is to use a fragment of script file as data and then have your script "source" this fragment. You could have one script file for each process and your central script could fetch them all during each processing pass.

In like manner, your central script could write its own fragment and your processes could grab it -- perhaps in response to a SIGINT or SIGHUP restart.

The fragment file:
```

#++
#  fragment for variables
#--
foo=10
#
bar="stuff"
#
framis="false"
#

```

Then in your script
```

myFragment="/path/filename.typ"
...
if [ -r "$myFragment"] then
    source "$myFragment" $fragmentOptions
else
    echo "??? no data file available"
    exit $errorStatus
fi
...

```

You can pass parameters when you source the fragment. Those options  could then cause conditional processing of the the fragment script. Parameters are not required but they are an option if you want or need them. (Ask if you need more explanation of this.)

Bonne chance,
~~~ 0;-Dan

---

### Post by ShadowBlade72 on 2010-09-23
```

#!/bin/bash
source /byond2/bin/byondsetup
DDVER="$(DreamDaemon --version)"
COUNTER='0'

############DO NOT EDIT ABOVE THIS LINE############

CONFIGFILE='config.ini'

############DO NOT EDIT BELOW THIS LINE############

CheckServer() {
if ps -ef | grep -v grep | grep ${scriptconfig[1]} | grep ${scriptconfig[4]} > /dev/null
then
   return 
else
   echo "$(date):${scriptconfig[1]} is not running!" >> ${scriptconfig[3]}/DreamCheck.log
   echo "$(date):Cheking logs and adding the person who crashed the server to hostban.txt if present." >> ${scriptconfig[3]}/DreamCheck.log
   USER="$(cat ${scriptconfig[3]}/${scriptconfig[1]}.log | grep -A 6 -i 'Crashing' | grep -i 'Load()' | gawk -F'(' '{ print $1 }')"
      if [ -n "$USER" ]; 
      then
         cp -f /home/${scriptconfig[2]}/.byond/cfg/hostban.txt /home/${scriptconfig[2]}/.byond/cfg/hostban.old
         echo "$USER flags=4&message=Autoban for server crashing." >> /home/${scriptconfig[2]}/.byond/cfg/hostban.txt
         echo "$(date):$USER added to ban list." >> ${scriptconfig[3]}/DreamCheck.log
      else
         echo "$(date):No user found... Continuing server startup." >> ${scriptconfig[3]}/DreamCheck.log
      fi
   if [ ! -d "${scriptconfig[3]}/logs" ]; then
      echo "Logs folder not present, creating folder." >> ${scriptconfig[3]}/DreamCheck.log
      mkdir ${scriptconfig[3]}/logs
   fi
   echo "$(date):Moving current log to ${scriptconfig[3]}/logs" >> ${scriptconfig[3]}/DreamCheck.log
   mv ${scriptconfig[3]}/${scriptconfig[1]}.log ${scriptconfig[3]}/logs/"$(date +%d%b%y:%H%M)".log
   echo "$(date):Deleting ${scriptconfig[1]}.dyn.rsc file from ${scriptconfig[3]}" >> ${scriptconfig[3]}/DreamCheck.log
   rm -f ${scriptconfig[3]}/${scriptconfig[1]}.dyn.rsc
   echo "$(date):Starting ${scriptconfig[1]} now" >> ${scriptconfig[3]}/DreamCheck.log
   echo "$(date):Current Version: $DDVER" >> ${scriptconfig[3]}/DreamCheck.log
   DreamDaemon ${scriptconfig[3]}/${scriptconfig[1]}.dmb ${scriptconfig[4]} -safe -logself &
      if ps -ef | grep -v grep | grep ${scriptconfig[1]} > /dev/null
      then
         echo "$(date):${scriptconfig[1]} started successfully." >> ${scriptconfig[3]}/DreamCheck.log
         return
      else
         echo "$(date):${scriptconfig[1]} not started successfully!" >> ${scriptconfig[3]}/DreamCheck.log
         return
      fi
fi
}

if [ -e $CONFIGFILE ]; then
   SERVERS=`cat $CONFIGFILE | grep SERVERS | gawk -F= '{ print $2 }'`
   while [ $COUNTER -lt $SERVERS ]; do
      declare -a scriptconfig
      scriptconfig=(`cat "$CONFIGFILE" | grep -A5 Server$COUNTER | gawk -F= '{ print $2 }'`)
      CheckServer
      let COUNTER=COUNTER+1
   done
else
   echo "Config file not found! Please ensure config file is present."
   exit
fi

```

```

SERVERS=4

SERVER=Server0
SERVICE=dmg
SERVERUSER=byondsrv
SERVERPATH=/home/byondsrv/dmu
PORT=6002

SERVER=Server1
SERVICE=dmg
SERVERUSER=byondsrv
SERVERPATH=/home/byondsrv/dmgstar
PORT=6004

SERVER=Server2
SERVICE=dmg
SERVERUSER=byondsrv
SERVERPATH=/home/byondsrv/dmgsin
PORT=6005

SERVER=Server3
SERVICE=iconultima
SERVERUSER=byondsrv
SERVERPATH=/home/byondsrv/iconultima
PORT=6003
```

---

