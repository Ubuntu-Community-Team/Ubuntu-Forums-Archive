---
title: "Torcat"
date: 2012-02-15
forum: Programming Talk
---

### Post by emiller12345 on 2012-02-15
I was working on this script and it's not working quite right. It's designed to be a wrapper for socat to handle netcat like functionality over the tor network.  Independently the commands work outside of a BASH script, but I can't make it work just like nc.  Anyone know whats wrong?

```
#!/bin/bash

ARGC="$#"
ARGV1="$1"
ARGV2="$2"
ARGV3="$3"
FORCE_SSL=0
TEMPFILE=$(tempfile)

function exit_torcat(){
    PID=$(pidof -s "socat")
    if [ -n "$PID" ]; then
        kill -2 $PID
        sleep 2;
        if [ -d /proc/"$PID" ]; then 
            kill -9 $PID
        fi
    fi
    rm $TEMPFILE; 
}

trap "exit_torcat; " SIGINT

if [ $ARGC -eq 3 -a \( "$ARGV1" = "--ssl" -o "$ARGV1" = "-s" \) ]; then
    FORCE_SSL=1
    HOSTNAME="$ARGV1"
    HOSTPORT="$ARGV2"
elif [ $ARGC -eq 2 ]; then
    HOSTNAME="$ARGV1"
    HOSTPORT="$ARGV2"
else
    HOSTNAME="check.torproject.org"
    HOSTPORT="443"
fi

echo "host=$HOSTNAME:$HOSTPORT"

if [ $HOSTPORT -eq 443 -o $FORCE_SSL -eq 1 ]; then
    PORT=$(($RANDOM+32767))
    echo "socat TCP4-LISTEN:"$PORT",fork SOCKS4A:127.0.0.1:"$HOSTNAME":"$HOSTPORT",socksport=9050 &"
    socat TCP4-LISTEN:"$PORT",fork SOCKS4A:127.0.0.1:"$HOSTNAME":"$HOSTPORT",socksport=9050 &
    echo "socat STDIO OPENSSL:127.0.0.1:"$PORT",cafile="/etc/ssl/certs/ca-certificates.crt",capath="/etc/ssl/certs/""
    socat STDIO OPENSSL:127.0.0.1:"$PORT",cafile="/etc/ssl/certs/ca-certificates.crt",capath="/etc/ssl/certs/"
else
    socat STDIO SOCKS4A:127.0.0.1:"$HOSTNAME":"$HOSTPORT",socksport=9050;
fi

exit_torcat

```

I'd like it to run with a command like
```
echo -ne "GET / HTTP/1.1\r\n\r\n" | ./torcat
```

---

