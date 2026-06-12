---
title: "Ubuntu 13.10 - multiple users and logging in using fingerprints"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by mariusz-ciszewski on 2014-03-19
Hello


1 I'm interested in logging in to Ubuntu using fingerprint ( multiple users, each with its own fingerprint ) .
The login manager installed by default in Ubuntu 13.10 , gives you the opportunity ?


2 Where can I find information about which log manager is installed by default in Ubuntu 13.10 / 13.10 Lubuntu / Xubuntu 13.10 ?


3 Is it possible to omit the user name ? ( I would like Ubuntu only based on the scanned finger recognize the user and log on him )


4 Where in the most correct way I can define / execute automatically run the script /home/user/scripts/accepted.sh when you log in to the system ( the same behavior for each newly added user )


5 Where in the most correct way I can define / implement automatic start of script /home/scripts/declined.sh when your try to log on was unsuccessful ?


6 How to gather (collect fingerprints) people who have tried to authorize and were not entitled to it ?

Thank you for a feedback
Best reagrds

Mariusz

---

### Post by Mark Phelps on 2014-03-19
The linked thread would be a good place to start reading -- as having fingerprint readers working in Linux is the first step: [http://ubuntuforums.org/showthread.php?t=760018]("http://ubuntuforums.org/showthread.php?t=760018")

---

### Post by mariusz-ciszewski on 2014-03-19
Currently I'm trying to use fingerprint in shell / bash scripts. It is easy to single user. But I need this functionality for multiple users.

Sollution:

1. First fingerprint scan:

```
root@msi:/home/mariusz# fprintd-enroll
Using device /net/reactivated/Fprint/Device/0
Enrolling right index finger.
Enroll result: enroll-stage-passed
Enroll result: enroll-stage-passed
Enroll result: enroll-stage-passed
Enroll result: enroll-stage-passed
Enroll result: enroll-completed
```


2. Verification:

```
root@msi:/home/mariusz# fprintd-verify
Using device /net/reactivated/Fprint/Device/0
Listing enrolled fingers:
 - #0: right-index-finger
Verify result: verify-match (done)
```


3. Time interval effect exist

You can check it playing with this script:

```
#!/bin/sh


res=`timeout 5 fprintd-verify | grep result`


if [ "$res" = "" ]
 then
 echo "`date +%Y.%m.%d-%T` - rescan to fast, please wait a few seconds..."
 fi


if [ "$res" = "Verify result: verify-match (done)" ]
 then
 echo "`date +%Y.%m.%d-%T` - acces confirmed"
 fi


if [ "$res" = "Verify result: verify-not-match (done)" ]
 then
 echo "`date +%Y.%m.%d-%T` - acces dennied"
 fi
```

---

### Post by mariusz-ciszewski on 2014-03-19
[COLOR=#000000]But as it was mentioned this sollution is valid for one user only (and one finger only). [/COLOR]

[COLOR=#000000]If I need to use it for more than only one user it is not possible.[/COLOR]

[COLOR=#000000]So I'm still searching for sollution for many users (see points mentioned in the first post in this topic) [/COLOR]

[COLOR=#000000]Please let me know if there are any other ideas.[/COLOR]

---

### Post by steeldriver on 2014-03-19
Isn't there a PAM module (libpam-fprint) for that?

```

Description-en: PAM module allowing authentication via fprint
 pam_fprint is a PAM module which uses libfprint's fingerprint verification
 functionality to implement a fingerprint-based authentication scheme.

```

IIRC there's also pam_thinkfinger for the Thomson scanners found in some Thinkpads. It's been a while since I played with any of this stuff though.

---

