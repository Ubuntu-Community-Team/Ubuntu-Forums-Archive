---
title: "Collabnet install error: &quot;must be root to perform this action&quot;"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by jeanke2 on 2013-06-02
When trying to install collabnet subversion edge, as described in the installation instructions:

> [COLOR=#000000][FONT=Helvetica]   4. Optional. Install the application so that it will start automatically[/FONT][/COLOR]
      when the server restarts.  This command generally requires root/sudo to      execute.            $ cd csvn [COLOR=#000000][FONT=Helvetica]      $ sudo -E bin/csvn install[/FONT][/COLOR]
When performing last command, I get the error "[COLOR=#222222][FONT=Verdana]Must be root to perform this action.[/FONT][/COLOR]"I thought sudo command would make it possible to execute it with root right.Any ideas why I can't perform this action?

---

### Post by MirrorUniverse on 2013-06-02
You have to provide your password when you do things as root.  If it was not necessary, any attacker could run sudo in the terminal and execute programs and what not on your computer.  Which I suppose is partly why Windows is so unsecure? ;)

---

### Post by jeanke2 on 2013-06-02
When using sudo it obviously prompts for my password, which I entered. After this the error is given...
> [COLOR=#000000]You have to provide your password when you do things as root. If it was not necessary, any attacker could run sudo in the terminal and execute programs and what not on your computer. Which I suppose is partly why Windows is so unsecure? [/COLOR][IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]
Using sudo should execute the command as root, or am I mistaken?

---

### Post by MirrorUniverse on 2013-06-02
Just to be sure, you are in an admin account, right?  I don't think it works if you are in a user account.
> Using sudo should execute the command as root, or am I mistaken? 				
Yes it does.

---

### Post by jeanke2 on 2013-06-02
Yes, I'm in an admin account.

> **MirrorUniverse said:**
> Just to be sure, you are in an admin account, right?  I don't think it works if you are in a user account..

---

### Post by MirrorUniverse on 2013-06-02
Typing "man sudo" in the terminal gives information about the command.  Here is a webpage with more info.
[http://askubuntu.com/questions/70534/difference-between-su-sudo-s-sudo-i](http://askubuntu.com/questions/70534/difference-between-su-sudo-s-sudo-i)  Beyond that I can't be of much help as I am very new to this myself.

---

### Post by jeanke2 on 2013-06-02
> **MirrorUniverse said:**
> Typing "man sudo" in the terminal gives information about the command.  Here is a webpage with more info.
[http://askubuntu.com/questions/70534/difference-between-su-sudo-s-sudo-i](http://askubuntu.com/questions/70534/difference-between-su-sudo-s-sudo-i)  Beyond that I can't be of much help as I am very new to this myself.

Samer error response using su

---

### Post by Paqman on 2013-06-02
So, to be clear, the command you're trying to execute is:
```
sudo -E bin/csvn install
```
Yes? I suspect the problem is the use of the -E flag. Do you get the same error if you drop it?

---

### Post by jeanke2 on 2013-06-02
```
sudo bin/csvn install
``` returns same error response

---

### Post by ShadowVegan on 2013-06-02
Perhaps try sudo su?
```
sudo su
-E bin/csvn install
```
(separate lines; type the second line after entering password)

Note that you will now be using a terminal as root, so it as if you are doing 'sudo' for all commands, so be careful what you type in it. Close the terminal as soon as you are done with the commands you want to perform as root.

---

### Post by jeanke2 on 2013-06-02
same result I'm afraid...

---

