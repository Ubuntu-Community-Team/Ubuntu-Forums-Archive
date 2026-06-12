---
title: "how do i log in as root"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by jimi_hendrix on 2008-07-09
hi all

i just downloaded a game but for some reason its locked and i need to access it as root...how do i do that?

:guitar:

---

### Post by Cypher on 2008-07-09
Your user account has root privileges, so execute the game with "sudo" or "gksudo" or "kdesu" so..
```

sudo <game/executable>

```

---

### Post by Tatty on 2008-07-09
In ubuntu there is no need to log in as root, the root account is actually disabled as a security measure.

As Cypher posted, you should use preface the command with "sudo" to run a command with root privilages.

However if is is a graphical application you are using then you should preface it with "gksu" if you are using Gnome, or kdesu if you are using KDE.

I recommend you read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) to fully understand root and sudo in Ubuntu.

---

### Post by jimi_hendrix on 2008-07-09
well this is the thing...

the game is called planeshift and it took me a day to get installed...

only thing is it says under properties its owned by "root" so i need to be root to change it so i can execute it...(the little box next to executeable in properties isnt checked)

---

### Post by Cypher on 2008-07-09
Hit ALT-F2 and type "gksu nautilus" which open up a file manager with Root privileges, now you can go to the location of the game and change it's ownership to you. 

Once done, be sure to close this particular file manager..

---

### Post by appi2012 on 2008-07-09
just type:
```
gksudo name_of_game
```
or if it is in a folder:
```
gksudo nautilus
```
and open it from there.

---

### Post by appi2012 on 2008-07-09
just type:
```
gksudo name_of_game
```
or if it is in a folder:
```
gksudo nautilus
```
and open it from there.
type:
```
sudo chmod +x nameofgame
```
to make it exectuable

---

### Post by protogenesis on 2008-07-09
Could you not just create another 'root' account named 'soot' or 'toot' or 'billybob' with UID/GID 0 and set a secure password for that account?  I assume that 'root' since the username is well-known is the reason the account is disabled, but if you create a GID/UID 0 account with a non-standard name, it seems things would be a bit more secure.  Again, this assumes no one has access to your system and can gain a userlist of IDs.

Thoughts??

---

### Post by Cypher on 2008-07-09
> **protogenesis said:**
> Could you not just create another 'root' account named 'soot' or 'toot' or 'billybob' with UID/GID 0 and set a secure password for that account?  I assume that 'root' since the username is well-known is the reason the account is disabled, but if you create a GID/UID 0 account with a non-standard name, it seems things would be a bit more secure.  Again, this assumes no one has access to your system and can gain a userlist of IDs.

Thoughts??
This not a good idea..Ubuntu disables the Root account by default and makes users use the SUDO commands for Root tasks so that they know what they're about to do is a Root task.

Should there be an absolute need to have a 'root' account, then it can be safely enabled with
```

sudo passwd -l root

```
Once the password is set, the 'root' account becomes active.

It is not a good idea to create a seperate account with UID/GID of 0 to get around the 'root' account..

---

### Post by billgoldberg on 2008-07-09
> **protogenesis said:**
> Could you not just create another 'root' account named 'soot' or 'toot' or 'billybob' with UID/GID 0 and set a secure password for that account?  I assume that 'root' since the username is well-known is the reason the account is disabled, but if you create a GID/UID 0 account with a non-standard name, it seems things would be a bit more secure.  Again, this assumes no one has access to your system and can gain a userlist of IDs.

Thoughts??

The root account is disabled because to much users would damage their systems by fiddling around in things.

You can easily active the root account, but one of the mods asked to not share how to do this.

If you don't know how to active the root account, you shouldn't be using one.

---

### Post by Vivaldi Gloria on 2008-07-09
> **protogenesis said:**
> Could you not just create another 'root' account named 'soot' or 'toot' or 'billybob' with UID/GID 0 and set a secure password for that account?  I assume that 'root' since the username is well-known is the reason the account is disabled, but if you create a GID/UID 0 account with a non-standard name, it seems things would be a bit more secure.  Again, this assumes no one has access to your system and can gain a userlist of IDs.

Thoughts??

There is already a root account with uid 0 but it has a hidden password. Changing that password to something usable is not suggested. It is a security risk and makes it possible for you to destroy your system more easily. Using sudo in the terminal and gksudo for gui apps is more than enough to do whatever you want. I suggest you get used to it. ;)

---

### Post by protogenesis on 2008-07-09
Right, I'm aware that root is disabled/no password.  The reason behind this is that 'root' is known as, well, the 'root' account on all POSIX-compliant systems.  My suggestion was, if you absolutely *need* a root account, you could create another account with a different name but a UID/GID 0, one that someone trying to 'hack' your system wouldn't know.  

Case in point: I set up Ubuntu server about three weeks ago.  Within the first 24 hours, someone from China spent about ninety minutes trying to SSH to my machine (which tye could) and guess the root password.  They never did breach the system as root has no password. 

Granted, I agree with this logic: no password for root!

My argument is that if you NEED a root account, you could create one with a different username but UID/GID 0.  Leave root there, no password, but give the new 'root' account a password.  I do not advocate this as secure, but consider the sudo command and what it allows.  If you argue that you should use sudo, what would the logic be?  Using your own account name, one that someone wouldn't be able to guess in a 'hack' attempt?  All someone has to do is guess your username, guess the password and they'll be able to 'sudo' until their heart's content.  What is the difference between cracking a priveleged /etc/sudoer account versus a UID/GID 0 account with a name that isn't 'root?'  In either case, a cracker only needs to guess the password of the account in question and boom, compromised system.  

Thoughts on this?

---

### Post by protogenesis on 2008-07-09
Ah, I did see something with which I agree:  Using 'root' can easily destroy your system if you make the mistake of logging on as root.  

This does make sense, then, to disable the root account as far too many people were using root for their GUI sessions, something that, well, should never happen.  I can only imagine how many ruined Linux installs there were/are because someone thought being logged in as 'root' was a good idea.

Based on THAT, yes, I agree completely, do not friggin' set a pasword for root, use sudo until you're blue in the face and then some.  

It seems like, then, that the root account is becoming archaic.  Does having an actual root account, save for single-user mode, even make sense any more?  sudo seems to be more than sufficient, and one can always 'sudo su - ' if one needs to be 'root.'

Thoughts (more?)

---

### Post by Vivaldi Gloria on 2008-07-09
You cannot create another user with uid 0 beacause there is already one: root. If you insist to change the root password then google it.

About root in ubuntu read:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

I have used systems with root accounts in the past but I like ubuntu approach because of the reasons I mentioned above and also a practical one: I prefer memorizing one pwd rather than two. :-)

---

### Post by protogenesis on 2008-07-09
[QUOTE=Vivaldi Gloria;5351009]You cannot create another user with uid 0 beacause there is already one: root. If you insist to change the root password then google it.


This is untrue.  You can create another UID with '0' and call it whatever you'd like.  This is a truism that dates back to early Unix systems and still holds true on Linux today.  A popular public-access system has about six different 'root' accounts with different names for their various users associated with those, all having UID 0 and GID 0.  On that note, you can also create accounts that have the same UID as your main non-root account.  I can create one called 'proto1' with UID 1000 and 'proto2' with UID 1000, log in seperately as both without a conflict or problems.

As a test, create an account called 'boot' or 'coot' or whatever you'd like to call it.  Give it UID/GID 0.  Set a password for it, pwvonc, sync, et cetera, and then log in with that new account.  

That being said, disabling root is fine and dandy as long as one doesn't (a) enable a password for root, and/or (b) creates another UID/GID 0 account and passwords that and logs in as that.  sudo works just as well.

---

### Post by jimi_hendrix on 2008-07-10
> **appi2012 said:**
> just type:
```
gksudo name_of_game
```
or if it is in a folder:
```
gksudo nautilus
```
and open it from there.
type:
```
sudo chmod +x nameofgame
```
to make it exectuable

so far ive tried sudo chmod +x PlaneShift and gksudo PlaneShift


it asks me for a password then nothing happens

---

### Post by snowpine on 2008-07-10
> **jimi_hendrix said:**
> so far ive tried sudo chmod +x PlaneShift and gksudo PlaneShift


it asks me for a password then nothing happens

Maybe this is just me being paranoid, but aren't you suspicious of a *game* that requires root access?

---

### Post by jimi_hendrix on 2008-07-10
it doesnt require it...but under properties it says root is the owner of the file and it says its read only and and that im not allowed to read it as an executable...

i got the game from here
 [http://ubuntuforums.org/showthread.php?t=427205]("http://ubuntuforums.org/showthread.php?t=427205")

it took me a while to figuer out how to install it (that was another post XD) but someone got it to work look here[http://ubuntuforums.org/showthread.php?t=853712]("http://ubuntuforums.org/showthread.php?t=853712")

---

### Post by appi2012 on 2008-07-10
[URL="http://translate.google.com/translate?hl=en&sl=pt&u=http://www.ubuntugames.org/PlaneShift&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dhttp://www.ubuntugames.org/PlaneShift%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26hs%3DVDH"]http://translate.google.com/translate?hl=en&sl=pt&u=http://www.ubuntugames.org/PlaneShift&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dhttp://www.ubuntugames.org/PlaneShift%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26hs%3DVDH
[/URL]
Page that has instructions for installing. Hope that helps!

---

### Post by mcduck on 2008-07-10
> **jimi_hendrix said:**
> it doesnt require it...but under properties it says root is the owner of the file and it says its read only and and that im not allowed to read it as an executable...

i got the game from here
 [http://ubuntuforums.org/showthread.php?t=427205]("http://ubuntuforums.org/showthread.php?t=427205")

it took me a while to figuer out how to install it (that was another post XD) but someone got it to work look here[http://ubuntuforums.org/showthread.php?t=853712]("http://ubuntuforums.org/showthread.php?t=853712")
Then you should just make it executable by everyone.
```

sudo chmod a+x nameofthefile
```

---

### Post by redfox1160 on 2008-07-10
When I need root access, I type
```
sudo -s
```
and it make you root untill you close the terminal. Correct me if I'm wrong.

---

### Post by jimi_hendrix on 2008-07-10
ty all now shiny thanks badges for all of you

---

### Post by youthforlinux on 2008-07-11
> **protogenesis said:**
> Right, I'm aware that root is disabled/no password.  The reason behind this is that 'root' is known as, well, the 'root' account on all POSIX-compliant systems.  My suggestion was, if you absolutely *need* a root account, you could create another account with a different name but a UID/GID 0, one that someone trying to 'hack' your system wouldn't know.  

Case in point: I set up Ubuntu server about three weeks ago.  Within the first 24 hours, someone from China spent about ninety minutes trying to SSH to my machine (which tye could) and guess the root password.  They never did breach the system as root has no password. 

Granted, I agree with this logic: no password for root!

My argument is that if you NEED a root account, you could create one with a different username but UID/GID 0.  Leave root there, no password, but give the new 'root' account a password.  I do not advocate this as secure, but consider the sudo command and what it allows.  If you argue that you should use sudo, what would the logic be?  Using your own account name, one that someone wouldn't be able to guess in a 'hack' attempt?  All someone has to do is guess your username, guess the password and they'll be able to 'sudo' until their heart's content.  What is the difference between cracking a priveleged /etc/sudoer account versus a UID/GID 0 account with a name that isn't 'root?'  In either case, a cracker only needs to guess the password of the account in question and boom, compromised system.  

Thoughts on this?

I really don't see the benefit of this if you already have a user with sudo privelges because they give themselves root privelges via sudo anyways, the need for another root account is pointless because if they could "guess" your username wouldn't they "guess" the new root account's name?

---

