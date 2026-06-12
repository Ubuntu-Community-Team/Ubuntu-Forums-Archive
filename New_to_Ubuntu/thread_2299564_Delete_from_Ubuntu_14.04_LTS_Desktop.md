---
title: "Delete from Ubuntu 14.04 LTS Desktop"
date: 2015-10-19
forum: New to Ubuntu
---

### Post by stephenhumlengrinstead on 2015-10-19
Hi Guys & Gals,
Until recently I could put something on my desktop and then delete it (using "del" key) when I was finished with it there. However, suddenly I cannot do this anymore or for example rename them. I did not make any changes to the installation apart for download and install W10 on the other drive. I have checked the propreties for read and write, they are correct. I have reset Ubuntu to default settings, that didn't help. I'd be grateful if someone could help me with a simple non jargon solution as I am not an PC "aficionado" like most of you lot ;).

---

### Post by Geoffrey_Arndt on 2015-10-20
A couple threads from AskUbuntu may help:

[http://ubuntuhandbook.org/index.php/2013/07/disable-unlock-login-keyring-ubuntu-13-04/](http://ubuntuhandbook.org/index.php/2013/07/disable-unlock-login-keyring-ubuntu-13-04/)

[http://askubuntu.com/questions/30584/delete-key-assigned-to-a-keyboard-shortcut-and-now-doesnt-work](http://askubuntu.com/questions/30584/delete-key-assigned-to-a-keyboard-shortcut-and-now-doesnt-work)

In second link above, scroll down to the very last answer in the thread about resetting your keyboard default settings.

---

### Post by col48 on 2015-10-23
I never store anything on the desktop, but I guess that if you do, it puts a link in ~/Desktop and that if the link is deleted, the item disappears from the Desktop (but the file it refers to, elsewhere on your disk, is unaffected).

Have you tried deleting the link in Terminal?

```
cd Desktop
dir -al                                     just to list all the filenames and verify ownership
rm MYLINK                              assuming MYLINK is the one to get rid of
dir -al                                     to verify it has worked
```
If the link is owned by root for some (unlikely) reason you'd need to use 'sudo rm MYLINK' and enter your password.
Doesn't solve any issue with the 'del' key, of course.

---

