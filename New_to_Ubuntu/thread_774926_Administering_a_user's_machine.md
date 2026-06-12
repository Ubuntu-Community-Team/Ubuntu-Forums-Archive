---
title: "Administering a user's machine"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by chip616 on 2008-04-29
I'm used to having a root account and being able to administer my daughter's laptop without giving her that kind of access.  Even from within her user account, I can give the root password for minor maintenance.

In Ubuntu the user password is the root password if the account is enabled with admin privileges.  That gives her a loaded gun, which I do not want to do.  If the account is NOT admin enabled, then it appears that there is no way that any system administration can be done from within that account.  It seems that I have to log into another account and do it from there.

Surely there must be a way around this.

Thanks.

Frank.

---

### Post by chenel on 2008-04-29
Of course there's a way around it... but are you sure you really want to?  After all, if you can "su root" from a user account, it's already classified as an "administrator" account in some sense (it's part of the 'wheel' group).  Probably any maintenance that is done should be done from another user account anyway (you could use the 'fast user switcher' applet that you can add to the panel by right-clicking to speed this up), to avoid accidentally leaving a root terminal open or something like that.  That's the whole purpose of locking out the root password.

If you *really* think you need to re-enable the root account, you can (see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)), but usually it's not the best answer.  Ubuntu's default configuration is designed to help you administer your system better (that is, safely and with fewer chances of mistakes).

---

### Post by chip616 on 2008-04-29
Chenel:

I wasn't asking how to open the root account.  I know how to do that.  I was assuming that Ubuntu users had a way around enabling the root account and still doing what I wanted to do.  That is what I am  looking for.

> After all, if you can "su root" from a user account, it's already classified as an "administrator" account in some sense (it's part of the 'wheel' group).

OK, is this what I am looking for?  Is that what I type in to a console opened in a user account that does not have admin privileges?  If so, what password do I supply at this point?

Thanks.

Frank.

---

### Post by chenel on 2008-04-29
Sorry, maybe I wasn't clear enough.

I don't know how you're accustomed to doing it.  I was assuming that formerly you executed "su" (which is semantically equivalent to "su root") from your daughter's account to gain root privileges.  But for this to work, there are a number of things that need to be true:
 (1) the root account needs to be enabled.  'su' basically just opens up a shell of the specified user (if you give it no options it assumes root) for you.  If root is locked, then 'su' won't be able to let you into the root shell.  (In this case the password you'd enter would be the root password)
 (2) your daughter's account would need to be part of the group that's allowed to become root.  When I wrote my post earlier I assumed this was "wheel" since that's what it is in most other distros, but since ubuntu doesn't have an enabled root account by default, it seems they have eliminated it (I don't have any entries for 'wheel' in /etc/group).  It seems as though they have replaced it by the 'admin' group: which means you would have to put your daughter's account in the 'administrator' category anyway, which seems to be rather contradictory to your purpose, as it would allow her to use sudo... :)

I'm not sure I've ever heard of someone trying to do what you want to do.  I think the vast majority of ubuntu users have some account that they're comfortable leaving admin privileges for (since the first account you install, by default, can do that)... and they're willing to switch accounts to do maintenance stuff (or don't have another account).  (And probably most of the people who *could* come up with some hack to do that would tell you that it's a security risk and to avoid it, anyhow :))

Hope that helps.  Sorry if I sounded grouchy earlier -- I was in a hurry writing that post.

---

### Post by chip616 on 2008-04-29
Chenel:

> Hope that helps.

Sorry, but not really.  :)  I was looking for someone familiar with Ubuntu to show me the "Ubuntu" way of doing something that I have been doing with Xandros and Fedora for years.  While I will accept the 'dangerous root account' philosophy of the Ubuntites if that is what they want (they are the only ones on the planet to adopt this approach, however), I still need to be able to administer my daughter's machine.  I find that the lack of a root account complicates this.  I could always su into a root shell, or a root copy of Konqueror from the my daughter's user account.  This is fast and convenient.  This is taken away, however, when the root password and the user account password are the same.

Unless I am missing something, and that is the something that I hope someone will jump in with.

> Sorry if I sounded grouchy earlier -- I was in a hurry writing that post.

Not at all!  I appreciate your trying to help.

Frank.

---

### Post by lazyart on 2008-04-30
```
sudo passwd
```

changes the root password to something else (whatever you provide).  Keep it secret and only you knowing the password can administer, even if she is logged in.  This enables the root account.

---

### Post by chenel on 2008-04-30
Here we go, I just thought of this this morning.  I think it'll do what you want.

Do (in a terminal)
```
su *adminuser*
```
where *adminuser* is an administrator-level user on your system.  That will open a shell for the admin-level user, who can then use sudo *with his (her) own password* rather than the password of the restricted user.  The beauty of this is that 'su' will accept either the root password or (in this case much better) the password of the target user.

Hope this solves it for you.

Cheers.

---

### Post by chenel on 2008-04-30
Also, being Linux, you could always restore the behavior you're used to if you have no problem with the potential security risks.  Have a look at /etc/pam.d/su (the comments there are pretty helpful).

The other thing is that sudo can be configured to allow certain users to only execute certain commands as root, though it takes some effort.  The sudoers man page has a lot of information about this.

Hope that Ubuntu's behavior doesn't irritate you too much in the end...  It was put in place for good reason, I think, but one person's "good reason" is another person's "idiocy" :)  Hopefully you can find some satisfactory compromise between Ubuntu's default (which was supposed to help people make good security habits) and what's convenient for you.

---

### Post by Zalbor on 2008-04-30
Sorry if I've misunderstood, but I don't think you have to enable logging in as root (which isn't a good idea).
You can simply create a new user account for your daughter, which doesn't have administrative rights (can't use sudo and gksu). Let her use that one, and log with the main account (which can use sudo) when you need to do something as administrator.

---

### Post by Dylnuge on 2008-04-30
> **chip616 said:**
> Chenel:

While I will accept the 'dangerous root account' philosophy of the Ubuntites if that is what they want (they are the only ones on the planet to adopt this approach, however), I still need to be able to administer my daughter's machine.

Actually, the sudo program is used by the MacOS as well, and quite a few distros have something equivalent to it (most Gentoo users I know have it configured, though Gentoo is manual).

Anyway, it sounds to me like what you want to be able to do is:
A. Keep your daughter from accessing the admin privileges herself
while
B. Being able to access admin privs from her account.

This usually isn't the best choice, on any Linux system. The root account and sudo exist as security layers, to prevent the user from messing something up or prevent a malicious program from getting access into the computer without permission. Unlike a "limited" account on Windows, your daughter can do just about anything she needs to, except change essential system functions. So, I think the best option you have is just to create your own account, put it in the admin group, and use that to change these settings. Ubuntu is, by design, a multiuser system.

Now, maybe I misunderstood something. Perhaps, instead of wanting to be able to change settings from your daughters account, you want to be able to have her change some settings, but not all. There is a way to do this, since the execution of a lot of things relies on groups and you can configure how groups operate and make it so that some programs allow sudo access while others do not. It is rather complicated and involves using the system terminal (at least, I don't know of a way around it without the terminal). If this is what you want to do, let me know.

I know that doesn't really answer your question, but really, Linux is designed to have multiple user accounts, so I think that it is the best solution, and the "Ubuntu way," as you described it.

-Dylan

---

### Post by ayenack on 2008-04-30
Hello chip616. If I were you I'd create an admin account on the system for yourself to administer your daughters account and do this.

Log in as admin open a terminal and type this.

**sudo gedit .gnome2/nautilus-scripts/Right\ click\ root**

This will open an empty file add this to it.

[B]for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do

gksudo "gnome-open $uri" &

done[/B]

Save it and exit.

Then in terminal do this.

**sudo chmod +x .gnome2/nautilus-scripts/Right\ click\ root**

Log out and then in again or reboot the system.

That's it. This will enable you to edit/open files/applications with root privileges by right clicking them and selecting **Scripts_Right_click_root**. This can be used on whole folders so you can administer your daughters /home folder by right clicking it or any other root/user's file from your admin account without having to use sudo in terminal. Far easier than sudo in terminal. Quick note be very careful when using this as it's very easy to mess up your system. This could probably be used over an ssh connection also but haven't tried it.

Well hope that's of some help to you. BTW the admin account is NOT the root account the root account is not enabled by default in Ubuntu unlike many other distro's. It is possible to enable the root account but there's no need as you may as well just use sudo or gksudo from the admin account. There seemed to be some confusion over root and admin accounts so thought that I'd point this out.

---

### Post by chip616 on 2008-04-30
Zalbor:

> Let her use that one, and log with the main account (which can use sudo) when you need to do something as administrator.

That is what Ubuntu currently forces me to do.  I am trying to get around this.  This is not outlandish.  I've done this for years.  Xandros (a newbie distro) has an entry for root console and root file manager right in the menu structure of every user account.  One needs the root password however to access it.  It is done in Ubuntu - the user administers his own account.  I shouldn't need to log into another account to administer the one that is open.

dylnuge:

> This usually isn't the best choice, on any Linux system. The root account and sudo exist as security layers, to prevent the user from messing something up or prevent a malicious program from getting access into the computer without permission.

I suspect that the majority of user accounts that are set up on Ubuntu systems are admin accounts.  Most Ubuntu machines are single-user machines, no? The user administers his own account. However, I am not faced with that particular setup.  I need to do something that may be a bit different from the majority of installs out there.

In any case folks, this is rapidly digressing from what I hoped was a simple question to yet another discussion of the 'no root' philosophy.  I will concede the 'no root' argument as I don't want to go down this path yet again.  While I appreciate help anyone might offer with regard to this specific question, can we please avoid any further discussions of philosophy?  And, please, I don't say that unkindly.  It just gets frustrating when any question I ask with regard to no root administration gets back on the same old track.  /end rant.

Here is the question:  How do I administer a user account with no admin privileges from within that user account?  I do not want to open a second account.

If this is not possible in Ubuntu, then just let me know.  If that is the case, THEN I'll move on to plan 'B'.  But PLEASE, don't tell my why it is a bad idea.  I've heard all those.  :)

Thanks, all, for your patience.

Frank.

---

### Post by Calash on 2008-04-30
The best solution I can think of is to give her account Sudo privileges, but do not tell her the password.  You can set the computer to automatically login to that account so she will never need the password to get local access to the system and her home folders.

For local maintenance you can then authenticate with that password to get Sudo access.

Is that what you are looking to do?

---

### Post by pt_lam on 2008-04-30
Sorry that I probably don't get what you mean.
But... why you need to do administration through your daughter's account?

---

### Post by ayenack on 2008-04-30
I don't quite understand the problem. If you want to use sudo on your daughters account then give here sudo privileges. Don't tell her the password and that's an end to it. Using sudo in any form on the account is still using sudo so in theory it's just the same as using the admin account. Root terminals in all other distro's that I know require a password to be used to access them. You could try setting up a chroot account if that's what your after take a look at this tutorial.

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

### Post by chenel on 2008-04-30
> **chip616 said:**
> 
Xandros (a newbie distro) has an entry for root console and root file manager right in the menu structure of every user account.  One needs the root password however to access it. 
Here is the question:  How do I administer a user account with no admin privileges from within that user account?  I do not want to open a second account.


The short answer: in Ubuntu you don't.  (At least, not without some serious headache -- see below.)

As for why you could do this in Xandros and not in Ubuntu: Xandros may (I don't know) be built on the GNU version of 'su' (which allows a user to get root privileges).  GNU su has philosophical differences with other implementations of su/sudo (like Ubuntu's); GNU su will let any user switch to root (see [this page]("http://www.gnu.org/software/coreutils/manual/html_node/su-invocation.html#index-MIT-AI-lab-2101")), and distros like Ubuntu and Gentoo and almost all the BSD variants require you to be part of some special group (since they figure this increases security).  In Ubuntu (as well as these others), "limited" users are TRULY limited in that you can't do anything with a limited account that you ought to need to be an administrator for, including get root privileges.

So, the way to hack around this is to make your daughter's account part of the group that allows her to switch to root.  In Ubuntu, this will take four steps:

(1) Change the credentials necessary to switch to root.  You'll need to edit the file "/etc/pam.d/su".  Look for this section:
```
# Uncomment this to force users to be a member of group root
# before they can use `su'. You can also add "group=foo"
# to the end of this line if you want to use a group other
# than the default "root" (but this may have side effect of
# denying "root" user, unless she's a member of "foo" or explicitly
# permitted earlier by e.g. "sufficient pam_rootok.so").
# (Replaces the `SU_WHEEL_ONLY' option from login.defs)
# auth       required   pam_wheel.so
```

Uncomment the 'auth' line, and add group=XXX, where XXX is the name of the group you want to make.

(2) Create the group XXX.  You could use the System>Administration>Users and Groups tool for this.
(3) Add your daughter's account to this group.
(4) Unlock the root password as detailed before.
Now you can use "su" from this account to get a root shell.

**[COLOR="Red"]NOTE:  mucking around with the su settings is DANGEROUS.  Be careful, or you could completely lock yourself out of the root account altogether.[/COLOR]**

I think creating a second account is probably much simpler and more efficient :)

Also, you'll need to have an account that is admin-capable to do any of this stuff in the first place... so, I suppose you could do all of it, then delete that account -- but it seems more straightforward just to leave it there and [do what I suggested earlier]("http://ubuntuforums.org/showpost.php?p=4842503&postcount=7") :)

Is this what you're looking for?

---

### Post by chip616 on 2008-04-30
Chenel:

> but it seems more straightforward just to leave it there and do what I suggested earlier

Is this what you're looking for?

Yes, this looks good.  Had a chance a few hours ago to give this a try, and it does allow me to switch to my other account that DOES have admin privileges.

However....

I tried to open both synaptic and konqueror from within a konsole and got the following:

```
temp@office:~$ su frank
Password:
frank@office:/home/temp$ konqueror
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

konqueror: cannot connect to X server :0.0
frank@office:/home/temp$ synaptic
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(synaptic:6956): Gtk-WARNING **: cannot open display:
frank@office:/home/temp$
```

I created an account 'temp' with only user privileges.  I su'ed to my account (frank) that has admin privileges.  However, I cannot run GUI programs from within that konsole, it seems.

Do you know if there is a way around this?

We're getting somewhere.  :)

Thanks for your kind help.

Frank.

---

### Post by chenel on 2008-05-01
Any command which uses X will need to be run using sudo from the privileged account.  So, for example, in your case you would want to do:
```

temp@office:~$ su frank
[enter your password]
frank@office:~$ sudo konqueror
[enter your password again to run konqueror as root]

```

The reason for this is that Frank is not the owner of the X session that is currently running.  But as root, you can do whatever you want, so 'sudo + command' should work fine.

Cheers.

---

### Post by chip616 on 2008-05-01
Chenel:

> so 'sudo + command' should work fine.

Tried that.  Same error.  Also tried changing to the home directory of "frank" and trying variations on the command from there too.  No change.

I'm still open to other suggestions.  :)

Frank.

---

### Post by chenel on 2008-05-01
Really?  Weird.  I tried it and it works just fine on my machine ...

I'll have to think about it some more, I guess.

---

### Post by chenel on 2008-05-05
I can't think of any other way to do it.  I'm still baffled why my last suggestion worked for me, and not for you.  I guess if you're going to keep the second user you'll probably just have to switch users (I like the 'user switcher' applet that you can add to your panel... I use it regularly). :-\

Sorry I couldn't help you more.

---

### Post by lemming465 on 2008-05-05
> Anyway, it sounds to me like what you want to be able to do is:
A. Keep your daughter from accessing the admin privileges herself
while
B. Being able to access admin privs from her account.

If Dylnuge has understood the goal here correctly, the idea is that your daughters password shouldn't provide root access, which means some other password should.  There are two choices for other password, root, or a different user in the admin group.  If you don't want to do a full login as a different user, you could use "su otheruser" to become that other user from a terminal window.  You might have some minor X authentication issues to overcome if you run GUI applications from there.
Or you could set a password on the root account; it's not the default setup in Ubuntu, but there is nothing preventing it (sudo passwd root).  

My daughters accounts on our home Linux installs don't have sudo privileges either, so I sympathise.  Our solution is to just use the gdm "switch user" functionality, and we log in independently, and switch back and forth.

You can take her out of the admin group to remove her sudo privileges using *sudo vigr*, but only after creating another account with admin privileges, or setting a root password.  Otherwise you'll have to boot single user to a root shell and set up the privileges after the fact.

Speaking of which, by default anyone with console access can do that.  If that is a problem, you will need to change the SULOGIN setting in /etc/default/rcS and you probably do need to set a root password.

---

### Post by chenel on 2008-05-15
Here is another possibility that I came across today:

If you don't want to have to completely switch users, you can install the package 'xserver-xephyr', and edit your menus (right-click on menu bar and click "Edit Menus") so that the entry "New login in a window" under "System tools" is enabled.  Then you'll be able to run a session as another user on the system in a window from your unprivileged account.  I noticed when I tested it that on my system mouse movement is rather laggy when Compiz is running, but under Metacity it seems to work fine.

This of course still means you need to have the other user, so it's not your ideal solution, but maybe it's better?

---

### Post by chip616 on 2008-05-15
Chenel:

You are a true friend to keep up with this thread.  :)  I have received some other suggestions in the CompuServe Linux forum as well, but have just not had the time to look at them yet.  Hope to do so perhaps this holiday Monday here in Canada.  I will post back if I find something that works (or even if I don't).  :)

Frank.

---

### Post by chip616 on 2008-05-19
Chenel:

Well, I tried the other suggested solutions from the fine folks in the [CompuServe Linux Forum]("http://community.compuserve.com/n/pfx/forum.aspx?tsn=1&nav=messages&webtag=ws-linuxforum&tid=128625"), and none of them worked.

```
sudo su
```

Of course, that did not work, as the user account is not in the sudoers file.

```
kdesu -u frank konqueror
```

where 'frank' is the name of the account on my daughter's machine that DOES have admin privileges.  This didn't work either.  The command was ignored, and I ended up back to the command prompt with no error message.

So, I guess having an enabled root account is a good thing after all.  :)  There seems to be no elegant way around it for my needs.

Thanks for your help.





Lemming465

> Or you could set a password on the root account; it's not the default setup in Ubuntu, but there is nothing preventing it (sudo passwd root).

My daughters accounts on our home Linux installs don't have sudo privileges either, so I sympathise.

I think I'll just enable the root account.  Seems like the easiest and most elegant solution.  I've been using Linux for some 6 years now, and haven't had a security breach or trashed any of my machines by running the root account from time to time.

I'll get flak for that last comment.  :)  Head's up!

Frank.

---

### Post by chenel on 2008-08-11
Dunno if anybody  is still following this thread, but I ran across a nifty little Bash script that allows you to run programs as another user on your own display (it takes care of all of the business of who 'owns' the display, etc.).  It's called "sux" (="su X") and it's conveniently packaged in the universe repository.  It works quite well :)

Run it from a terminal window:
```
sux [other user name] [command]
```
e.g.,
```
sux tux firefox
```
then enter the other user's password and you're golden.

Hope this helps somebody.

---

### Post by chip616 on 2008-08-11
Chenel:

Yes, I'm still watching it.  :)  However, I've found that just enabling the root account and editing the sudoers file got things back the way I was familiar with.  I am using Kubuntu now on my personal laptop, and have been for a couple of months now.  I was going to put it on my daughter's machine, but it died.  I'm waiting for a new one from Dell so I can hand this one down to her.  :)

Frank.

---

### Post by hyper_ch on 2008-08-11
Hmmmm, if she has physical access to the notebook then she can gain su/sudo rights if she really desires it. Steps involved:

(1) Reset bios - if there is a password
(2) Set bios to boot from a cd
(3) Run any live cd
(4) Mount the harddrive
(5) Alter the group file so that she's in the admin group or whatever or set another root password or or or...

---

### Post by chip616 on 2008-08-15
hyper_ch:

I'll make sure that she does not see you post.  :)

Yes, I know that there are ways around anything.  I'm not running a server for the CIA, however.

Frank.

---

### Post by airtonix on 2008-08-21
> I'm not running a server for the CIA, however.

awww... I had high hopes for you. lol :)

---

### Post by Mr_JMM on 2008-11-21
Hi,

Can I just confirm something...

I set up a new user with limited access.
I login to their user session with their login details.
I want to modify some aspects of their workspace including which programs are loaded, desktop theme etc. so I try to start the Synaptic Package Manager. I can't because it requires a password and as the new user doesn't have admin rights, their password fails.
What I was basically trying to do (and this is where I hope I've grasped Chip's question correctly) was to be able to enter an admins password to allow a change (I hate to say this but it's the best way), like you can in Vista.

My question is simply this: Would allowing this process be what is referred to as enabling root access? Is this the same as what is being discussed here?
I appreciate that this is a bad thing and I don't want to enable root user.

Sorry, I know that may seem daft, I have read the thread but I've just woken up!!

If so, then in order for someone to be able to customise their workspace, do they need admin rights?

Thanks.

ps Hope it's ok to revive the thread. I felt so sure that I'm asking the same question I didn't want to bloat the forums with another thread.

---

### Post by chenel on 2008-11-21
> **Mr_JMM said:**
> 
I want to modify some aspects of their workspace including which programs are loaded, desktop theme etc. so I try to start the Synaptic Package Manager.

/snip

My question is simply this: Would allowing this process be what is referred to as enabling root access? Is this the same as what is being discussed here?



Synaptic is for installing software, not for customizing the desktop.  (It's not the same thing as the Windows control panel -- maybe that's what's confusing you?)  You don't need it to customize a user's theme (go to the System menu > Preferences > Appearance) or the programs that are loaded on startup (System > Preferences > Sessions).  If you want to install software that's not installed on the system, you should probably do it by running Synaptic with a privileged user account, since by default installed software that isn't meant to be root-only is available to all users.

So I don't think the discussion in this thread applies to what you want to do.

---

### Post by chip616 on 2008-11-21
Mr J:

Your basic thinking is correct, but chenel has provided the accurate answer.  You don't need root privileges to change a user's workspace.  However, if you do want to install software for that user (and all others on the machine) then you have to go to an account that has root privileges and do it from there.

I find that limitation a pain, so I have enabled the root account, and yes, I am still alive, and my machine has not blown up.  What is overblown is the 'no root' taboo.  Most other distros have root accounts by default, and the world has not ended because of this.

Now, I'll probably get flamed for stating the above, but I don't care what anyone else thinks.  All are entitled their own opinions.  Enabling root is not evil.

Frank.

---

### Post by chenel on 2008-11-21
I think mostly it boils down to the details of one's particular situation.  In what seems like the vast majority of cases, there's no need for a root user because the day-to-day user is one who can gain root privileges when necessary.  Avoiding a root user in that case is supposed to help the user 'think twice' every time they go to root privileges -- "is this something I really want to be doing?"  Since they're supposed to use 'sudo' every time they want to do something that requires root privileges, in theory there should be less "ohmygosh I didn't realize I was still root" mistakes.

However, every once in a while there's a situation where it does make more sense to unlock the root user account (like Frank's, as we discovered).  But because there are usually better solutions for almost every situation people are usually reluctant to recommend unlocking the root user (most people counsel it as a last resort).  Unless you have a real need for the only regular user of the machine to not be able to modify system settings, the standard Ubuntu setup will probably work better and (in the long run) be a bit more secure.

---

### Post by LowSky on 2008-11-21
I found this to be a great thread! We had a simular discussion at work. I personally like Ubuntu's sudo style, but it has limitations, for example in a workplace. Ubuntu seems like a poor choice in its normal config for any business to use without modifying the OS. But as a home based or single user machine Ubuntu is great.

---

### Post by scorp123 on 2008-11-21
> **LowSky said:**
> Ubuntu seems like a poor choice in its normal config for any business to use without modifying the OS. Nonsense. We use Ubuntu a lot in our company and it works tip top, even without the "root" account. As a matter of fact we really love that feature. "root" is the one account that every *nix system has per default, so by taking it out of the equation potential intruders will have a hard time guessing any accounts. And even if they guess a working account name and even if by any chance they happen to guess a password ... there is still no guarantee that the account they guessed will give them access to anything significant.

Ubuntu is tip top for businesses.

---

### Post by chip616 on 2008-11-21
chenel:

You are a reasonable person.  I like your style.

Frank

---

### Post by chenel on 2008-11-21
> **chip616 said:**
> chenel:

You are a reasonable person.  I like your style.

Frank

Many thanks :)

---

