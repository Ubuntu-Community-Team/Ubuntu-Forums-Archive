---
title: "My virtualbox script won't run. Help?"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by softappstudio on 2013-08-22
Using the latest Ubuntu (ex zorin 6) I can enter this from a console and it works ...
virtualbox --seamless --startvm Win-XP

But if I paste that exact command into a text file, set all its permissions RW, check
[*] the box for {Make Executable} then run the file it starts virtualbox *but* virtualbox cannot find the Win-XP vitrual machine. I have tried copying the script linker to /home  (same directory as the console?) but that does not help.

Can anybody help (probably very simple!).

Thanks,
--Grahame

---

### Post by JKyleOKC on 2013-08-22
How are you running your script file? If you do it via "sudo" then it will run as "root" rather than as your user, and the VM files are normally stored in a subdirectory of your $HOME directory. That would explain why vbox fails to find the VM. However if you are simply running the script as your normal user, I have no clue why the lookup would fail. You might try adding lines to the script to echo the result of "pwd" and "whoami" to a log file in your home directory, to see exactly what conditions actually are when it launches virtualbox...

---

### Post by softappstudio on 2013-08-22
Thanks Jim, obviously worth doing. I do everything as "joanne" (I'm doing this on my wife's computer), who has admin priv.
So if I do pwd from a console I get /home/joanne/  , and if I put pwd>debug.txt in the script file (which is located in /home/joanne/) it shows me /home/joanne/  [the same] . Similarly, whoami always reports "joanne".
Still a dysfunctional mystery!
Any further thoughts on how to address this?
--Grahame

---

### Post by JKyleOKC on 2013-08-23
If the object is to create a script and thus simplify the process of getting the VM started, try "VBoxManage startvm Win-XP" instead. That's the command I use in my scripts and it definitely does work. It doesn't in itself force the "seamless" operation, but you can set it to run in seamless mode once it's started, then save the state instead of shutting down the VM, and the "startvm" command will then bring it back as if it had been simply suspended from the previous session.

There may be a VBoxManage command that will force seamless operation, that you could put into your script following the "vmstart" line, also. VBoxManage is a much more powerful tool than is the VBox GUI itself; while I've been using VBox for quite a few years now, I've never managed to learn more than a small fraction of the capabilities in VBoxManage. The manual, which you can reach through the "help" menu of the VBox GUI, has full details and some examples...

Hope this helps. I've never tried to use the exact command that you're using, having come across VBoxManage first.

---

### Post by softappstudio on 2013-08-28
Thank you Jim, I am in debt to your experience.
I installed VboxManager and it works for me as you  advertised.  Magic!
--Grahame

---

### Post by JKyleOKC on 2013-08-29
> **softappstudio said:**
> Thank you Jim, I am in debt to your experience.
I installed VboxManager and it works for me as you  advertised.  Magic!
--GrahameIf you mark the thread solved as per the link in my sig, it may help others in the future...

---

