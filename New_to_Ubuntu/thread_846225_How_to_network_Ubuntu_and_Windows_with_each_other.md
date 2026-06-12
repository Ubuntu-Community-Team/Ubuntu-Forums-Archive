---
title: "How to network Ubuntu and Windows with each other"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-07-01
I wonder if someone could point me to a tutorial or step-by-step on home networking in Ubuntu. I've searched, without success.

I have a couple of Ununtu machines, a couple of Windows Vista, and a couple of Windows XP. They're all linked to a router, which is linked to the Internet.

The Ubuntu machines both access the Internet fine.

The Windows machines all access the Internet and each others' shared folders fine.

Questions:

[LIST=1]
[*]**How do I get the Ubuntu machines to access the Windows shared folders?**
[*]**How do I create shared folders on the Ubuntu machines and let Windows access those Ubuntu folders?**
[/LIST]
Thanks...

---

### Post by Tatty on 2008-07-01
Samba is what you need to get linux and windows machines talking together:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

That should sort you out, good luck.

---

### Post by konungursvia on 2008-07-01
+1 for Samba, it's easy and works.

---

### Post by superprash2003 on 2008-07-01
to access windows files from ubuntu go to places->network.. if not go to the terminal and type sudo nautilus smb://x.x.x.x  ..Replace x.x.x.x with your windows ip address.

---

### Post by Paddy Landau on 2008-07-01
> **superprash2003 said:**
> to access windows files from ubuntu go to places->network.. if not go to the terminal and type sudo nautilus smb://x.x.x.x  ..Replace x.x.x.x with your windows ip address.
So, now I'm *really* confused...

As I said, I have two Ubuntu machines.

[LIST]
[*]My machine, where I've been experimenting (with a view to migrating to Ubuntu from Windows).
[*]My son's machine, which has a recent fresh install.
[/LIST]
The two machines are very nearly identical hardware, and they used the same installation disk to install Ubuntu.

But...

On my son's machine, Places->Network->Windows Network shows all the Windows machines and gives me full access (as I want).
Whereas on my machine, Places->Network->Windows Network shows nothing there. :confused:

This is so frustrating!

Anyway, I used the nautilus command you gave me, and it gave an error message: **Couldn't display "smb://192.168.5.103". Nautilus cannot handle smb: locations.**

I shall experiment with Samba. Wish me luck, unless you have some suggestions for me.

---

### Post by Paddy Landau on 2008-07-01
> **Tatty said:**
> Samba is what you need to get linux and windows machines talking together:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

That should sort you out, good luck.
I've got stuck already.

I followed the instructions up to [Fill in your settings]("https://help.ubuntu.com/community/SettingUpSamba#Fill%20in%20your%20settings:"):
```
Windows Networking
Tick Enable Windows networking
Description:       <whateveryouwant>
Domain/Workgroup:  <yourdomainorworkgroup>
```These options don't exist on System->Administration->Network->General!

What do I do next?

---

### Post by superprash2003 on 2008-07-01
try this samba tutorial [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by Paddy Landau on 2008-07-02
> **superprash2003 said:**
> try this samba tutorial [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)
Thanks for the link to the tutorial.

Sadly, I'm having no luck at all.

I carefully followed the instructions.

[LIST]
[*]The Windows machine still cannot see my Ubuntu machine.
[*]It also takes me no further to letting my Ubuntu machine see the Windows machines (which, for some reason that I don't know, my other Ubuntu machine can do).
[/LIST]
There is a new warning message showing that wasn't showing yesterday: Whenever I use sudo in a terminal, it first shows a warning message:
```
sudo: unable to resolve host paddy-ubuntu
```(*paddy-ubuntu* is my computer's Host name in System->Administration->Network->General)

Do you know what's going on, and how I can fix this? I really, really want to migrate from Windows to Ubuntu, but I absolutely need to access the LAN before I can do so.

---

### Post by Paddy Landau on 2008-07-02
Stop the press! I'm getting somewhere... :)

**Ubuntu shared folder**

[LIST]
[*]I can see my Ubuntu shared folder from Windows, with full access (exactly as I want it).
[*]However, I have to disable my firewall to achieve this. How do I configure *firestarter* to allow the LAN to access the Ubuntu shared folder?
[/LIST]
**Windows shared folder**

[LIST]
[*]I can see Windows shared folder from Ubuntu.
[*]Again, I have to disable my firewall to achieve this. How do I configure *firestarter* to allow Ubuntu to see the Windows network?
[*] **And** it's read-only access. I need read-write access. How do I set that up?
[/LIST]
**Further information**

My Windows network is set up under the workgroup name PADDYWORK. However, it seems that my Ubuntu machine is using the workgroup name WORKGROUP.
[LIST]
[*]Would this difference in name affect my results?
[*]How do I change my Ubuntu workgroup name to PADDYWORK?
[/LIST]

---

### Post by superprash2003 on 2008-07-02
in firestarter there is an option to allow all connections from an ip address. there enter your windows ip there.. for windows shared folders firstly go to windows explorer then tools->folder options.. under view tab at the end uncheck "simple file sharing" .. now try sharing...to get write access..you can change the workgroup name in the smb.conf file .. go to the terminal and type sudo gedit /etc/samba/smb.conf .. there look for WORKGROUP and replace it with PADDYWORK

---

### Post by Paddy Landau on 2008-07-04
Thanks for all the help you have given.

I've had some success, but still remain with a couple of small problems.

Let's address the one problem first...

The good news:

[LIST]
[*]From Ubuntu, I can access shared folders on my Windows computer (over the LAN)
[*]From Windows, I can access shared folders on my Ubuntu computer (over the LAN)
[*]From Ubuntu, I can delete existing files on the Windows shared folder.
[*]From Ubuntu, I can edit and modify existing files on the Windows shared folder.
[/LIST]
However, the bad news:

[LIST]
[*]BUT... from Ubuntu, I cannot create new files or folders on the Windows shared folder.
[/LIST]
Do you know what I need to do to be able to create files and folders on the Windows shared folder from Ubuntu? I have already given full permissions on the Windows Public folder to Guest and to Everyone.

---

