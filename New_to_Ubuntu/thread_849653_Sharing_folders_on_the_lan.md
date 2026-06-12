---
title: "Sharing folders on the lan"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by rsnow on 2008-07-04
I have two Windows computers (1XP, 1Vista) on my lan with my Ubuntu machine.

When I click on Places/network, I can find Windows Network and the workgroup but then I get a message saying "The folder contents could not be displayed."

I have the shared folders on both of the windows machines set so that they can be shared with anyone. What do I need to do so that I can share between Windows and  Ubuntu?

---

### Post by unutbu on 2008-07-04
Have you installed samba?
Perhaps this document will be helpful: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by jamesrfla on 2008-07-04
I use Samba for my file sharing. It is Linux way of sharing files. It is more secure than XP file sharing

---

### Post by rsnow on 2008-07-04
I installed samba and tried to follow the instructions of going to System/Administration/Network. There is nothing in the instructions about roaming mode and that is what is checked when I go into wired connection/properties. Should I leave that checked as enabled?

---

### Post by jamesrfla on 2008-07-04
Roaming mode means that you are receiving a IP address from your DHCP server or router. You should probably keep that checked so it is enabled unless you are going to use a static IP address

---

### Post by rsnow on 2008-07-05
O.K., thanks for that info. I started all of this once before last year but had some health problems and had to shelve most of my computer projects for about 7 months. Maybe this time I can get further along.

---

### Post by rsnow on 2008-07-05
I installed Samba. I guess there is still something out of whack as I am getting the same results, i.e., I can find the Windows Network and the workgroup but cannot display the shared files. Here are my settings, perhaps someone can spot the problem:

When I go to System/Administration/Network/Wired connection/properties, the following appears "eth0 properties - roaming enabled. The General tab shows my computer name as the Host name and the Domain name is blank. The DNS tab shows DNS Servers - 192.168.1.1 The Hosts tab reveals a list of IP Addresses and Aliases with the topmost one highlighted - 127.0.0.1/localhost.

When I go to System/Administration/Samba/Preferences/Server Settings, the Basic tab shows the workgroup and the Description: %h server (Samba, Unbuntu).
The current settings under the Security tab are, Authentication Mode - User; Authentication Server - * (greyed out); Kerberos Realm - blank; Encrypt Passwords - yes;  Guest Account - No guest account.

Samba/Preferences/Users shows a list of names such as games, nobody dhcp, etc. with games as the top one highlighted.

The Samba server configuration shows all of the files I have designated to be shared on the Ubuntu machine plus the printer.

On my Windows machines the files I want to share have been marked to share and to allow them to be changed. I do not require a password to access the Windows machines. When I try to access the Ubuntu machine from a Windows machine I am asked for the user name and password which I type in but I do not get connected. Any help is much appreciated.

---

### Post by bodhi.zazen on 2008-07-05
First you do not need the samba package unless your ubuntu box is acting as a server. In this case it sounds as if your ubuntu bos is acting as a client.

Browse to your windows share, open it

Enter your windows user name and windows password.

Make sure the Domain is correct

---

### Post by rsnow on 2008-07-05
I get the same results with or without Samba installed and whether or not I enter user name/password.

---

### Post by rsnow on 2008-07-06
Maybe I need to back up and take this one step at a time. First, thinking it could help, I thought upgrading to 8.04 might be a good idea....so I did.

Now, I cannot get quite as far as I was getting with 7.10. I can only get as far as the workgroup icon when I click on Places/Network/Windows Network. Clicking on the workgroup icon brings no results.

I checked the add/remove and it showed that neither Samba nor GSAMBAD are installed.

I am still in the 'baby steps' stage of working with Linux so please be patient with me and explain as clearly as possible. If you need me check any settings I will be happy to do so.

---

