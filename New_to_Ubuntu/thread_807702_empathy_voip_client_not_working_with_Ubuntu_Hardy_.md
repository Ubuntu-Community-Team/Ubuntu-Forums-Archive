---
title: "empathy voip client not working with Ubuntu Hardy 8.04"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by noworry on 2008-05-26
Hi,
   I had a very hard time finding an application which will be able to do pc to pc calls (voice chat) with google talk (gtalk) and I was happy to find something called empathy. But it is not working and shows the following error. 

Could you please help me in resolving this?

I am badly in need of something that can do voice chats with gtalk / yahoo messenger.

** (empathy:9174): DEBUG: mission_control_get_presence_actual: MC not running.
** (empathy:9174): DEBUG: mission_control_get_presence_message_actual: MC not running.
** (empathy:9174): DEBUG: mission_control_get_online_connections: MC not running.
** (empathy:9174): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:9174): DEBUG: mission_control_get_tpconnection: MC not running.

Ubuntu Hardy 8.04
empathy 0.23.1
Compaq nc6400 Laptop

Thanks a lot in advance.

---

### Post by noworry on 2008-05-26
Attached the screenshots of the empathy ui with network error and my configuration.

Please help me out in this !!

If you know any other software that does voice chat and works with Ubuntu, please let me know.

---

### Post by amendt on 2008-05-26
Make sure you have  telepathy-mission-control, telepathy-gabble, installed

I had to update my software sources to get empathy working.

---

### Post by noworry on 2008-05-27
Still its not working. I found that there is some package called telepathy-gnome and tried that. I was able to connect to yahoo, but call option is disabled. But gtalk is still not working, same old error !!!

---

### Post by toMeloos on 2008-07-12
Got the same problem.

```
$ empathy
/home/tom/.themes/Clearlooks-DarkOrange/gtk-2.0/gtkrc:58: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/tom/.themes/Clearlooks-DarkOrange/gtk-2.0/gtkrc:59: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/tom/.themes/Clearlooks-DarkOrange/gtk-2.0/gtkrc:60: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/tom/.themes/Clearlooks-DarkOrange/gtk-2.0/gtkrc:61: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
** (empathy:23883): DEBUG: mission_control_get_presence_actual: MC not running.
** (empathy:23883): DEBUG: mission_control_get_presence_message_actual: MC not running.
** (empathy:23883): DEBUG: mission_control_get_online_connections: MC not running.
** (empathy:23883): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:23883): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:23883): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:23883): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:23883): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:23883): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:23883): DEBUG: mission_control_get_connection_status: MC not running.
** (empathy:23883): DEBUG: mission_control_get_tpconnection: MC not running.
** (empathy:23883): DEBUG: mission_control_get_tpconnection: MC not running.
** (empathy:23883): DEBUG: mission_control_get_tpconnection: MC not running.
** (empathy:23883): DEBUG: mission_control_get_tpconnection: MC not running.
** (empathy:23883): DEBUG: mission_control_get_tpconnection: MC not running.

** (empathy:23883): WARNING **: Glade is missing widget 'entry_screenname'.
```

It doesn't seem to connect to GTalk, often it doesn't connect to MSN through Telepathy (if I want to use Haze, I can just as well use Pidgin) and I get no errors for AOL, ICQ and Yahoo

Haven't found a solution yet. Anyone?

---

### Post by sergiom99 on 2008-07-12
me too!
[http://ubuntuforums.org/showthread.php?t=819046&page=3](http://ubuntuforums.org/showthread.php?t=819046&page=3)

---

### Post by sergiom99 on 2008-07-13
Filed a Bug for Empathy:
[http://bugzilla.gnome.org/show_bug.cgi?id=542815](http://bugzilla.gnome.org/show_bug.cgi?id=542815)

---

### Post by sergiom99 on 2008-07-14
got it working... sort of.
please look the bug report>
[http://bugzilla.gnome.org/show_bug.cgi?id=542815](http://bugzilla.gnome.org/show_bug.cgi?id=542815)

Now gotta solve the crappy sound.

---

### Post by toMeloos on 2008-07-15
Please note that the issue raised by Noworry and confirmed by me seems to not be directly related to VOIP functionality. It is a generic issue with Mission Control integration into Empathy, which causes the application to be unable to login certain IM accounts. MSN seems to be affected most in my case.

p.s. I got GTalk to work. didn't add @gmail.com to my username before :(

---

### Post by bluegray on 2008-08-13
I think I got it working. Can anyone help me to test? I don't have any Gtalk contacts with a mic setup ;)

---

