---
title: "Root password reset problem"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by Niemil on 2013-04-14
For first time ever I installed Ubuntu yesterday. Version 12.10. Installed it via LiveUSB and overwrited the Windows Vista I had in the installation.
The computer I'm using is an old DELL Inspiron 1525.

Everything worked great until today when I got tired of always have to write the long password I made when installing. So I choosed to not have any password on my usernames (administrator account). I also made another administrator account, but deleted it instantly as I thought it would be no idea to use it anyway (we're often two people using this laptop so that's why I had it in mind first but changed my mind).

Now, the authoriazing (or whatever it may be called in English) is not working, or as somebody said the root password.

I googled and found out how I can change it in the recovery mode that I access by holding down SHIFT button on boot up. I tried doing this like 4 times now but got nothing to pop up. Tested hold it in all way, tried press it several times and all kind of ways.
Tried also to press F12 to get into the BIOS startup mode thing or whatever it is called, where I could use to start up from HDD etc, where I went to start up the LiveUSB. But here had no recovery alternative, and didn't find anything in the BIOS setting/setup menu, the one that is very blue like windows blue screen.


Now when I doesn't have this root password, I cannot install any more apps, softwares etc.
How can I get this to work again?

According to a dude on an IRC channel I'm on, he says linux doesn't like to have none password and that was messing it all up. Even though there was an alternative to have no password.


So, anyway how do I get this to work? Do I really need to reinstall whole Ubuntu?


[RESOLVED]
Yeah well, it seems like I just had to go terminal and type passwd username, then put a new password and wolla.
Not sure if this called even root password? According to some guy in another site/forum, they said it was root pass that got changed for me. But this fix was just easier than I thought it would be.

---

### Post by Impavidus on 2013-04-14
For some background, read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) and [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Root password is disabled and it's best to leave it like that. The first few days you have to type your password a lot, although it's cached for 15 minutes, but when you've properly set up your system you don't need it that often.

---

