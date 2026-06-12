---
title: "Correct Use of SUDO"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by adam-werling on 2014-04-02
Hi there!

I am aware of the need to use SUDO every once in a while (like now, when installing Calibre from the binaries as suggested on their project website).  I keep wondering what Ubuntu's approach to using SUDO looks like.  The last time around when I was using Linux, I could do SUDO from within my regular-use, every-day account.  Running Ubuntu 13.10, I cannot do so.  I have to log out, and then log in as administrator to use any SUDO command.  I find that quite bothersome, but I am guessing this is for a reason.

So how do I properly use SUDO?  Do I really have to log out of my regular user account and log into my administrator account for every single thing that involves SUDO?

All the best,

Adam

---

### Post by bshatt1987 on 2014-04-02
Are you capitalizing SUDO in the terminal?  If you are, then that's the problem.  It needs to be lowercase.  
I've never had to log out of my account and log in as root in order to execute a command as super user.  In fact I believe that it's highly discouraged, as you could easily break something.

---

### Post by su:bhatta on 2014-04-02
You should be able to log in as regular user and use 'sudo' e.g. 

```
sudo apt-get update
sudo apt-get install <packagename>
sudo apt-get autoclean 
etc
```

First point of start should be 

```
man sudo
```

this will give the man pages.

In case you are not able to use sudo e.g. sudo apt-get update as a regular user, please revert back.
I am not that conversant with it, but others will be able to help.

---

### Post by Double.J on 2014-04-02
Hi there!

same as it ever was; sounds like the user you added isn't in the sudoers file?

```

sudo usermod -aG sudo <username>

```

---

### Post by Navneet_Kumar on 2014-04-02
No its not necessary,you just have to use sudo with your current user name and it will work fine.Or you can change root passwd using: sudo passwd root......
and then type su...to become the root user,....

---

### Post by Double.J on 2014-04-02
We're not supposed to advise enabling root ;)

---

### Post by Navneet_Kumar on 2014-04-02
Yup.........it is not advisable for a long session......

---

### Post by gigix85 on 2014-04-02
sudo for command-line utilities, gksudo for GUI apps started from the terminal. 

[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by Lars Noodén on 2014-04-02
It is not necessary to log out in order to switch users.  You have in the far upper right corner a symbol that is a cross between the on/off icon and a gear.  In that you can choose another account and use that for a while.  Then when you log out of that other account's session, you can get back to the original account's session just as it was.

---

### Post by philinux on 2014-04-02
+1 Lars.

It sounds like the OP set up a non admin user account for regular use.

---

### Post by ajgreeny on 2014-04-02
As has been said already, enabling the root account in Ubuntu is not recommended, and in my experience is certainly not needed.

I have no idea if it makes a difference to the use of sudo if you have by chance enabled the root account, so that may be worth checking.

All the information you need about sudo and the Ubuntu way of doing things as administrator is shown in the [RootSudo]("https://help.ubuntu.com/community/RootSudo") link in my signature at the bottom of this post.

Read it carefully and you will see how easy it makes life for you.

---

### Post by bapoumba on 2014-04-02
> **ajgreeny said:**
> 
I have no idea if it makes a difference to the use of sudo if you have by chance enabled the root account, so that may be worth checking.

Nope, no difference. sudo/gksuso grant users having admin privileges (the ones in the sudo group in later Ubuntu releases, as reflected in the sudoers file) to run applications "as" root without knowing the root password.

---

### Post by Rob Sayer on 2014-04-02
> **adam-werling said:**
> Hi there!

I am aware of the need to use SUDO every once in a while (like now, when installing Calibre from the binaries as suggested on their project website)....

Calibre is in the beta tested repos and you don't need to add their ppa manually or use the terminal at all.  It's available from software centre (which I rarely use) or Synaptic (which is what I prefer).

Developers may suggest installing the latest version from their ppa but I don't do that unless there's some new feature I can't live without.  Turns out I can apparently live without them because I'vev always used the standard repos.

The version in the repos is tested for your version of ubuntu.  That's worth a lot more than some feature you probably don't particularly need.

New users should stick to the programs in the repos until they get some more experience.  There are some exceptions like Google Chrome or Handbrake which are trusted programs.  But some of them can really cause problems.

---

### Post by adam-werling on 2014-04-04
> **bshatt1987 said:**
> Are you capitalizing SUDO in the terminal?  If you are, then that's the problem.  It needs to be lowercase.  
I've never had to log out of my account and log in as root in order to execute a command as super user.  In fact I believe that it's highly discouraged, as you could easily break something.
No, I did that only to highlight the word here.  But thanks for checking back, because, of course, that would have been a problem.

---

### Post by adam-werling on 2014-04-04
> **gnu/mirow said:**
> Hi there!

same as it ever was; sounds like the user you added isn't in the sudoers file?

```

sudo usermod -aG sudo <username>

```

That is exactly the message I get when trying to use "sudo".

> **Lars Noodén said:**
> It is not necessary to log out in order to switch users.  You have in the far upper right corner a symbol that is a cross between the on/off icon and a gear.  In that you can choose another account and use that for a while.  Then when you log out of that other account's session, you can get back to the original account's session just as it was.

Thanks for the hint!  I have never tried using that option.

> **philinux said:**
> +1 Lars.

It sounds like the OP set up a non admin user account for regular use.

I am afraid I did.  Isn't that the way to go for security purposes?

---

### Post by adam-werling on 2014-04-04
BTW - thanks for all the feedback and help so far!

---

### Post by Lars Noodén on 2014-04-04
> **adam-werling said:**
> 
I am afraid I did.  Isn't that the way to go for security purposes?

Yes, having a separate non-admin account is IMHO a very useful added layer.

If you want to see what a user can do try "sudo -l"

---

### Post by adam-werling on 2014-04-17
So, basically, it's a safe bet to use a separate admin account to do all the SUDO stuff, right?

---

### Post by bapoumba on 2014-04-17
> **adam-werling said:**
> So, basically, it's a safe bet to use a separate admin account to do all the SUDO stuff, right?

Well, depends on what you want to do.

I use a regular user with admin privilege and use sudo whenever I need it. I would find tiresome to switch users every time I need it.
Now when my kids were younger, they had users without admin privileges.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by monkeybrain20122 on 2014-04-17
> **gigix85 said:**
> sudo for command-line utilities, gksudo for GUI apps started from the terminal. 

[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

Well not sure why gksu (the package needed for running gksudo) is not even installed by default. I have been wondering what is the problem if you use sudo instead of gksudo for say, gedit. It seems that gksudo is a Debian/Ubuntu thing which doesn't even exist in other distros (e.g Fedora)

---

### Post by kurt18947 on 2014-04-18
It is possible to enable non-privileged users to execute single commands that normally require sudo privileges. Here is the guide I used. The link is about suspend & hibernate but I presume the 'user permission method' apply to other commands as well.

[https://wiki.archlinux.org/index.php/pm-utils#Suspend.2Fhibernate_as_regular_user](https://wiki.archlinux.org/index.php/pm-utils#Suspend.2Fhibernate_as_regular_user)

Incidentally,  there's a note that that upower is deprecated.  That may be but the pm-utils commands still work in 14.04.

---

### Post by bapoumba on 2014-04-18
> **monkeybrain20122 said:**
> Well not sure why gksu (the package needed for running gksudo) is not even installed by default. I have been wondering what is the problem if you use sudo instead of gksudo for say, gedit. It seems that gksudo is a Debian/Ubuntu thing which doesn't even exist in other distros (e.g Fedora)
[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)
If you use sudo with a graphical application, you can end up messing permissions in your /home.
 
> **kurt18947 said:**
> It is possible to enable non-privileged users to execute single commands that normally require sudo privileges. Here is the guide I used. The link is about suspend & hibernate but I presume the 'user permission method' apply to other commands as well.

[https://wiki.archlinux.org/index.php/pm-utils#Suspend.2Fhibernate_as_regular_user](https://wiki.archlinux.org/index.php/pm-utils#Suspend.2Fhibernate_as_regular_user)

Incidentally,  there's a note that that upower is deprecated.  That may be but the pm-utils commands still work in 14.04.
The method described in the ArchWiki can be used on Debian or Ubuntu :)
The sudoers file can be finely tuned : [http://linux.die.net/man/5/sudoers](http://linux.die.net/man/5/sudoers) or **man sudoers**

The first user created on Ubuntu is in the sudo group that has permissions to run any application "as" root, but you can restrict one user to use one application only with root privilege. This user should not be in the sudo group.

---

### Post by monkeybrain20122 on 2014-04-18
> **bapoumba said:**
> [https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)
If you use sudo with a graphical application, you can end up messing permissions in your /home.
 .

Then why is it that gksudo doesn't even exist in other distros? In Fedora you either su to root or just sudo for graphical and non graphical applications.

Edited
[https://ask.fedoraproject.org/en/question/7185/no-gksudo-so-just-su-or-sudo-then/](https://ask.fedoraproject.org/en/question/7185/no-gksudo-so-just-su-or-sudo-then/)

---

### Post by bapoumba on 2014-04-18
> **monkeybrain20122 said:**
> Then why is it that gksudo doesn't even exist in other distros? In Fedora you either su to root or just sudo for graphical and non graphical applications.

Edited
[https://ask.fedoraproject.org/en/question/7185/no-gksudo-so-just-su-or-sudo-then/](https://ask.fedoraproject.org/en/question/7185/no-gksudo-so-just-su-or-sudo-then/)

I'm not familiar with Fedora. I see they have beesu in place of gksudo. The distro may have made different choices regarding the admin account and regular user escalating to admin privileges.

Remember not to use sudo for graphical apps (the /home permissions thing). In addition, it allows to keep the same graphical environment as the regular user, although running as root.

---

