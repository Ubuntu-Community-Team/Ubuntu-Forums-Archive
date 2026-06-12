---
title: "[General]Running command as sudo, from the terminal, no-login"
date: 2008-10-03
forum: Programming Talk
---

### Post by Pyro.699 on 2008-10-03
Hello,

Sorry for the long title, its kind of hard to get the main idea of the problem into one short sentence. A longer sentence however would produce the following. How would you go about running a sudo process, such as **shutdown**, from the command prompt, without actually having to login. Something similar to **sudo -s --password=steal_me shutdown -s 0**.

Thanks for all your help
~Cody Woolaver

---

### Post by yoda2031 on 2008-10-03
I'm not quite getting it.  You want to run a command in a tty pre-login or a terminal emulator like gnome-terminal or konsole without typing in your password?

I'm also not sure why this is in the Programming section...

---

### Post by Pyro.699 on 2008-10-03
I was planning to get into that later on, its going to be run from a java application. I need to shutdown the computer from a java application using the shutdown command found in the terminal. I know that in order to use the shutdown command properly, you need to login as root.

Sorry for that
~Cody Woolaver

---

### Post by yoda2031 on 2008-10-03
Ahh I see what you're trying to do, now!  I think the process calling the shutdown command would need root access in order to execute the shutdown command.  Might I ask why your application needs to shut the computer down?

---

### Post by Pyro.699 on 2008-10-03
You've probably seen my previous posts, about terminals, process' and other applications. To put it simply im making a website that can control all aspects of my own laptop from a remote location (this is not being used as RAT if you were wondering that(for computers other than my own)). Im on dial-up at home and need some means of access to high speed, so ive been given permission to leave my laptop in certain areas and would like a convenient means of controlling it without having to go to the laptop every day. I cant use VNC and other tools like that because i have no access to the router meaning no ports available, so i need to use the ones that are already available to me, like number 80 :)

Thanks
~Cody Woolaver

---

### Post by Rich78 on 2008-10-03
I wouldn't host a public site that controls your laptop if I were you.

Could you not test what ports you're able to communicate over?  I would be looking at SSH to start with.

I'm still non the wiser as to what you're trying to achieve, unless it's to use it for browsing the net using it's connection.  You'd still have dire results for your home end as the dial up will still have to refresh the screen and handle keystrokes and mouse movements.  I've used some slow connections before and it gets very tiring.

If you really must go this route, look into the possiblility of going via SSL (ie https).  You'd need to register a cert though.

---

### Post by The Cog on 2008-10-03
> **Pyro.699 said:**
> I was planning to get into that later on, its going to be run from a java application. I need to shutdown the computer from a java application using the shutdown command found in the terminal. I know that in order to use the shutdown command properly, you need to login as root.


I take it that the java program will be running as a user other than root. You could try doing **Runtime.exec("sudo shutdown");** and configure sudo such that the user that launches the java prog is allowed to sudo shutdown without being challenged for a password.

---

### Post by Pyro.699 on 2008-10-03
Just so everyone knows the website will be on a personal remote server with no access to the public, I've ensured that. How do you exactly configure it so the user using **sudo** doesn't need to input a password.

Thanks
~Cody Woolaver

---

### Post by Rich78 on 2008-10-03
> **Pyro.699 said:**
> Just so everyone knows the website will be on a personal remote server with no access to the public

Via secure point to point VPN?  I wouldn't use anything else.

Sorry it's not answering your question but I would recommend against doing this unless it is truely tied down.

If not OpenVPN is probably the simplest option, if you don't have access to some nice Cisco routers.

---

### Post by Pyro.699 on 2008-10-03
Believe me when i say that Ive tied it down. Its got several access points, theres 2 .htaccess passwords, theres a PHP login as well as a MySQL one, totaling 4 accounts with md5 passwords. Thankyou for your concirn though. VNC wouldnt work because it requires a specific IP and the location where i have permission to do this has litterally thousands of IPs with a router im not aloud to access. Still looking for the code though, thankyou

---

### Post by geirha on 2008-10-03
> **Pyro.699 said:**
> Just so everyone knows the website will be on a personal remote server with no access to the public, I've ensured that. How do you exactly configure it so the user using **sudo** doesn't need to input a password.

Thanks
~Cody Woolaver

In a terminal:
```
sudo visudo
```
I think nano is the default editor. If you want to use a different editor, set the EDITOR variable for that command, e.g. for vim: ```
sudo EDITOR=vim visudo
```

Add a line like this at the end of the file visudo brings up:
```
*someuser* ALL=NOPASSWD: /sbin/shutdown
```
After you've saved, *someuser* will be able to run **sudo shutdown ...** without having to type a password.

The order of the lines is important. It must be below the line for the admin-group (the line staring with %admin). Read **man sudoers** and **man visudo** for more detailed information.

---

### Post by Pyro.699 on 2008-10-03
I added that line, and then added it so the group **cody** was able to do this. After i restarted my laptop it still asked me for the password after i typed **sudo gedit**.

```


Defaults        env_reset

# %sudo ALL=NOPASSWD: ALL
root    ALL=(ALL) ALL
cody    ALL=NOPASSWD: ALL
%cody ALL=(ALL) ALL

```

Thanks
~Cody Wolaver

---

### Post by geirha on 2008-10-03
As I said, the order of the lines are important.

```
cody    ALL=NOPASSWD: ALL
``` Says cody should be able to run all commands without typing a password, but ```
%cody ALL=(ALL) ALL
``` overrides this by saying anyone in the group cody can run all commands, but must provide a password.

It's not a good idea to allow a user to run any command as root without a password btw. Limit it to the commands you actually need run.

---

