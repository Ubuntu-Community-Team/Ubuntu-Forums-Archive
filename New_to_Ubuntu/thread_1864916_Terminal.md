---
title: "Terminal"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by jeffers2011 on 2011-10-19
HI, I am a complete newbie that has just installed version 11:10 on a Toshiba laptop, (got rid of Windows) Since then I have added Docky, a firewall and chome web browser. the problem I have is the terminal consul, if you can call it that, is different  to the ones I have seen on various websites. I have a large black screen telling me things about sudo, commands, and admin rights. Oh and if I press ALT+CTRL+T it is this box that appears. Thanks

---

### Post by kriegoamigo on 2011-10-19
can you post the image of that black window that you are getting..... ???

---

### Post by Lars Noodén on 2011-10-19
What is it that you want to do in the terminal?  It helps to have some goals in mind.

---

### Post by jeffers2011 on 2011-10-19
I can do but I am away from the said laptop for about an hour

---

### Post by jeffers2011 on 2011-10-19
I was going to try and add a screensaver as that seemed a simple thing to do to get used to the terminal.

---

### Post by dniMretsaM on 2011-10-19
That only comes up the first time, you should still see a prompt (name@localhost~$). Type a command (for a simple command, just type [FONT=courier new]ls ~/[/FONT]) and run it. After it runs, close the Terminal and reopen it. The message should have disappeared.

---

### Post by kriegoamigo on 2011-10-19
take ur time and post it :)

---

### Post by jeffers2011 on 2011-10-19
sorry for delay. it brings up the words. Desktop folders ubuntu one and other bits

---

### Post by jeffers2011 on 2011-10-19
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

gandm@gandm-Satellite-A210:~$

this is everything that is on the screen at present

---

### Post by dniMretsaM on 2011-10-19
> **jeffers2011 said:**
> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

gandm@gandm-Satellite-A210:~$

this is everything that is on the screen at present

Did you try what I said in my previous post?

---

### Post by jeffers2011 on 2011-10-19
Yes, this is the result.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

gandm@gandm-Satellite-A210:~$ ls ~/
Desktop    Downloads         Music     Public     Ubuntu One
Documents  examples.desktop  Pictures  Templates  Videos[/COLOR]
gandm@gandm-Satellite-A210:~$

---

### Post by Sef on 2011-10-19
> To run a command as administrator (user "root"), use "sudo <command>".

For administrative tasks you need to put sudo before the command. E.G., sudo apt-get update will update your system. apt-get update will get you an error message.

---

### Post by jeffers2011 on 2011-10-19
Yes. this is the result.


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

gandm@gandm-Satellite-A210:~$ ls ~/
Desktop    Downloads         Music     Public     Ubuntu One
Documents  examples.desktop  Pictures  Templates  Videos
gandm@gandm-Satellite-A210:~$

---

### Post by dniMretsaM on 2011-10-19
> **jeffers2011 said:**
> Yes, this is the result.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

gandm@gandm-Satellite-A210:~$ ls ~/
Desktop    Downloads         Music     Public     Ubuntu One
Documents  examples.desktop  Pictures  Templates  Videos[/COLOR]
gandm@gandm-Satellite-A210:~$

Even after you restart the terminal?

---

### Post by jeffers2011 on 2011-10-19
Thanks, time to get me hands dirty.

---

