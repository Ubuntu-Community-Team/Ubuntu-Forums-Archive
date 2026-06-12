---
title: "Extraction Permissions tar.bz2"
date: 2014-01-07
forum: New to Ubuntu
---

### Post by zeusturtle on 2014-01-07
Hey all, 

    I'm a recent dual booter (win7/12.04) and I'm running into issues when attempting to install the latest version of VUZE. I downloaded the tar.bz2 from Vuze's site, since the most recent on the software center is .3 versions behind, and when I try to extract to either /usr/local or /opt I receive a message seen below. 

[ATTACH=CONFIG]249312[/ATTACH]

    How do I go about fixing this problem? I have attempted to search this problem and found similar issues; however, none of the fixes I've found have worked. I have attempted opening the terminal and typing: su, entering my password only to be told "Authentication failure". I am the only user on this laptop (other than those on the Windows Partition). Both the /usr/local and /opt folders are root permissions only if that helps.

Thanks in advance!

~Farnsworth

Ps. Please let me know if the SS is too small or doesn't show enough info!

---

### Post by Dennis N on 2014-01-07
Extract to your Desktop, then use **mv** with sudo to move the files or directories into root-owned directories (such as /opt or /usr).

---

### Post by Impavidus on 2014-01-08
> **Dennis N said:**
> Extract to your Desktop, then use **mv** with sudo to move the files or directories into root-owned directories (such as /opt or /usr).

If you do it that way, you may have to recursively chown them to root afterwarts. Alternatively, extract with root permission.

su without an argument is to switch user to root, but the root account is locked by default on Ubuntu. On other distros it may work. It's designed that way because with a locked root account it's more secure. Have a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

---

### Post by zeusturtle on 2014-01-09
> **Impavidus said:**
> If you do it that way, you may have to recursively chown them to root afterwarts. Alternatively, extract with root permission.

su without an argument is to switch user to root, but the root account is locked by default on Ubuntu. On other distros it may work. It's designed that way because with a locked root account it's more secure. Have a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

This is great info; however, I can't seem to find anywhere that describes how extract with root permission. I know you can use the CLI for extraction but I am *extremely* new to CLI commands. Do you have any idea how to go through this process?

Thanks!

---

### Post by Dave_L on 2014-01-09
In my opinion, since you're unfamiliar with the command line, the safe method is to use Dennis N's solution above.

To move the files to the desired location, launch an instance of the file manager as root:
```
gksudo nautilus &
```

You can also change the file ownership and permissions if needed.

Close that instance of the file manager as soon as you're finished moving the files.

---

### Post by zeusturtle on 2014-01-10
> **Dave_L said:**
> In my opinion, since you're unfamiliar with the command line, the safe method is to use Dennis N's solution above.

To move the files to the desired location, launch an instance of the file manager as root:
```
gksudo nautilus &
```

You can also change the file ownership and permissions if needed.

Close that instance of the file manager as soon as you're finished moving the files.

So, for my understanding, that command says - graphical instance with superuserdo permission (aka root) in nautilus (the default ubuntu file manager)... im not sure what the '&' is for though. And thank you, this is exactly what I was looking for!

~H

---

### Post by zeusturtle on 2014-01-10
Oh and not to discount Dennis N's contribution. I really appreciate it!

---

### Post by Impavidus on 2014-01-10
The & is to start the program in the background, so that you get a new prompt in the terminal. You don't really need it here, but any program that doesn't expect terminal input can be started in the background.

If your problem has been solved, could you mark the thread as solved? Click thread tools &#8594; mark as solved.

---

### Post by zeusturtle on 2014-01-12
> **Impavidus said:**
> The & is to start the program in the background, so that you get a new prompt in the terminal. You don't really need it here, but any program that doesn't expect terminal input can be started in the background.

If your problem has been solved, could you mark the thread as solved? Click thread tools &#8594; mark as solved.

Sorry for the delay in response. Although I can run Vuze now, I cannot discover it in Unity. The Vuze file will show up but does not show as installed on my system. I attempted to update it via CLI and that's how I found out that even though it extracted now it is not technically installed. Any ideas?

---

### Post by 3rdalbum on 2014-01-13
It is perfectly fine where and how it is. You just need to set up a ".desktop" file so it will appear in the menu... there might even be one already that you can just copy into /use/share/applications/

If there is no .desktop file already, you can install Alacarte (also known as Main Menu) which makes it easy to create menu items. Alacarte is in Ubuntu Software Center and is called Main Menu in Unity.

---

### Post by zeusturtle on 2014-01-13
> **3rdalbum said:**
> It is perfectly fine where and how it is. You just need to set up a ".desktop" file so it will appear in the menu... there might even be one already that you can just copy into /use/share/applications/

If there is no .desktop file already, you can install Alacarte (also known as Main Menu) which makes it easy to create menu items. Alacarte is in Ubuntu Software Center and is called Main Menu in Unity.

So I apparently already have this installed; however, there is not a menu bar (or anything for that matter) at the top left side of my desktop except the default "Ubuntu Desktop". Any ideas how I can get this to integrate?

ps. I'm adding a screenshot incase I'm not explaining it very well.
[ATTACH=CONFIG]249470[/ATTACH]

---

