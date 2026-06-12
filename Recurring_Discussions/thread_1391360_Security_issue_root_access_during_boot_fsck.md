---
title: "Security issue: root access during boot fsck"
date: 2010-01-26
forum: Recurring Discussions
---

### Post by mcglnx on 2010-01-26
All,

After upgrading to 9.10 I found regressions (correct me if I'm wrong) during boot fsck sequence.

When fsck starts at boot time:
[LIST=1]
[*]There is no more progress bar as in 9.04
[*]If the user press 'ESC', a root console is provided. I consider this as a security flow.
[/LIST]

Is it something already mentioned somewhere? (I did some search without success)
Is it considered as a security breach? (for me, it is)
How can I change this behavior back to the 9.04 one?

Thanks in advance,
M

---

### Post by bodhi.zazen on 2010-01-26
Moved to recurring discussions.

Physical access is a security flaw, and this has been discussed many many times on these forums.

[http://ubuntuforums.org/showpost.php?p=8697994&postcount=4](http://ubuntuforums.org/showpost.php?p=8697994&postcount=4)

That is but one post in one such thread ^^ .

If someone has physical access they can simply boot a live CD and have full access to your system.

The root shell you are asking about is a feature, it helps make system recovery easier.

If you like you can set any number of  passwords, from a BIOS password to a grub password.

Know that such things are easily defeated, but if it makes you feel better , go for it.

---

### Post by juancarlospaco on 2010-01-26
Yep, anyways if the user got a hammer or rocket launcher can destroy the system, 
phisical acces=root acces, can even boot from USB or CD and wipe HD.
:)

---

### Post by mcglnx on 2010-01-28
> **bodhi.zazen said:**
> Moved to recurring discussions.

Physical access is a security flaw, and this has been discussed many many times on these forums.

[http://ubuntuforums.org/showpost.php?p=8697994&postcount=4](http://ubuntuforums.org/showpost.php?p=8697994&postcount=4)

That is but one post in one such thread ^^ .

If someone has physical access they can simply boot a live CD and have full access to your system.

The root shell you are asking about is a feature, it helps make system recovery easier.

If you like you can set any number of  passwords, from a BIOS password to a grub password.

Know that such things are easily defeated, but if it makes you feel better , go for it.

Thanks anyway for the reply. 

This I know already: just unplug the drive, and you're done. I do not think about big Mr Hacker: I'm afraid of my kid getting *too easy* access to root. Pressing [ESC] during the process and playing with some commands.

---

### Post by mcglnx on 2010-01-28
> **juancarlospaco said:**
> Yep, anyways if the user got a hammer or rocket launcher can destroy the system, 
phisical access=root acces, can even boot from USB or CD and wipe HD.
:)

As said: I do not target protection against some professional, but against mistakes from my own family.

---

### Post by Tibuda on 2010-01-28
> **mcglnx said:**
> Thanks anyway for the reply. 

This I know already: just unplug the drive, and you're done. I do not think about big Mr Hacker: I'm afraid of my kid getting *too easy* access to root. Pressing [ESC] during the process and playing with some commands.

"Big Mr Hacker" don't usually have physical access to computer he wants access to.

Solution to your problem: Add a GRUB password.

It will still allow you to boot from a live CD.

Solution: Add a BIOS password.

It is very easy to reset a BIOS password if you have physical access to your computer.

Solution: lock your computer.

It is possible to break locks.

---

### Post by bodhi.zazen on 2010-01-28
> **danielrmt said:**
> "Big Mr Hacker" don't usually have physical access to computer he wants access to.

Solution to your problem: Add a GRUB password.

It will still allow you to boot from a live CD.

Solution: Add a BIOS password.

It is very easy to reset a BIOS password if you have physical access to your computer.

Solution: lock your computer.

It is possible to break locks.

solution: Teach your children to sys admin.

Your system is only as secure as the users, boot to recovery mode or not.

If you can not trust your children / family, you have a problem beyond what these forums are intended to manage.

---

### Post by Tibuda on 2010-01-28
> **bodhi.zazen said:**
> solution: Teach your children to sys admin.

Your system is only as secure as the users, boot to recovery mode or not.

If you can not trust your children / family, you have a problem beyond what these forums are intended to manage.

This is a very good solution. :)

---

### Post by mcglnx on 2010-01-28
> **danielrmt said:**
> This is a very good solution. :)

Funny, but not really helpful.

---

### Post by juancarlospaco on 2010-01-28
> **bodhi.zazen said:**
> solution: Teach your children

***The best reply award winner...***

---

### Post by mcglnx on 2010-01-28
> **juancarlospaco said:**
> ***The best reply award winner...***

:) indeed!
So, looks we can not change this behvior... Pity limitation.

---

### Post by Tibuda on 2010-01-29
> **mcglnx said:**
> :) indeed!
So, looks we can not change this behvior... Pity limitation.

Have you not read my first reply? You can protect GRUB with a password.

---

### Post by mcglnx on 2010-01-30
> **danielrmt said:**
> Have you not read my first reply? You can protect GRUB with a password.

Ok. For me GRUB is not controlling fsck. Will it protect the fsck process as well?

---

