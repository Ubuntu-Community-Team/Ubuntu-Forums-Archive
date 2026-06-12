---
title: "Backup Problems"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by wide-load on 2014-01-02
I running 13.04. Backup hasn't worked since September. It runs automatically everyday. When it starts it asks for my encryption password. I type it in and it Prepares. After a while it comes back and ask for my encryption password again. I'm typing in the right password but it keeps coming back and asks for my password over and over.

I'm stumped as to how to make a current backup. The same thing happens with either an automatic or manual backup.

---

### Post by wide-load on 2014-01-13
I used to get excellant help in this forum.  Now nobody seems to respond anymore.  What has changed?

---

### Post by UltimateCat on 2014-01-14
When you try to manually plug in an external usb memory stick or a external hard disk drive you still get the same result?
That's odd:-

I could be wrong but it sounds like the "Backup" application could be broken or somehow comprimised-

Try finding the path to the Backup application and see if any of the arguments in the configuration file seem odd or corrupt to you.
If backup is a file you can edit it with nano or whatever text editor you like.
If it's a directory you will have to have administrative privileges to delete that directory--

As a last resort  you can delete it and than reinstall it-

That's all I can think of.

If you continue to have this issue private message one of the Moderators and tell them it's important.

Hope that helps-;)
Ultimatecat

---

### Post by UltimateCat on 2014-01-18
Is everything ok now?

---

### Post by Mdh3MHY on 2014-08-01
Having recently upgraded to 14.04 (from 12.04), I am now experiencing the same problem. I used to have backup working perfectly with a weekly backup onto an external HDD. Now I have upgraded to Trusty every time I enter the password (correctly), the window disappears then reappears asking for the password again. As such I cannot make a backup - having looked at the backup settings in order to remove the encryption password, I noticed that this option has been removed. Hence I have a password with no way of changing or disabling it.

Any terminal commands that could disable the password? - or any other solution would be appreciated.

---

