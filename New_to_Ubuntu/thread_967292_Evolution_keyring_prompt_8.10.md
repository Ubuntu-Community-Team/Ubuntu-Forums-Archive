---
title: "Evolution keyring prompt 8.10"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by dndrich on 2008-11-01
Ubuntupals:

I have allowed automatic login on my user for my recent clean install of Ubuntu 8.10.  Now, Evolution prompts for a keyring password when I fire it up.  Is there a way around this?  There used to be a work around in 8.04 for the same problem, but the keyring manager appears to have changed in 8.10.  Thoughts?

---

### Post by mdpalow on 2008-11-06
bump

---

### Post by quirks on 2008-11-06
I am interested in a solution, too. I use my fingerprint for authentication and I am prompted, when the computer resumes from hibernation. I will search a bit on the web ... until then, I would be glad if someone else pointed out a solution.

---

### Post by njigsaw on 2008-11-07
Ladies, Gents. 

Being laid up ont he sick I have spent most of the day today (6 hours plus) trying to resolve this Evolution / Keyring issue.
Im not a programmer just a user who doesnt want to pay for windows and the anti virus junk to go with it.

I have just loaded Ubuntu 8.10 onto a Advent 4211 Netbook.

Through todays seaching as far as understand you can only get the keyring to automatically connect your evolution mail as long as you are manually logging onto the computer at start up.
If you have enabled automatic logon then it doesnt appear to matter what applications you use (libpam-keyring?) then when trying to connect to your POP mail though Evolution Send/Receive option you will always be asked to provide the access to the default keyring.

I have no issue with the wireless connectivity and keyring which some people appear to have. Don't know whether this is because I'm using Wicd and not network manager.



I have introduced a number of friends and family to Ubuntu mainly because all they want is internet access. these include my 80 year old father inlaw. He doesnt want to have to keep on typing in passwords especially when he doesnt understand exactly what they're doing. Try and explain in it old persons terms!?


Hopefully someone will come up with a simple solution to this.

---

### Post by dndrich on 2008-11-07
Back when I was running Hardy, I ran into the same problem.  Interestingly, I don't think Thunderbird suffered from the same issue.  So, if you need email only, that might be the way to go.  Changing to Thunderbird is easy.  I may have to try that.

---

### Post by quirks on 2008-11-10
The following workaround did the trick for me. You may have stumbled over it in the forums:

1. Go to System -> Preferences -> Encryption and Keys.
2. On the Password Keyrings tab, highlight the login keyring.
3. Click Change Unlock Password and specify an empty password.
4. Accept the warning, that the passwords will be stored unencrypted on disk.

I know it's not perfect, but it seems to work. In my case, it is not much of a risk, that passwords are not stored safely, because I use a desktop PC and it is highly unlikely that a malicious user gets physical access to my harddisk (and if he does, I have way more serious problems).

If you still want to store some confidential passwords safely, create a new keyring with a strong password.

---

### Post by PaulWhipp on 2008-11-12
There is a solution mixed in with this diatribe - its my notes as I try to deal with the problem so might help people anyway ;)

There seems to be a total lack of documentation on the keyring management even though its an important part of ubuntu particularly if, like me, you want to use many email accounts with Evolution.

On a fresh 8.10 install, Evolution is prompting me for each password every time it starts and it then prompts me for the keyring password after each account password - if I hit deny it bails on checking the rest of the accounts. It sorts itself out but with 12+ email accounts for my sins, this is a real pain.

going to the Accessories > Passwords and encryption keys option looks useful but hits the same access prompt when I click on passwords.

Using my login password or a blank password fails (I've never used or set a password here so I've no idea what is going on with this bit).

Following the advice earlier in this thread The System > Preferences > Password and Encryption Settings on my system has two tabs Encryption and 'PGP Passphrases'.  Help on this app shows nothing about passwords or keyrings... so I'm blocked there.

[http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/) contains instructions on reseting the keyring but the keyring folder off the bat contains only a login.keyring file.

"find / -type f -name *.keyring >> keyrings.txt" hums in the background for a while and confirms that this is the only keyring currently in existence.

[http://ph.ubuntuforums.com/showthread.php?t=914996](http://ph.ubuntuforums.com/showthread.php?t=914996) suggests deleting the login.keyring...
I "mv login.keyring ~/Temp/login.keyring~" to be on the safe side...

When I relaunch Evolution, it now prompts me for a password for a new keyring. I give it my login password in the hope of optimization further down the line.

Everything now seems to work and I can relaunch Evolution without being prompted for any passwords. When I go to the Passwords and Encryption keys tool I can see the keys there too (can't do more than look at them or delete them but hey - this is progress ;)

So the conclusion is -
[LIST=1]
[*]Delete the login.keyring file - "rm ~/.gnome2/keyrings/login.keyring"
[*]Use your login password as the password when prompted to create a new one in Evolution.
[/LIST]

Hopefully, when I restart my machine it will automatically work - there is info on that on the web but I'd better put in a few hours real work before checking that out. Let me know if this response is helpful!

---

### Post by PaulWhipp on 2008-11-13
When you log back in, you will be prompted once for the keyring password. You can check the box to automatically unlock the keyring on login so this does not happen again.

You just get prompted once for the send and once for the receive passwords on any new account you add to Evolution.

---

