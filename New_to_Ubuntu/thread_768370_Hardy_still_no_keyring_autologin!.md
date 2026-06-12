---
title: "Hardy: still no keyring autologin?!?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by inverseroom on 2008-04-26
Just upgraded yesterday...it went off without a hitch, and Hardy is great!  Very snappy.

But I thought that there was supposed to be a "remember this password" type prompt on the keyring dialog.  I don't want to enter my password every time I turn on my computer!  I'm the only one who uses it, and don't have security problems.  How can I accomplish this in Hardy?  (I don't mind entering it when it's time to install/uninstall software, or change important functions.)

---

### Post by frup on 2008-04-26
Hey man, that's always existed, even on gutsy. I set up my grandparents installation to just boot straight to desktop as merely entering a username and password is a great hassle for them.

System > Administration

Click on the security tab and the first option is enable automatic login. should be obvious what you do from there :) Hope it helps... remember the security implications too, like I wouldn't do that on a laptop you take out doors.

---

### Post by SunnyRabbiera on 2008-04-26
The thing is though that autologin is disabled FOR YOUR PROTECTION, I know popping in a password at login can be a drag but its better for your security.
Even if you are the only user on your computer it is still good to have a password at login for a secure session.
I know as a former windows user a password at login can be annoying, but why do you think windows has so many vulnerabilities?

---

### Post by Sheep Me on 2008-04-26
The guy is asking about the keyring dialog, not the login dialog.

---

### Post by gfg on 2008-04-26
I find this a hassle as well. I set up an Ubuntu box, with autologin for my father, who is not very computer literate, and the one thing he has a problem with is the keyring dialog. I really hoped this would be fixed in Hardy, but it seems like this problem will persist for a while longer. Hopefully it will be fixed in Ibex at least.

---

### Post by ogcub on 2008-04-26
I get conected to my WPA protected network without entering any pw. I think this works because i never set any password for it.

---

### Post by inverseroom on 2008-04-26
> **Sheep Me said:**
> The guy is asking about the keyring dialog, not the login dialog.

Yes, that's right.  A few people found workarounds in Gutsy but none of them ever worked on my machine.  Anybody know a solution in Hardy?

One nice thing, it has stopped asking for my keyring login when it comes out of hibernation.  Getting the laptop to GO into hibernation is still hit and miss though.

---

### Post by diafygi on 2008-04-29
> **inverseroom said:**
> Anybody know a solution in Hardy?

I haven't found one yet. This is really annoying for me as well. They included the handy [seahorse]("http://www.gnome.org/projects/seahorse/") gui for managing the keys, but I can't figure out how to allow access without the password.

Also, the libpam-gnome-keyring package is installed by default. When you [read]("http://packages.ubuntu.com/hardy/admin/libpam-gnome-keyring") the description, doesn't it sound like you should be able to automatically load the keyring for your wireless network? Are there any extra commands you need to do?

---

### Post by Pat L.I. on 2008-05-21
bump!

---

### Post by shifty_powers on 2008-05-21
thats strange as i never have to enter the pw for my wpa-enabled network...

---

### Post by HotShotDJ on 2008-05-21
> **frup said:**
> System > AdministrationOOPS... frup is correct, except he/she left out the last part... System > Administration > Login Window

Now follow the rest of frup's post. :)

EDIT:  Hmmmmm... After reading the posts that came up while I was typing this, I'm wondering if I've misunderstood what the OP is asking.  Frup's (and my addition) post is about automatic login without a password.  I can't say I know what this keyring login is all about.

---

### Post by turezky on 2008-05-24
bummpidy bump!
Have the same problem, nothin' really works :(
Any "real" proven solutions?

---

### Post by bungee_70 on 2008-05-31
Hi!!!

Had the same problem and finally found a solution on this site (see 04/21/2008 update near the end):
[http://www.savvyadmin.com/pam_keyring-automatic-keyring-authentication/](http://www.savvyadmin.com/pam_keyring-automatic-keyring-authentication/)

Works great!!!

---

### Post by Kinst on 2008-05-31
Make your keyring password blank, you'll always auto-login.

---

### Post by anewguy on 2008-05-31
I believe the pam package is installed by the upgrade if you had it installed before.  If not, the first thing you want to do is install 
the pam package via synaptic.  Then delete your old keyring.  The first time it prompts for a keyword password, enter your logon password
and it won't ask again.  But you will need to delete the old keyring
first.  This all it takes and has always worked great for me.

If you check synaptic and find that pam is already installed, then 
you need to delete your old keyring.  Then when you are prompted for
a keyring password to set it, enter in you logon password.

If you have any questions, just post back!  :)

---

### Post by ScaredNoob on 2008-06-07
Think Kinst had it right on the money.  First, log in to your wireless network and get it working to your liking (you will need to unlock your keyring to do this with your password).  Then, to elaborate, in Ubuntu Hardy, go to System > Preferences > Encryption and Keyrings, select the password keyring you want to unlock (mine says login ... Automatically unlocked when user logs on.)  So after it's been selected, click Change Unlock Password, enter your old password (probably your login password) and then leave the other two fields blank, click ok and click to store unsafe or whatever the warning message is, and you will be good to go.  Ahhhh auto user and wireless network login.... this is heaven on earth.

P.S. for Kubuntu Hardy, when you first log on to your wireless network and it wants to store it in kwallet (for the first time) it will want you to set your kwallet password.  Leave it blank and click ok and you will be good to go.

---

### Post by inverseroom on 2008-06-22
THANK YOU--that did the trick.

Come to think of it, though, I DO also want to get rid of the logon password prompt, as well (and yes, I'm aware of the security risks).  But under the Login Window dialog in System > Administration, I do indeed have enable automatic login checked.  Yet I'm still asked for a password when I turn my computer on.  Any idea why?

---

### Post by van_Zeller on 2008-07-11
> **ScaredNoob said:**
> Think Kinst had it right on the money.  First, log in to your wireless network and get it working to your liking (you will need to unlock your keyring to do this with your password).  Then, to elaborate, in Ubuntu Hardy, go to System > Preferences > Encryption and Keyrings, select the password keyring you want to unlock (mine says login ... Automatically unlocked when user logs on.)  So after it's been selected, click Change Unlock Password, enter your old password (probably your login password) and then leave the other two fields blank, click ok and click to store unsafe or whatever the warning message is, and you will be good to go.  Ahhhh auto user and wireless network login.... this is heaven on earth.

P.S. for Kubuntu Hardy, when you first log on to your wireless network and it wants to store it in kwallet (for the first time) it will want you to set your kwallet password.  Leave it blank and click ok and you will be good to go.

100% the solution I was looking for! Thank you!

---

### Post by van_Zeller on 2008-07-11
> **inverseroom said:**
> THANK YOU--that did the trick.

Come to think of it, though, I DO also want to get rid of the logon password prompt, as well (and yes, I'm aware of the security risks).  But under the Login Window dialog in System > Administration, I do indeed have enable automatic login checked.  Yet I'm still asked for a password when I turn my computer on.  Any idea why?

What is the user that is set for automatic login? Is it yourself? Maybe there is something wrong there.

---

### Post by dgandhi on 2008-07-15
> **Kinst said:**
> Make your keyring password blank, you'll always auto-login.

I would like to point out that this is the wrong solution. 7.10 was working with login decryption of wifi password keyrings and that 8.04 does not is not really acceptable.

Somebody (Canonical?) needs to package pam-keyring-tool for hardy and get this working again. Storing passwords in the clear should never be an acceptable solution.

---

