---
title: "How to exit Sudo for first time?"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by jimrazz on 2008-09-11
Hi,

I have just install xubuntu alternative 7.04 on a 11 year old laptop and I am stuck in Sudo. How do I exit sudo to begin enjoying xubuntu?

Thank you in advance,

Jim

---

### Post by gvartser on 2008-09-11
Exit sudo?

type in:
```
exit
```

/g

---

### Post by RomeReactor on 2008-09-11
Hi. Can you please explain in more detail?

---

### Post by jerome1232 on 2008-09-11
I think the question needs to be phrased better what do you mean by "stuck in sudo" are you stuck in a root shell? (typing exit will get you back to a normal shell) 

Or are you not used to the mechanics of sudo and need help with using sudo.

---

### Post by WRDN on 2008-09-11
If you have gained sudo privileges and want to loose them, open the Terminal and type:

```
sudo -k
```

I would also recommend changing the sudo timeout, though this is purely optional. I find the default time too long, so on my PC, the sudo privileges timeout after 2 minutes. To change this, type:

```
sudo nano /etc/sudoers
```

Now, add ",timestamp_timeout=2" to the end of the line "Defaults env_reset".
The result will be:

> Defaults env_reset,timestamp_timeout=2

You can change the value 2 to something else if you wish.

Now save the file by pressing Ctrl + X, then entering the letter "y".

---

### Post by Bulat Sirazetdinov on 2008-09-11
I suppose that the problem is that Xfce doesn't start automatically ?  So you don't need to _exit_ text-mode command-line shell (why do you call it "sudo" ?). You need to _start_ X-Windows.  Try typing this:
startx

At least, you'll get some error messages that we'll let you dig the problem further. :)

---

### Post by jimrazz on 2008-09-11
I am sorry, I was not very clear. The software was just installed and I appear to be upon boot up in the following:

oem@ubuntu:~$  

I type in the oem ID that I was assigned upon installation. Upon exiting sudo I should be able to assign my own ID an d begin using ubuntu.

I hope this is more clear.

Jim

---

### Post by Tatty on 2008-09-11
> **jimrazz said:**
> I am sorry, I was not very clear. The software was just installed and I appear to be upon boot up in the following:

oem@ubuntu:~$  

I type in the oem ID that I was assigned upon installation. Upon exiting sudo I should be able to assign my own ID an d begin using ubuntu.

I hope this is more clear.

Jim

Um, im a bit confused.  Have you just installed this yourself or has an OEM installed it for you?

I know there is an OEM option on the ubuntu install CD but I have never used it (as it is designed for manufacturers who want to sell ubuntu pre-installed).  Is this what you used to install Ubuntu?

Can you give us a link to the guide you are following?

Also what version of Ubuntu have you installed?

---

### Post by jimrazz on 2008-09-11
I have installed xubuntu 7.04 alternative and the oem version. I am not working with a guide.

Any suggestions would be appreciated.

Jim

---

### Post by ilrudie on 2008-09-11
> **WRDN said:**
> ```
sudo nano /etc/sudoers
```Now, add ",timestamp_timeout=2" to the end of the line "Defaults env_reset".


This is not the best way to do this.  ```
visudo
``` is preferred because it checks the syntax of the file before saving it helping to insure that a typo doesn't lock you out of your system.  As I understand it any syntax error at all kinda shuts sudo down and you'll have to reboot into rescue mode and fix it before you can administer your system normally again.

---

### Post by jimrazz on 2008-09-11
The reply I received was 

visudo: /etc/sudoers: permission denied

---

### Post by jerome1232 on 2008-09-11
You'll have to run it as root

```
sudo visudo
```

---

### Post by Bulat Sirazetdinov on 2008-09-11
> **jimrazz said:**
> I am sorry, I was not very clear. The software was just installed and I appear to be upon boot up in the following:

oem@ubuntu:~$  

I type in the oem ID that I was assigned upon installation. Upon exiting sudo I should be able to assign my own ID an d begin using ubuntu.

I hope this is more clear.

Nope. :) That's also very confusing. :-/
Where from did you get that you'll be able to assign your own ID upon exiting "sudo" ? :O
And why do you want to assign your own ID instead of using "oem" user login ? :)

By the way, you are not in "sudo". I know that because of the error message you've got when trying to use "visudo" to edit system configuration files.

Maybe you have to go into super-user mode and then leave it ?  Then you can do just "su". Or run a shell using "sudo" - type in "sudo bash".

P.S. I suppose that you've read a chunk of some sort of an installation guide. A useless chunk. :)  Maybe it was written there how to create a new user (login) and that you'll need a "sudo" command to be able to do that ?  But you also need to know the very command that will create a new user. I don't remember that command - try using google yourself. :)

---

### Post by t0p on 2008-09-11
I too am confused as to what exactly you are talking about.

You mention "oem id" a few times.  Did you install xubuntu using the oem option?  If so, why?

I've never used the oem option to install ubuntu.  It's meant for computer manufacturers who want to sell pcs with (x)ubuntu pre-installed.  I don't know, but I'd suspect using this option is not a good idea.  If you haven't customized xubuntu too much yet (I don't think you have) it might be an idea to reinstall, *not* using the oem option this time.

As for this "exit sudo" - whatever you are calling "sudo" is *not* sudo.  Are you talking about the terminal (a command line like the dos prompt)?

Someone here will certainly be happy to help you.  But you need to make yourself clear first.

---

