---
title: "Evolution wants access to keyring"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by corkscrew on 2008-05-30
My laptop shutdown when battery went flat, evolution was running at the time.
When i restarted the computer, i started evolution i get a message saying 
Enter password for default keyring to unlock

The application 'evolution' (/usr/bin/evolution) wants access to the default keyring, but it is locked

I have no idea what this means

---

### Post by iamnotthemessiah on 2008-05-30
happened to me too and i had no idea what my keyring password was, as it was set up soooo long ago and i never used it i guess. anyway i found a fix. 

I DO NOT KNOW IF THIS IS THE RECOMMENDED SOLUTION AND WHAT IMPLICATIONS IT MAY HAVE. DONT BLAME ME IF SOMETHING GOES WRONG

1 i went to ~/.gnome2/keyrings and made backup copies of the files elsewhere

2 system > preferences > encryption and keyrings

3 removed the default keyring

4 (if i remember correctly) clicked add keyring and called it default and made it default in the bottom drop down menu

i think i had to enter a new password here. this time i chose one ill remember


problem gone

---

### Post by DrTaylor on 2008-05-30
If you do not have a default keyring you can set it to anything from this point, and it will remember whatever you put in. Otherwise, you can reset it as shown above without causing significant long term damage. Not sure of the point of a keyring, really. You also have the option to shut it off.

---

### Post by corkscrew on 2008-05-30
when i go to
system > preferences > encryption and keyrings
it says under default none promt for a key and it wont let me change anything

---

### Post by The Cog on 2008-06-02
Well, I don't use a keyring (I've never seen an explanation of what it actually is). Deleting the directory ~/.gnome2/keyrings has stopped the nag popup from evolution every time I log in. I'll post an update tomorrow as to whether evolution still works.

I notice that the directory and its content file gets recreated very quickly, but the nac popup hasn't returned.

---

### Post by The Cog on 2008-06-03
Bloody thing still asks for access to the keyring when I try to send an email. 

Does anyone know how to undo an update, so I can revert to the previous version?

---

### Post by sum1cross on 2008-06-04
After the last round of updates I had the same problem with Evolution requesting the default keyring password. (Ubuntu 8.04 64bit version)

After some checking around the forums, I found enough information to resolve my issue.

Apparently there is a known bug in the keyring manager which can lead to it not updating the default password when you change your login password (which I have done a couple of times).

In my case, the solution proved to be relatively easy (I remembered my install password).

1. Go to System/Preferences/Encryption & Keyrings
2. Ensure Password Keyrings tab is selected
3. In the window, select "login Automatically unlocked when user logs in"
4. Select the "Change Unlock Password" option
5. Type your old login password in the "old password" field
6. Type your current login password in the "password" field, and confirm in the "confirmation" field
7. Click OK.

Sorry, I can't help those who bypass the login screen during boot, as I have never installed my system that way.

I also have no idea why the keyring should suddenly be required by Evolution - my password was changed many months ago and it has only now become a problem.

I hope this helps someone!

---

### Post by trolley on 2008-06-04
I had the same problem after updating this morning. The password that worked for me was "ubuntu", but every time I log in I get asked again. Has anyone logged a bug?

---

### Post by pagaboy on 2008-06-04
> **sum1cross said:**
> After the last round of updates I had the same problem with Evolution requesting the default keyring password. (Ubuntu 8.04 64bit version)

After some checking around the forums, I found enough information to resolve my issue.

Apparently there is a known bug in the keyring manager which can lead to it not updating the default password when you change your login password (which I have done a couple of times).

In my case, the solution proved to be relatively easy (I remembered my install password).

1. Go to System/Preferences/Encryption & Keyrings
2. Ensure Password Keyrings tab is selected
3. In the window, select "login Automatically unlocked when user logs in"
4. Select the "Change Unlock Password" option
5. Type your old login password in the "old password" field
6. Type your current login password in the "password" field, and confirm in the "confirmation" field
7. Click OK.

Sorry, I can't help those who bypass the login screen during boot, as I have never installed my system that way.

I also have no idea why the keyring should suddenly be required by Evolution - my password was changed many months ago and it has only now become a problem.

I hope this helps someone!

Thanks for this - worked nicely for me.  Like you, I'd changed my password months ago, so not sure why it came up now.

---

### Post by trolley on 2008-06-04
Had I read more closely this morning I would have realised that that recommendation would work for me as well. Thanks!

---

### Post by Not Sure on 2008-06-07
> **sum1cross said:**
> After the last round of updates I had the same problem with Evolution requesting the default keyring password. (Ubuntu 8.04 64bit version)

After some checking around the forums, I found enough information to resolve my issue.

Apparently there is a known bug in the keyring manager which can lead to it not updating the default password when you change your login password (which I have done a couple of times).

In my case, the solution proved to be relatively easy (I remembered my install password).

1. Go to System/Preferences/Encryption & Keyrings
2. Ensure Password Keyrings tab is selected
3. In the window, select "login Automatically unlocked when user logs in"
4. Select the "Change Unlock Password" option
5. Type your old login password in the "old password" field
6. Type your current login password in the "password" field, and confirm in the "confirmation" field
7. Click OK.

Sorry, I can't help those who bypass the login screen during boot, as I have never installed my system that way.

I also have no idea why the keyring should suddenly be required by Evolution - my password was changed many months ago and it has only now become a problem.

I hope this helps someone!

Thanks for this post!  It worked for me after the Evolution keyring problem was created by updating.  I am getting afraid to update now.  The old saying,"If it works - leave it alone." has a lot of meaning. 
Thanks again. :popcorn:

---

### Post by Steve R. on 2008-06-08
Minor issue.  I am getting the error message "Evolution wants access to keyring" now.  The problem is that I do not know my "old" password.  Would there be a way to use the password command from terminal to resolve this issue?

The alternative would be to remove evolution and then re-install it.  Any thoughts?
-----------------------------------------------------------------------------

Well, I hope that this is not premature, but I have not received the keyring message now for a few minutes. I killed the evolution process and deleted the login file under /.gnome2/keyrings/. I then rebooted.

See this [**keyring** ]("http://www.linuxquestions.org/questions/fedora-35/fedora-8-and-evolution-keyring-problem-605989/")post.

---

### Post by wvprez on 2008-12-01
I have only been using Linux for 3 days. I installed Ubuntu 10.0 However, I had the keyring problem with evolution and based on info I found on this forum I did the following to rid myself of the problem.

Select Application
Accessories
Password and ***
Select edit when new screen comes up
Select preferences from edit menu
Hi Lite Default
Select Change unlock
Type in old password
(Leave new passwords blank)
Select change
Reboot when all menus are closed.
Note: I did not set up my computer to require a user name and password on boot up..

---

