---
title: "User Privileges..."
date: 2008-08-14
forum: New to Ubuntu
---

### Post by triplenine on 2008-08-14
What is the best way to get my normal user account to have full administration privileges? I am the only user on this machine and not being able to simply edit a file (in this case GRUB's menu.lst) and save it is driving me nuts. Let me know what you think or I might just be missing something. Just would like to be able to click and go on these sorts of things rather than using a terminal + sudo.

---

### Post by Ryadt on 2008-08-14
It's not recommended cause of security reasons. You won't find help on the forum as it is against forum rules for a member to help on this issue.

---

### Post by finer recliner on 2008-08-14
sudo is a good thing. the first rule in linux is "do not log in as root unless you have to".

more here:

[https://help.ubuntu.com/community/RootSudo#Benefits%20of%20using%20sudo](https://help.ubuntu.com/community/RootSudo#Benefits%20of%20using%20sudo)

---

### Post by LowSky on 2008-08-14
Using sudo is much safer, sorry if you don't like it, You must right off of Windows. if you want click and open then save, you'll need to enable your Root account, which isn't safe at all!!!! Got to System> admin> user & groups
 OR
to edit grub just put open a terminal and type ```
gksu nautilus
``` leave the terminal open, and the mess with what ever file you need to fix. CAREFUL YOU CAN BREAK STUFF EASILY

---

### Post by Nepherte on 2008-08-14
Every time, an operation requires administrative powers, place sudo in front of the command if it's a terminal application or gksudo if it's a gui application.

Even if you're the only user on your computer, not being logged in as root has its value!

---

### Post by triplenine on 2008-08-14
> **Ryadt said:**
> It's not recommended cause of security reasons. You won't find help on the forum as it is against forum rules for a member to help on this issue.

Wow. OK. I don't really get it but why not? Linux has always been hard to use for reasons like this so I guess there is no reason to change that.

---

### Post by Oldsoldier2003 on 2008-08-14
> **triplenine said:**
> What is the best way to get my normal user account to have full administration privileges? I am the only user on this machine and not being able to simply edit a file (in this case GRUB's menu.lst) and save it is driving me nuts. Let me know what you think or I might just be missing something. Just would like to be able to click and go on these sorts of things rather than using a terminal + sudo.

The best answer would be to get used to using the sudo security model. What you are asking to do is become root. At the forums we discourage use of the root account or posting tutorials on how to enable root.

Using sudo and gksu/gksudo just requires you to relearn some habits that are probably heavily ingrained from prior experiences with windows. Hang in there the benefits far outweigh the extra step of invoking a program as SU.

---

### Post by sayakb on 2008-08-14
You may launch nautilus as root. Press Alt+f2 and type in [B]gksudo nautilus.
[/B]Caution: Launching nautilus as root gives write access to all system folders. Be careful while doing anything. Also, it is **not** recommended to log into X as root.

EDIT: w00t, people are fast here :)

---

### Post by Nepherte on 2008-08-14
Not having administrator rights prevents you from doing something stupid (I'm not talking about you in particular, but everyone in general including me). If it requires root privileges, it is commonly a serious change that might damage your system. Placing sudo in front of it, should make you aware of the gravity of the change.

There are other reasons as well.

---

### Post by Riffer on 2008-08-14
One of the main reasons that Windows is so prone to attacks is that by default you login as "root" or "admin" every time.  By this simple default Ubuntu is much more secure.

There methods that enable you to do multiple things as a "SuperUser" and are easily found by doing a search in these forums.  But please get use to the security model that Ubuntu uses.

---

### Post by Oldsoldier2003 on 2008-08-14
> **Nepherte said:**
> Not having administrator rights prevents you from doing something stupid (I'm not talking about you in particular, but everyone in general including me). If it requires root privileges, it is commonly a serious change that might damage your system. **Placing sudo in front of it, should make you aware of the gravity of the change.**

There are other reasons as well.

+1 sudo should be like that robot waving his arms and shouting "Danger Will Robinson!"

Well not exactly :) but my point here is that its important to always know what you are doing when you sudo because the results could be catastrophic. But on the bright side, sudo also protects you from most boneheaded moves. Just remember the old saying, "With great power comes even greater responsibility".

---

### Post by triplenine on 2008-08-14
I get it. The model works well in a multi-user situation. Not so much for me on my notebook.

---

### Post by Lord Xeb on 2008-08-14
Yes, that is why these systems are in place. If you were running around in root (or having complete power over your whole system) and not knowing what you are doing can be a really bad combination.

I know of some people who have tried to be in root all the time and deleted something that was really important (becuase if you delete something in root, it is gone forever and does not go into the trash). On top of this, one simple command can destroy your system if someone tricks you into using.

DO NOT USE THIS COMMAND EVER UNLESS YOU KNOW EXACTLY WHAT YOUR ARE DOING!!!!

This is one of the commands I am talking about:

```
rm -rf /
```

This means it will delete root forcefully and recusively (or completely). Never ever use this command ever!

---

### Post by Ryadt on 2008-08-14
> **triplenine said:**
> Wow. OK. I don't really get it but why not? Linux has always been hard to use for reasons like this so I guess there is no reason to change that.

Typing a password doesn't make Linux that hard....:popcorn:

---

### Post by Nepherte on 2008-08-14
> **Oldsoldier2003 said:**
> +1 sudo should be like that robot waving his arms and shouting "Danger Will Robinson!"
Lol, this quote will most likely haunt me every time I use sudo ^^

---

### Post by Oldsoldier2003 on 2008-08-14
> **triplenine said:**
> I get it. The model works well in a multi-user situation. ```
Not so much for me on my notebook
```.

Browsing the web as root or doing day to day operations as root can be extremely hazardous to your system. Even in non sudo distributions of Linux it is highly discouraged to log on as root. Even the RHEL gurus will tell you, don't log in as root unless you have a good reason and then log out as soon as you are done with that reason.

---

### Post by Nepherte on 2008-08-14
> **triplenine said:**
> I get it. The model works well in a multi-user situation. Not so much for me on my notebook.
Actually, the point we're trying to make, is that it also works well in a single-user environment. It prevents possibly unwanted scripts execution as well.

---

### Post by triplenine on 2008-08-14
> **Ryadt said:**
> Typing a password doesn't make Linux that hard....:popcorn:

Yeah it doesn't make it hard. Adding unnecessary keystrokes makes it hard-to-use. Especially when I can click myself there but not actually be able to do anything without taking those extra key stokes. These are the types of issues I face when using Linux. 

You fellows suggest that I am just a silly windows user. Well, I guess I must be. 

Sorry if I come off kind of snarky.

---

### Post by appi2012 on 2008-08-14
Say you were logged in as root, or were the administration on windows xp. If you downloaded a program, that was actually a virus, it would be able to destroy your system without you knowing (until it was too late). With sudo, a system administrator has to give permission for every activity that can change or harm your system. That way, applications can't harm your system unless you run them with sudo, and also, hackers can't do this either.

---

### Post by t0p on 2008-08-14
First of all, let me make it clear that I am not arguing with the ubuntu sudo-model.  I don't think it's at all difficult to prefix administrative commands with sudo, and I haven't enabled root login on my computer.

But I really must object to the repeated claims in this thread that use of root is somehow "dangerous".  Ubuntu adopted default use of sudo because it is safer than using root, but that does NOT make root dangerous!  Unless you are seriously suggesting that most Linux distros are hazardous to use and developers of those distros are irresponsible.

---

### Post by Oldsoldier2003 on 2008-08-14
> **t0p said:**
> First of all, let me make it clear that I am not arguing with the ubuntu sudo-model.  I don't think it's at all difficult to prefix administrative commands with sudo, and I haven't enabled root login on my computer.

But I really must object to the repeated claims in this thread that use of root is somehow "dangerous".  Ubuntu adopted default use of sudo because it is safer than using root, but that does NOT make root dangerous!  Unless you are seriously suggesting that most Linux distros are hazardous to use and developers of other distros are irresponsible.

My posts are based on forum policy and the reason we have this policy. I have in the past administered  servers that do not have sudo installed. I prefer using sudo because its an extra layer of security and can *sometimes* prevent an inadvertently caused disaster.

With all that said, responsible use of root is no more dangerous than responsible use of sudo. We just do not advocate it on this forum. hence this [policy]("http://ubuntuforums.org/showthread.php?t=765414").

---

### Post by Riffer on 2008-08-14
No what we are saying is, being logged in as "root" continuously is dangerous.  Which is what the OP wants to do.

---

### Post by Oldsoldier2003 on 2008-08-14
Since this thread has answered the original question and will not present any further useful information to the OP, I am closing this thread. 

If the OP wants to enable root thats perfectly fine, it is the perogative of every user to do what they want with their own computer. There are lots of other places on the web where the OP can get the info without running up against forum policy issues.

My personal thanks to everyone for being civil and informative.

---

