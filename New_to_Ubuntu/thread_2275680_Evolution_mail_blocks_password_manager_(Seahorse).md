---
title: "Evolution mail blocks password manager (Seahorse)"
date: 2015-04-27
forum: New to Ubuntu
---

### Post by Frans_Meijer on 2015-04-27
On starting Evolution it asked me for the password on one of the imap accounts. Unfortunately the Ubuntu app-finder was blocked by Evolution so I could not get to the passwod manager. 

End Evolution, start Seahorse, find and copy the password, start Evolution and, damn, can't paste the password??? Can't switch to Seahorse either. No password. Oh, now it wants passwords for other acounts as well. Looks like I will not be able to access any email with Evolution. This is bad.

So, how do I get the passwords from Seahorse to Evolution?

---

### Post by Frans_Meijer on 2015-04-27
When I use Librewriter as intermediate I can copy-paste passwords to Evolution, but it doesn't store them in th keyring, so I'd have to jump through all these hoops every time?!?

---

### Post by buzzingrobot on 2015-04-28
> **Frans_Meijer said:**
> ...Ubuntu app-finder was blocked by Evolution... 

Not sure what that means. Tapping the Windows key did not display the search?

When Evolution is first asked to access a server -- typically on its first use after setup -- it prompts for the password for the user's account on that server.  So, if you're using IMAP, the first time you use Evolution to check in mail from that IMAP server, it will prompt for a password.  Later, the first time you try to send mail, Evolution will prompt for an SMTP password.

After that, the passwords are stored in Seahorse and shoud be retrieved automatically from Seahorse.  There should be no need to retrieve or enter them manually.

I don't know how Evolution deals with a password manager, or vice versa; I don't use one.

---

### Post by Frans_Meijer on 2015-05-03
Yup, the tool that comes up when you tap de windows key. Everything was basically blocked. With later attempts I started Seahorse before trying to run Evolution, but then I still couldn't switch to it, or read and copy/paste stored passwords. All I could do was copy/paste the passwords in a text-editor, before starting Evolution, and then I could copy/paste the passwords from the text-editor when Evolution asked for them. 

Seahorse is the default system keyring / password manager, I think. Programs can use it to save login data (username / password) and in addition I use it to manually store passwords for programs that don't use it (like Skype), or, well for cases where you have to fill in your password again. 

Everything was filled in, I have used Evolution for a couple of months now. It just decided it had to ask for passwords again. It's working again now, and I have no clue as to why it acted like it did.

Well, working ... now it has decided it won't send mail anymore, or at least, it tells me it's sending mail, but doen't finish in an acceptable time.

---

### Post by kvamlnk on 2015-05-23
When evolution prompts for a password you lose all gnome/unity functions.  No other programs can be started or run.  The X mouse functions still work.  You can mark a password with your mouse and then middle-click paste into Evolution's password dialog box.  So once you know evolution has lost contact with seahorse: cancel the first dialog boxes, get your passwords visible so you can use the mouse to mark and middle-click paste  I can't figure out why evolution is unable to pull passwords from sea horse.  This is fairly new behavior.  I'm running ubuntu 14.04

---

