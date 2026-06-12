---
title: "Delete unknown password from Ubuntu 14.04; NO adminstrat. rights 4 solo user!"
date: 2016-11-19
forum: New to Ubuntu
---

### Post by helmcken on 2016-11-19
HELP!! The technician who installed my dual-boot set-up (Win 7 & Ubuntu 14.04) on my Fragbox (from the most-Excellent Falcon Northwest company!!) also INADVERTENTLY -and unbeknownst to him @ the time - set a master password on the Ubuntu OS that DOES NOT allow me to enjoy Adminstrative rights over my own computer!! Short of upgrading to a newer OS, IF I can EVEN do that, lacking admin. rights/password!...., I do NOT know how to solve this problem! Can anyone instruct me how to delete all existing passwords from this OS? EXTREMELY frustrated!! Thank-you for reading and considering my problem. Stay safe, everyone!!

Fr.02 December 2016 UPDATE:  Tried advice offered but was NOT helpful. Followed instructions exactly only to end up with a "frozen" computer, on which ONLY the power button worked! NO access to mouse OR keyboard, so could do NOTHING! Computer wouldn't even detect/acknowledge USB with memory stick or disc in CD/DVD drive, so no rescue possible.
    End result: Had to take computer into technician and pay $$!! Tech. then uninstalled problematic Ubuntu and re-installed my (dual-boot) grubloader and both my Windows OS and my beloved Ubuntu (newer version @ 16.04) OS - WITHOUT the cursed, unknown password!! Now, I am happily able to access both sides and, once again, have a secure, trouble-free way of accessing the internet (thru' Ubuntu, natch!) as well as access to all my (now "old" Windows-based games!)
    Main point of this update is this: "Everyone, do NOT TRY the advice given above for deleting passwords! There's a very large chance you'll end up having to pay $$ to a technician to undo the damage!" (Marking as "Solved" now.)

---

### Post by #&amp;thj^% on 2016-11-19
This method has worked for me in the past.
[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)
I do feel your frustration though!
And I am sure you have looked around in Your Documents for any clues of him leaving it there...or even tried calling them to ask.
Best of Luck and Kind Regards
EDIT: After you re-gain Administrative rights (Root) rights you can then delete any other existing users...even if they have Administrative Rights.

---

### Post by helmcken on 2016-11-19
Hello and thank-you for trying! First, yes, I did try contacting him AND tried all common tech passwords to no avail! Now, to your advice. I tried it and was unsuccessful - BECAUSE I do not know the existing password. I can operate competently at a basic level in Root/Sudo terminal commands. However, your string/ command was not correct for my system. This string is: sudo <myname> passwd  However, at this point, the computer/Ubuntu demands the existing password from me before it will grant access to create a new password!! This has been the stumper for all my helpers to this point. What can I do? I'm about to try upgrading to a newer (16.04) Operating System, but, as I canNOT upgrade through the built-in Software Upgrader (because I don't know password - AGAIN!!), I have to try it through USB memory stick upgrade. Rather unlock this OS, if easier.... Again, thank-you!

---

### Post by cariboo on 2016-11-19
When you start in recovery mode, you start at a root prompt, you don't need to use sudo. You can tell if you are at a root prompt when the last charcter of the prompt is a #, eg:

```
root@alexis:~#
```

the regular user prompt ends with a $, eg:

```
cariboo@alexis:~$
```

---

### Post by Impavidus on 2016-11-19
The link posted by 1fallen is essentially correct, except that the file system should be remounted read-write. This tutorial is more recent: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I've never heard it to fail, assuming you can get to the grub menu.

---

### Post by bearlake on 2016-11-19
> **Impavidus said:**
> The link posted by 1fallen is essentially correct, except that the file system should be remounted read-write. This tutorial is more recent: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I've never heard it to fail, assuming you can get to the grub menu.

+ 1 I have used this one and it did the job.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

