---
title: "General questions about Ubuntu 14.04"
date: 2015-07-19
forum: New to Ubuntu
---

### Post by jerry50 on 2015-07-19
Noob questions:  recently had Ubuntu 14.04 installed as a dual boot with Win 7 and am learning new terminology! 

[LIST]
[*] 	 		 			:KS 		
 	
[/LIST]

1.  What is a keyring password?  How is it different from the password for the computer?

2.  What is my desktop environment?  Unity?

---

### Post by sotiris2 on 2015-07-19
1)The ubuntu keyring is a database that stores passwords used by programs such as your email client and maybe browser (don't know for sure if they use it or do the password keeping on their own). It is encrypted (so it's unreadable if someone just plugged in your hard drive in their machien they could not see your passwords) with your keyring password which I am pretty sure is the same as your Ubuntu login pass. In fact if you type your password to login when you startup your machine you probably won't be asked for your keyring password. 

2) If you are running the 'plain' Ubuntu (not Xubuntu, Kubuntu etc) it is Unity. It has a bar on the left side right?

---

### Post by monkeybrain20122 on 2015-07-19
The keyring password is not the same as the login password. You are supposed to  have set it at some point, but most people don't remember ever setting one, yet it keeps popping up to ask for keyring passwords to unlock this or that and always says you enter the wrong password.  

I  have experienced this problem back in Ubuntu 10.04/10.10 but have not seen it in  Ubuntu proper ever since (I have seen this on xfce/xubuntu more  recently, but not on Ubuntu with Unity,--though there was a recent thread by someone who ran into this)

If you are having this problem of nagging for keyring password and never getting it right, just open the file manager and press ctrl+H and find the hidden folder .local/share and delete the subfolder keyrings. Next time when the window pop up asks you to set a keyring password just enter nothing and confirm then it won't pop up to bug you anymore. (Well of course you could enter a password that you actually remember at this point instead of blank so in the future it will still pop up but you you'll remember what the password is) I think the keyring password is supposed to be a password to access all other passwords, I am not the CIA and I don't need that many layers of passwords. :)

---

### Post by jerry50 on 2015-07-20
Monkeybrain, I was trying to follow your instructions...found local share but there wasn't a subfolder keyrings.  Any other advice?  I'm using Ubuntu 14.04 with unity de.

---

### Post by monkeybrain20122 on 2015-07-20
> **jerry50 said:**
> Monkeybrain, I was trying to follow your instructions...found local share but there wasn't a subfolder keyrings.  Any other advice?  I'm using Ubuntu 14.04 with unity de.

The path is ~/.local/share/keyrings, so keyrings is inside share, and share is inside .local, and .local (note the '.') is a hidden folder inside your home. I just checked, I have that folder. 

Edited: there is another local/share inside /usr in the file system (full path /usr/local/share) that is NOT the one.

---

