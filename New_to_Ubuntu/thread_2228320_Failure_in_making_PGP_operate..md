---
title: "Failure in making PGP operate."
date: 2014-06-06
forum: New to Ubuntu
---

### Post by Leo Rivers on 2014-06-06
Failure in making PGP operate.

My first question is has anyone had any experience with the failure of PGP or GPG to operate under Ubuntu 14.04? :o

Within ‘Thunderbird’ I try to generate the key generation and it locks up about 1 tenth of the way across the little thermometer and nothing ever gets done. So I tried another program.

When I try to run ‘gpa’ and uses certificate creation Wizard I get an error message “key pair creation failed. So I tried another program.

When I open up the ‘KCleopatra’ self test results I see a series of tests that pass and are backlit green except with the second to the second to the last of them which is backlit red and says “GP G-agent connectivity unexpected error.” So when in doubt, generate the key pair in the terminal mode.

When I try the terminal mode this is what I get on screen:

leo@leo-ThinkPad-T61:~$ gpg --gen-key
gpg: /home/leo/.gnupg/gpg.conf:5: argument not expected
gpg: /home/leo/.gnupg/gpg.conf:6: invalid option
leo@leo-ThinkPad-T61:~$ ^C
leo@leo-ThinkPad-T61:~$ 

Honestly, I think I've tried about everything. Is there any test or log that I can do to get information to get myself out of this?

Leo

‘’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’’
This is all been very spooky to me because when I try to run gpg on my Mac OS Snow lion on my MacPro4,1 running Mac OS X 10.6.8 (10K549)  I get a failure there as well! I'm being haunted. :o
When I run GPG I get an error when it tries to generate the keys that goes “Ups, something went wrong. There was a problem creating your key. 
Generate new key failed! (No pineentry)
Code = 85

Error text:
gpg: problem with the agent: No pineentry
gpg: /dev/fd/5.0: Key generation canceled

---

### Post by squirrel2003 on 2014-12-08
[https://ubuntuforums.org/showthread.php?t=2190580&p=13183506#post13183506](https://ubuntuforums.org/showthread.php?t=2190580&p=13183506#post13183506)   That makes it work.

---

