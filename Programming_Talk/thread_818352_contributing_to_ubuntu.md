---
title: "contributing to ubuntu"
date: 2008-06-04
forum: Programming Talk
---

### Post by doorman on 2008-06-04
[FONT=Verdana]after using ubuntu a while, i've decided i should start contributing to it...

so, i read all the stuff at  [/FONT][https://wiki.ubuntu.com/ContributeToUbuntu](https://wiki.ubuntu.com/ContributeToUbuntu) i figured the best way i can contribute is by writing code and / or maintaining the packages. so, i went to [https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment) and [https://wiki.ubuntu.com/UbuntuDevelopers](https://wiki.ubuntu.com/UbuntuDevelopers) . I read everything written there... It's time to start contributing!

Before that, I should have signed the code of conduct (which i didn't)... So, I went to launchpad and tried to sign it... The page said i must register my openpgp keys first... bump... i followed the instructions written there but when i enter my fingerprint, i constantly get the error:

```
Launchpad could not import your OpenPGP key.       
[LIST]
[*]Did you enter your complete fingerprint correctly? A         fingerprint is a long sequence of numbers and letters.         You should use the output produced by the command:         [INDENT]         gpg --fingerprint         [/INDENT]
[*]Have you published your key to a public key         server? You can do that by by entering in a terminal:          [INDENT]         gpg --keyserver keyserver.ubuntu.com --send-keys         [/INDENT]
[*]Has your key been automatically mirrored to the Ubuntu key         server? Keys sometimes take up to an hour to be synchronized         between servers. You can check if it has by querying the Ubuntu key server directly.         If it hasn't, you can publish directly to our server by entering in a         terminal:         [INDENT]         gpg --keyserver keyserver.ubuntu.com --send-keys[/INDENT]
[/LIST]

```[FONT=Verdana]

So, I'd waited a day, but i keep getting the same result... When i try to query the keyserver, it get the error no keys found, so i'm guessing i didn't upload the key properly...
And, yes, i tried to send the keys to the ubuntu keyserver...

every command i enter (gpg) seems to complete without error...

Can anyone help?

P.S. Sorry if this is not the appropriate place to put the thread in. Please, feel free to move it if needed
[/FONT]

---

### Post by doorman on 2008-06-10
Anybody???

---

### Post by pmasiar on 2008-06-10
maybe you can try IRC or email ubuntu developers, this forum is just for random programmers (some  even using windows and not ubuntu), ubuntu developers are rarely present here, sorry.

---

