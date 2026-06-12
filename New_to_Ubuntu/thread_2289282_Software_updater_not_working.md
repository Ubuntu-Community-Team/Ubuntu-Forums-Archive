---
title: "Software updater not working"
date: 2015-08-02
forum: New to Ubuntu
---

### Post by kevin174 on 2015-08-02
I am not able to open the software updater, and when I tried to update from a terminal I received the following message:

E: Syntax error /etc/apt/apt.conf.d/00aptitude:5: Extra junk after value

So I looked at the file, and this is the output:
```

NTPDATE_CONF=/etc/default/ntpdate
NTPDATE_DHCP_CONF=/var/lib/ntpdate/default.dhcp


ntp_servers_setup_remove() {
    rm -f $NTPDATE_DHCP_CONF
}


ntp_servers_setup_add() {
    if [ -e $NTPDATE_DHCP_CONF ] && [ "$new_ntp_servers" = "$old_ntp_servers" ]; then
        return
    fi

    if [ -z "$new_ntp_servers" ]; then
        ntp_servers_setup_remove
        return
    fi

    tmp=$(mktemp "$NTPDATE_DHCP_CONF.XXXXXX") || return
    chmod --reference=$NTPDATE_CONF $tmp
    chown --reference=$NTPDATE_CONF $tmp

    (
      echo "# NTP server entries received from DHCP server"
      echo "NTPSERVERS='$new_ntp_servers'"
    ) >>$tmp
    
    mv $tmp $NTPDATE_DHCP_CONF
}


ntp_servers_setup() {
    case $reason in
        BOUND|RENEW|REBIND|REBOOT)
            ntp_servers_setup_add
            ;;
        EXPIRE|FAIL|RELEASE|STOP)
            ntp_servers_setup_remove
            ;;
    esac
}


ntp_servers_setup


```
Any ideas what I can do to fix this? Thanks in advance for the help!

---

### Post by oneindelijk on 2015-08-02
Hi, 

I have no idea what this error means but on my system I only have this in the file
```
Aptitude::Get-Root-Command "sudo:/usr/bin/sudo";
```

Maybe try moving this file out of its directory and put a new file with only this in its place ?

EDIT
Or try opening the file in an editor where you can show spaces and linefeeds. Maybe there's illegal characters in the file (on line 5 ?)

---

