---
title: "Networking/Setting up a share"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by ekyjim on 2012-01-11
I just finished installing 11.10 on my computer that has (2) 80 GB hard drives and wireless networking.  My goal is to set this up as a media server for our home media.

The wireless is working fine, pulls an IP address, I have Internet access, but I'm having trouble getting the computer on our existing Windows network.

What I want to do is use the second drive for file storage, I've set the share up in Samba, but I can't see the share on the Windows network.  I also can't pull the Windows network up on this machine, getting a "Failed to retrieve share list from server" when I try.

I've modified the smb.conf file to reflect the Windows workgroup.

What am I missing?

Thanks
Jim

---

### Post by ekyjim on 2012-01-13
Well, I'm halfway there.  I was working on this machine at work, and could not get it to work on this network.

I took it home last night, changed the settings for wireless and changed the workgroup name, and it showed up on the network, and I could copy files to it.  My network at home is basically the same network setup as it is at work, same kind of security and encryption, and I didn't change anything other than the wireless SSID and Security Mode.

I still can't get it to read the Windows computers, so if anyone has some suggestions on what I can look at there, I'd appreciate it.

So, in summary, I can pull the Ubuntu shares up in My Network Places on my Windows XP computer, copy from Windows to the Ubuntu shares, but the Ubuntu machine still won't connect to the Windows computers.

Thanks
Jim

---

