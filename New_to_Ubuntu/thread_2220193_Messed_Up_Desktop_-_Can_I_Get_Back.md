---
title: "Messed Up Desktop - Can I Get Back?"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-04-27
I had a normal unity 12.04 desktop environment with a single user.  I wanted to add a tempory second user, for test purposes, that had a kde desktop.  A few days later I intended to delete the second user and get back to unity/one user.  So ... I creaed a second users account and added them to the sudoers group and could login and out to each user with their unity desktops.  I then logged into the 2nd user and (this is where I went wrong!) typed into terminal **sudo apt-get install kubuntu-desktop**.  I shut down the pc from the 2nd users environment and noticed the shut down screen was grey and kde.   Now when I reboot I go to the burg/grub screen, choose ubuntu 12.04 (dual boot) and after a while am presented with the kde logon window.  Whether I choose user 1 or user 2 at this point I get booted into their respective desktops - but they are both Unity.  Not what I wanted to achive.  Can somebody help me get back to where I was and have one user (permanent) with unity and a second user (temp) with kde.  Thanks.

---

### Post by Quarkrad on 2014-04-27
Not sure whether this helps.  Booted into my original unity desktop (the permanent user) and looked for gparted in the Dash.  I clicked on it, entered my password and nothing.  Tried this a number of times and gparted will not launch. I typed kd in the Dash and there was KDE Partition Manager.  I launched it putting in user 1 password.  So although I thought I installed a kde desktop only in user 2 environment it looks like I have kde on the whole system - even though both desktops boot to unity.

---

### Post by steeldriver on 2014-04-27
Installing kubuntu-desktop is a system-wide thing - you can't make it apply only to a single user account. However you should be able to select which installed desktop is actually used on per-user basis (and it will default to the previously-chosen desktop - which is why both your users are defaulting to the unity desktop).

You can either continue using the kubuntu login screen (it's probably using KDM in place of the original lightdm display manager) or if you prefer, you should be able to get back to lightdm using

```
sudo dpkg-reconfigure lightdm
```

After that, to get KDE for your 2nd user you will need to select it from the lightdm screen menu next time you log in as that user (using the Ubuntu "button" next to the username).

There may be some other residual Kubuntu splash components (plymouth-theme-kubuntu-logo and/or plymouth-theme-kubuntu-text) that need to be removed to get back to 100% Ubuntu.

There's probably a plain KDE desktop metapackage that you could have installed to get the desktop without the KDM display manager and other bits.

---

### Post by Quarkrad on 2014-04-27
Afraid that did not work - I got the graphic and chose lightdm but nothing has changed.  Is there some sort of purge command to undo what has happened re  **sudo apt-get install kubuntu-desktop**?

---

### Post by deadflowr on 2014-04-27
Do you mean the login screen is the one for kubuntu and not the normal unity one, right?
Perhaps you just need to reset the unity-greeter.
If you open the file
/etc/lightdm/lightdm.conf
there should be a line session=something
if the line doesn't say session=unity-greeter, change it to say that.
Save and exit.
(that file needs to be edited as root)

Reboot
(I don't know, but you may be able to just kill X, but reboot should work)

You should now have the unity-greeter login screen.

To change desktops per user, simply click on the logo that is in the box where you input your password.
It's in the top right corner of said box.

You don't have to login when you set it, the preference, from my own experience, stays set, until I change it, regardless of whether I login or not.

So, I really don't know if any of this will help you but worth a shot.

---

### Post by Quarkrad on 2014-04-27
Yes - the login screen was for kubuntu, however, I have managed to recover (get back to both users and the whole system being in a pure ubuntu environment) by following:
**[http://www.psychocats.net/ubuntu/pureubuntuprecise](http://www.psychocats.net/ubuntu/pureubuntuprecise)**.  What I'm not sure is - is it possible to have user 1 with a ubuntu desktop and user 2 with a kde desktop?  When I delete user 2 I'm back to everything ubuntu.

---

### Post by deadflowr on 2014-04-27
>  What I'm not sure is - is it possible to have user 1 with a ubuntu  desktop and user 2 with a kde desktop?  When I delete user 2 I'm back to  everything ubuntu.                 

Yes, totally possible to have user 1 log into one desktop session and user 2 login another different desktop session.
I do this all the time.

Of course when you delete a user , that users ability to change desktop session is removed as well.;)

But if you wanted to log the existing user into the other desktop session, he/it can still do so, if you wish.
Is that more confusing , less confusing?

---

### Post by Quarkrad on 2014-04-28
This is what I tried to do (have a kde desktop for user 2) but I used the wrong command.  Ideally I would like to create an additional user 2 and user 3 with different desktops.  So I would have my permanent user 1 with ubuntu/unity, user 2 with kde and user 3 with lxde.  Having mesed up first time I'm nervious as I do not know the appropriate terminal commands.

---

### Post by squakie on 2014-04-28
Any of that should be possible, as long as you have the corresponding desktop environements packages installed.  After installing all of these desktops (it looks like all you have to do is add lxde), change the logon splash as per above.  When User2 gets a log on screen, they should select kde.  When user3 gets a log on screen, they should selet ldxe.  Again, as mentioned previously, you can force that in each users profile file.

---

