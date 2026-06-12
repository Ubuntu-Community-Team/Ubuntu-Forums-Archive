---
title: "I can not work with terminal"
date: 2018-09-13
forum: New to Ubuntu
---

### Post by pravin-c-shah on 2018-09-13
My password for logging in UBUNTU 18.04 should be the same as for terminal but when I use terminal it does not work. What to do? I had upgraded from 17.10 UbUNtu .

---

### Post by DuckHook on 2018-09-13
*Thread moved to **New to Ubuntu** as the more appropriate forum.*

---

### Post by Impavidus on 2018-09-13
What does not work?

You need the password in terminal when you use sudo (or when you change password). Use **sudo <whatever command you want to run>**. sudo will ask you for your password. Type it. No feedback will show in the terminal, not even ******, but you can type. Then hit enter. If the password was wrong, it wil tell you. You get three chances. If something else goes wrong, you get a different error message.

---

### Post by TheFu on 2018-09-13
What do you mean by "terminal?"   Did you change to a different TTY or are you trying to ssh into the machine from some other machine?  "terminal" is vague, inexact.

---

### Post by oldos2er on 2018-09-14
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by yetimon_64 on 2018-09-15
> **pravin-c-shah said:**
> My password for logging in UBUNTU 18.04 should be the same as for terminal but when I use terminal it does not work. What to do? I had upgraded from 17.10 UbUNtu .
If the terminal gives no feedback then that is normal, as  Impavidus notes ...
> [COLOR=#000000]No feedback will show in the terminal...[/COLOR] ... and that is normal for linux, keep entering it as you normally would and then press the "Enter key".

If you want feedback from the terminal it is possible to set up by editing as root the file /etc/sudoers; let us know if that is what you need.

If you can log into the machine OK but are getting an authentication error when you try to use the terminal (please give more info as to what is actually happening, we're having to take a lot of "guesses" here ;-)), you may have a problem with your username containing an illegal character, which can also prevent authentication on the command line while logging into the machine will still work.
If you have capitalised your username or used special characters on the keyboard in your username, the installer and GUI will sometimes be OK with it but the system can often replace such characters with an underscore when authentication is attempted on the CLI.
If this is what seems to be happening when attempting authentication on the command line, first use the command ...
```
whoami
``` 
...to see how the system is seeing/using your username and use it as it is returned by the command (with underscores etc, if any) when trying to authenticate on the CLI.

There are a few possibilities depending on the exact nature of your problem, but we need to know more specifics of the situation before any real help can be given.  Please let us know a lot more detail about how it "does not work". 

Regards, yeti.

---

