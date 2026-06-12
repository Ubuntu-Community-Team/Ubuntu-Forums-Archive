---
title: "Ubuntu 14.04 LTS Unity terminal `sudo' doesn't ask for password . . ."
date: 2014-05-02
forum: New to Ubuntu
---

### Post by sadhu44 on 2014-05-02
. . . but I can still run critical operations from the terminal window.

Other apps, such as software update or software center, open a message box to receive a password.  However, I can open a new terminal type in something outrageous, and it doesn't ask for my password, for example:
```

sadhu@desktop:~$ whoami
sadhu
sadhu@desktop:~$ sudo su
root@desktop:/home/sadhu#
```
Is this the way it is supposed to work in Ubuntu 14.04 LTS?  --it makes life easier, but it's kinda dangerous, if you ask me.

-sadhu

---

### Post by Lars Noodén on 2014-05-02
What options does sudo say it grants you?

```

sudo -l

```

Do you still get the weird permissions even after clearing the timestamp?

```

sudo -K

```

---

### Post by grahammechanical on 2014-05-02
It definitely does not work like that on my 14.04 system. In fact the developers stopped installing gksu by default back when Ubuntu 13.10 was released. So, there cannot be any intention on the part of developers to make such dangerous commands easy to use without entering the password.

I agree with you that it is kind of dangerous but I would not have mentioned this in the Absolute Beginners forum. This thread should be moved or closed.

Have you removed the password prompt for sudo? It is possible to do this. Here is something from a Ubuntu wiki page, which I will not link to because of this thread being in the Absolute Beginners section:

> **if you disable the sudo password for your account, you will seriously compromise the security of your computer. Anyone sitting at your unattended, logged in account will have complete Root access, and remote exploits become much easier for malicious crackers.**

---

### Post by LastDino on 2014-05-02
That is not how it is suppose to work, in fact; like grahmmechanical said, this is a serious problem. I've tried Ubuntu Unity 14.04 as well as Xubuntu 14.04 and that is not how it is for me. I doubt that permission file has been edited or you're running terminal as a root.

---

### Post by sadhu44 on 2014-05-03
for Lars Noodén:
```
sadhu@desktop:~$ sudo -K
sadhu@desktop:~$ sudo -l
Matching Defaults entries for sadhu on desktop:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User sadhu may run the following commands on desktop:
    (ALL : ALL) ALL
    (ALL) NOPASSWD: ALL
    (ALL) NOPASSWD: ALL
    (ALL) NOPASSWD: ALL
sadhu@desktop:~$
```

for grahammechanical:

I will ask the mods to move this thread to a more appropriate forum. I hope they will tell me where it is moved to.

Because of your concerns for absolute beginners, I just give this info from my sudo configuration file:
```
%admin ALL=(ALL) ALL
%sudo    ALL=(ALL:ALL) ALL
```
I dunno where the NOPASSWD:ALL lines displayed above got in there. Seems to me that the password ought to be required.  Should I edit the those lines back to ALL:ALL?

Thanks for everybody's help.

-PS I'm an absolute beginner with ubuntu (unity). Still, from now on I'll use a different forum.

---

### Post by sadhu44 on 2014-05-03
> **grahammechanical said:**
> I would not have mentioned this in the Absolute Beginners forum. This thread should be moved or closed.

I googled a link on this forum that said I should mark the the thread as inappropriate, and the mods would move it. I can find no button or link to that effect. Maybe I'm blind.  Or do I use the Contact Us link in the poge footer?

---

### Post by Lars Noodén on 2014-05-03
> **sadhu44 said:**
> Should I edit the those lines back to ALL:ALL?

I think that would be consensus here.  If you have specific actions that you want to facilitate with sudo, you can add them in on a case by case basis, including specific run-time options.  That would be by far safest.  

The manual page for sudoers has a lot of info and even some examples.  If you would like a thorough exploration of the full capabilities of sudo then the book *Sudo Mastery: User Access Control for Real People* by Michael W Lucas can be recommended.

---

