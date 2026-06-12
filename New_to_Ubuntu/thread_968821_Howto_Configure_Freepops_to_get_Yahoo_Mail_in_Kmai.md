---
title: "Howto: Configure Freepops to get Yahoo Mail in Kmail"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-03
Hi, all!

This is my first howto.  If I can improve it, please let me know.

I'm running Intrepid with KDE 4.1.2.  I wanted my Yahoo Mail in Kmail.  Here's what to do.  

1.  Run: sudo apt-get install freepops
2.  Go to System Settings --> Advanced tab/ Autostart.  Click "Add Script".  Type "/usr/bin/freepopsd" in the box at the top and press enter or click OK.  Exit out of System Settings.
3.  Restart your machine.
4.  Run "pgrep freepopsd"
5.  If you get a process number, freepops is running in the background, and you're good to go.
6.  Open Kmail. Settings --> Configure Kmail --> Accounts/tab.  Add a new account along with your other email accounts there.  Click POP3.  Name your account.  In "host", put "localhost".  In "port" put 2000.  In login, put your full yahoo email address.  Put in your password, and if desired, click the box to store the password.  Leave the security settings alone (they should be "no encryption" and "plain text").
7.  Try checking your mail.

Hopefully it works for you!

---

### Post by vikramaditya on 2008-11-03
127.0.0.1 is your own computer.  Could this be the reason for the host error? :-k

---

### Post by tarahmarie on 2008-11-03
I'm aware it's my own computer.  

I believe it's just that it's a buggy hack.  Still, it works.  I haven't ever been able to find another way to get my Yahoo Mail into Kmail.  It's still working like a champ.

---

### Post by Denestria on 2008-11-04
I'm not getting the error.  Do you have 127.0.0.1 localhost in your /etc/hosts?

---

### Post by tarahmarie on 2008-11-05
I do now.

---

### Post by tarahmarie on 2009-04-02
In KDE 4.2 with Intrepid, I've had to modify that script to: 

/usr/bin/freepopsd &

to avoid X server/windows errors.  FYI.

---

### Post by SCBrazil on 2009-07-21
Hi,

Thanks for your 'howto'. It was easy to follow but did not work for me.
I am a newbie using Kubuntu Jaunty. I got through your instructions but when I tried my inbox i got the following message

 p, li { white-space: pre-wrap; }  Could not login to localhost. The password may be wrong.
 
 The server said: "UNKNOWN ERROR, PLEASE FIX"

Do you have any ideas as to what could have gone wrong? I tried the password a few times and it is correct. 

As an afterthought - the error takes a couple of seconds to come back and the security settings are set to the default which is a little different from the ones you mention

Encryption - none
Authentication - clear text

I did try 'login' and 'plain' as the authentication method but the error (a different one) came back instantaneously thus,

 p, li { white-space: pre-wrap; }  Login via SASL (PLAIN) failed. The server may not support PLAIN, or the password may be wrong.
 
 The server said: "ONLY PASS IS SUPPORTED"

The version I am using came with my Kubuntu install disk;

KDE 4.2.2
Kmail Version 1.11.2

Thanks for any help you can offer.

---

