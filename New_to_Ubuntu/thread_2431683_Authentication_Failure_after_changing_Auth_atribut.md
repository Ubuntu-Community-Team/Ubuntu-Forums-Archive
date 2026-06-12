---
title: "Authentication Failure after changing Auth atribute"
date: 2019-11-20
forum: New to Ubuntu
---

### Post by matgroup on 2019-11-20
Hi Everyone,
I hope so someone will help me with the following problem.
Good security pratices require that the user/administrator session will be locked after a number of authentication failures to avoid automated brute force attacks.
So I am trying to apply the following additional options to /etc/pam.d/common-auth:

auth          required                             pam_faillock.so preauth audit silent deny=5 unlock_time=900     

auth          [success=1 default=bad]     pam_unix.so                                                         

auth          [default=die]                      pam_faillock.so authfail audit deny=5 unlock_time=900            
auth          sufficient                            pam_faillock.so authsucc audit deny=5 unlock_time=900
          
I have Ubuntu 18.04 LTS and after reboot, I am struggling to log back in to system.
Its keep showing me "Login incorrect".

---

### Post by TheFu on 2019-11-20
[https://www.tecmint.com/lock-user-accounts-after-failed-login-attempts-in-linux/](https://www.tecmint.com/lock-user-accounts-after-failed-login-attempts-in-linux/)
says there are specific order for integrating  pam_faillock with other PAM needs.

The example there is:
```
auth  required      pam_env.so
auth  required      pam_faillock.so preauth silent audit deny=3 unlock_time=300
auth  sufficient    pam_unix.so  nullok  try_first_pass
auth  [default=die] pam_faillock.so  authfail  audit  deny=3 unlock_time=300
auth  requisite     pam_succeed_if.so uid >= 1000 quiet_success
auth  required      pam_deny.so

```
On my systems, there isn't  pam_faillock.so, so be certain that module/package is installed.

You'll need to use either a recovery console login (selected at the grub boot Advanced menu) or boot from alternate media like a *Try Ubuntu* flash drive. Either method should allow you to mount the correct partition and modify the pam.d/ files as needed.

---

### Post by matgroup on 2019-11-22
Hi,
I have only common-auth common-password and common-account files where I can edit specific values.

If I will apply settings same as in your reply the result is same, that I can try multiple times to log back in and and will show login invalid.

I dont know where is problem. I am quite new to those settings.

---

### Post by TheFu on 2019-11-22
Have you been watching the system log files?  Anything inside those?  

Depending on how you've setup the system, some of those might be removed at each reboot.  You can set limit for how many or how large the logs can get using some systemd log controls.  I don't remember the exact method, but it was pretty easy to fine and set.  Think I just had to create a specific directory for them to last between boots.

---

### Post by matgroup on 2019-11-25
Hi again,
Thank you for your last reply.
I have check auth.log file so of the reason why maybe auth is failing and did found some records.
First is pam_unix replies:
pam_unix(login:auth) : authentication failure; logname=LOGIN uid=0 euid=0 tty=/de/tty1 ruser= rhost=
FAILED LOGIN (1) on '/dev/tty1' FOR 'UNKNOWN' , Authentication failure
but this occassion I think I have provided wrong user name but next record is more related to my issue:
PAM unable to dlopen(pam_faillock.so): /lib/security/pam_faillock.so: cannot open shared object file: No such file or directory
PAM adding faulty module: pam_faillock.so
PAM unable to dlopen(pam_fprintd.so): /lib/security/pam_fprintd.so: cannot open shared object file: No such file or directory
PAM adding faulty module: pam_fprintd.so
PAM unable to dlopen(pam_pwquality.so): /lib/security/pam_pwquality.so: cannot open shared object file: No such file or directory
PAM adding faulty module: pam_pwquality.so
FAILED LOGIN (1) on '/dev/tty' FOR 'support' , Module is unknown
FAILED LOGIN (2) on '/dev/tty' FOR 'support' , Module is unknown
FAILED LOGIN (3) on '/dev/tty' FOR 'support' , Module is unknown
FAILED LOGIN (4) on '/dev/tty' FOR 'support' , Module is unknown
FAILED LOGIN (5) on '/dev/tty' FOR 'support' , Module is unknown
TOO MANY LOGIN TRIES (5) on '/dev/tty1' FOR 'support'
pam_mail(login:session) : pam_putenv: delete non-existent entry; MAIL
pam_unix(login:session) : session closed for user support

Looks like faillock and other files not exist in my directory and thus why system cant log me in properly.
What to do now? How can I now add faillock.so?

---

### Post by TheFu on 2019-11-25
Two things.

Remove the pam settings that point at any non-existent modules (read the error messages for those) ... or just restore from the backup you had prior to messing with these things.  
> On my systems, there isn't pam_faillock.so, so be certain that module/package is installed.

root logins are disabled in Ubuntu, so to be able to login, use a different account.

---

