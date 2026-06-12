---
title: "Messed up user creation in Ubuntu, any possible fix ??"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by TripleTea on 2011-09-13
Greetings everyone,

can someone interpret this error messages upon logging in a fresh new user created through the System>Administration>Users and Groups ??


```
Could not update ICEauthority file /home/abc/.ICEauthority

There is a problem with the configuration server.(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

Nautilus could not create the following required folders: /home/abc/Desktop, /home/abc/.nautilus

```i think this command is what i did that broke my current Ubuntu in creating new users
```
sudo chmod 755 /
```i look forward to hearing the different possible fixes =D

thank you in advance !

---

### Post by Wim Sturkenboom on 2011-09-13
Re-install; you did a good job in messing it up (:D) and it will take you ages to set the permissions for every individual file and directory correctly

Alternatively, you can boot from a liveCD and start resetting the permissions one-by-one (check on liveCD, change on system).

PS
Wonder what triple was in your tea when you issued the command :lol:


//EDIT (see post #5 as well)
Misread the command. Actually the command that you issued is harmless as far as I know.

---

### Post by varunendra on 2011-09-13
> **Wim Sturkenboom said:**
> 
PS
Wonder what triple was in your tea when you issued the command :lol:
Perhaps it was something that said "777" which tempted him to test the power of super-user in linux :lolflag:

TripleTea, it's best to just reinstall.

---

### Post by TripleTea on 2011-09-13
hahahahaha, thank you all for your replies....I was already expecting to re-install....i just wanted to know how bad i messed it up.

being a windows user since i ever owned a computer, im having a good time fiddling with ubuntu =D....cant wait for more re-installs to come....

anyways, can you guys enlighten me on what i did when i issued the command
```
chmod 755 /
```

wasn't it to make / non world writeable ??i was curious about / being world writeable.....as i lauched the ufw status, there was a warning for / being world writeable ??

btw, i didnt get your joke Wim Sturkenboom...
and what about 777 varunendra ? O_O

---

### Post by Wim Sturkenboom on 2011-09-14
I have to apologize (misread the command that you issued (thought that there was a -R in there as well)). You actually did not screw anything up with that command as far as I know.

The normal permissions on the root directory are 755 so issuing the command should not make a difference. This also implies that / is not world writable.

So now I don't know what is actually wrong.

With regards to the joke
You drink tea and have a triple whisky/wodka/whatever in it before you start messing with your system

---

### Post by varunendra on 2011-09-14
> **Wim Sturkenboom said:**
> ....thought that there was a -R in there as well.
..and I didn't even think it may require that switch! Having never done it the commandline way (I prefer "gksu nautilus"), I thought it was sufficient to set the same permission for everything in the root directory (if not the sub-directories too). However, after reading above post I tried it on a Natty VM, then created a new user. Nothing wrong happened with me.

> **TripleTea said:**
> ....anyways, can you guys enlighten me on what i did when i issued the command
```
chmod 755 /
```....
....
and what about 777 varunendra ? O_O
777 means "full permissions to everyone" (or full power to everyone, nobody can deny nothing to anybody!!!!)!

If you don't already know it, these three digits (0 to 7) supplied to chmod are actually interpreted in their binary form to decide the permissions to be granted. Here's some detail for those who feel interested:

The supplied decimal numbers are converted/interpreted in their binary form as follows:
[formula: decimal=>binary]

[LIST]
[*]0=>000, 1=>001, 2=>010, 3=>011, 4=>100, 5=>101, 6=>110, and 7=>111
[/LIST]
Thus 755 means => 111 101 101

The permissions are decided by the place value of these binary digits. The nine place values are: **[COLOR=Black][COLOR=DarkRed]rwx[/COLOR] [/COLOR][COLOR=Blue]rwx [/COLOR][COLOR=Red]rwx[/COLOR]**(r=read, w=write, x=execute), where -

[LIST]
[*]first three places are permissions for the [COLOR=DarkRed]**owner **[/COLOR](who created that file or directory)
[*]next three places are permissions for the [COLOR=Blue]**owner's group**[/COLOR] (the user-group to which the owner belongs)
[*]last three places are permissions for [COLOR=Red]**others **[/COLOR](everyone else)
[/LIST]
[It should be recalled that "root" has full permissions on each and every file/directory in Linux/Unix]


Now '1' for a place value means 'permission related to that place value is granted', while  '0' means 'permission is denied'.

With all this info, now we can get back to 755, which we'll now see as "111 101 101". Applying the above explained theory, it may be written as:
**[COLOR=DarkRed]r(1) w(1) x(1)..  [/COLOR][COLOR=Blue]r(1) [/COLOR]**[COLOR=Blue]_w(0)_[/COLOR]**[COLOR=Blue] x(1)..  [/COLOR][COLOR=Red]r(1) [/COLOR]**[COLOR=Red]_w(0)_[/COLOR]**[COLOR=Red] x(1)[/COLOR]**

which means the owner (which is "root" in case of '/') has all permissions (all 1s), while others (including owner's group) have only **r**ead and e**x**ecute permissions because values pertaining to '**w**' are '0' for them.

If we apply the same with 777, its binary form will be 111 111 111, which shows that all permissions are '1', that is, 'allowed'.

Hope this makes up for my mistake in the interpretation of how the command works without the -R switch. :)


By the way, it'll be interesting to see the permissions on /home/abc directory (that is if you haven't already reinstalled!). They should be owned by "abc" (with create/delete permissions), and not by "root" or someone else.

---

### Post by TripleTea on 2011-09-15
hmmm....okay...if that chmod 755 / didn't screw anything up, then i have no idea how i screwed up my user creation O_O...

varunendra: thank you for taking your time to explain what those numbers actually mean, though i was already aware of what there are =D...just didn't bother to convert those numbers to rwx since im not very familiar with binary. also, good news, i haven't re-installed it yet. ill have a look at what permissions are when i get to touch my Ubuntu again.

anyone have any ideas what messed up my user creation just by looking at the errors ??

---

### Post by varunendra on 2011-09-15
See if this works for you:
```
sudo chmod 1777 /tmp
```
I stole it from an interesting discussion here: [http://ubuntuforums.org/showthread.php?t=1061084](http://ubuntuforums.org/showthread.php?t=1061084)

Some more random approaches: [http://ubuntuforums.org/showthread.php?t=1587918](http://ubuntuforums.org/showthread.php?t=1587918)

Then probably it's time to file a new bug report, or confirm an existing one (in 10.04) here: [https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/577545](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/577545)

---

### Post by maverick_doc on 2011-09-15
hi a newbie here .. 
having the same problem after creating a new profile ..
admin profile wont load :(
just one question how do i get to my data ?(documents folder) before re installing.

---

### Post by varunendra on 2011-09-15
> **maverick_doc said:**
> hi a newbie here .. 
having the same problem after creating a new profile ..
admin profile wont load :(
just one question how do i get to my data ?(documents folder) before re installing.
If it is not encrypted, boot into live session using the live cd/usb which you used to install the OS, then simply browse to the folder and copy the files over to another partition or preferably- an external drive.

By the way, didn't the **chmod 1777 /tmp** trick work?

---

### Post by dfarrell07 on 2011-09-16
> **maverick_doc said:**
> admin profile wont load :(

What do you mean? Privileged rights in Ubuntu are very different than Windows. You can run commands as root (admin) by prefixing 'sudo' before terminal commands. You can also run sudo -i to 'become' root in a terminal session, but that is the same thing as running commands with sudo. Sudo is running as root. It is not really smart to login as root like I described, as avoiding that is a great advantage of Ubuntu's security. If you do try that, make sure you type 'logout' after you are done playing around with root.

---

### Post by maverick_doc on 2011-09-16
thanks for the reply's guys
varunendra : tried running the   " sudo chmod 1777 /tmp "command 
after entering the password this line apperars

atif is not in the sudoers file.  This incident will be reported.

:confused:

---

### Post by varunendra on 2011-09-16
> **maverick_doc said:**
> thanks for the reply's guys
varunendra : tried running the   " sudo chmod 1777 /tmp "command 
after entering the password this line apperars

atif is not in the sudoers file.  This incident will be reported.

:confused:
Oops! Your misbehavior will be reported now :lol:

Try booting into recovery mode > drop to shell, and try it from there.

Although the thread I picked the trick from didn't mention using sudo, yet I think root privilege will be required to change the permission. In the recovery mode, you will already be on root prompt (if I remember correctly), so won't need sudo.

Let's see how it goes.



**_EDIT_:**
Press and hold 'shift' key on the keyboard while booting to bring up the advanced grub menu if it does not come up by default. That is the place where you get the option to select [recovery mode].

---

