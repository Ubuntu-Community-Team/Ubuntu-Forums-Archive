---
title: "I know I've been hacked but are these parts of log files proof?"
date: 2017-06-10
forum: New to Ubuntu
---

### Post by redhouse70 on 2017-06-10
Hi, I've been hacked for a couple months now, it's came to the situation where I just use LiveCD but I think they have such control of my network that doesn't matter, they can still log all the keys I'm pressing and even connect my wifi adapter to their modem which I think is strange.

Anyway I'm a complete noob so I will just ask if there is any thing suspicious about these couple of log excerpts.  Also, I ran rkhunter and I don't have permission to read it even though I am the Administrator.  Someone has given themselves higher privilidges.  Oh yeah, they also recently contacted me via speech despatcher when I was listening to YouTube.  They said they were going to shoot me and burn me.  I understand it could be just crazy kids messing but this has been two months and the power of their ability doesn't match up with such stalking.  I mean they hacked my android too.  That started flashing TTY tonight for the first time I've ever seen it but I never heard any sound.  There is mention of TTY in this log file I looked at in the Security folder.

Forgive me if this is a normal access.conf.  I just thought all the specifics looked suspicious.

```
# Login access control table.
#
# Comment line must start with "#", no space at front.
# Order of lines is important.
#
# When someone logs in, the table is scanned for the first entry that
# matches the (user, host) combination, or, in case of non-networked
# logins, the first entry that matches the (user, tty) combination.  The
# permissions field of that table entry determines whether the login will
# be accepted or refused.
#
# Format of the login access control table is three fields separated by a
# ":" character:
#
# [Note, if you supply a 'fieldsep=|' argument to the pam_access.so
# module, you can change the field separation character to be
# '|'. This is useful for configurations where you are trying to use
# pam_access with X applications that provide PAM_TTY values that are
# the display variable like "host:0".]
#
#     permission : users : origins
#
# The first field should be a "+" (access granted) or "-" (access denied)
# character.
#
# The second field should be a list of one or more login names, group
# names, or ALL (always matches). A pattern of the form user@host is
# matched when the login name matches the "user" part, and when the
# "host" part matches the local machine name.
#
# The third field should be a list of one or more tty names (for
# non-networked logins), host names, domain names (begin with "."), host
# addresses, internet network numbers (end with "."), ALL (always
# matches), NONE (matches no tty on non-networked logins) or
# LOCAL (matches any string that does not contain a "." character).
#
# You can use @netgroupname in host or user patterns; this even works
# for @usergroup@@hostgroup patterns.
#
# The EXCEPT operator makes it possible to write very compact rules.
#
# The group file is searched only when a name does not match that of the
# logged-in user. Both the user's primary group is matched, as well as
# groups in which users are explicitly listed.
# To avoid problems with accounts, which have the same name as a group,
# you can use brackets around group names '(group)' to differentiate.
# In this case, you should also set the "nodefgroup" option.
#
# TTY NAMES: Must be in the form returned by ttyname(3) less the initial
# "/dev" (e.g. tty1 or vc/1)
#
##############################################################################
#
# Disallow non-root logins on tty1
#
#-:ALL EXCEPT root:tty1
#
# Disallow console logins to all but a few accounts.
#
#-:ALL EXCEPT wheel shutdown sync:LOCAL
#
# Same, but make sure that really the group wheel and not the user
# wheel is used (use nodefgroup argument, too):
#
#-:ALL EXCEPT (wheel) shutdown sync:LOCAL
#
# Disallow non-local logins to privileged accounts (group wheel).
#
#-:wheel:ALL EXCEPT LOCAL .win.tue.nl
#
# Some accounts are not allowed to login from anywhere:
#
#-:wsbscaro wsbsecr wsbspac wsbsym wscosor wstaiwde:ALL
#
# All other accounts are allowed to login from anywhere.
#
##############################################################################
# All lines from here up to the end are building a more complex example.
##############################################################################
#
# User "root" should be allowed to get access via cron .. tty5 tty6.
#+ : root : cron crond :0 tty1 tty2 tty3 tty4 tty5 tty6
#
# User "root" should be allowed to get access from hosts with ip addresses.
#+ : root : 192.168.200.1 192.168.200.4 192.168.200.9
#+ : root : 127.0.0.1
#
# User "root" should get access from network 192.168.201.
# This term will be evaluated by string matching.
# comment: It might be better to use network/netmask instead.
#          The same is 192.168.201.0/24 or 192.168.201.0/255.255.255.0
#+ : root : 192.168.201.
#
# User "root" should be able to have access from domain.
# Uses string matching also.
#+ : root : .foo.bar.org
#
# User "root" should be denied to get access from all other sources.
#- : root : ALL
#
# User "foo" and members of netgroup "nis_group" should be
# allowed to get access from all sources.
# This will only work if netgroup service is available.
#+ : @nis_group foo : ALL
#
# User "jane" should get access from ipv4 net/mask
#+ : jane : 127.0.0.0/24
#
# User "jane" should get access from ipv4 as ipv6 net/mask
#+ : jane : ::ffff:127.0.0.0/127
#
# User "jane" should get access from ipv6 host address
#+ : jane : 2001:4ca0:0:101::1
#
# User "jane" should get access from ipv6 host address (same as above)
#+ : jane : 2001:4ca0:0:101:0:0:0:1
#
# User "jane" should get access from ipv6 net/mask
#+ : jane : 2001:4ca0:0:101::/64
#
# All other users should be denied to get access from all sources.
#- : ALL : ALL
```


This us the group file from the same folder.  Sorry for th length of them but I have absolutely no clue how to combat this hack.  Even buying a new computer would probably be hacked in 5 minutes because they come through the network.

They will know I have posted this as they have a keylogger and also can just watch what I'm doing because even the screen keyboards don't seem to last long.  They wait till I've got everything looking good again (like all my passwords in Lasspass and multifactor auth then all of a sudden all my passwords change)  I have no idea why because I haven't annoyed anyone that much.  Well, maybe someone on here by posting such a large amount of text straight away.

Oh yeah when I reset my modem and go to change the password to log into it, it's already been changed by the time I finish and I can touch type at a decent rate.  I'm tethering my phone because of it but God knows what damage they are doing to that all the time it's on the network.

```
#
# This is the configuration file for the pam_group module.
#

#
# *** Please note that giving group membership on a session basis is
# *** NOT inherently secure. If a user can create an executable that
# *** is setgid a group that they are infrequently given membership
# *** of, they can basically obtain group membership any time they
# *** like. Example: games are allowed between the hours of 6pm and 6am
# *** user joe logs in at 7pm writes a small C-program toplay.c that
# *** invokes their favorite shell, compiles it and does
# *** "chgrp play toplay; chmod g+s toplay". They are basically able
# *** to play games any time... You have been warned. AGM
#

#
# The syntax of the lines is as follows:
#
#       services;ttys;users;times;groups
#
# white space is ignored and lines maybe extended with '\\n' (escaped
# newlines). From reading these comments, it is clear that
# text following a '#' is ignored to the end of the line.
#
# the combination of individual users/terminals etc is a logic list
# namely individual tokens that are optionally prefixed with '!' (logical
# not) and separated with '&' (logical and) and '|' (logical or).
#
# services
#       is a logic list of PAM service names that the rule applies to.
#
# ttys
#       is a logic list of terminal names that this rule applies to.
#
# users
#       is a logic list of users or a netgroup of users to whom this
#       rule applies.
#
# NB. For these items the simple wildcard '*' may be used only once.
#     With netgroups no wildcards or logic operators are allowed.
#
# times
#       It is used to indicate "when" these groups are to be given to the
#       user. The format here is a logic list of day/time-range
#       entries the days are specified by a sequence of two character
#       entries, MoTuSa for example is Monday Tuesday and Saturday. Note
#       that repeated days are unset MoMo = no day, and MoWk = all weekdays
#       bar Monday. The two character combinations accepted are
#
#               Mo Tu We Th Fr Sa Su Wk Wd Al
#
#       the last two being week-end days and all 7 days of the week
#       respectively. As a final example, AlFr means all days except Friday.
#
#       Each day/time-range can be prefixed with a '!' to indicate "anything
#       but"
#
#       The time-range part is two 24-hour times HHMM separated by a hyphen
#       indicating the start and finish time (if the finish time is smaller
#       than the start time it is deemed to apply on the following day).
#
# groups
#    The (comma or space separated) list of groups that the user
#    inherits membership of. These groups are added if the previous
#    fields are satisfied by the user's request
#
# For a rule to be active, ALL of service+ttys+users must be satisfied
# by the applying process.
#

#
# Note, to get this to work as it is currently typed you need
#
# 1. to run an application as root
# 2. add the following groups to the /etc/group file:
#        floppy, play, sound
#

#
# Here is a simple example: running 'xsh' on tty* (any ttyXXX device),
# the user 'us' is given access to the floppy (through membership of
# the floppy group)
#

#xsh;tty*&!ttyp*;us;Al0000-2400;floppy

#
# another example: running 'xsh' on tty* (any ttyXXX device),
# the user 'sword' is given access to games (through membership of
# the sound and play group) after work hours.
#

#xsh; tty* ;sword;!Wk0900-1800;sound, play
#xsh; tty* ;*;Al0900-1800;floppy

#
# yet another example: any member of the group 'admin' running
# 'xsh' on tty*, is granted access (at any time) to the group 'plugdev'
#

#xsh; tty* ;%admin;Al0000-2400;plugdev

#
# End of group.conf file
#
```

Thanks for reading and I hope you can give me some kind of advice even though the hackers will be reading it too.  There must be some way to stop them because it just seems too powerful and would bring down major networks.  I mean Linux and Android are supposed to be quite safe.  The phone isn't rooted either but they always come back after a factory reset.

They'll probably wreck all my firmware now and nothing will work at all.  I had to ask someone for advice though, it's been too long and death threats even if funny in a computer voice are scary when it's a stalker.

---

### Post by smd3 on 2017-06-10
These are sample configuration files, with example lines.  All the lines are commented out, and don't do anything.

---

### Post by Habitual on 2017-06-10
Reset your router?

---

### Post by LastDino on 2017-06-11
> **Habitual said:**
> Reset your router?

^
This
Also, take yourself off the internee, download and install security tools like firewall and stuff with wired connection somewhere else. Then bring back the able machines to form your home network. 

You will do good to just watch package transfer and probably block all the ports and IP's you don't have explanation for.  Also, hacking Android is relatively very easy, that is usually the first divice to get compromised along with Windows on network, so restrict their access to guest in future.

Well, with death threats and all, even if its a joke, I would go and contact cyber crime team in your country. That is pretty serious deal.

---

### Post by HermanAB on 2017-06-11
Why do you think you've been hacked?

Install Linux properly, use long >12 character passwords, relax a bit and enjoy your computer system.

---

### Post by redhouse70 on 2017-06-16
Ok I'm not going to go into any detail because I was sharply reminded no  matter how cool this guy/crew are to talk to they are black hatters  first and foremost.  They posted a cookie with my comment on this page.   It was like a message saying we see everything, do not make us angry.  I  tried to save it but they took it away.

Then my Lastpass account  was hacked, password and email changed which means it cannot be deleted  because I was dumb enough to put my security email in there duh.  But  Lastpass&#347; policy is they will never delete an account, I think because  of the sensitive data and possible impersonation.

But the killer  was when I went to reset my modem, there was a key on it!  It couldn be  reset and I had no idea of the password, they had total control of it.   My god I understand they maybe don like people discussing a hacking  situation involving them but they have to understand I want to know  what&#347; happening to my computer.  Why would they totally take over my  modem anyway, of course I was going to order a new one.  I cant plug it  in yet though because they are too fast for me, might even have a script  that enters the modem once Ive put the password in.

Is it  possible to put a key on a modem if its connected by ethernet?  If they  put a key on again which I assume they will cause this will probably make them angry, is there any way I can access my modem settings and  remove the key or better still put my own on?  Does the internet work  normally with a private key on the modem?  I was thinking every site  would have to have the public key?

Any ideas as to what the name of the keylogger might be?  I tried to gain Superuser but couldnt.  

This  is how McGregor is going to feel when he gets in a boxing ring with  Mayweather.  Crazy guy, every punch will have permission denied.  In the  Octagon it would be the other way around.  You think Mayweather is  going to go anywhere near that and get messed up silly?  As much chance  as the Patriots playing the All Blacks at Rugby Union.  Brady is the  best thrower of a ball Ive seen but without protective gear you do not  want sacked by 3 Mauris.  I think McGregor should wear an NFL uniform,  give him a chance.

Anyway, sorry for posting long code again but  its confusing me why I cant install rkhunter when it was no problem  before.  Is this basically saying let rkhunter run but if it sees some  specific files then remove them from the log (which I dont have  permission to read haha).  In some cases it looks as if its just saying  report Error file not found which is mostly what it does even after  extracting it as normal.

Im hoping because this is a LiveCD I  cant be messed up too bad if they get all Joe Pesci and want to display  their skills by bricking my machine?  Btw I was using the Ubuntu onboard  keyboard to input passwords to Lastpass so its very obvious a  sophisticated keylogger can run on Linux.

Does Spyshelter for  Windows really work?  I cant really put a key on my modem because they  will log the password dear God I am in an impossible situation.  Can you  believe the engineer had never heard of a key on a modem before?  These  guys are good, Im sure it&#347; a crew of hackers now with bigger ideas  after practising on my Linux.  Probably dont get many chances to inspect  as Superuser but the virus was installed via Windows.  Why didnt I  change before, Ubuntu is so much better than Windows, nice and simple  with plenty of software.  Wonder if yubikey is a safe way to  authenticate?  Indicator keyboard is listed as a program that will run  now and then.  Messages too.  Is there any way to make a list of all  http remote addresses that files are scheduled to be sent to?  Those  cookies definitely were sent, no way they watch the machine that much.   There are some guys from maybe Eastern Europe leaving messages ¨Please  add LiveCD to hard disk¨ haha I am dumb but I bet within 5 minutes there  would be a key on that too!

Should I root my android and protect it with Cyanogen mods and tools?  I feel like rooting anything is asking for trouble.
I  need a white hat to remote connect with.  I dont want to find out who  it is though, like Mr Robot finding the Tor site.  I just want to find  out about security.  Now I just seen a web page from 2013 saying Reaver  can crack WPA2?  What hope is there if the best security was cracked 4  years ago?  I think keys are much harder depending on length of  password, like 63 characters would take a while.  I did that on my  modem.  It lasted about 15 minutes hehe.  

You think this script suggests rkhunter is a feared program among hackers?  Chkroot and Clamav dont get so much attention.

Sorry  for the long post, thanks for reading if you did and hope you can give  me some clues.  Even though they will also see any advice they should  appreciate the challenge and the fact I need to know what&#347; happening.

I hope there is nothing personal or identifying in this script, I couldnt see anything but Ill remove it straight away if there is.  I doubt it because he would know I would read it and all logs are cleared completely.

---

### Post by QIII on 2017-06-16
I do not believe we can help with this.  I suggest professional help.

Thread closed.

---

