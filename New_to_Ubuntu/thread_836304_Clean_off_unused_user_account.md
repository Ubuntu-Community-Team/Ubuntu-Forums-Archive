---
title: "Clean off unused user account"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by techuser on 2008-06-21
In trying to figure out how to create multiple user accounts and see how Hardy deals with the account a Test1 account was made. Now that I am done The account has been removed from System>Administration>Users and Groups but the folder "Test1" and it sub-folders are still on my drive. Properties shows that I have no permission nor can I create permissions to delete the Folders and contents.
I attempted to use the Terminal and:  sudo rm -r ~/Test1
My use of terminal commands is obviously weak. The attempt failed.
Does anyone know how to remove the file in question?

---

### Post by KenBW2 on 2008-06-21
"~" refers to *your* Home folder, for example ~/ means /home/kenneth/ for my PC.
You'll have better luck with
```

sudo rm -r /home/Test1

```

---

### Post by qix on 2008-06-21
You're almost right. Type
sudo rm -rI /home/Test1

But be aware. Using the "sudo rm -r" can be really nasty if you don't know what you're doing!! Therefore I advice to do it with -rI instead, so you'll be asked to confirm.

---

### Post by techuser on 2008-06-21
Perfect! I knew it was something simple. The advice worked great!

---

### Post by Canis familiaris on 2008-06-21
> **KenBW2 said:**
> "~" refers to *your* Home folder, for example ~/ means /home/kenneth/ for my PC.
You'll have better luck with
```

sudo rm -r /home/Test1

```
Please NEVER advise sudo rm -rf, advise this:
```
sudo nautilus /home

```
And in the Nautilus Window, delete ~username~ folder.

---

### Post by KenBW2 on 2008-06-21
The OP was asking where he/she was going wrong with the command. I corrected that. And since when did an "Are you sure" prompt make a difference :confused:

I'm aware of the dangers of sudo rm -r, but the OP clearly knew what he/she was doing and what the command was made to do.
/rant

---

### Post by windlocker on 2008-08-26
Got the following message:rm: cannot remove `/home/myoldaccount/.gvfs': permission denied.....

---

