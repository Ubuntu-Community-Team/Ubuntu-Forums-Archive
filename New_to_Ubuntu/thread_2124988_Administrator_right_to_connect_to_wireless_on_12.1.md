---
title: "Administrator right to connect to wireless on 12.10"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by LLigetfa on 2013-03-12
I setup a user that doesn't have administrator rights on a laptop.  When that user tries to connect to a wireless network, they get prompted for my password.  How can they connect to a wireless network without making them admin?

---

### Post by aim on 2013-03-12
have check "allow other users to connet"?

---

### Post by LLigetfa on 2013-03-12
No, I don't want a user to make global settings.  That would need more rights than they have.

---

### Post by varunendra on 2013-03-12
> **LLigetfa said:**
> No, I don't want a user to make global settings.  That would need more rights than they have.

I think you misunderstood what *aim* suggested.

It is just a setting for a network to make (only) it available for all users. It does not extend their rights anymore than making them able to use that particular network.

In the nm-applet drop-down menu, click "**Edit Connections..**" > goto "**Wireless**" tab > double-click the network you want to make accessible for all > in the bottom left corner of the settings box, put a tick in the checkbox that says "**Available to all users..**".

---

### Post by LLigetfa on 2013-03-13
The particular wireless SSID that my non-admin user wants to connect to is not on the list because it has never been connected to.  The laptop is back in my office and the SSID is at my user's house.  When he tries to connect at his house, he gets a "System policy prevents modification of network settings for all users" and he is prompted for my password which I'm not prepared to give him, nor am I prepared to go to his house with him so that I can connect and then make available to all users.  

I don't want him modifying settings for all users.  If I did, I would just make him an admin.  I just want him to be able to connect to his home SSID without admin rights.

I found this bug report that suggests that the SSID can be manually entered but when I try it wants a keyring setup and it is way too complicated of a work-around for my users.  All they (and I) want is to choose from the list of SSIDs.
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1077982](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1077982)

---

### Post by LLigetfa on 2013-03-14
So... nobody knows?  Is this a problem only in 12.10?  I don't understand how this could go unresolved for so long if that is the case.

Should I give up on 12.10 and try 12.04?  Can anyone say if this won't be a problem in 12.04?

---

### Post by steeldriver on 2013-03-14
I've struggled with this several times in the past, just made another attempt and there does seem to be at least one workaround

1. If you just select one of the available networks from the nm-applet list and try to connect to it, a non-privileged user will get a popup saying "System policy prevents modification of networks for all users". The only option is to 'Cancel'. This seems to be because the default for any connection creation operation is 'Available for all users' which implies write permission to the /etc/NetworkManager directory

2. Likewise if you select Edit connections --> Wireless --> Add, the dialog box comes up with the 'Available to all users' box checked - and greyed out! With this box checked, it is impossible for a non-privileged user to save the new connection.

3. **The 'Available to all users' box only becomes editable after you type something into the SSID box** - you can then uncheck it and fill in the SSID and any Wireless Security tab / IPv4 / IPv6 details

4. You should then be able to go back and select the SSID from the list, and it *should* connect - if not, make sure the 'Connect automatically' box is checked and then try disabling and re-enabling wireless

I just tried this as an unprivileged user on my laptop running 12.04 and it does seem to work - yes it's very confusing and ugly, even the developers seem confused by it --> [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/964705](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/964705)

You will find another workaround on the web that involves modifying  the network-manager polkit file - however I *think* that method allows  unprivileged users to modify *any* connection (not just to add their  own) and possibly allows them to see any stored wireless passphrases.

---

### Post by varunendra on 2013-03-14
Have you tried to search for "group management" in Linux?

I didn't find time to do so but I am sure there must be an existing group for network users or a way to create such a group.

I know that there exists a "**dip**" user group that allows users to use dial up devices like modem, but I'm not sure it can do the same for wireless interface. But you may try that (I have no wireless networks around to try myself) -
```
sudo adduser <user id> dip
```

---

### Post by LLigetfa on 2013-03-16
I don't want workarounds.  I don't want to elevate a user to be able to make 'Available to all users'.

Is this issue a regression that started with 12.04?  Should I consider an older version?  Should I consider another distro?

Essentially what I need to work is brain-dead simple wireless with limited powers.  Also need Citrix Receiver to work flawlessly.  These laptops may go from one user to another so the previous user's wireless security settings should not be visible 'to all users'.  Users should not have enough rights to bork up settings.

CorpIT will not support them and if my users pester them for support (which they will) they will come back on me hard.  I cannot support them either so I need to demonstrate that my time is not squandered on them otherwise I'd just make the user admin and re-image the laptop every time it gets borked or returned to me.  If I fail at this, the alternative is to toss them in the waste bin.

---

### Post by varunendra on 2013-03-16
> **LLigetfa said:**
> Essentially what I need to work is brain-dead simple wireless with limited powers.
A quick lookup turned up this -
> **Connect to wireless and ethernet networks**
This right is gained by adding the user to the "**netdev**" group.
....
....
The "netdev" group can administer wicd and wpasupplicant.

The "netdev" group can set the avahi host name using DBus.

The "netdev" group can administer Bluetooth devices.
(from : [https://wiki.ubuntu.com/Security/Privileges#Connect_to_wireless_and_ethernet_networks](https://wiki.ubuntu.com/Security/Privileges#Connect_to_wireless_and_ethernet_networks))

Try it on a test user and let us know if it does what you want -
```
sudo adduser <test user id> netdev
```

---

### Post by LLigetfa on 2013-03-18
The user without privilege that I setup is **mPortal User** so I believe the shortname **mportaluser** is what I would use with the above command.
```
sudo adduser mportaluser netdev
```
Unfortunately that did not work.  User still gets prompted for my password.

---

### Post by varunendra on 2013-03-18
> **LLigetfa said:**
> The user without privilege that I setup is **mPortal User** so I believe the shortname **mportaluser** is what I would use with the above command.

Usually, when there are spaces in user name, the first word is picked as user id by default. So that 'should' be - **mportal**.

But you don't have to guess the user id, just open the terminal when you are in the account in question and the terminal prompt will show you the user id to be used. For example, my terminal prompt is like this :
> varun@varun-K54C:~$
Everything before @ is user id, and after that is the host name of the computer. So my user id is **varun**, and hence the command for me would be -
```
sudo adduser varun netdev
```
Another easier way to get the user id is to simply look in the /home directory. It contain Home directories of all the users created, and they are named exactly as their user IDs. So my $Home is-
> /home/**varun**

Mind you, any user or group level change may require you to log out and log back in for the change to take effect.

I'm not sure if it'll work, just making sure you do it the right way.

---

### Post by LLigetfa on 2013-03-18
The command did not throw an error so I think I got the name right.  If I repeat the command then it says that mportaluser is already added.  None the less, I will run the sanity checks tomorrow.

---

### Post by LLigetfa on 2013-03-19
Confirmed that the name is in fact mportaluser.

---

### Post by varunendra on 2013-03-19
Not a solution, but just for the record for the moment, can you please post the output of -
```
id mportaluser
```
It will tell us which groups the mportaluser is currently a member of. We can then look deeper *(probably with a dummy account)* to see what may be preventing the account to use the service that the netdev group is supposed to offer.

---

### Post by LLigetfa on 2013-03-19
```
mportaluser@HP-Compaq-nc6320:~$ id mportaluser
uid=1001(mportaluser) gid=1001(mportaluser) groups=1001(mportaluser),109(netdev),119(nopasswdlogin)
mportaluser@HP-Compaq-nc6320:~$ 
```

---

### Post by LLigetfa on 2013-03-19
BTW, thanks for sticking with me on this.  If I am slow to provide answers it's because CorpIT does not want me to work on this on company time so I'm relegated to do this on my breaks or after hours.

---

### Post by varunendra on 2013-03-19
No problem, most often I am much slower than you on the forums :)

Only two more things I could sum up -

1) Install gnome-system-tools. I don't think it does anything extra regarding user management than what we did using command line, but at least it makes it easier by presenting a gui for the task (and a menu of groups to choose from). After installation it is listed as "Users and Groups" in dash menu.

2) Since the part that I quoted from the wiki page link in post #10 specifically talks about **wicd** (and says something confusing about Network Manager that I skipped in the quote), install wicd and disable Network Manager for a test, and see if wicd can enforce the group policy any better than NM.

The bug report page steeldriver linked to is also related to NM, so I believe the netdev group (or may be yet another one) is indeed meant to support what you want, but is not working as expected due to some bug. May be wicd can circumvent that. If it doesn't help, I suggest you remove > re-add the user to the group AFTER installing wicd using the installed gui for gnome-system-tools or -
```
sudo deluser mportaluser netdev
sudo adduser mportaluser netdev
```

Although as obviously apparent, I am mostly taking blind shots now. :|

---

### Post by LLigetfa on 2013-03-22
Well... it looks like CorpIT is putting a kybosh on my original plan.  Last I heard, I'm supposed to dispose of them, not just lessen the Microsoft and other license costs.

Still, I hate to toss them in the ewaste bin and hope to salvage some of my time I put into them.  Plan B now is to give them away to employees with the agreement that they are never to call CorpIT helpdesk for support nor are they to burden me with support.  It would seem CorpIT is concerned about possible support costs.

I then would need to rename my account and change the password on it so the user I give the laptop to, can administer it.  When I installed Ubuntu, I used my proper name which I now want to change.

Can I rename my account with  "Users and Groups" and if so, how do I change the /home/(my first name) folder name?
Can I simply create a new "admin" account and delete mine?

---

### Post by varunendra on 2013-03-22
> **LLigetfa said:**
> Can I rename my account with  "Users and Groups" and if so, how do I change the /home/(my first name) folder name?
Can I simply create a new "admin" account and delete mine?

I'm not sure about above. You should be okay with creating a new admin with similar privileges, but I don't know if deleting the first user would be safe or not. I also remember from somewhere that certain things are bound to the first UID/GID (1000), but I think you should be all good after adding the new admin to that GID, in case some related issues arise.

Unless someone can confirm, I'm afraid you'll need to do some experiments yourself. Maybe a dummy installation in VirtualBox?

---

### Post by LLigetfa on 2013-03-23
I decided to just leave the /home/* folder the same and just renamed the account.  When I changed the password in "Users and Groups" the keyring ended up being out of sync.

I found the tread [http://ubuntuforums.org/showthread.php?t=1781787](http://ubuntuforums.org/showthread.php?t=1781787) that explained how to get them in sync.

If I missed something then I guess I'll just reinstall from scratch.

---

