---
title: "Getting request for 2nd input of password at login (Keyring Popup)"
date: 2014-07-02
forum: New to Ubuntu
---

### Post by JeQhdMD on 2014-07-02
Been using Xubuntu for a while now on a new test laptop.  All was running smooth for a couple o weeks, but the past 3 days, upon a normal login, I get a popup window requesting a keyring password.   The specific message is:

"An application wants access to the keyring 'Default keyring' but is is locked" . . the remaining part of the popup contains a field to input a password, two option buttons (Cancel and Unlock).   Also, a checkbox is enabled that reads "Automaticall unlock this keyring whenever I'm logged in".

So, just a couple questions:

>  what exactly is a keyring . . is it part of the login security settings?

>  What application wants or needs access?   

>  Why would it need access? (what benefit or feature does it provide?)

>  Can I get rid of the keyring popup?  How?

Thanks for helping and clarifying this . . it seems to remind me of something but I can't quite put my finger on it so to speak>

---

### Post by grahammechanical on 2014-07-02
It may be Network Manager asking permission to connect to the router/wireless access point. Is the connection set up to connect automatically? Is the connection available to all users? If it is not available to all users and it is set to connect automatically then we get the request.

I also found this thread relative to Xubuntu

[http://ubuntuforums.org/showthread.php?t=1953998](http://ubuntuforums.org/showthread.php?t=1953998)

Oh, the keyring is a utility that stores passwords in an encrypted form and makes them available to other utilities upon request. Look for something called Passwords and Keys.

Regards

---

### Post by JeQhdMD on 2014-07-02
Thanks Graham,

I don't have access to the laptop this eve (it's about 2030 now in central US) . . . but I will check it on Thursday, starting with network manager.  

Greg

---

