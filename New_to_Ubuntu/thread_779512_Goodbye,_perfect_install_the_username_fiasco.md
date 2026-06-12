---
title: "Goodbye, perfect install: the username fiasco"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by uubailey on 2008-05-02
I am truly, truly embarrassed for what I have done today, but I believe I am in the right forum and please cut me some slack, because as you'll notice this is post numero uno.

This morning, I had my fresh installation of Kubuntu Hardy running like a train full of money. One of my goals (although it is seeming more and more unattainable) is setting up a samba share on said Kubuntu workstation.

Well, this morning, I had the bright idea to create an identical login (my name) just for the samba share in a different group with no password and no root/ssh/etc access, along with an account for my fiancee. 

It didn't work - no dice on the Samba.

So I got home from work this evening, and the computer had to be shut down because of some heavy storms in the area. When it booted back up, all of my personal settings were gone and the resolution was a paltry 640x480, so it was hard getting around.

My solution? Delete the "me" account in the other group (1003).

This appears to have been a mistake. Not only is everything so giant on the screen that I can hardly click on more than one icon, I **can't even log into my account as admin![B]**[/B]

Is there some way I can get back into this machine? My primary account was the only one with Admin access. 

Please, please help. And even I am surprised at what an idiot I am for thinking it was okay to create two identical usernames - I thought it would be able to sort them out since they were in two different groups.

Any help is greatly appreciated!:confused: :(

I think if I hear any Samba music - or even Bossa Nova - before I get this resolved, I will burst into tears.

---

### Post by uubailey on 2008-05-02
I don't know if this makes the situation any sunnier, but I can get into another user account, but without root access (as far as I know).

And I hope the title of my thread didn't come off as cocky, because  it was intended to be sarcastic. This is my first install - someone else set me up with my first...

Thanks again to anyone who reads this and to the forum in general.

:(

---

### Post by Patb on 2008-05-02
Bailey.  Perhaps you could try booting into recovery mode at the grub menu stage.  If you don't see the grub menu, try hitting escape as you boot.  

Bear in mind of course that in recovery mode you are root user and therefore can do even more damage, much more! :)

I would try to add a new user - "man adduser" for guidance.  Then you may need to give that new user admin privileges "sudo adduser <user> admin".  Then reboot as that user and try to sort out the problem from there.

Hope this helps.  Good luck.  Cheers, Pat

PS:  Yes, use that other user instead of creating a third.  If you boot into recovery mode you should be able to give user2 admin privileges.

---

### Post by unbuntued on 2008-05-02
Simple solution, in case you didn't think of it already.
Since you are able to login with another username, try to become superuser from there.
In the terminal, type:
```
su
```
When it asks for the password, type your admin password.

Also try to executing admin commands, using sudo.

If this is working, it should get you started in fixing the mess.

---

### Post by uubailey on 2008-05-02
ubuntued - for whatever reason that didn't work. I have already tried every variation of sudo, su, sudo su, kdesu, kdesudo, etc. that I can think of and nothing will let me modify the account.

PatB - That makes me nervous - at this point I'd rather reinstall than mess up my current installation, but it may be my last resort before reinstalling just to see what happens.

Thanks again guys.

---

### Post by lemming465 on 2008-05-02
It's not necessary to reinstall, though if the frustration level gets higher than the reinstall time, you can do that.  I'd go with Patb's advice: boot in "recovery mode", which puts you in a root shell on a text console in "single user" mode.  File systems should be mounted, but services won't be running.  To use sudo or gksu, the user has to belong to the *admin* group.  So a good thing to do is:```
useradd -G admin fooey
passwd fooey
```

Type [Ctrl-D] or *exit* and the system will continue booting to the normal graphic console.  Log in as the temporary user *fooey* using the password you just set.  User fooey will have sudo permission.

If you are comfortable with text editors, you can use *vipw* and *vigr* to fiddle with /etc/passwd (and /etc/shadow), /etc/group (and /etc/gshadow) by hand.  If you are not a vi kind of guy, do ```
export VISUAL=nano
``` first.  If you need more specific advice, post the output from```
cat /etc/passwd; cat /etc/group
```

---

### Post by uubailey on 2008-05-02
I shouldn't have been so wary of PatB's advice - I didn't realize all they wanted was for me to use recovery mode. I'm proud to say I was actually able to figure this one out. 

I didn't realize that root access was granted in recovery mode until a few minutes ago. Things aren't quite as dark as I thought, although my xorg.conf got mangled in the process.

That's the price I pay for making such a foolish move. Thanks again for the help, folks. More love for the newb in this forum and not as much of the disdain like some other linux user haunts...

It sure does make it easier for someone with moderate skills to jump right in. :) Although that's probably a mixed blessing in most respects.

---

### Post by Patb on 2008-05-03
> **uubailey said:**
> I'm proud to say I was actually able to figure this one out. Great Bailey.  It always seems difficult beforehand, then afterwards it looks easy.  Cheers, Pat.

---

