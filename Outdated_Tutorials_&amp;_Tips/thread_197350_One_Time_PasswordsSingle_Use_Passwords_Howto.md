---
title: "One Time Passwords/Single Use Passwords Howto"
date: 2006-06-15
forum: Outdated Tutorials &amp; Tips
---

### Post by braddock on 2006-06-15
I couldn't find any Ubuntu-specific info for getting one time passwords to work using OPIE.  Turns out there is a needed option in sshd_config.  Here are my notes that got me working on Dapper:

apt-get install opie-server

edit /etc/pam.d/common-auth at add:
auth sufficient pam_unix.so nullok_secure
auth sufficient pam_opie.so
auth required pam_deny.so
# and comment out the below line to make OPIE work:
#auth   required        pam_unix.so nullok_secure

Here is the trick for Ubuntu (sshd works fine with Debian Sarge): sshd will
work with the above, but will not tell you the challenge or give any
indication that it is working.  To get sshd to give you the challenge,
you must edit /etc/ssh/sshd_config and set:

ChallengeResponseAuthentication yes

Be sure that the following is also set (it is by default in Ubuntu)
UsePAM yes

Googling around, it appears that earlier versions of OpenSSH required
Privilege seperation to be turned off as well, and a
PAMAuthenticationViaKbdInt set to on.  The PAMAuthenticationViaKbdInt
is deprecated and is no longer necessary, and PAM seems to work just
fine with Privilege seperation turned on, so just turn on ChallengeResponseAuthentication and you are all good.  This little note cost me a
couple hours!

With these settings, when you attempt to ssh, ssh will first prompt
you for your normal password.  If that fails, it will be provide you
with an OPIE challenge containing a sequence number and a seed.

$ ssh localhost
Password: <enter>
otp-md5 498 la0585 ext, Response:

Now, as your user, you can set your opie passphrase with:
opiepasswd -f -c

Of course, you need a key generator to give you some passwords to
answer the challenge.  This is the purpose of opiekey:
opiekey -n 2 491 la0585
Enter secret pass phrase: <insert here>
490: SAYS KID SOW BEAM OBOE AIDE
491: IRMA ITCH SKY JOIN KENT MODE

I don't know why, but the challenge number always counts DOWN; odd.

JAVA OPIE CALCULATOR for your CELL PHONE
[http://www.ii.uib.no/~janfrode/jotp/](http://www.ii.uib.no/~janfrode/jotp/)
Works on my Nokia s60.

-Braddock Gaskill

---

### Post by SolidSilver on 2006-08-28
> I don't know why, but the challenge number always counts DOWN; odd.That's the way S/KEY works.  Each password is a product of successive hashes of the last ones, and you start at the end of the list.  That way, an attacker can't derive the next password to be used from the current one.

Thanks for the HOWTO.  Good stuff.

---

### Post by bantai on 2007-05-24
Thanks for this thread. It helped me to get started with my OPIE authentication. A couple of changes i made though. Since I was only interested in the OPIE authentication when logging in through ssh i didnt edit /etc/pam.d/common-auth with the above changes.

Instead i edited /etc/pam.d/ssh and did the following.

Change 
```

@include common-auth
```

to
```

#@include common-auth
auth sufficient pam_opie.so
auth required pam_deny.so
```

This will disable the normal login and require only the OPIE password. If you want to require both then remove the #.

I also have
```

PasswordAuthentication no
```
in /etc/ssh/sshd_config

---

