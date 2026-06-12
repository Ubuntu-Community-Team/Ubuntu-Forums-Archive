---
title: "Get SMART warnings when your harddrive might fail"
date: 2007-03-04
forum: Outdated Tutorials &amp; Tips
---

### Post by AllBuntu on 2007-03-04
Otra mas, the saint is back:

so smartmontools is broken in Edgy, but not beyond repair! This is how you get a notifier window in Gnome whenever there is a status change for the worse with your hard drives. it's really nice to get a notification ahead of time before your drives fail...
(it won't tell you what it is, but WILL tell you somezup):

[LIST=1]
[*]sudo bash # become god (or root)
[*]apt-get install smartmontools smart-notifier # get the basic packages
[*]gedit /etc/smartd.conf &
# add a line "/dev/hda -a -n standby,q -m <nomailer> -M test -M exec  /etc/smartmontools/haraldgetsasmartnotifier"
# /dev/hda is the drive you want to monitor, add lines for additional drives
# geek around for other options
# we have our own little script here because /bin/run-parts is out of order
# --could someobody file a bug on that?
[*]cat >/etc/smartmontools/haraldgetsasmartnotifier
[*]/etc/smartmontools/run.d/60smart-notifier /dev/null
[*]ctrl-D
[*]chmod u+x /etc/smartmontools/haraldgetsasmartnotifier # make it executable
[*]gedit /etc/default/smartmontools &
# add a line "start_smartd=yes" that starts the background daemon
[*]#this is already done: Gnome > System > Preferences > Sessions > Startup programs: add smart-notifier
[*]smart-notifier & # this will be done when you log into gnome, but for now we must do manual 
[*]/etc/init.d/smartmontools restart # starts the daemon, should immediately notify
[*]# you should get a dialog popup "Hard Disk Health Warning"
[*]# if you get [fail] instead of [ok] try to find spelling errors by tail /var/log/syslog
[*]# if you get nothing it needs troubleshooting
[*]# if it hangs you might be executing run-part, goto step 1 of these instructions
[*]delete the "-M test " from /etc/smartd.conf and you happy camper
[/LIST]
This will check your harddrive every 30 minutes whenever the drive is spinning. If there is any SMART worsening, you get a popup and can call for help or investigate yourself.

that's Smart!

Harald Rudell

---

### Post by mgrusin on 2007-05-20
Hi Harald,

Thanks for the howto!  Works great on Feisty, except when testing, if I click in the popup to see "original smartd message" I get a blank window.  Is this normal for testing, or should I be seeing some text there?

Thanks again, -MG

---

### Post by soro2005 on 2007-10-12
Thanks a bunch. You might not care, but here's one more computer on which harald got a smart notifier ;-)

---

