---
title: "The first time the folks over at Ubuntu HQ have ever annoyed me this much..."
date: 2008-05-31
forum: Recurring Discussions
---

### Post by jgrabham on 2008-05-31
Now I want a seperate root account - It's in my opinion a HUGE security risk to be able to control an entire system from a simple login password.

So,I went here - 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


And it says

> Enabling the root account

    *

      <!> Enabling the root account is rarely necessary.
      Anything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. If you really need a persistent root login, use sudo -i. Logging in to X as root may cause very serious trouble. If you believe you need a root account to perform a certain action, please consult the official support channels first, to make sure there is not a better alternative.



Now, Ubuntu is as far as I know the only distro which talks like this - even mint, which is essentially Ubuntu with a shiny theme and some codecs chucked in gives you the option when you log in for the first time, and I can understand not wanting to confuse people new to Linux, but to actually have the audacity to say "We removed this vital part of any *nix system, and we're not telling you how to get it back, so there" is beyond a joke.

I am not a happy bunny :mad:

EDIT - and might I add 

```
james@main:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
james@main:~$ su
Password: 
root@main:/home/james# 

```

mwahaha  *RAISES MIDDLE FINGER*

---

### Post by Mateo on 2008-05-31
Agree.  It's fine to suggest that someone doesn't do something a certain way, but it should end there.

---

### Post by jrusso2 on 2008-05-31
As a long time Linux user this kind of thing used to annoy me to no end.  I am used to it now. But I still think an option should be given on install.

I don't feel like I need baby sitting.

---

### Post by forestpixie on 2008-05-31
> mwahaha *RAISES MIDDLE FINGER*

feeling grown up now are we

---

### Post by arvevans on 2008-05-31
Have you considered building your system new, and at the install prompt for "username" and"password" enter "root" and your favourite root password?    ;-)  
Then you can use the provided tools to add non-root users as your feel necessary.

There are alternative ways to make a real "root" ID, password, and root directory, but these may compromise your security by allowing users to remotely log in as root if they know or can guess your root password.

As a long-time UNIX user (since Bell Labs in 1980) I too fought with the "Ubuntu Way", however now that I understand why it was done, and how to work with it...I LIKE IT!  :)

Arv
_._

---

### Post by Barrucadu on 2008-05-31
The wiki has a point, running X as root is rather stupid.

---

### Post by Mateo on 2008-05-31
> **Barrucadu said:**
> The wiki has a point, running X as root is rather stupid.

Maybe, maybe not.  Whether they are correct is not the point.  Giving advice is fine, but withholding information is Orwellian.

---

### Post by jgrabham on 2008-05-31
> **forestpixie said:**
> feeling grown up now are we

Very, now if you don't mind, must get back to hurling insults at the redwings on TV...

---

### Post by 23meg on 2008-05-31
What is Ubuntu HQ?

---

### Post by rune0077 on 2008-05-31
To be fair, the option is there. You have a user in user-settings called root, and it's as easy as setting a password for that user. If you have the skills to add new users to the system, you also have what is required to set a root password, no fancy command-line needed. So okay, maybe they don't let you set it during installation, but it's not like it's hidden or kept out of your way either.

---

### Post by p_quarles on 2008-05-31
> **jgrabham said:**
> Now I want a seperate root account - It's in my opinion a HUGE security risk to be able to control an entire system from a simple login password.
On what grounds? Is your login password a weak one? 

> Now, Ubuntu is as far as I know the only distro which talks like this - even mint, which is essentially Ubuntu with a shiny theme and some codecs chucked in gives you the option when you log in for the first time, and I can understand not wanting to confuse people new to Linux, but to actually have the audacity to say "We removed this vital part of any *nix system, and we're not telling you how to get it back, so there" is beyond a joke.
What did they remove? 

Well, I already know the answer: nothing. Ubuntu locks the password of the root account, which is a very simple and universal function of the UNIX passwd shell command. In addition, they added a patch that allows a user to boot into single-user mode even though the root password is locked. 

> **Mateo said:**
> Maybe, maybe not.  Whether they are correct is not the point.  Giving advice is fine, but withholding information is Orwellian.
That statement betrays a lack of perspective, in my opinion. The information is easy to find. The Ubuntu developers should not be expected to support a use that goes against their own system policy design. 

> **rune0077 said:**
> To be fair, the option is there. You have a user in user-settings called root, and it's as easy as setting a password for that user. If you have the skills to add new users to the system, you also have what is required to set a root password, no fancy command-line needed. So okay, maybe they don't let you set it during installation, but it's not like it's hidden or kept out of your way either.
Exactly. My position is that anyone who hasn't figured this out is really not knowledgeable enough to have the grounds for second-guessing the OS's developers. It's not that having the root password enabled is somehow essentially a security risk, it's that Ubuntu is designed to operate without it, and as such, enabling it should mean that you know what you're doing.

---

### Post by Tomosaur on 2008-06-01
If you think about it, locking the root account is actually adding an extra layer of security.

Every nix system has a root. The attacker only has to guess the root password.

Ubuntu has a locked root. This means the attacker not only has to find out a user-name which has sudo access, but ALSO has to find out that user's password.

---

### Post by p_quarles on 2008-06-01
> **Tomosaur said:**
> If you think about it, locking the root account is actually adding an extra layer of security.
This is a misconception. Whether the root account is locked or enabled has very little to do with security, all other things being equal.

> Every nix system has a root. The attacker only has to guess the root password.

Ubuntu has a locked root. This means the attacker not only has to find out a user-name which has sudo access, but ALSO has to find out that user's password.
First of all, "guessing" the password should not be easy to do. A good password takes a staggering amount of resources to crack. The list of system users, on the other hand, is not treated by a *nix system as confidential. In any case, the default Ubuntu setup makes it easy to know who the administrator is: it's uid 1000. The sudo application allows the uid to be entered instead of a username, so the idea that you have to "guess" the administrator's name is just wrong.

---

### Post by Kinst on 2008-06-01
You're entering into the world of fundamental ubuntu philosophy. Every distro has quirks like these which they hold dear. It's best to just accept ubuntu for what it is, there are a couple of things which can never change, like the colour brown, or the 6 month release cycle, or the bi-yearly fork from debian, or Mark Shuttleworth, etc.

---

### Post by loell on 2008-06-01
> **23meg said:**
> What is Ubuntu HQ?

or where is it? I'd like to see some pics of this HQ thing...

---

### Post by damoxc on 2008-06-01
also if you note the "community" in the url means anyone can edit that, you just need a launchpad account.

---

### Post by 23meg on 2008-06-02
> **damoxc said:**
> also if you note the "community" in the url means anyone can edit that, you just need a launchpad account.

Why bother to get involved when you can just safely speculate from the outside? It's much easier and much more fun. Contributing and getting your hands dirty is exhausting and tedious. There's always someone else, some mysterious folks "over at the HQ" that can do that.

---

### Post by ubuntu-freak on 2008-06-03
> **jgrabham said:**
> Now I want a seperate root account - It's in my opinion a HUGE security risk to be able to control an entire system from a simple login password.

 
Don't have a simple login password then.
 
Nathan

---

### Post by jgrabham on 2008-06-05
> **reassuringlyoffensive said:**
> Don't have a simple login password then.
 
Nathan

Its not particularly simple, but it's not the hex key I use for my root accounts.  My login password takes me about 1/2 a second to type in, so I can get into my system ASAP, it would just p*** me off if I had to type in a hex key just to log in.

---

### Post by cardinals_fan on 2008-06-05
> **jgrabham said:**
> 
EDIT - and might I add 

```
james@main:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
james@main:~$ su
Password: 
root@main:/home/james# 

```
What's the problem?  You seem to have things solved...

---

### Post by bwhite82 on 2008-06-05
> 
Code:

james@main:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
james@main:~$ su
Password: 
root@main:/home/james#

mwahaha *RAISES MIDDLE FINGER*

Popcorn for you. :popcorn: By solving your own problem, you've begun your descent into Linux-geekdom. _IMO_, 97% of the questions asked in the Beginner's Forum can be solved with a little googling and perseverance -- which is all I do when I am attempting to answer someone's question (is google).

---

