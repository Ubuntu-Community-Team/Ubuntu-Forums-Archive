---
title: "How do you make sure you are not root?"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by NattyLight on 2011-10-28
Only reason I ask is I clicked on the "Software to date" up on the upper task menu by your name, sound, wireless etc and when I clicked to install the updates, it didnt ask for the pw, it just went straight to DLing the updates, so I want to make sure that I'm still not root even though I shouldnt be. I have Ubuntu 11.10.

---

### Post by 3rdalbum on 2011-10-28
That's normal behaviour in Ubuntu 11.10.

If you can run this command:

```
touch /etc/asdf
```

and **not** get a "permission denied" error message, then you are probably root. If you do get that message, then you're definitely not root.

---

### Post by NattyLight on 2011-10-28
> **3rdalbum said:**
> That's normal behaviour in Ubuntu 11.10.
 
If you can run this command:
 
```
touch /etc/asdf
```
 
and **not** get a "permission denied" error message, then you are probably root. If you do get that message, then you're definitely not root.
 
Ok cool, I'm not on Ubuntu now, back on the Windows 7 side to check up on updates, but I will do that when I log back on and report back! :)
 
ninja edit! If I dont get the permission denied message then how would I log off of the root?

---

### Post by lisati on 2011-10-28
On a side note, have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by decoherence on 2011-10-28
By default, sudo (the program that gives you root access) will cache your credentials for a period of time it considers 'reasonable' basically allowing you to run administrative commands without asking for a password.

To clear this cache type

```
sudo -K
```

The next time you run sudo (or try and do something that requires admin access) you will be prompted for your password.

If you want to disable credential caching completely so that you are ALWAYS prompted for a password, open a terminal and type
```

sudo EDITOR=gedit visudo
```

and add the following line to the end of the file

Defaults    timestamp_timeout = 0

---

### Post by NattyLight on 2011-10-28
> **lisati said:**
> On a side note, have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thank you for the link! Puts my mind at ease now :)

---

### Post by NattyLight on 2011-10-28
> **decoherence said:**
> By default, sudo (the program that gives you root access) will cache your credentials for a period of time it considers 'reasonable' basically allowing you to run administrative commands without asking for a password.

To clear this cache type

```
sudo -K
```The next time you run sudo (or try and do something that requires admin access) you will be prompted for your password.

If you want to disable credential caching completely so that you are ALWAYS prompted for a password, open a terminal and type
```

sudo EDITOR=gedit visudo
```and add the following line to the end of the file

Defaults    timestamp_timeout = 0

Do you have to install any packages to do this? after adding that line do you try and save the file?

---

### Post by Paqman on 2011-10-28
> **NattyLight said:**
> Do you have to install any packages to do this?

No, Gedit is the default text editor, it's preinstalled. You're just using it to edit a configuration file that's on your system.

> 
after adding that line do you try and save the file?

Yep.

---

### Post by Lars Noodén on 2011-10-28
> **3rdalbum said:**
> If you can run this command:

```
touch /etc/asdf
```


A less intrusive way would be to run [whoami](http://manpages.ubuntu.com/manpages/oneiric/en/man1/whoami.1.html)

---

### Post by NattyLight on 2011-10-28
Ok, thanks everyone! I appreciate the responses! Now if I can just figure out how to edit my posts to say RESOLVED lol  edit! Nevermind :)

---

### Post by critin on 2011-10-28
[I]<<Now if I can just figure out how to edit my posts to say RESOLVED>>
[/I]
Do you see the handy dandy Thread Tools link at the top of this forum?   Click that and you can do it.

---

### Post by bogan on 2011-10-29
**Critin** posted:>  [I]<<Now if I can just figure out how to edit my posts to say RESOLVED>>
[/I]
Do you see the handy dandy Thread Tools link at the top of this forum?   Click that and you can do it.
When I left-click on Thread Tools I get:>  Show Printable Version
Email this page
Subscribe to this Thread A right-click gives a Firefox menu.
So what is so Handy Dandy about it?
I would like to add "Solved" to some of my threads.

---

### Post by Paqman on 2011-10-29
> **bogan said:**
> **Critin** posted:
When I left-click on Thread Tools I get: A right-click gives a Firefox menu.
So what is so Handy Dandy about it?
I would like to add "Solved" to some of my threads.

You only get the option to "Mark as solved" if you started the thread.

---

