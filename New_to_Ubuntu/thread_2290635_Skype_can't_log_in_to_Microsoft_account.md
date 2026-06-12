---
title: "Skype can't log in to Microsoft account"
date: 2015-08-13
forum: New to Ubuntu
---

### Post by les9 on 2015-08-13
Hello,

I'm on Ubuntu 14.04 and have downloaded Skype 4.3. I have a microsoft account that I use for Skype but every time I try to log in, it takes my skype back it it's home window - the one where you choose to use a skype account or microsoft one. Does anybody know how to make it work?

Thanks

---

### Post by Bucky Ball on 2015-08-14
Welcome. No idea about your issue, unfortunately, but I have bumped your thread by changing your thread title to improve your chances of support as Skype is a [VOIP client]("http://voip.about.com/od/glossary/a/VoipClient.htm"), not a [chat client]("http://www.wisegeek.com/what-is-a-chat-client.htm"). :)

Good luck.

---

### Post by monkeybrain20122 on 2015-08-14
Works here. Maybe delete ~/.Skype and try again.

---

### Post by les9 on 2015-08-14
I've installed and uninstalled it about 6 times. It keeps redirecting me to the window where I can choose to log in via my skype name or my microsoft account. This happens after I enter my password and push enter.

Has anyone managed to get Skype to work on Pidgin? That doesn't seem to be working either.

---

### Post by monkeybrain20122 on 2015-08-14
> **les9 said:**
> I've installed and uninstalled it about 6 times. It keeps redirecting me to the window where I can choose to log in via my skype name or my microsoft account. This happens after I enter my password and push enter.

Has anyone managed to get Skype to work on Pidgin? That doesn't seem to be working either.

If your config is corrupted uninstalling and reinstalling won't do you any good. Like I said delete the config folder and start again. Close Skype. Open your file manager, press ctrl h or choose show hidden from file menu and find the hidden folder .Skype and delete it then start Skype (note the ".") Alternatively, close Skype, open terminal and type
```
rm -r .Skype
``` and then start Skype.

Edited: Skype version 4.3.0.37 here. No problem logging in with hotmail account.

---

### Post by les9 on 2015-08-14
I just did that and it does the same thing. :(

---

### Post by monkeybrain20122 on 2015-08-14
Maybe you are missing  libssl1.0.0:i386. Try this. Close Skype then in terminal
```
sudo apt-get install libssl1.0.0:i386
```

From this old bug report [https://bugs.launchpad.net/ubuntu/+source/skype/+bug/1082954](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/1082954)

---

### Post by les9 on 2015-08-14
Well, I did appear to be missing that. But it did not solve my problem, unfortunately. :/

---

### Post by Habitual on 2015-08-17
Try your login at [https://login.skype.com/account/login-form](https://login.skype.com/account/login-form)

Successful?

---

