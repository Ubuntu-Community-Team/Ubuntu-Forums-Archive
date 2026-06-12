---
title: "T61 fingerprint reader. help!"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by b_d on 2008-04-29
so yai got me a t61. it pretty much all works .. but i cant get the fingerprint reader to work. am running the new hardy, and got thinkfinger installed and ran my prints and everything .. it just never asks for me to input print. :( 

any and all help appreciated :D         ty

---

### Post by Charlie708 on 2008-04-30
Is it a new T61?  My new T61 doens't have a SGS microelectrics chipset, it has a UPEC TouchStrip.  Right now, only BioAPI supports it.

---

### Post by David Valentine on 2008-04-30
I just set this up on a brand new ThinkPad T61, and the following worked like a charm.  I excerpted it from [https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger), which was originally written for an earlier version of thinkfinger; now most of the complications and warnings are no longer relevant:

1.  Ensure all repos are enabled.
2.  Install thinkfinger```
sudo apt-get install thinkfinger-tools  libpam-thinkfinger
```3.  Scan and verify your fingerprint```
sudo tf-tool --acquire
sudo tf-tool --verify
```4.  Open a terminal and type ```
sudo cp /etc/pam.d/common-auth /etc/pam.d/common-auth.backup
gksudo gedit /etc/pam.d/common-auth
```and change it so it looks like this (simply add the bold text):> #
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
** auth    sufficient      pam_thinkfinger.so**
auth    required        pam_unix.so **try_first_pass** nullok_secureIn other words, embed "try_first_pass" in the existing line and insert the "auth sufficient..." line **before** the existing "auth required..." line.

Doing the above will prompt for fingerprint scan (or password--your option) during login and following any gksudo commands.  I'm no guru, but feel free to let me know if you run into complications.

**Update**

A much more comprehensive guide is available at [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger)

---

### Post by b_d on 2008-04-30
thanx man :) 

 im stuck at the part about /etc/pam.d/common-auth . how do i access this to change it .. sorry for the noob questions lol but im really new to the terminal and pretty much all of ubuntu

---

### Post by David Valentine on 2008-04-30
Sorry about that.  Open a terminal and type:```
gksudo gedit /etc/pam.d/common-auth
```I've updated my original post to reflect this.

---

### Post by Charlie708 on 2008-04-30
I have an exception with my system.  It is a new T61 with a T8300 and a UPEK scanner.  common-auth looks like this:

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth	requisite	pam_unix.so nullok_secure
auth	optional	pam_smbpass.so migrate
```

Putting in what is above doesn't work, replacing sufficient and required with requisite and optional results in the inability to authenticate a login.

---

### Post by David Valentine on 2008-04-30
> Putting in what is above doesn't work.Like I said, I'm no guru--I just posted what worked on my T61.  Did you successfully scan and verify your fingerprint (there should have been a notice of a file "thinkfinger.so" being saved)?  What happens if your /etc/pam.d/common-auth winds up like this (be sure to back it up first)?> #
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth    sufficient      pam_thinkfinger.so
auth requisite    try_first_pass      pam_unix.so nullok_secure
auth    optional    pam_smbpass.so migrate

---

### Post by Charlie708 on 2008-04-30
I just messed around and came up with the same conclusions, except I commented out the optional line:

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth 	sufficient	pam_thinkfinger.so
auth	requisite	pam_unix.so try_first_pass nullok_secure
#auth	optional	pam_smbpass.so migrate
```

Edit: I put the optional back in, as leaving it out caused no authentication for sudo and the likes.
Edit2:  Putting optional back in and removing try_first_pass didn't have any effect; does the software assume it is me since I used my finger to login?

---

### Post by David Valentine on 2008-05-01
Your "optional" line appears to have something to do with samba; are you running samba-server?> does the software assume it is me since I used my finger to login?Ubuntu remembers your password for a while after you use "sudo" or "gksudo" in a given session, so in a way, yes.  You should restart x (ctrl-alt-bksp) to test.  Finally, if you're using your finger to login, then it seems to me that you have everything working already!

---

### Post by Charlie708 on 2008-05-01
I am not running samba-server, atleast not that I am aware.

Restarting X did not cause sudo to require a password (it didn't ask, not even the first time), but a full system restart did the trick.

---

### Post by Evender.Wen on 2008-05-01
Thanks to Dave. These commands works for my new X61.

---

### Post by b_d on 2008-05-01
ty all :) 

im up and running...gotta love this community!

---

### Post by nowhere@cox.net on 2008-05-01
Hey guys!!! How did your Hardy install on the T61 go? I have fubar'ed my Gutsy system so badly I would love to try out Hardy. Did you do 32 or 64? intel or nvidia?  Guess that would really be the only differences since I do not have a fingerprint reader. 

Thanks for quick update!
Eric

---

### Post by David Valentine on 2008-05-01
> **nowhere@cox.net said:**
> Hey guys!!! How did your Hardy install on the T61 go? I have fubar'ed my Gutsy system so badly I would love to try out Hardy. Did you do 32 or 64? intel or nvidia?  Guess that would really be the only differences since I do not have a fingerprint reader. Mine went very smoothly with Intel and 32-bit.  I found [thinkwiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_%28Hardy_Heron%29_on_a_ThinkPad_T61") to be a good resource for polishing things up.

---

### Post by djs_uk on 2008-05-18
Hi,

I followed the instructions in this thread to try and get finger print reading enabled on my T61 (running Ubuntu 8.04).

After little effort, it is all working. At the main login screen I can click on my username and then swipe my finger to get access.  And within a Ubuntu session, I can again swipe my finger whenever I am prompted to unlock a keyring.

However I have discovered one problem.  The *su* command no longer works:

```
$ **su**
su: Module is unknown

```

Anyone else encountered this problem?

Regards,

Darren

My /etc/pam.d file is:

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth    sufficient      pam_thinkfinger.so
auth	requisite	try_first_pass pam_unix.so  nullok_secure
auth	optional	pam_smbpass.so migrate

```

---

### Post by David Valentine on 2008-06-05
Your /etc/pam.d/common-auth file looks just like mine.  Have you checked /etc/pam.d/su?

---

### Post by ghostagent on 2008-07-04
ubuntu noob here tying to get my finger scanner working on a t61 6465-cto model. 

i have acquried all the application and was able to run the following commands with success. 

sudo tf-tool --acquire
sudo tf-tool --verify


however when it comes to editing my common-auth files, i just can't get it to work. 

here's my original common-auth file

> #
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth	requisite	pam_unix.so nullok_secure
auth	optional	pam_smbpass.so migrate missingok



here's what i have edited with. 
> #
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth 	sufficient	pam_thinkfinger.so
auth 	required 	pam_unix.so try_first_pass nullok_secure 
#auth	requisite	pam_unix.so try_first_pass nullok_secure
#auth	optional	pam_smbpass.so migrate missingok


i've tried different version and they all don't seem to work even with restart. i don't get the prompt to swipe my finer during initial login .. pleasde help

---

### Post by ghostagent on 2008-07-04
just got this message as well


[IMG]http://i28.tinypic.com/msj90p.png[/IMG]


when i try to reinstall i get the following message


> sudo apt-get install thinkfinger-tools  libpam-thinkfinger
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libthinkfinger0
The following NEW packages will be installed:
  libpam-thinkfinger libthinkfinger0 thinkfinger-tools
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/50.9kB of archives.
After this operation, 336kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 115318 files and directories currently installed.)
Unpacking libthinkfinger0 (from .../libthinkfinger0_0.3+r118-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libthinkfinger0_0.3+r118-0ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libthinkfinger.so.0.0.0', which is also in package thinkfinger
Unpacking libpam-thinkfinger (from .../libpam-thinkfinger_0.3+r118-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libpam-thinkfinger_0.3+r118-0ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man8/pam_thinkfinger.8.gz', which is also in package thinkfinger
Unpacking thinkfinger-tools (from .../thinkfinger-tools_0.3+r118-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/thinkfinger-tools_0.3+r118-0ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/sbin/tf-tool', which is also in package thinkfinger
Errors were encountered while processing:
 /var/cache/apt/archives/libthinkfinger0_0.3+r118-0ubuntu3_i386.deb
 /var/cache/apt/archives/libpam-thinkfinger_0.3+r118-0ubuntu3_i386.deb
 /var/cache/apt/archives/thinkfinger-tools_0.3+r118-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by pytrisss on 2008-07-30
```

``````

```> **djs_uk said:**
> Hi,

I followed the instructions in this thread to try and get finger print reading enabled on my T61 (running Ubuntu 8.04).

After little effort, it is all working. At the main login screen I can click on my username and then swipe my finger to get access.  And within a Ubuntu session, I can again swipe my finger whenever I am prompted to unlock a keyring.

However I have discovered one problem.  The *su* command no longer works:

```
$ **su**
su: Module is unknown

```

Anyone else encountered this problem?

Regards,

Darren

My /etc/pam.d file is:

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth    sufficient      pam_thinkfinger.so
auth	requisite	try_first_pass pam_unix.so  nullok_secure
auth	optional	pam_smbpass.so migrate

```

just comment out the optional line, like this:

```

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
#auth	requisite	pam_unix.so nullok_secure
#auth	optional	pam_smbpass.so migrate missingok
auth 	sufficient	pam_thinkfinger.so
auth	requisite	pam_unix.so try_first_pass nullok_secure

```

for me, it did the trick with missing su module

---

### Post by slidersv on 2008-08-26
Thanks for all the help! now it works!


But after login it asks that it need password "for default keyring"... and I have to enter my password.

But I guess I can live with that.

---

