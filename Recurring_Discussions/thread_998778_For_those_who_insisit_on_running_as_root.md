---
title: "For those who insisit on running as root"
date: 2008-12-01
forum: Recurring Discussions
---

### Post by randiroo76073 on 2008-12-01
:confused:

Maybe you'd be happier with Fedora or some other distro that allows you to setup root at the getgo, thats why there are so many different flavors of Linux, so the individual can pick & choose.  I constantly am trying new ones(multi-boot) but keep Ubuntu as my main :)

---

### Post by chucky chuckaluck on 2008-12-01
thanks for the tip.

---

### Post by ryry46d9 on 2008-12-01
if you really want to see root@blaablaa on your term then type 



sudo passwd root

poof you just added a password for root that you can use 

then "su" when needed 


unless you really want to log in X as root , that is a question I cant answer 


but I do feel the sudo pain from time to time

---

### Post by Swagman on 2008-12-01
You can do that with debian anyway ( and ubuntu - sudo su) and you can still use your apt-get knowledge.

---

### Post by ibutho on 2008-12-01
If you don't want to switch, you can tinker with your Ubuntu settings and revert to the classic model. Its forbidden on these forums to discuss this, but there are many articles on google that can help.

---

### Post by jespdj on 2008-12-01
> **ryry46d9 said:**
> if you really want to see root@blaablaa on your term then type  ...

You are [violating the forum policy](http://ubuntuforums.org/showthread.php?t=716201).

---

### Post by Dr Small on 2008-12-01
> **jespdj said:**
> You are [violating the forum policy](http://ubuntuforums.org/showthread.php?t=716201).
+1

Arch sets you in root at installation, and that is fine.
But I setup sudo, because it is faster to type than logging in as root to type every command.

---

### Post by saulgoode on 2008-12-01
> **jespdj said:**
> You are [violating the forum policy](http://ubuntuforums.org/showthread.php?t=716201).

Ryry46d9 did not post how to perform a graphical root login -- in fact, he stated he could not -- presumably owing to forum policy. Neither did he describe how to arrange things so that the root account was logged into automatically. It would also be a rather tenuous argument to assert that a single command constitutes a "tutorial".

---

### Post by ryry46d9 on 2008-12-01
> **saulgoode said:**
> Ryry46d9 did not post how to perform a graphical root login -- in fact, he stated he could not -- presumably owing to forum policy. Neither did he describe how to arrange things so that the root account was logged into automatically. It would also be a rather tenuous argument to assert that a single command constitutes a "tutorial".



Thank you 




I my self find sudo to be a pain some times when I'm building a server for the first time, over half the time sudo will time out on me, due to me doing a little RTFM

---

### Post by ibutho on 2008-12-01
> **Dr Small said:**
> +1

Arch sets you in root at installation, and that is fine.
But I setup sudo, because it is faster to type than logging in as root to type every command.

You don't have to login as root every time you need to run a command. You can use "su -c" e.g.
```
su -c "/sbin/ifconfig -a"
```
You will be asked for roots password and the command will run as root. When the command has finished, you are dropped back to your normal users command prompt. Its not so different from prefixing every command with sudo and then entering your own password.

---

### Post by JohnFH on 2008-12-01
> **ibutho said:**
> If you don't want to switch, you can tinker with your Ubuntu settings and revert to the classic model. Its forbidden on these forums to discuss this, but there are many articles on google that can help.

Is it really?  Why?  Where does it say that?

---

### Post by ibutho on 2008-12-01
> **JohnFH said:**
> Is it really?  Why?  Where does it say that?

The thread is [here]("http://ubuntuforums.org/showthread.php?t=716201"). It seems pretty lame to me because the information can be found elsewhere, but I will abide by the forum rules even if I don't agree with them.

---

### Post by cmay on 2008-12-01
[http://www.psychocats.net/ubuntucat/whats-so-bad-about-the-eee-pc-xandros-anyway/](http://www.psychocats.net/ubuntucat/whats-so-bad-about-the-eee-pc-xandros-anyway/)
xandrox runs as root all time. and it cant be changed. so this is perfect if you have a root complex then you can  buy a Eeepc then.

i just got mine and i am going to play wiht it all night and then by the morning i hope to have either eeebuntu or debian in it. whit proper sudo rights set up :)

---

### Post by JohnFH on 2008-12-01
> **ibutho said:**
> The thread is [here]("http://ubuntuforums.org/showthread.php?t=716201"). It seems pretty lame to me because the information can be found elsewhere, but I will abide by the forum rules even if I don't agree with them.

Oh I see.  I thought you were saying it's forbidden to talk about how to make a minimal Ubuntu install (I thought that's what you meant by classic model).

---

### Post by ibutho on 2008-12-01
> **JohnFH said:**
> Oh I see.  I thought you were saying it's forbidden to talk about how to make a minimal Ubuntu install (I thought that's what you meant by classic model).

I was referring to the Unix classic security model.

---

### Post by Asgar on 2008-12-01
Sudo this Sudo that Sudo Sudo, to sudo or not to Sudo? Who cares! it's just 4 key strokes. "I want a root account becuse I can't type Sudo fast enough with my two fingers." :P

---

### Post by JohnFH on 2008-12-01
> **Asgar said:**
> Sudo this Sudo that Sudo Sudo, to sudo or not to Sudo? Who cares! it's just 4 key strokes. "I want a root account becuse I can't type Sudo fast enough with my two fingers." :P

What happens if you have a 20 character password?  Enter that every 15 mins and you would get annoyed.  What about piping the results of a command to a second command that requires sudo access?  What about performing command A that takes 20 mins and command B immediately after.  I can't just do sudo backup && sudo shutdown and then go to bed as it would prompt for the password again.  What happens if you start editing a file (with nano say) that requires root access only to discover that after you've made your changes?  What about putting commands into the background, like sudo backup &?  

Yes, I know the solutions to all these things, but I'm just playing devil's advocate.  Using sudo (which I prefer over root login) is not just a case of pressing four extra keys (also, with my pedant hat on, it's actually 5 characters as a space is needed).

---

### Post by BackwardsDown on 2008-12-01
> **JohnFH said:**
> What happens if you have a 20 character password?  Enter that every 15 mins and you would get annoyed.  What about piping the results of a command to a second command that requires sudo access?  What about performing command A that takes 20 mins and command B immediately after.  I can't just do sudo backup && sudo shutdown and then go to bed as it would prompt for the password again.  What happens if you start editing a file (with nano say) that requires root access only to discover that after you've made your changes?  What about putting commands into the background, like sudo backup &?  

Yes, I know the solutions to all these things, but I'm just playing devil's advocate.  Using sudo (which I prefer over root login) is not just a case of pressing four extra keys (also, with my pedant hat on, it's actually 5 characters as a space is needed).

You have heard of sudo -i? With that knowledge, there is no need to complain about sudo.

---

### Post by cmay on 2008-12-01
alias 's'

---

### Post by Dr Small on 2008-12-01
> **JohnFH said:**
> What happens if you have a 20 character password?  Enter that every 15 mins and you would get annoyed.  What about piping the results of a command to a second command that requires sudo access?  What about performing command A that takes 20 mins and command B immediately after.  I can't just do sudo backup && sudo shutdown and then go to bed as it would prompt for the password again.  What happens if you start editing a file (with nano say) that requires root access only to discover that after you've made your changes?  What about putting commands into the background, like sudo backup &?  

Yes, I know the solutions to all these things, but I'm just playing devil's advocate.  Using sudo (which I prefer over root login) is not just a case of pressing four extra keys (also, with my pedant hat on, it's actually 5 characters as a space is needed).
If I know that I am going to be running a bunch of different commands that all require sudo (for installing and setting up something), I just login as root, and skip sudo.

But sudo is faster (for me), if I need to just run one command, instead of logging in as root, running the command, and exiting the shell.

---

### Post by Icehuck on 2008-12-01
Maybe it's because I'm totally doing something wrong, but I can't use fdisk with sudo. I can do it fine when I log in with root, but not with sudo. So at the moment there is one reason to use root access.

---

### Post by JohnFH on 2008-12-01
yes, yes, yes *I *know about sudo -i and sudo -s.  I'm used to it, I prefer sudo over root login, I'm a big advocate of sudo, BUT it is not as simple as four extra keystrokes and I do quite often forget to prefix sudo when editing root-write-only files.  It requires a different knowledge of how to get root permission.

---

### Post by infoseeker on 2008-12-01
Something I always wanted to know was how close to the 'real' root login is booting into 'recovery mode'?  The reason I ask is because if I 'cd ~' under recovery mode I end up in /root ?  Would it not be more appropriate to require you to login to your own user and from there issue commands using 'sudo'?

---

### Post by Asgar on 2008-12-01
> **BackwardsDown said:**
> You have heard of sudo -i? With that knowledge, there is no need to complain about sudo.

*wink*

---

### Post by igknighted on 2008-12-01
You can also turn off sudo asking for a password for a given user, so all that is required is to prepend any command with 'sudo'.  Certainly a sketchy security practice, but possible...

---

### Post by fishtoprecords on 2008-12-01
> **jespdj said:**
> You are [violating the forum policy](http://ubuntuforums.org/showthread.php?t=716201).

No, I don't see how you could claim this. The forum policy explicitly says not to tell folks who to run X-windows as root

It says nothing about shell root.

---

### Post by bodhi.zazen on 2008-12-01
> **ryry46d9 said:**
> if you really want to see root@blaablaa on your term then type 



sudo passwd root

poof you just added a password for root that you can use 

then "su" when needed 


unless you really want to log in X as root , that is a question I cant answer 


but I do feel the sudo pain from time to time

If you are going to post instructions on these forums for how to set a root password please be sure to include the appropriate precautions and please be prepared to fix the breakage you cause.

If you do not know what will break, well I guess you should not be posting that advice should you ?

The way one obtains root access with Ubuntu is :

```
sudo -i
```

Or boot to recovery mode.

If sudo - is sooo difficult to type, they set an alias in .bashrc :

```
alias 'su -'='sudo -i'
```

There are times when it is necessary to set a root password, but in general this is discouraged.

---

### Post by ryry46d9 on 2008-12-01
sudo allows a permitted user to execute a command as the superuser or
       another user, as specified in the sudoers file.  The real and effective
       uid and gid are set to match those of the target user as specified in
       the passwd file and the group vector is initialized based on the group
       file (unless the -P option was specified).  If the invoking user is
       root or if the target user is the same as the invoking user, no pass&#8208;
       word is required.  Otherwise, sudo requires that users authenticate
       themselves with a password by default (NOTE: in the default configura&#8208;
       tion this is the user’s password, not the root password).  Once a user
       has been authenticated, a timestamp is updated and the user may then
       use sudo without a password for a short period of time (15 minutes
       unless overridden in sudoers).






 The su command is used to become another user during a login session.
       Invoked without a username, su defaults to becoming the superuser. The
       optional argument - may be used to provide an environment similar to
       what the user would expect had the user logged in directly.







sudo allows a permitted user to execute a command as the superuser or
       another user / The su command is used to become another user during a login session.

hmmm they both DO THE SAME DAMAGE it's just sudo has a timer 



and as for sudo -i I don't understand what they mean 
-i  The -i (simulate initial login) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.
           The command name argument given to the shell begins with a ‘-’ to
           tell the shell to run as a login shell.  sudo attempts to change to
           that user’s home directory before running the shell.  It also ini&#8208;
           tializes the environment, leaving TERM unchanged, setting HOME,
           SHELL, USER, LOGNAME, and PATH, and unsetting all other environment
           variables.  Note that because the shell to use is determined before
           the sudoers file is parsed, a runas_default setting in sudoers will
           specify the user to run the shell as but will not affect which
           shell is actually run.

 


so your saying sudo -i is the same as su ,but with a default 15 minute timer , That I aways forget about because I got other crap on my mind 


as for fixing a mess I created, no
  all I did was offer yet another idea, its up to you to do the home work, if your that stupid  to follow ANY ones how-to's  step for step with out doing your home work then you might as well be running Microsoft windows

---

### Post by lswb on 2008-12-01
As others have already posted,

sudo -i 

is for practical purposes the same as logging in as root; You get root's environment, home directory, .profile & .bashrc, etc.
--------------------------
On an unrelated subject, if a user is currently working at a vt (accessed with Control-Alt-F1 through Control-Alt-F6) and wishes to start X, one way to do so is to issue the command

startx -- :1

Where 1 is an unused display available to an X server.

---

### Post by cardinals_fan on 2008-12-01
My opinions:

Running as root = BAD!  You can do it if you like, but it's terrible security.

Having a root user, accessible through *su* = GOOD.  I like to *su* to root to handle my system.  I don't particularly like *sudo*.

---

### Post by starcannon on 2008-12-01
I love Ubuntu, I love these forums, and the community they represent; however, I am very discouraged to see "books being removed from the shelves". The ability to share information is the bedrock of the community we enjoy, and while I agree with most of the forum policies, this ["New forum policy on on log-in-as-root tutorials"]("http://ubuntuforums.org/showthread.php?t=716201") is not in my opinion a good road to start going down. The circular reasoning found in the policy, as well as the "your responsible for what others do with your tutorials" mentality is not good for free and open computing. 

Freedom carries the price of NOT being able to pass the buck if you do something you ought not have done; this does not mean I would take this to the extreme of say, allowing social viruses to be spread in the forums (variations of the rm command who's intent is nothing more than to hose someones computer for instance). But I would say that if someone wants to know how to do X, and that X's purpose is NOT to do be vicious, then it would be perfectly reasonable to explain how to do X.

I will abide by the rules, but I am worried that with the passage of this kind of nanny policies, it is only a matter of time before the forums are little more than pink ponies.

---

