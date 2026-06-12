---
title: "Create /add Workspaces"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by olhat on 2008-09-17
I would like to add more workspaces (viewports ???) but I get error message when I try to do it by the Ubuntu manual.  I did read someplace that you can right click “workspace shifter” to add workspaces but I don't know what and where is this shifter.  

My vanished/crashed/GRUBbyly deceased previous Ubuntu with Kubuntu-desktop did have eight workspaces that I somehow stumbled upon and happily shifted between with hotkeys for a cpl of days before the catastrophe.

There is something else fishy too with this 8.04.  I don't have Wine for instance on this one by default but that previous one had that, or at least I think so.:confused:




GCONFTOOL error message:
 gconftool-2 --direct \
>   --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory \
>   --type int \
>   --set /apps/metacity/general/num_workspaces 8

(gconftool-2:8862): GConf-WARNING **: None of the resolved addresses are writable; saving configuration settings will not be possible

Error setting value: Unable to store a value at key '/apps/metacity/general/num_workspaces', as the configuration server has no writable databases. 
There are some common causes of this problem: 
1)your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found
2)somehow we mistakenly created two gconfd processes 
3)3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 
4)4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. 


If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf

---

### Post by aeiah on 2008-09-17
the workspace shifter (or whatever its called) is the bit that's usually at right hand side on the bottom panel. a series of squares. i think be default ubuntu just has two viewports but i dunno. if it isnt there you can always rightclick on a blank bit of panel, go to add to panel, and select the workspace switcher and add it. you should get a config menu if you right click on it that'll let you set the number of workspaces. i think in some instances this conflicts with compiz settings because you can set it from there also.

the 5 boxes here is the workspace switcher in gnome:

[img]http://wazem.dyndns.org/temp/ubuntu-forum/gnome-panel-dialog/workspace.png[/img]

and this is the small config window for them:
[img]http://news.cnet.com/i/bto/20080324/03_25_08UbuntuWorkspace1.jpg[/img]

---

### Post by aeiah on 2008-09-17
as for the errors, have you reinstalled ubuntu but kept the same home partition, or attempted to copy over settings files from your previous installation or anything?

---

### Post by olhat on 2008-09-17
> **aeiah said:**
> the workspace shifter (or whatever its called) is the bit that's usually at right hand side on the bottom panel. a series of squares. i think be default ubuntu just has two viewports but i dunno. if it isnt there you can always rightclick on a blank bit of panel, go to add to panel, and select the workspace switcher and add it. you should get a config menu if you right click on it that'll let you set the number of workspaces. i think in some instances this conflicts with compiz settings because you can set it from there also.

the 5 boxes here is the workspace switcher in gnome:

[img]http://wazem.dyndns.org/temp/ubuntu-forum/gnome-panel-dialog/workspace.png[/img]

and this is the small config window for them:
[img]http://news.cnet.com/i/bto/20080324/03_25_08UbuntuWorkspace1.jpg[/img]


Workspaces solved thankyou.  Now I remember how I got those working the first time around. Real killer app btw.:)

---

### Post by olhat on 2008-09-17
> **aeiah said:**
> as for the errors, have you reinstalled ubuntu but kept the same home partition, or attempted to copy over settings files from your previous installation or anything?


My new Ubuntu is now equipped with Kubuntu-desktop like the departed one.  This previous Ubuntu is on a separate hard disk that works perfectly well except for small linux partition that is inaccessible without special tools like Diskinternals Linux Recovery for Windows.  Later I need to try access the disk for my Thunderbird settings and mails (*.default) that I used for about ten days without saving anyplace else and without even having read all the mails I ought have read.  

This new Ubuntu I'm going to set up with my old Windows Thunderbird profile that has my mail history except for those missing ten days.  Some difficulties combining those two are expected even if I would be able to retrieve the old Linux profile.

Those error messages I don't care too much about now that I have Workspaces in place of course supposing that nothing else arises.

Now that you mention there was one question mark in Kubuntu installation also.  It ended a bit fuzzily without any words like DONE, SUCCESS or FAILURE.  The last line in terminal was sth like "initiating this or that":confused: and after that there was this start line"olhat@nyl:~$".  Everything seems to be working but why not a clear notification that install is done.

---

