---
title: "maximum number of characters which may be used in a password?"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by 1888software on 2013-09-10
I tried to use a random generated 100 character password for the user "ubuntu".

It didn't go well.

The system crashed at the time of the "ubuntu" password change.

My question: What is the maximum number of characters which may be used in a password?

Supplementary question: are there any reserved characters prohibited from use in a password?

Thank you!

---

### Post by tgalati4 on 2013-09-10
First, I wouldn't use "ubuntu" for a username.  That might be a reserved user name for default user accounts.

According to the configuration for pamd--the authentication daemon:

tgalati4@Mint14-Extensa /etc/pam.d $ cat common-password 
#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
# used to change user passwords.  The default is pam_unix.

# Explanation of pam_unix options:
#
# The "sha512" option enables salted SHA512 passwords.  Without this option,
# the default is Unix **crypt**.  Prior releases used the option "md5".
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs.
#
# See the pam_unix manpage for other options.

# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
password	[success=1 default=ignore]	pam_unix.so obscure **sha512**
# here's the fallback if no module succeeds
password	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
password	optional	pam_gnome_keyring.so 
# end of pam-auth-update config

```
man passwd
man crypt
```

       MD5     | 22 characters
       SHA-256 | 43 characters
       SHA-512 | 86 characters

So it is either 43 or 86 characters depending on which SHA* is used.  In 12.10 SHA512 is used.

I would try 43 characters and a unique username.  Remember, you need to enter this password every time you blow your nose.

---

### Post by 1888software on 2013-09-10
Thank You 
 [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar241895_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=241895") 				 				 					 						 	[**[COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895") 	 

 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]

What an incredibly detailed and complete response. Much appreciated!

---

### Post by tgalati4 on 2013-09-10
Just as a test, I fed 110 characters into *sha512sum* and it spit out a hash:

tgalati4@tpad-Gloria7 ~/Desktop $ echo 12345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890 | sha512sum 
7fc831adf3d931cc17d896460d2f49dd470b1ced96904cc1070814ee35b01b1ca1405c6541573481f9f0502e63e1d5aa1a47e980bf6acadeefc9d01282203f28 

So the password limitation must be somewhere else.  I will keep looking.

Much more than you want to know about hashing:  [http://en.wikipedia.org/wiki/Sha512](http://en.wikipedia.org/wiki/Sha512)

A google search turned up some interesting answers:

[http://blog.anthonyrthompson.com/2010/02/maximum-password-length-on-linux/](http://blog.anthonyrthompson.com/2010/02/maximum-password-length-on-linux/)

[http://stackoverflow.com/questions/2179649/are-passwords-on-modern-unix-linux-systems-still-limited-to-8-characters](http://stackoverflow.com/questions/2179649/are-passwords-on-modern-unix-linux-systems-still-limited-to-8-characters)

[http://www.ratliff.net/blog/2007/09/20/password-length/](http://www.ratliff.net/blog/2007/09/20/password-length/)

The consensus seems to be 32 characters for username and 79 to 128 characters for password depending on what flavor of linux.

This [page]("http://wpollock.com/AUnixSec/PasswordSecurity.htm") seems to indicate 22 random characters contains enough entropy to make a decent password.

So, forget everything I have said.  I really don't know.

---

