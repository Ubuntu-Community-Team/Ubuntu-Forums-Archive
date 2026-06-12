---
title: "Ubuntu and Firefox ~ Help, please"
date: 2020-03-02
forum: New to Ubuntu
---

### Post by xcfstarflight1 on 2020-03-02
[B]Hi happy people 

[/B]My question is if anyone has time to help me figure out a couple of things, and how we should communicate.
I am thinking just following this thread is the easiest.. Well, I will start my questions now as follows:
I have too many passwords. 
I have a couple of users on my Ubuntu system,. the Admin and another user that I am going to use now, and I will explain why in my question.
The thing is that I have sooo many passwords that I need to find in a physical book I have. This can be very inconvenient.
What I would like is to have one master password (I Guess it is a web browser(firefox) thing, but any way I could store the passwords and
retrieve or view them from is fine I guess. Wow, imagine if I could set it up in the web browser as well. So my question is really what 
application to use. But also how Ubuntu and firefox are connected and some help along the way to set up the most easy and convenient 
solution for me.

Greetings to all from Sigurd!

---

### Post by sdsurfer on 2020-03-02
> I have too many passwords.

I swear by Keepass. It is portable, the databases are cross platform compatible, and completely encrypted, not stored in the cloud. By portable I mean you can run it from a USB stick. There are other password managers, Keepass rocks, only remember one password ever again.

[https://keepass.info/](https://keepass.info/)

---

### Post by walts48 on 2020-03-02
Lockwise is a built-in feature since version 70.0.


> 
More security protections from Firefox Lockwise, our digital identity and password management tool:
 
[LIST]
[*]Lockwise for desktop lets you [create, update, and delete]("https://support.mozilla.org/kb/manage-passwords-firefox-desktop-firefox-lockwise") your logins and passwords to [sync across all your devices]("https://support.mozilla.org/products/firefox-lockwise/lockwise-settings"), including the Lockwise mobile apps and Firefox mobile browsers&#8232;. 
[/LIST]



[https://www.mozilla.org/en-US/firefox/70.0/releasenotes/](https://www.mozilla.org/en-US/firefox/70.0/releasenotes/)

---

### Post by coley9225 on 2020-03-02
I use lockwise, built into firefox. I you have more than 1 person using your computer, make sure they have their own firefox account, then enable master password. By doing that, you must use your master password to log into firefox. This keeps others from using your passwords. If you let others use your firefox, then an outside password manager would be in order. I can't offer help in that area because I only use lockwise, but I know there are a lot out there. I like lockwise, because I can log into firefox from my phone, or someone elses computer, and all my passwords are right there, no need to carry a thumbdrive with me. Best of luck to you.

---

### Post by mastablasta on 2020-03-03
i use keepass2, but there are also keepass, xkeepass and few others. cross platform. one password or password+key or just key (e.g. on USB) to unlock them all.

---

### Post by oldrocker99 on 2020-03-04
For most people's computers, if you are the only person who uses your deck, choose a simple password to log in, which will be just about as hard to guess as a longer one; I use a 4-character password to get into the system myself. Yes, though, a password manager can be a huge help.

---

### Post by mastablasta on 2020-03-05
> **oldrocker99 said:**
> For most people's computers, if you are the only person who uses your deck, choose a simple password to log in, which will be just about as hard to guess as a longer one; I use a 4-character password to get into the system myself. Yes, though, a password manager can be a huge help.


it's not for the OS, it's for the browser. And although we do have Gnome Keyring and KDE wallet for these, they are not necessarily portable to other OS.

with keypass you can securely transfer website  password database to for example android OS or to windows. 

the OS password is just a hurdle for the malware. on desktop maybe it is not as important as on server where ports are usually open and where remote access is regularly made.

---

### Post by xcfstarflight1 on 2020-03-07
Thank you. My telephone operator suggested the same thing.

---

### Post by xcfstarflight1 on 2020-03-07
I drink my coffee at "Starwars Coffe" not the starbucks. I like that. 
Rock on! Drink coffee whatever you prefer :) Cheers!

---

### Post by sanhuesoft on 2020-03-09
Keepass is one of the most valuable apps available.

---

### Post by ipv on 2020-03-10
> **sanhuesoft said:**
> Keepass is one of the most valuable apps available.

[https://arstechnica.com/information-technology/2015/11/hacking-tool-swipes-encrypted-credentials-from-password-manager/](https://arstechnica.com/information-technology/2015/11/hacking-tool-swipes-encrypted-credentials-from-password-manager/)

[URL="https://www.lifehacker.com.au/2016/06/keepass-vulnerability-lets-attackers-steal-passwords-but-dont-expect-it-to-be-patched/"]https://www.lifehacker.com.au/2016/06/keepass-vulnerability-lets-attackers-steal-passwords-but-dont-expect-it-to-be-patched/
[/URL]
if it can happen once it can happen again.

---

### Post by mastablasta on 2020-03-11
> **ipv said:**
> [https://arstechnica.com/information-technology/2015/11/hacking-tool-swipes-encrypted-credentials-from-password-manager/](https://arstechnica.com/information-technology/2015/11/hacking-tool-swipes-encrypted-credentials-from-password-manager/)

[URL="https://www.lifehacker.com.au/2016/06/keepass-vulnerability-lets-attackers-steal-passwords-but-dont-expect-it-to-be-patched/"]https://www.lifehacker.com.au/2016/06/keepass-vulnerability-lets-attackers-steal-passwords-but-dont-expect-it-to-be-patched/
[/URL]
if it can happen once it can happen again.

bunch of click baits.

Keepass is not the same as Keepass2 or KeepassX

a shocking discovery indeed.

> [COLOR=#000000][FONT=opensans]"Indeed, if the operating system is owned, then it's game over,"[/FONT][/COLOR]

also if someone is standing behind you while you type in master password, will gain access to all passwords. If someone has full access, then they have full access.

Well why would you download update from dodgy website? in linux updates arrive through repositories.
> According to Florian Bogner, an Austrian IT security expert, an attacker can make users download a dodgy update for KeePass that redirect them to a malicious download page.
The recommendation from Bogner is to use HTTPS encryption for update notifications and to download updates only from a trusted source. Also, it's worth noting KeePass will only run the update checker when a user authorises it at launch


---

### Post by sdsurfer on 2020-03-11
> **ipv said:**
> if it can happen once it can happen again.

Note 1: the references you posted are from 2015 and 2016.
Note 2, from one of them:
> "The bug is part of the password manager's automatic update check  function. The problem stems from KeePass using unencrypted HTTP requests  to check for new updates and other tasks."

IMO the whole point of a standalone app is to **avoid** connection to the web or network. Don't do that! I have never even thought about automatic updates with KeePass (and really never knew Keepass had them lol . . . )

Even at that, you're correct, nothing is **impossible** to crack if you have access and time. This guy seems to think it would take 50 million years for a well formed password. :-D
[https://security.stackexchange.com/questions/8476/how-difficult-to-crack-keepass-master-password](https://security.stackexchange.com/questions/8476/how-difficult-to-crack-keepass-master-password)

 I see an article on cracking Keepass from 2019 (I won't post the link but it's well discussed on the Keepass forum) which is basically a dictionary attack on a database they created, and very likely a simple password. Like anything else you have to weigh probability against risk. For most of us it is highly unlikely anyone would even be interested, but even so, physically secure your databases and if they are compromised go old-school - time for a passsword sweep!

---

### Post by ipv on 2020-03-12
> **sdsurfer said:**
> Note 1: the references you posted are from 2015 and 2016.

precisely why i wrote :

> **ipv said:**
> if it can happen once it can happen again.

---

### Post by mastablasta on 2020-03-13
which is why we have backups and passwords (at least important ones) are constantly changed, right?

---

### Post by ipv on 2020-03-13
> **mastablasta said:**
> which is why we have backups and passwords  (at least important ones) are constantly changed, right?

right.

---

### Post by scriber on 2020-03-15
I use Bitwarden for all my browsers in Ubuntu, Mint, Win10 and my Android smartphone.

I used to use LastPass but that turned into a fiasco when it was sold.

---

