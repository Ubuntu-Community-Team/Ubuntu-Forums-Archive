---
title: "HOWTO: Installing Standalone Firewall"
date: 2004-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by wallijonn on 2004-10-31
Standalone (1 NIC in your PC) Firewall:

Go to SPM, list alphabetically, "S", download / install Shorewall 2.0.2-4ubuntu2

[http://www.shorewall.net/shorewall_setup_guide.htm](http://www.shorewall.net/shorewall_setup_guide.htm) 
[http://www1.shorewall.net/pub/shorewall/Samples/samples-2.0.1/one-interface.tgz](http://www1.shorewall.net/pub/shorewall/Samples/samples-2.0.1/one-interface.tgz)

From [www.shorewall.net](www.shorewall.net) :
"The configuration files for Shorewall are contained in the directory /etc/shorewall -- for simple setups. After you have installed Shorewall, download the one-interface sample, un-tar it (tar -zxvf one-interface.tgz) and and copy the files to /etc/shorewall"

start a root terminal

sudo cp /usr/share/doc/shorewall/default-config/shorewall.conf.gz /etc/shorewall
sudo cp /usr/share/doc/shorewall/default-config/modules /etc/shorewall
sudo cp one-interface.tgz /etc/shorewall
cd /etc/shorewall
gunzip shorewall.conf.gz
tar -zxvf one-interface.tgz
cd one-interface
sudo cp * /etc/shorewall
cd ..

sudo gedit /etc/default/shorewall
change STARTUP_ENABLED=Yes. 
exit the editor.

cd /home
exit

reboot your PC.
check the boot up screen file and /var/log/messages and /var/log/shorewall-init.log

[EDIT]
While you're at it why not edit your HOSTS file to include:
[http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)
(just add the entries to the last line at /etc/hosts; add the lines after #start of lines added by WinHelp2002)

ALWAYS make backup copies of config files to /home/<username>. that way you can sudo cp /home/<username> hosts /etc/hosts 
or sudo cp /home/<username> XF86Config-4 /etc/X11 (incase XWindows blows up).



.

---

