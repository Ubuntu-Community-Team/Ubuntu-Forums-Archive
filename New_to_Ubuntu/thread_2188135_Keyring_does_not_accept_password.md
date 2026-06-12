---
title: "Keyring does not accept password"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by ralphpam on 2013-11-15
I have Ubuntu 13.10 installed and keyring will no longer accept my password which is how I get into Ubuntu one.  I found on the internet that I should open applications, accessories, password then encrption keys to reset the password.  The problem is this 69 yearold can even find how to open applications.  I like Ubuntu better than windows but some parts can be frustrating to a old foggy. Help/

---

### Post by ajgreeny on 2013-11-15
Always assuming this was not a scam of some sort, I have just received an email with the following contents:-
> 
Hi,

We are continually enhancing the security of all the Ubuntu One services
(login, payments, file syncing, etc).
In the past week we have made some changes to our servers that may log you out
of the Ubuntu One clients on Ubuntu, Windows, Mac, Android or iOS.

In order to get them working again, just remove and add your account again.
You can find instructions for each platform in our FAQ if you don't know how:
[https://one.ubuntu.com/help/faq/](https://one.ubuntu.com/help/faq/)

We are working to improve our clients to handle this situation better in the
future, making it a seamless experience while still not compromising on
security.

If you have any questions, don't hesitate to contact our support team:
[https://one.ubuntu.com/help/contact/](https://one.ubuntu.com/help/contact/)


Kindly,

The Ubuntu One team

I have not yet checked if this is really from ubuntu, but I have looked at the merssage source info and it appears to be all above board.  If this is a real ubuntu-one message you may simply need to do what it says.  I can not see any reason why doing so would be a security risk, so go for it, give it a try.

---

### Post by ralphpam on 2013-11-15
I have tried that through the web and it works however I still have the keyring problem trying to get on directly from ubuntu.

---

### Post by steeldriver on 2013-11-15
If you're using the standard (Unity) desktop, you can press the Ubuntu button to open the 'dash', then just type the first few letters of the application in the search box:

[ATTACH=CONFIG]247855[/ATTACH]

Otherwise, you can run it from a terminal by typing

```
seahorse
```

---

### Post by jdeca57 on 2013-11-16
If the problem is logging out and restarting try this:
```

Open Applications->Accessories->Terminal and run:

  u1sdtool -q; killall ubuntuone-login ubuntuone-preferences;
  sudo rm -rf ~/.local/share/ubuntuone
  rm -rf ~/.cache/ubuntuone
  rm -rf ~/.config/ubuntuone
  mv ~/Ubuntu\ One/ ~/Ubuntu\ One_old/ 

Open Applications->Accessories->Passwords and Encryption Keys, go to the Passwords tab, delete the Ubuntu One and Desktopcouch tokens by right-clicking on them and selecting "Delete"
Back in a terminal session, run:

  u1sdtool -q; killall ubuntuone-login; u1sdtool -c 

```
Then you get a new prompt for the e-mail and the password
Source: [https://wiki.ubuntu.com/UbuntuOne/Bugs](https://wiki.ubuntu.com/UbuntuOne/Bugs)

---

### Post by wolfen10862 on 2013-11-16
My Keyring problem is slightly different, I have to enter my password every time i turn on my compute for Keyring.
I know nobody's trying o steal my personal information because there simply is none on the computer :)

---

### Post by heir4c on 2013-11-16
See the right column in this link:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Disable-the-keyring-password-on-your-laptop](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Disable-the-keyring-password-on-your-laptop)
In the link when say: "look at the folder .gnome2", I think you don't find that one, because this instructions are not up to date for 13.10 and/or 14.04 (What I have here on my comp). 
So, open your home folder and click the keycombination: Ctrl+H to see the hidden files (hidden files begin with a . ) if you don't find the .gnome2 folder, than look for the folder .local and than click on it. Than doubleclick on the share folder and than on the keyrings folder. You see now the file: login.keyring
rightclick on that and choose "rename" (or something like that, I have no Englisch version here).
Rename it to: login.keyring.origineel  or: login.keyring.old 

You can do it also via terminal:
(To open a terminal you can do it via the Dash (UbuntuLogo at the top Left) or by keycombination: Ctrl+Alt+T)

```
cd .local/share/keyrings
mv login.keyrings login.keyrings.original

```

Reboot and "When prompted for a password, leave the password field blank (simply click OK and agree to unsafe storage)."

---

