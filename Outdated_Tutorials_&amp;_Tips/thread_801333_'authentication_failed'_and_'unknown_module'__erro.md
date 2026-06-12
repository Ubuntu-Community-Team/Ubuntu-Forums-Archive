---
title: "'authentication failed' and 'unknown module'  errors preventing logon"
date: 2008-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by MikeEvans on 2008-05-20
**Effected Systems:**
I experienced this issue on Hardy but I found evidence of it occurring on earlier versions and on Debian.

**Symptoms: ** 
[LIST]
[*]You can't login using your normal credentials.  Logging on in X (the graphical environment) raises an "authentication failed" error and the shell complains about an "unknown module".
[*]You can access the system in recovery mode and you can confirm that the users and passwords are set correctly.
[*]Attempting the su command from the shell raises "Unknown module: su" but you may be able to switch users (in single user mode)
[*]You may also see "Segmentation fault" errors.
[*]The system logs provide no help, there is no entry related to this failure.
[/LIST]

**Cause: **
PAM (Pluggable Authentication Modules) is failing to authenticate you because it can't load its essential modules.

**Resolution:**
[COLOR="Red"]**WARNING** Following these directions should be safe but you will run a potentially dangerous command.  Take the proper precautions like backing up important data or the entire system. **[/COLOR]

If you haven't messed with PAM the easiest thing to do is to take it out and replace it with a working copy from the official repositories. 

**Step 1:** Start ubuntu using the recovery option (singe user mode)

**Step 2:** Purge the pam runtime and modules packages and some related files (don't try using apt for this):
```
dpkg --force-all --purge libpam-runtime
dpkg --force-all --purge libpam-modules
rm -rf /etc/pam.d
rm -rf /lib/security
```

**Step 3:** Reinstall those packages from the repositories:
```
apt-get install libpam-runtime libpam-modules
```

**Step 4:** Reboot. You should be able to login normally now:
```
reboot now
```

**Notes:**
My main source for fixing my issue and deriving these instructions:
[http://unixadmintalk.com/f11/cannot-login-su-73323/]("http://unixadmintalk.com/f11/cannot-login-su-73323/")

The user in the following post had a similar issue but fixed it a different way, which did not work for me:
[http://www.linuxquestions.org/questions/linux-general-1/passwd-module-is-unknown-25194/]("http://www.linuxquestions.org/questions/linux-general-1/passwd-module-is-unknown-25194/")

---

### Post by markbuntu on 2008-05-23
That works and when it doesn't you can also do a few other easy things to remedy some specific missing parts.

If you are unable to log in normally but can login with Gnome safe mode and:

If your auth.log or some other log like syslog reports a missing pam_smbpass. You can install the missing libpam_smbpass with Synaptic and that may work. It worked for me in the 386i but not in the amd64. In the amd64 I then got this message:

pam_smbpass(gdm:auth): unrecognized option [missingok]

If you get this remove libpam_smbpass completely and that will fix that. Be sure and check the remove completely option in synaptic to remove all dependencies.

In both instances you will probably then get another message like this:

May 23 18:36:43 mark-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  

To get rid of this you can install nscd, then remove it completely and that should fox your login problem.

There are more than a few reports of this problem in the forums. It seems to particularly effect a few AMD Athlon64 installs with both 386i and amd64 kernel builds. 

I ran into it installing both kernels. It seems both installs leaves a few unresolved dependencies in gdm.

Autologin and login in Gnome safe mode works without this fix since they do not use gdm.

---

### Post by borobudur on 2008-07-29
Worked fine for me, thanks [MikeEvans]("http://ubuntuforums.org/member.php?u=268566")!

---

### Post by lmn. on 2011-05-13
absolute legend, many thanks mate :):):):):)

---

### Post by rbwerst on 2011-06-03
Worked like a charm when I got hit with this problem on a fairly new upgrade to 11.04...it worked a few times then I got the "unknown module" error...

Thanks!!

---

