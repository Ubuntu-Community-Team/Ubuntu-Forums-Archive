---
title: "Terminal access for standard users"
date: 2015-12-08
forum: New to Ubuntu
---

### Post by Kikikikikik on 2015-12-08
I'm using Lubuntu and I would like to remove the access of terminal from standard users. What would be the easiest way to do it?

---

### Post by mastablasta on 2015-12-08
why? they can't do any system changes in it.

otherwise by using groups and permissions. e.g. user can't launch the terminal or drop to it.

---

### Post by buzzingrobot on 2015-12-08
It's likely that any user who knows enough to interfere with the system or other users via a terminal also knows that launching a terminal is just one way to get at a command line. So, if your goal is to block all users from any opportunity to access a command line, you should think about disabling their ability to reboot the system, block their access to bash and prevent them from installing any other shell.

 Many programs also include a way to "shell out" to bash. If it was me, I might try creating a 'vi.desktop' file in ~.local/share/applications, then launch vi by clicking the icon/menu entry that my desktop environment then displayed, and shelling out to a command line, or just simply running commands in vi.

---

### Post by Kikikikikik on 2015-12-14
Is it possible to remove terminal from bootloader somehow, so you cant access the command line anywhere?

---

### Post by sudodus on 2015-12-14
Maybe the best option for you would be to install a ***kiosk*** operating system. There are free linux systems, that are made such that there is no access to 'anything' except the web browser.

[Linux distros for kiosks](http://tuxdiary.com/2014/11/05/linux-distros-for-kiosks/)

Examples:
[porteus-kiosk.org/](porteus-kiosk.org/)
[https://webconverger.com/](https://webconverger.com/)

---

### Post by Kikikikikik on 2015-12-14
> **sudodus said:**
> Maybe the best option for you would be to install a ***kiosk*** operating system. There are free linux systems, that are made such that there is no access to 'anything' except the web browser.

[Linux distros for kiosks]("http://tuxdiary.com/2014/11/05/linux-distros-for-kiosks/")

Examples:
[porteus-kiosk.org/]("http://porteus-kiosk.org/")
[https://webconverger.com/](https://webconverger.com/)


I was thinking of that solution but I still need that customers/guests can add digital signature to files on HDD, watch videos on HDD and have some games to play to kill time. I just need to disable all command line access somehow so they can't connect themselves to company domain and create a chaos, that is just in case an "advanced guest" with some Linux skills wants to have some "fun".

---

### Post by sudodus on 2015-12-14
It is possible to create a custom system like what you describe, but very difficult to make it 'hacker-proof'.

What about the guest account that is part of the standard Ubuntu systems? A normal 'guest' will not be able to touch anything outside the sandbox of the guest account.

An advanced guest - well, the sky is the limit. Will it be possible to insert USB pendrives? Will it be possible to boot the computers from USB pendrives?

---

### Post by Kikikikikik on 2015-12-14
> **sudodus said:**
> It is possible to create a custom system like what you describe, but very difficult to make it 'hacker-proof'.

What about the guest account that is part of the standard Ubuntu systems? A normal 'guest' will not be able to touch anything outside the sandbox of the guest account.

An advanced guest - well, the sky is the limit. Will it be possible to insert USB pendrives? Will it be possible to boot the computers from USB pendrives?

Hmm... Is Guest account secure enough, so they can't get more privileges by altering some files?

I'm thinking about physically blocking USB ports or just removing them. Which means I need PS2 KB and Mouse, just incase they unplug USB ones and insert pendrive instead.

---

### Post by ian-weisser on 2015-12-14
> **Kikikikikik said:**
> Is Guest account secure enough, so they can't get more privileges by altering some files?

Yes, Guest account is secure enough.
*All* accounts, including user accounts and Guest account, are secure from privilege escalation attacks through the shell.
If you discover ANY way for an unprivileged user to escalate, please file a bug.

---

### Post by sudodus on 2015-12-14
+1 to Ian Weisser's description. It should work with Lubuntu and the users running in the guest session.

[hr][/hr]
If you want more security, but want 'more features than in a kiosk', you can install your Lubuntu with 'Encrypted disk'.

Only you (yourself or employed people) can boot that system (using the passphrase). Then select guest session at the log in screen. At reboot or logout it will stay at guest session, and the guest/customers will be limited to the guest session. You should have a very good passphrase and also a very good password for the user id. (There are ways to hide the user id from the login screen.)

It should be safe enough (but I think there are people who can still get into that system). It is more work for you compared to an unencrypted system, because some people will shutdown or reboot and you have to enter the passphrase.

A simpler method is to use a password in to UEFI/BIOS menu. It will also make it hard to boot the computer, even without encryption of the disk.

---

### Post by mastablasta on 2015-12-15
> **Kikikikikik said:**
> Hmm... Is Guest account secure enough, so they can't get more privileges by altering some files?

I too would dare you to alter system files on Ubuntu as a non sudo user. the only way to do that would be use of live OS (boot from USB). and even that can be prevented using disk encryption. for example

[https://en.wikipedia.org/wiki/TrueCrypt](https://en.wikipedia.org/wiki/TrueCrypt)

> Operation Satyagraha[[edit]("https://en.wikipedia.org/w/index.php?title=TrueCrypt&action=edit&section=27")]In July 2008, several TrueCrypt-secured hard drives were seized from Brazilian banker [Daniel Dantas]("https://en.wikipedia.org/wiki/Daniel_Dantas_(entrepreneur)"), who was suspected of financial crimes. The Brazilian National Institute of Criminology (INC) tried unsuccessfully for five months to obtain access to his files on the TrueCrypt-protected disks. They enlisted the help of the [FBI]("https://en.wikipedia.org/wiki/FBI"), who used [dictionary attacks]("https://en.wikipedia.org/wiki/Dictionary_attack") against Dantas' disks for over 12 months, but were still unable to decrypt them


---

