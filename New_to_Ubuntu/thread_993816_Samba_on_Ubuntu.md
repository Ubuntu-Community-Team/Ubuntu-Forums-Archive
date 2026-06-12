---
title: "Samba on Ubuntu"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by wstay on 2008-11-26
My ubuntu 8.04 does not have samba installed.
I want to do net-working with windows.
Where and how can I install samba.

---

### Post by Peter09 on 2008-11-26
If you only want to see windows shares then you only need the samba client, which is normally already installed.

Have you looked through the Places->network menu for your windows shares?

to install the Samba client - in a terminal type-

```
sudo apt-get install smbclient 
```

to fully install Samba

```
sudo apt-get install samba
```

**Terminal Basics**
To make life easier when using the terminal:
1. The up and down arrow keys allow you to move through the command history of the terminal. So if you make a mistake in a command the up arrow will return to it, you can the edit the command using the left/right arrows and the del/backspace keys. Hit enter when you are ready to re-issue.

2. Hitting the TAB key when you are in the middle of typing a command makes the terminal attempt to autocomplete the command/filename that you are typing.  Hitting the TAB key twice displays all the options available for autocompletion

---

### Post by roger_1960 on 2008-11-26
Hi

Have a look at:

[http://samba.netfirms.com/](http://samba.netfirms.com/)

---

### Post by roger_1960 on 2008-11-26
Hi

Have a look at:

[http://samba.netfirms.com/](http://samba.netfirms.com/)

---

### Post by Dedoimedo on 2008-11-26
Hello,

I've written a short tutorial on Samba sharing for Windows and Linux hosts in a mixed environment. Check my site (sig), if you want. There's an article "highly useful linux commands & configurations" that explains sharing. Other articles go into this too, but they are for other distros (pclinuxos, wolvix), so they're less relevant.

I hope this helps.

Dedoimedo

---

### Post by wstay on 2008-11-28
> **Dedoimedo said:**
> Hello,

I've written a short tutorial on Samba sharing for Windows and Linux hosts in a mixed environment. Check my site (sig), if you want. There's an article "highly useful linux commands & configurations" that explains sharing. Other articles go into this too, but they are for other distros (pclinuxos, wolvix), so they're less relevant.

I hope this helps.

Dedoimedo
How can I navigate to your site (sig)?

---

### Post by bodhi.zazen on 2008-11-28
You can do it all from the GUI.

Do not share your home directory, but instead select a directory (folder) in your home directory, say "Documents"

right click on the folder -> share options -> Click the "Share this folder" box.

You will get a pop-up menu -> Select "Install Service"

Enter your password ->  This will install samba (server).

You need to log off and back in for the changes to take effect. Then a second time right click "Documents" and set the share name and permissions.

Viola, done. You should see the share on Windows. username = you ubuntu log in password = your ubuntu password.

---

### Post by benhur99ph on 2008-11-28
I've posted a mini-howto about this ... you can find it here --> [http://ubuntuforums.org/showpost.php?p=6261247&postcount=8]("http://ubuntuforums.org/showpost.php?p=6261247&postcount=8")

Hope it helps.

---

### Post by Dedoimedo on 2008-11-29
> **wstay said:**
> How can I navigate to your site (sig)?

Well, to make it easier:
[http://www.dedoimedo.com/](http://www.dedoimedo.com/)

Dedoimedo

---

### Post by wstay on 2008-11-30
> **Dedoimedo said:**
> Well, to make it easier:
[http://www.dedoimedo.com/](http://www.dedoimedo.com/)

Dedoimedo
But where do I find a short tutorial on Samba sharing for Windows and Linux hosts in a mixed environment as you mention on your site.

---

### Post by wstay on 2008-11-30
I can connect  to my network ms windows pc but when I open the share folder, it is empty,  though I have got some files in it. Am I missing something in my smb.conf file.

---

### Post by Dedoimedo on 2008-11-30
> **wstay said:**
> But where do I find a short tutorial on Samba sharing for Windows and Linux hosts in a mixed environment as you mention on your site.

Here you go:
[http://www.dedoimedo.com/computers/linux_commands.html](http://www.dedoimedo.com/computers/linux_commands.html)

Check under sharing ...

Likewise, check the PCLinuxOS tutorial and Sharing folders between Windows and Linux (on Wolvix) for general concepts on how to setup things. But your best best is the first article ...

Dedoimedo

---

### Post by wstay on 2008-12-13
I am having problem with networking.
The problem is after connecting both my ubuntu8.04 and my wins xp computers, I can see ubuntu shared files from wins xp
but I cannot see wins xp shared files from ubuntu even with firewall turn to off in wins xp 
(though I can see the wins xp network computer from ubuntu).
What should I put under [global] in the smb.conf file to solve this problem?

---

