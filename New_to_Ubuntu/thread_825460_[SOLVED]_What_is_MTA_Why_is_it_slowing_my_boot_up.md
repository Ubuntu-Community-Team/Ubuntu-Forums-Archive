---
title: "[SOLVED] What is MTA? Why is it slowing my boot up?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Kecheri on 2008-06-11
I have been using Ubuntu 8.04 for about 3 weeks now. Of late, I have noticed that the boot up process gets stuck at 

Starting MTA 

for about 2 minutes. Bootup then continues normally.
What is this service doing ? Can I disable it , if not needed ?

Additional Info: Ubuntu 8.04 running on Toshiba U300-153 Laptop. Everything except bluetooth is working :)

---

### Post by Oldsoldier2003 on 2008-06-11
> **Kecheri said:**
> I have been using Ubuntu 8.04 for about 3 weeks now. Of late, I have noticed that the boot up process gets stuck at 

Starting MTA 

for about 2 minutes. Bootup then continues normally.
What is this service doing ? Can I disable it , if not needed ?

Additional Info: Ubuntu 8.04 running on Toshiba U300-153 Laptop. Everything except bluetooth is working :)

you appear to have installed a mailserver on your machine. MTA is "mail transfer agent"

---

### Post by iaculallad on 2008-06-11
Try disabling some of your "unused" services to speed up your boot time process. System->Administration->Services.

---

### Post by Kecheri on 2008-06-11
Eeks! A mail server ? I am using Evolution, thats a mail client.. right ? Does Evolution have anything to do with MTA ?

Can I atleast differ MTA till I login ?

---

### Post by fenian on 2008-06-11
See fix [here]("http://ubuntuforums.org/showpost.php?p=4532555&postcount=4").

---

### Post by frankos44 on 2008-06-11
> **Kecheri said:**
> Eeks! A mail server ? I am using Evolution, thats a mail client.. right ? Does Evolution have anything to do with MTA ?

Can I atleast differ MTA till I login ?

MTA is mail transfer agent, I am sure postfix uses the MTA and postfix is used by Evolution to transfer mail. You can reconfigure postfix as follows:

$ sudo dpkg-reconfigure postfix

Read the documentation first so you understand what you are doing.

Has your PC been set up as a mail server at any time? if so look at the security issues regarding relaying mail, you could check your logs to see if the mail server is unusually busy.

---

### Post by brian_p on 2008-06-11
> **Kecheri said:**
> Eeks! A mail server ? I am using Evolution, thats a mail client.. right ? Does Evolution have anything to do with MTA ?

Can I atleast differ MTA till I login ?

You have installed an MTA, possibly exim or postfix and do not know why you have done it. You do not need an MTA and neither does evolution. The sensible, quick and efficient way to deal with the situation is to remove it from the system with your package manager.

---

### Post by frankos44 on 2008-06-11
> **brian_p said:**
> You have installed an MTA, possibly exim or postfix and do not know why you have done it. You do not need an MTA and neither does evolution. The sensible, quick and efficient way to deal with the situation is to remove it from the system with your package manager.

Thanks for that, I stand corrected, you are absolutely right. I made the assumption that postfix was required for outgoing mail on Evolution.

---

### Post by Kecheri on 2008-06-12
Thanks Fenian!

 Your fix worked. Boot-up speed is back to normal.

Brian_P,

 Will remove MTA, thanks for your input.

---

### Post by frankos44 on 2008-06-12
sorry posted this by mistake, I was replying to a different thread and it got posted here!!

---

### Post by jessiebrownjr on 2009-12-02
I have to bump this because I am having the same problems... I just reinstalled ubuntu and now this is happening to be.. im on 9.04 and didn't install anything intentionally to do this. I checked synaptics and I dont have any postfix programs installed. I saw them and they were unchecked.

I tried the fix and this is the output of where I was told to go.
```
userj@desktop:/etc/rc2.d$ ls
README           S20winbind         S50saned                  S98usplash
S01policykit     S24hal             S50system-tools-backends  S99acpi-support
S10acpid         S25bluetooth       S70bootlogs.sh            S99laptop-mode
S10apmd          S30gdm             S70dns-clean              S99ondemand
S10sysklogd      S50avahi-daemon    S70pppd-dns               S99rc.local
S11klogd         S50cups            S89anacron                S99rmnologin
S12dbus          S50NetworkManager  S89atd                    S99stop-readahead
S20apport        S50pulseaudio      S89cron
S20hotkey-setup  S50rsync           S90binfmt-support
anonz@desktop:/etc/rc2.d$ 

```

---

