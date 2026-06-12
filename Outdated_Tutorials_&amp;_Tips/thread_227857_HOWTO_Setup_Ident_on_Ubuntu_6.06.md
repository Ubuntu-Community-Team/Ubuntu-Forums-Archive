---
title: "HOWTO: Setup Ident on Ubuntu 6.06"
date: 2006-08-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Nick Rivers on 2006-08-02
When I tried to install pidentd using synaptic in Ubuntu 6.06, it didn't take long to figure out that the package was missing needed configuration files and init scripts and that it didn't generate an identd.key file or setup the identd service. After some trial and error, I finally figured out how to get it up and running. Here's how.

First, install pidentd.  Open a console and type the command 'sudo apt-get install pidentd' without the apostrophes.

After pidentd is installed, type the following command 'sudo /usr/sbin/ikeygen'

This will generate the file /etc/identd.key

Next, type 'sudo nano -w /etc/init.d/identd' and enter the following code:

#!/bin/sh
#
# identd control script
#
#

PIDFILE=/etc/identd.pid
IDENTD=/usr/sbin/identd

if [ -f $PIDFILE ]; then
pid=`cat $PIDFILE`
fi

case $1 in
'start')
if [ -x $IDENTD ]; then
echo "Starting Identd"
$IDENTD
fi
;;

'stop')
if [ "${pid}" != "" ]; then
/bin/kill ${pid}
fi
;;

*)
echo 'usage: /etc/init.d/identd {start|stop}'
;;
esac

Hit Control-O to save the file to /etc/init.d/identd and then hit Control-X to exit nano.

Next type the command 'sudo chmod a+x /etc/init.d/identd'

Then type the command 'sudo ln -s /etc/init.d/identd /etc/rc3.d/S99identd'

***NOTE*** I put the link in /etc/rc3.d/S99identd because I use runlevel 3.  You will want to change the 'rc3.d' to reflect your runlevel (i.e. rc2.d for runlevel 2)

This will create a symbolic link in /etc/rc3.d/S99identd to the init script in /etc/init.d/identd

Next, edit /etc/identd.conf to configure your identd daemon to your liking by typing 'sudo nano -w /etc/identd.conf' (don't worry, the file is well documented and easy to understand)

You can now start the identd daemon by typing in your console 'sudo /etc/init.d/identd start' or you can just reboot and the daemon will start automatically. You can confirm that the daemon is running using System Monitor.

And THAT is how I got identd up and running in Ubuntu 6.06. I hope you find this HOWTO helpful and any remarks are appreciated as this is my first Linux HOWTO.

---

### Post by zeroepoch on 2006-08-08
Great HOWTO!  I needed identd to connect to some IRC servers in XChat.

---

### Post by Nick Rivers on 2006-08-11
> **zeroepoch said:**
> Great HOWTO!  I needed identd to connect to some IRC servers in XChat.

Glad it helped :) I needed ident for the same reason.

---

