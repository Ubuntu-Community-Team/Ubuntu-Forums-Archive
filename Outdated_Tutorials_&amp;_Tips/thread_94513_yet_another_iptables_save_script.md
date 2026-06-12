---
title: "yet another iptables save script"
date: 2005-11-24
forum: Outdated Tutorials &amp; Tips
---

### Post by veider on 2005-11-24
After having a look at present scripts available on the net for ubuntu to save/restore iptables rules i've written another one :) Maybe someone will find it useful.

---[ Script Begins ]---
#! /bin/sh

# /etc/init.d/iptables: save and restore iptables rules by VEiDER

test -x /sbin/iptables-save || exit 0
test -x /sbin/iptables-restore || exit 0
test -x /sbin/iptables || exit 0
test -x /usr/bin/touch || exit 0
test -x /bin/rm || exit 0

. /lib/lsb/init-functions

check_config() {
    if [ ! -e /etc/iptables.rules ]; then
        exit 1
    fi
}
check_lock() {
    if [ ! -e /var/lock/iptables.rules.loaded ]; then
        exit 1
    fi
}

export PATH="${PATH:+$PATH:}/usr/sbin:/sbin"

case "$1" in
  start)
        log_begin_msg "Loading iptables rules..."
        check_config
    /sbin/iptables --flush
    /sbin/iptables-restore </etc/iptables.rules   
    /usr/bin/touch /var/lock/iptables.rules.loaded
        log_end_msg 0
        ;;

  stop)
        log_begin_msg "Flushing iptables rules..."
    check_lock
    /sbin/iptables-save >/etc/iptables.rules   
    /sbin/iptables --flush
    /sbin/iptables -P INPUT ACCEPT
    /sbin/iptables -P OUTPUT ACCEPT
    /sbin/iptables -P FORWARD ACCEPT
    /bin/rm -f /var/lock/iptables.rules.loaded
        log_end_msg 0
        ;;

  restart|reload|reread)
        log_begin_msg "Reloading iptables rules..."
    check_lock
    /sbin/iptables-save >/etc/iptables.rules  
    /sbin/iptables --flush
    /sbin/iptables -P INPUT ACCEPT
    /sbin/iptables -P OUTPUT ACCEPT
    /sbin/iptables -P FORWARD ACCEPT
    /bin/rm -f /var/lock/iptables.rules.loaded
        check_config
    /sbin/iptables --flush
    /sbin/iptables-restore </etc/iptables.rules   
    /usr/bin/touch /var/lock/iptables.rules.loaded
    log_end_msg 0
        ;;

  *)
        log_success_msg "Usage: /etc/init.d/iptables {start|stop|reload|restart|reread}"
        exit 1
esac

exit 0

---[ EOF ]---

How-to use this:
1) sudo cat >/etc/init.d/iptables
2) Paste or type the script and ^D, now you should have this script in your
/etc/init.d/iptables
3) change permissions to execute the script
sudo chmod +x /etc/init.d/iptables
4) dump you current iptables settings for the script to be able to find them
/sbin/iptables-save >/etc/iptables.rules 
5) Make iptables run at startup
update-rc.d iptables defaults

This script won't reset your saved setting when double-stopped.
Ideas and Fixes for the script are welcome at 1 <at> ipex <dot> ru

---

