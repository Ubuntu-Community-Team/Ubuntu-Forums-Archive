---
title: "Ubuntu 18.04 Can't connect to Windows shares from Gnome's &quot;Files&quot; app"
date: 2018-09-01
forum: New to Ubuntu
---

### Post by martinu2 on 2018-09-01
I've got a Windows 7 PC which is sharing various folders. I've set these up as public shares with no password. They can be accessed from other Windows 7 or 10 computers.

I'm trying to do the same from Ubuntu 18.04, from the "Other Locations" of Gnome's Files application. In the "Connect to server" field I type either smb://martin-7/public or smb://192.168.1.70/public (I tried both in case NetBIOS name resolution wasn't working!).

I get a "Password required" dialog and choose to connect anonymously. I get an error "Failed to mount Windows share. File exists."

Is there a tutorial which might explain what I need to do to access a Windows shared folder?

---

### Post by martinu2 on 2018-09-02
I've examined the conversation with Wireshark when I do the following in the Files app:

- select Other Networks | Windows Network, then workgroup WORKGROUP, then select Martin-7

The trace shows:

Ubuntu does a NetBIOS name query of Martin-7<20> (the name of the Windows PC)
Martin-7 responds with its IP
Ubuntu does NetBIOS session request
Martin-7 give positive response
Ubuntu does SMB Negotiate Protocol Request using SMB(1) protocol
Martin-7 responds using SMB2
Ubuntu does SMB2 Negotiate Protocol Request
Martin-7 responds

Ubuntu does Session Setup Request NTLMSSP_NEGOTIATE
Martin-7 responds with error STATUS_MORE_PROCESSING_REQUIRED

Ubuntu does Session Setup Reponse NTLMSSP_AUTH User: \
Martin-7 responds SUCCESS

Ubuntu Tree Connect Request \\martin-7\IPC$
Martin-7 responds SUCCESS

Ubuntu Create Request File: srvsvc
Martin-7 responds STATUS_ACCESS_DENIED

Game over!

I've attached the Wireshark trace. Ubuntu is 192.168.1.76; Martin-7 is 192.168.1.70


Is there any more testing or evidence needed to help diagnose the problem.

If it helps at all, the converse process works fine: having installed the samba package on Ubuntu, I right-clicked on a folder in /home/ubuntu and added it as a share. The Windows PC could then see that share ("net view \\ubuntu", "dir \\ubuntu\videos", "copy test.ts \\ubuntu\videos" all worked from DOS prompt).

I've done the same operation (Other Networks | Windows Network, then workgroup WORKGROUP, then select Epson-SX515) for a network-connected printer which shares an SD card slot, and that works. When I've sorted out how to get Wireshark to see the traffic to/from the printer, I'll post a comparison trace. I suspect my router is filtering out traffic on the LAN segment that the Wireshark PC is on, since that traffic is only relevant to the wifi connection between Ubuntu and printer. I may need to connect the printer by Ethernet so it's on the same LAN segment as the Wireshark PC.

---

### Post by deadflowr on 2018-09-02
Morbius1's post should give some background on this for you:
[https://ubuntuforums.org/showthread.php?t=2390509&p=13761597#post13761597]("https://ubuntuforums.org/showthread.php?t=2390509&p=13761597#post13761597")
(Or at least I think it should; same issues or different issues?)

---

### Post by Morbius1 on 2018-09-02
When you use Connect to Server don't select anonymous. Pass it a user name and password instead - try your own Linux user name and password. Or your username and samba password.

I realize that doesn't make any sense but Samba since 4.3.9 has changed a few things.

---

### Post by martinu2 on 2018-09-02
> **deadflowr said:**
> Morbius1's post should give some background on this for you:
[https://ubuntuforums.org/showthread.php?t=2390509&p=13761597#post13761597](https://ubuntuforums.org/showthread.php?t=2390509&p=13761597#post13761597)
(Or at least I think it should; same issues or different issues?)

Hmm. Adding the client max protocol = NT1 line does alter the error: without it, the error is "invalid argument"; with it, the response is "connection timed out". And the wireshark trace in the latter case shows that it bombs out much earlier at the first SMB Negotiate Protocol Request which never gets a response from Windows because the additional protocols "SMB2.002" and "2..???" are not offered. This ties in with what Morbius says "If you set it back to NT1 you will be able to see all the servers but  you will not be able to connect to any that disabled SMB1. You can use a  cifs mount which works independent of how the smb client works."


For connection to "smb://windows-PC/sharename", I've tried non-anonymous by specifying either "ubuntu" (the username for the Ubuntu computer) or "martin" (the Windows username), in both cases with a blank password (I have not assigned a password in either case). I still get "Failed to mount Windows share: file exists". The LAN trace shows an SMB2 Tree Connect Request to \\server\sharename which is causing Windows to say "STATUS_ACCESS_DENIED. And this is to a share which allows guest access because any Windows PC, not necessarily logged in with a user of the same name as exists on the "server", can connec to shares.

Grrr.

---

### Post by martinu2 on 2018-09-02
I've got there at last. My mistake was to connect with a username, a workgroup and a **null** password. When I tried with a non-blank username and password (even though they were utter garbage!) it all worked.

I got the clue when I compared the LAN traces for Windows and Ubuntu accessing the same share on another Windows PC.

The difference was in the SMB Session Setup Request that precedes the SMB Tree Connect \\server\client:

- with a blank password (and a non-blank username) Session Setup had domain, user and password of (null) 
- with a non-blank password (and a non-blank username) the domain was WORKGROUP, the username and password were as I'd specified them

I'd say that this is either counter-intuitive or just plain wrong: in the first case I'd expect the three fields to be as typed - so domain=WORKGROUP, user=Ubuntu and only password=(null).

Many thanks to Morbius for the hint "Pass it a user name and password instead - try your own Linux user name and password. Or your username and samba password." I was misled by the fact that neither the Ubuntu user nor the Windows user *has* a password (ie logon does not ask for one) so **_I thought the password field should be blank. Not true: it should be any old gibberish, but it should not be blank._**

---

### Post by Morbius1 on 2018-09-02
It's actually doing what Windows has always done.

When a Windows client accesses a SMB / Samba server it passes that users local login user name and password to the server - even if the user thinks he has no password. The Windows user doesn't know that of course. If there is a match to those credentials then the user gains access. If there is no match the server will check to see if "guest" access is allowed.

The problem with the samba client is it thinks that whole process of sending your login credentials automatically is goofy so it prompts you for one. And it doesn't quite do "anonymous" correctly - at least not for a Windows server. What it should do is pass ... I don't know ... "bob" as the user name and "bobpw" as the password.

---

### Post by skimtneer on 2018-10-11
Hmm. I installed smbclient, then edited /etc/samba/smb.conf, but instead of "client max protocol = NT1" I used "client min protocol = SMB3". It's true that I still had to know the name (or alternatively, IP address) of my Windows PC that's acting as my media server and couldn't just browse the workgroup / network neighborhood. But that's fine in my case at least.

---

