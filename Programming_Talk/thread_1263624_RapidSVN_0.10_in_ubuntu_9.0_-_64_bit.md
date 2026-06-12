---
title: "RapidSVN 0.10 in ubuntu 9.0 - 64 bit"
date: 2009-09-11
forum: Programming Talk
---

### Post by nani2ratna on 2009-09-11
Hi, 

I am using Ubuntu 9.04 from last 2 months inmy work laptop.
We installed Subversion 1.6 in Solaris server and our team will use that through our svn clients.
We do have different clients in our systems. Mostly I use subclipse through eclipse.
But for perl or some other projects i started using Rapidsvn.
After some its started giving the below message

Error: Error while performing action: This client is too old to work with working copy '/home/ratnak/Work/Development'.  You need
to get a newer Subversion client, or to downgrade this working copy.
See [http://subversion.tigris.org/faq.html#working-copy-format-change](http://subversion.tigris.org/faq.html#working-copy-format-change)
for details.

Because I am using Rapidsvn 0.96 which was built on Subversion 1.5.

I want to install Rapid svn 0.10 which was built on Subversion 1.6.2.

In ubuntu repository only Rapidsvn 0.96 is available.

Can any any help solving this issue.

Thanks and Regards
RS.K

---

### Post by leorolla on 2009-11-23
In Ubuntu 9.10 you will have the right version.

But... if it is a *work laptop*, I recommend testing the 9.10 version in any form *except* replacing the 9.04.

If you have dual boot, test 9.10 with Wubi until you get *everything* working *for sure*.

Meanwhile, just don't touch SVN-1.5 working copy with the SVN-1.6 client...

If you have already messsed up important stuff, start a new working copy and transpose the changes manually.

I'm no expert... this is more "advise" than "help" ;-)

---

### Post by nani2ratna on 2009-11-24
Hi Leorolla,

Thank you very much for the reply.

We moved subversion 1.6 to 1.6.5 just 2 weeks back.

And I am using subclipse for perl also because i have installed perl plugin in eclipse.

I cant work on rapid svn now.

As you said its not good to replace 9.04 to 9.10.

Can I do like this----

Take the back up of 9.04 current version.
Keep it on external hard disk.
Replace 9.04 with 9.10.
If doesnt work properly then restore the 9.04 backup.

Thanks in advance
Ratna

---

### Post by leorolla on 2009-11-24
I cannot answer for sure.
I wouldn't do it if it were my work laptop.
Don't you have other partitions in your HD?

How did you install subversion 1.6.5?

And is the 64 bit version really much faster?

---

### Post by nani2ratna on 2009-11-24
Yeah thats the problem,

when i installed Ubuntu i have cleaned my vista.
So no other aprtition now.
I got HP 550.


We installed Subversion 1.6.5 in the solaris server.

I havent installed subversion in my work laptop.

Thanks and Regards
Ratna

---

### Post by leorolla on 2009-11-24
You can try LUBI, it is safe.

You can also install from one USB to another, without touching the HD.

---

### Post by leorolla on 2009-12-21
You can use a recent version of rapidsvn by adding some Karmic repositories to you list,setting the priority to a low value and fixing the priority of rapidsvn.

This is what I am doing now with a few applications.

---

