---
title: "Security Warning: Users access to each other's home folders!!"
date: 2006-06-18
forum: Recurring Discussions
---

### Post by iNerdSure on 2006-06-18
I discovered a security lapse in Dapper 6.06. When several user accounts are created, by default, each user has read and write access to all the others' home file folders!! :?:  :( 

Whereas in Breezy 5.10, each user has only read and write to his own folder. Other users' home file folders are not accessible, not even "read" access.

I wonder if this security gap is a bug, or it's only unique to my laptop set up. I'm using 2.6.15-25-686.

Any experts out there in the community can shed some light on this security gap or lapse. Thanks.

---

### Post by aysiu on 2006-06-18
The permissions seem to me as before.

Read-only for other users, read-write for the owner.

This is how it was in Breezy. I don't know how you got it so that others couldn't read each others' folders.

---

### Post by iNerdSure on 2006-06-18
[QUOTE=aysiu]The permissions seem to me as before.

Read-only for other users, read-write for the owner.

This is how it was in Breezy. I don't know how you got it so that others couldn't read each others' folders.[/QUOTE]
On Breezy 5.10 on my other laptop and desktop, it was each user having only read and write access to his own home folders, no "read" acccess to other users' folders.

---

### Post by kabus on 2006-06-18
It's not a bug., it's intentional. 

[http://thread.gmane.org/gmane.linux.ubuntu.devel/12422/focus=12448](http://thread.gmane.org/gmane.linux.ubuntu.devel/12422/focus=12448)
[QUOTE="Colin Watson"]
With the exception of big commercial shell account providers, it is generally
sensible to assume that multiple users on the same box have some
connection to one another (on home systems, they'll generally be family
members; on hobbyist colo systems, they'll be friends; on corporate
systems, they'll be colleagues), and it's often convenient for them to
be able to share files with one another without being able to jump
through hoops. I'd rather not encourage the use of mail for large files.

I don't buy "information leakage" as a trump card when the alternative
is making it difficult for (say) me to tell my wife "I haven't had time
to put those photos up on the web yet, but they're somewhere in my home
directory if you want to have a look", or for me to debug co-workers'
.bashrc files when they're having difficulty committing to arch
archives, or any of a number of other things people do frequently.[/QUOTE]

---

### Post by iNerdSure on 2006-06-18
[QUOTE=kabus]It's not a bug., it's intentional. 

[http://thread.gmane.org/gmane.linux.ubuntu.devel/12422/focus=12448](http://thread.gmane.org/gmane.linux.ubuntu.devel/12422/focus=12448)[/QUOTE]
Thanks for the clarification. I post the "warning" because as a Breezy 5.10 user who has just upgraded to Dapper 6.06, I'm unaware of such an "intentional access" design in Dapper.

Of course, any sys admin who prefers, or needs to set up multiple users WITHOUT access to each other's folders, then the workaround or setup is quite simple - by logging into each acount, and changing the folder "permissions".

---

### Post by aysiu on 2006-06-19
No, I think you're remembering it wrong. In Breezy, you could always read other users' files. I just tested it.

This is nothing new.

Notice how both group and other can read, even though the owner is the only one with write permissions.

---

### Post by wifiabc on 2006-06-30
Is this also true  in the Ubuntu server version?

---

### Post by aysiu on 2006-07-01
[QUOTE=wifiabc]Is this also true  in the Ubuntu server version?[/QUOTE]
Yes.

---

