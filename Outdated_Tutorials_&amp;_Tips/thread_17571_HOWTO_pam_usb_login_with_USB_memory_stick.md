---
title: "HOWTO: pam_usb login with USB memory stick"
date: 2005-03-01
forum: Outdated Tutorials &amp; Tips
---

### Post by weazle on 2005-03-01
Howto : pam_usb login with USB memory stick
=================================

Introduction

This relates to a project of mine, a Single Sign On solution using a usb-memory stick. An advantage is when you have too many passwords to remember, SSO brings this back to one password and one point where you have to login and then use these credentials to access all your applications and resources. For example your webmail, forums etc.

Goals:

[list]
[*]Login locally with your usb memory stick on the console (this howto)
[*]Login locally with your usb memory stick on XDM,GDM,KDM
[*]The possibility to remotely login (via ssh) with the the usb memory stick
[*]A layer build on top of the linux login process (locally/remote) which handles the authenication between the the usb memory stick and the keyserver/ Certificate Authority
[/list] 

Comments are welcome :-)

**PAM_USB**

1. Get **pam_usb** from the website [http://www.pamusb.org/](http://www.pamusb.org/) latest version is 0.3.2 

2. **Get all the packages needed by pam_usb**, it depends on what you have installed already, but I needed: 

[list]
[*]libncurses5-dev
[*]libreadline4-dev
[/list] 
 
3.** Unpack and install the source**, do a:

```

tar xvzf pam_usb-0.3.2.tar.gz
./configure
make
make install

``` 

4. **Read** the Quickstart and Options files on [http://www.pamusb.org/](http://www.pamusb.org/)

5. **Make the keys on the usb memory stick**, as described in the Quickstart. I made one for root and one for my normal user account. I used a DSA keypair of 4096 bits  :mrgreen:

```

usbadm keygen [/path/to/mounted/usbmemorystick] [username] [bits] 

``` 

**Check if the keys are made correctly**. They are in the .auth directory on the usb memory stick.

Simply by issueing a command like 
```

more .auth/[username].[hostname]

```

If it spits out all kind of DSA code gibberish, the key is ok.

6. **BACKUP** all the /etc/pam.d files somewhere, in case something goes wrong.

7. **Edit** /etc/pam.d/login. I added the following line (copy-pasted it from some gentoow forum). Check whether your filesystem is vfat, otherwise replace fs= with your filesystem, e.g reiserfs or ext3 or whatever.

```

auth       required   pam_usb.so fs=vfat check_device=-1 check_if_mounted=-1 force_device=/dev/sda log_file=/var/log/pam_usb.log

``` 

8. **Make the logfile** (for debugging purposes)

make a empty file:
```

vi /var/log/pam_usb.log

```
save & exit.

**My /etc/pam.d/login file:**
```

#
# The PAM configuration file for the Shadow `login' service
#
# NOTE: If you use a session module (such as kerberos or NIS+)
# that retains persistent credentials (like key caches, etc), you
# need to enable the `CLOSE_SESSIONS' option in /etc/login.defs
# in order for login to stay around until after logout to call
# pam_close_session() and cleanup.
#

# Outputs an issue file prior to each login prompt (Replaces the
# ISSUE_FILE option from login.defs). Uncomment for use
# auth       required   pam_issue.so issue=/etc/issue

# Disallows root logins except on tty's listed in /etc/securetty
# (Replaces the `CONSOLE' setting from login.defs)
#auth       requisite  pam_securetty.so

# Disallows other than root logins when /etc/nologin exists
# (Replaces the `NOLOGINS_FILE' option from login.defs)
#auth       requisite  pam_nologin.so

# This module parses /etc/environment (the standard for setting
# environ vars) and also allows you to use an extended config
# file /etc/security/pam_env.conf.
# (Replaces the `ENVIRON_FILE' setting from login.defs)
auth       required   pam_env.so

auth       required   pam_usb.so fs=vfat check_device=-1 check_if_mounted=-1 force_device=/dev/sda log_file=/var/log/pam_usb.log

# Standard Un*x authentication. The "nullok" line allows passwordless
# accounts.
@include common-auth

# This allows certain extra groups to be granted to a user
# based on things like time of day, tty, service, and user.
# Please uncomment and edit /etc/security/group.conf if you
# wish to use this.
# (Replaces the `CONSOLE_GROUPS' option in login.defs)
# auth       optional   pam_group.so

# Uncomment and edit /etc/security/time.conf if you need to set
# time restrainst on logins.
# (Replaces the `PORTTIME_CHECKS_ENAB' option from login.defs
# as well as /etc/porttime)
account    requisite  pam_time.so

# Uncomment and edit /etc/security/access.conf if you need to
# set access limits.
# (Replaces /etc/login.access file)
account  required       pam_access.so

# Standard Un*x account and session
#@include common-account
@include common-session

# Sets up user limits, please uncomment and read /etc/security/limits.conf
# to enable this functionality.
# (Replaces the use of /etc/limits in old login)
# session    required   pam_limits.so

# Prints the last login info upon succesful login
# (Replaces the `LASTLOG_ENAB' option from login.defs)
#session    optional   pam_lastlog.so

# Prints the motd upon succesful login
# (Replaces the `MOTD_FILE' option in login.defs)
#session    optional   pam_motd.so

# Prints the status of the user's mailbox upon succesful login
# (Replaces the `MAIL_CHECK_ENAB' option from login.defs). You
# can also enable a MAIL environment variable from here, but it
# is better handled by /etc/login.defs, since userdel also uses
# it to make sure that removing a user, also removes their mail
# spool file.
#session    optional   pam_mail.so standard noenv
@include common-password

```
9. Test stuff
Depending on how you set the mode on pam_usb, play a little around with it. There are 3 modes according to the Quickstart:

1. Unique 

auth       required        pam_usb.so

2. Alternative

auth       sufficient      pam_usb.so

3. Additional

auth       required        pam_usb.so

I found out that in Additional mode you cannot login if the usb memory stick isn't there (doh') and that you _can_ login if the stick is present. 

8. **If things go wrong**

Well, I if you stare at the screen at errors like this: 
```

Authentication token is no longer valid; new one required.

```
and you locked yourself out because you didn't leave a root terminal open  :shock:  

***don't panic***

There are a couple of things you can do:
[INDENT]
1. blame someone else
2. reboot into single user mode.I have GRUB installed as bootmanager so in the GRUB menu upon boot I edited the line starting the kernel and added the word "single" to it. Now your system will boot in single-user mode and you can login and repair the damage.[/INDENT]

// end

---

### Post by steil on 2005-03-21
Other packages needed on a fresh ubuntu install:
GCC (Obviously)
libssl-dev
libpam0g-dev

---

### Post by AndEat on 2005-06-24
I've been trying to install....installed everything mentioned so far....getting the following:

make all -C src
make[1]: Entering directory `/home/temp/pam_usb-0.3.2/src'
gcc -c -Wall -O2 -fPIC -o auth.o auth.c
In file included from auth.c:23:
dsa.h:4:26: openssl/rand.h: No such file or directory
dsa.h:5:25: openssl/pem.h: No such file or directory
dsa.h:6:24: openssl/bn.h: No such file or directory
dsa.h:7:25: openssl/dsa.h: No such file or directory
In file included from auth.c:23:
dsa.h:9: error: syntax error before '*' token
dsa.h:9: warning: type defaults to `int' in declaration of `import_public_key'
dsa.h:9: warning: data definition has no type or storage class
dsa.h:10: error: syntax error before '*' token
dsa.h:10: warning: type defaults to `int' in declaration of `import_private_key'
dsa.h:10: warning: data definition has no type or storage class
dsa.h:11: error: syntax error before '*' token
auth.c: In function `authenticate':
auth.c:182: error: `DSA' undeclared (first use in this function)
auth.c:182: error: (Each undeclared identifier is reported only once
auth.c:182: error: for each function it appears in.)
auth.c:182: error: `private' undeclared (first use in this function)
auth.c:183: error: `public' undeclared (first use in this function)
auth.c:214: warning: implicit declaration of function `DSA_free'
make[1]: *** [auth.o] Error 1
make[1]: Leaving directory `/home/temp/pam_usb-0.3.2/src'
make: *** [pam_usb] Error 2

[COLOR=DarkOrange]This is a bit above my head right now[/COLOR]...can anyone point me in the direction to help me solve this?

---

### Post by weazle on 2005-06-25
hmm, my initial guess would be to install the libraries for openssl, hope this will help 

libssl-dev - SSL development libraries, header files and documentation

---

### Post by nfvindaloo on 2005-10-30
As the previous posts explianed you need the following packages installed

libncurses5-dev
libreadline4-dev
libssl-dev
libpam0g-dev

The lines

dsa.h:4:26: openssl/rand.h: No such file or directory
dsa.h:5:25: openssl/pem.h: No such file or directory
dsa.h:6:24: openssl/bn.h: No such file or directory
dsa.h:7:25: openssl/dsa.h: No such file or directory

Are complaining that libssl-dev is not installed!

---

### Post by andrewsawyer on 2005-11-16
Can someone help me please?

I have installed pam_usb (0.3.3) in exactly the same way that you mention.  I have generated the key, and checked it is there.  I have exactly the same login file as you.  Whether the USB stick is in or not, when I boot my computer and it gets to the Gnome login, I am still prompted for my details.  I type in my username, followed by my password, and then it logs me in.

Am I missing something?  It's as if I haven't done anything at all to my system - it just behaves as normal - whether the USB stick is in my computer or not.

Should I type something in place of my login name to activate the pam_usb?

I would appreciate any help.

Andy

[edit]I've just made a key for root.  Typing sudo su takes me straight to root without needing a password.  So it is obviously working on the terminal side of things.  So can someone please explain how I get it to work with the GUI password bits?[/edit]

UPDATE...

Sorry to keep with the questions!

I have the line:
```
auth       required   pam_usb.so fs=vfat check_device=-1 check_if_mounted=-1 force_device=/dev/sda log_file=/var/log/pam_usb.log
```

As per this howto.  Unless I'm mistaken, using the 'required' option would mean one of two things.  Both of which would require my USB stick to be mounted.  Either typing sudo su would just let me straight in using the USB key, or I would get prompted for a password AND I would have to have the key mounted.

So how come, if I reboot without the USB stick in my PC, and type sudo su, I am prompted for my password, and after giving it all is fine?  Should it not check to make sure that my key is correct too?

Andy

---

### Post by mswoon on 2006-03-01
I got su and sudo su - to work with pam_usb. But not GDM. Odd. The result is the same for me even on Fedora Core 3, using pam_usb 0.3.3.

---

### Post by mswoon on 2006-03-03
Added allow_remote to the system-auth in Fedora and common-auth in Ubuntu and now it works for GDM. Hooray!

... but xscreensaver refused to work ... why?

---

### Post by pek on 2006-07-14
i do not understand the statement above :confused:

---

### Post by defishguy on 2006-07-14
I lost my track on where I found these, so if anyone knows the author of the deb's please give him my KUDOS!  I rec'd many compiler errors in dapper with the latest version, and stumbled on these.  I've uploaded them to a free file sharing site so that others can enjoy the dbl click install goodness.

[http://www.4shared.com/file/2511990/b77571ae/pamusb-doc_033-1_all.html](http://www.4shared.com/file/2511990/b77571ae/pamusb-doc_033-1_all.html)

[http://www.4shared.com/file/2511986/470de5da/pamusb_033-1_i386.html](http://www.4shared.com/file/2511986/470de5da/pamusb_033-1_i386.html)

Enjoy!

fish

---

### Post by jeromerousselot on 2006-08-21
Same thing for me, I could make login work with pam_usb 0.3.3 but not gdm.

I activated logging to a file :
auth    sufficient      pam_usb.so log_file=/var/log/pam_usb.log

both in /etc/pam.d/login and in /etc/pam.d/gdm

When I log with login, I type my username and it immediately logs me in. This generates some messages in the log file.

With gdm, I still get the password request, and nothing is writtent to the log file.

I believe that the ordering of the options is significant.

My /etc/pam.d/gdm file :

#%PAM-1.0

auth required pam_env.so

# pam usb
auth    sufficient      pam_usb.so log_file=/var/log/pam_usb.log

auth    requisite       pam_nologin.so
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password

---

### Post by jeromerousselot on 2006-08-21
It didnt work for me and I don't understand why it should work

Maybe xscreensaver starts and then immediately relogs you because the usb key is there ?

---

### Post by arcanus on 2006-08-22
you need to put

```
auth sufficient pam_usb.so **allow_remote=1**
```

in aswell. That solved the "Authentication denied: Remote user" error i got

EDIT

Depends on 

libncurses5-dev
libreadline5-dev
libssl-dev
libpam0g-dev

/EDIT

---

### Post by kk_sriram on 2007-02-01
can anyone pls tell me where can i use pam_usb other than with "linux login"?
Also i'm trying to understand the source code,any help(docs) will indeed be appreciated.

Regards,
Sriram

---

### Post by nemin on 2007-02-22
Perhaps someone is willing to post all /etc/pam.d/* files that matter, working for both login and GDM? 
That would be appreciated..

---

### Post by nemin on 2007-02-22
Looks like I've got it now, just add the following just right above the pam_unix line in /etc/pam.d/common-auth
```
auth       sufficient   pam_usb.so fs=vfat force_device=/dev/sda log_file=/var/log pam_usb.log allow_remote=1
```

---

### Post by MaleqAlhaq on 2007-03-30
Hi!
I followed the steps in this How To and logging in works just fine! Thank you!
But there is one thing I'm missing:
Can I unlock a kscreensaver with pam_usb ? I have seen this
[http://users.own-hero.net/~decoder/index.php/?s=pam_usb&submit=](http://users.own-hero.net/~decoder/index.php/?s=pam_usb&submit=)
Which does indicate that it works, but I can't get the script (lock.sh) to work. It just terminates on the command line and neither locks nor unlocks the screensaver. I modified the commands for starting and stopping the screensaver to fit to the KUbuntu setup and they do work on the command line (invoked manually, without the script). 
Can anybody point me to fitting resource? 

Thanks in advance!

Cheers
MaleqAlhaq

P.S.: I did apply the patches mentioned in the post, but it didn't improve anything...

---

### Post by aarcane on 2007-07-06
so the latest pam_usb is 0.4.1.  Compilation is a bit tricky, but with a little brain usage, it works.  install is simpler than ever.  it really is as easy as following the quickstart guide on the howto page at pamusb.org.  the only thing that needs mentioning for ubuntu now is that you MUST specify <option name="quiet">true</option> in the defaults section of pamusb.conf.

---

### Post by jouva on 2008-02-06
The way of using pam_usb has completely changed! Most of those parameters are no longer needed in the pam configuration file as they seem to now be in a config file. And the way the module authenticates seems to have changed too and no longer requires you generate a key file (it does so on its own).

I am not sure if these packages are available for anything prior to Gutsy, but here is how I did it:

```
$ sudo apt-get install libpam-usb pamusb-tools
$ sudo pamusb-conf --add-device DeviceNickname
$ sudo pamusb-conf --add-user yourusername
```

The DeviceNickname parameter can be whatever you wish. It will find the flash drive on its own.

Next, open up /etc/pam.d/common-auth
The last line should be something along the lines of:
```
auth    required    pam_unix.so nullok_secure
```
Above this, add:
```
auth    sufficient    pam_usb.so
```
Save the file and you're done! Try logging into a TTY or into your X Session with G/K/XDM. Simply enter your username and it should log you right in. It will even work when you use sudo and not require a password.

Other things of note:
[LIST]
[*]If you wish to use this as a required piece of hardware ALONG WITH a password, use "required" instead of "sufficient" in the pam file.
[*]If you wish to use pam_usb in only SPECIFIC modules, put the line in the specific modules. common-auth is a generic file that will work for tty login, gdm and sudo.
[*]ANOTHER method of excluding specific modules against pam_usb authentication is to have pam_usb simply disable specific services for authentication. For example, to disable using pam_usb to authenticate for sudo:
```

<services>
    <service id="sudo">
        <option name="enable">false</option>
    </service>
</services>

```
[*]The pamusb-tools package includes a program called "pamusb-agent". This allows you to state that you wish to run certain tasks (i.e.: lock/unlock the computer) upon removing or re-inserting the flash drive. To do so, you must manually edit /etc/pamusb.conf and enter the information necessary. Here is an example to use. They provided an example but the parameters for the application are wrong.
```

    <users>
        <user id="jouva">
        <device>
                MemorexTraveldrive256
        </device>
        <agent event="lock">gnome-screensaver-command --lock</agent>
        <agent event="unlock">gnome-screensaver-command --deactivate</agent>
        </user>
    </users>

```
Then simply add pamusb-agent to your startup configuration within Gnome/KDE/Whatever.
[/LIST]

I hope that about covers it!

---

### Post by ninjak on 2008-04-21
Hi. I followed all the steps, but after the (successfull) login, NetworkManager (via gnome-keyring) ask me for my account's password. Anyone can suggest me what I have to change/use, please?

---

### Post by jouva on 2008-04-26
FYI, if you have updated from 7.10 Gutsy to 8.04 Hardy and cannot use pam_usb anymore, there's a possibility that the Vendor Name of your drive may have changed. For example: I have a 256 Meg Sony flash drive. Originally it was listed as "SONY". Now it is listed as "Sony Corp.". Use the pamusb-config utility to make these changes. Though a potentially simple way is to simply run the utility with the --add-device param, look at the vendor name and change it accordingly.

---

### Post by mriedel on 2008-07-12
I use pam_usb in sufficient mode for common-auth. I'd prefer to have some kind of notification or confirmation prompt or window respectively when pam_usb is used to authenticate. Without it, my setup practically grants root to any process as long as the usb stick is plugged in. Starting up synaptic, for example, leads to immediate pam_usb authentication. Had I not used it before, I wouldn't even know that I just granted root privileges to it.

---

### Post by mriedel on 2008-07-14
bump

---

### Post by jouva on 2008-07-14
I'm not sure if this is the right place to ask for that. But you may want to ask for that on [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)  however considering there are very few people that use it, it may not get bumped up a lot.

---

### Post by Brothertucker on 2009-02-02
I am kind of a beginner and was wondering if you could give me detailed instructions on how to install PAM_USB.

---

### Post by jouva on 2009-02-02
> **Brothertucker said:**
> I am kind of a beginner and was wondering if you could give me detailed instructions on how to install PAM_USB.

Post #18 in this thread should give a decent amount of information.

---

### Post by SnappyU on 2009-03-15
Everything is working fine ... but note the following.
Tested on Ubuntu 8.10

PAM Module ***IMPORTANT***
According to the site above:
Locate the following line on /etc/pam.d/common-auth or /etc/pam.d/system-auth:
> auth    required        pam_unix.so nullok_secure

And change it to look something like that:
> auth    sufficient      pam_usb.so
auth    required        pam_unix.so nullok_secure


For Ubuntu 8.10, the above would cause strange behaviour, instead change it to the following:

> auth    sufficient      pam_usb.so
auth	[success=1 default=ignore]	pam_unix.so nullok_secure


---

### Post by HuckBerry on 2009-08-15
So I've been fiddling around with pam_usb for quite some time now and I have it working in many cases. I can login with the graphic welcome screen, I can bypass my password when resuming from xscreensaver and I can su,sudo su,gksudo just fine.
     
     My issue is that all of this works only when the device is mounted. But the pam_usb site clearly states the device doesn't have to be mounted in order for authentication to take place. This defeats the primary function of pam_usb which is: sitting down, plugging in a usb device, and logging in with no password.

     Should I have also altered fstab or a related file so the device would mount upon insertion, even if no user is logged in? Or does pam_usb just not have the proper authority to mount devices?

~Huckle Berry

---

### Post by M4NIC on 2009-10-07
I have a completely different problem. Ive installed pam_usb through apt-get and it seems to be installed ok. However, when I try to add a device as per the [instructions]("http://pamusb.org/doc/quickstart#devices_and_users"), I get the following errors:

```
root@ubuntu:~# pamusb-conf --add-device SD1
Traceback (most recent call last):
  File "/usr/bin/pamusb-conf", line 258, in <module>
    '/org/freedesktop/Hal/Manager')
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.6/dbus/connection.py", line 622, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files

```

Anybody has anything similar? I can verify that the dependencies for pamusb-conf are met. I have tried to cover the dependencies of pamusb itself (libxml2, PAM, HAL and pmount) but arent these relevant only when compiling? Ive also updated dbus but to no change :/

Any help appreciated :P

---

### Post by HuckBerry on 2009-10-08
```
root@ubuntu:~# pamusb-conf --add-device SD1
```would probably be better written as 

```
root@ubuntu:~# pamusb-conf --add-device=test
```note that there is a '=', no ' ', and that the name for the device is irrelevant because it is only used internally within pamusb-conf.

Are you using version 0.4.2-1 of libpam-usb and pamusb-tools? As I cannot recreate your error. If so, you may want to:

```
sudo apt-get purge pamusb-tools libpam-usb pmount
sudo apt-get clean
sudo apt-get install pamusb-tools libpam-usb pmount
```This will remove the pamusb and it's major dependencies and configs then clear your cache of packages and redownload/install the libs. It is possible the copy you have got corrupted when you downloaded it.

post a "#pamusb-conf --verbose --add-device=WHATEVER" before and after you do the above suggestion.

---

### Post by M4NIC on 2009-10-08
Ive tried with the = but I still get the same error:

```
root@ubuntu:~# pamusb-conf --add-device=SD1
Traceback (most recent call last):
  File "/usr/bin/pamusb-conf", line 258, in <module>
    '/org/freedesktop/Hal/Manager')
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.6/dbus/connection.py", line 622, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files

```

The version is 0.4.2-1. Ive removed it and reinstalled it as you said but I still get the same error :/

```
root@ubuntu:~# pamusb-conf --add-device=sd1
Traceback (most recent call last):
  File "/usr/bin/pamusb-conf", line 258, in <module>
    '/org/freedesktop/Hal/Manager')
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.6/dbus/connection.py", line 622, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files

```

any other ideas are more than welcome :confused:

---

### Post by HuckBerry on 2009-10-08
How about those '--verbose' outputs? I want to see if the error is in PAMUSB, PAM, or HAL. It sounds like HAL is the source of that error based on the output you have provided. In which case you would be better off in a HAL forum as that isn't something you can just reinstall because it doesn't work.

Is there any circumstance where adding a device does work, such as when you don't have any other devices on the USB tree? It might be that some device before your thumbdrive in the USB hierarchy isn't playing nicely with HAL.

maybe post a "#lshw" so we have an idea of what your serial buses have on them.

EDIT: Furthur searching shows that line 257-8 of pamusb-conf is :
halService = bus.get_object('org.freedesktop.Hal', '/org/freedesktop/Hal/Manager')

which is indeed the valid python code for connecting to HAL. which means you have a HAL error my friend and this is the wrong place for you.
as a last ditch effort, try "#apt-get upgrade hal" but I severely doubt that will help at all.

---

### Post by M4NIC on 2009-10-08
Sorry, forgot about the verbose. I was worried it might be HAL :(

upgrade did download and upgrade HAL, but still the same problem. Thnx for the help anw :P

---

### Post by kevinguillorytraining on 2009-10-09
Nice how-to. I'll try it tonight

---

### Post by jgdr20 on 2010-05-02
> **ninjak said:**
> Hi. I followed all the steps, but after the (successfull) login, NetworkManager (via gnome-keyring) ask me for my account's password. Anyone can suggest me what I have to change/use, please?

Ditto for me. Nothing seems to be able to communicate with the gnome-keyring-service if I login with my usb key. If I login with my password everything is fine.

I'm still pretty noobish so if someone can give me a hint as to where to start looking it would be much appreciated :)

---

### Post by snooze86 on 2010-06-17
If have the same problem.

---

### Post by haximusprime on 2010-07-17
Hey guys. 

The guide works perfect with 10.04, except I didn't need to make the keys (although I might have?)

I have a really simple problem though, pamusb doesn't seem to be running before I log in, even though I added it to /etc/rc.local

I put this line

```
/usr/bin/pamusb-agent &
```

and, is there any way to make it just lock the computer when the USB is pulled? as opposed to fully logging me out. :P

thanks guys!

edit 2: i got it!, if anyone is having login problems, try adding the line to /etc/pam.d/gdm-autologin

then set your account to auto login.

it will autologin, but if you put pamusb.so before it then it will look for that first! i set mine to required.

edit: what I really mean is that I still need to type in my password to log into gnome. I can see it working, trying to find the USB because there is a pause before the password box comes up. I am only guessing that it is not running before the login because afterwards it works fine.

---

### Post by jouva on 2010-12-01
If you're still having issues with logging out and X sessions, it's related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/libpam-usb/+bug/558451](https://bugs.launchpad.net/ubuntu/+source/libpam-usb/+bug/558451)

The gdm sessions is crashing due to hal crashing, so it's not so much a "logout" so much as it is a crash.

---

