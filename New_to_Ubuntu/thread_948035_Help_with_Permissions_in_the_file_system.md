---
title: "Help with Permissions in the file system"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by skrap1r0n on 2008-10-14
Newbie to Ubuntu (and linux), I installed it last night and I LOVE it so far, although I am stumped here. 

I am primarily using this to do web development on. I have XAMPP experience on windows platforms, but the permissions thing is killing me here. 

I am trying to create a subfolder in the htdocs and place some files I have been working on (in windows) in it.

As a windows user, I am used being able to drag a folder into another one and it's there. However, when I browse to the htdocs folder and try to drag a folder of the desktop in there it says permissions denied.

How do I overcome this? I am missing something real simple, obviously, but it's bugging me to no end that I can't create files in the folder.

Also, I somehow (no idea how) created a file in there and I want it gone, but I do not have permission to delete it either. How to I get full control over that folder?

---

### Post by fenian on 2008-10-14
What directory is the htdocs folder in?

---

### Post by nightcrawler27 on 2008-10-14
> **skrap1r0n said:**
> Newbie to Ubuntu (and linux), I installed it last night and I LOVE it so far, although I am stumped here. 

I am primarily using this to do web development on. I have XAMPP experience on windows platforms, but the permissions thing is killing me here. 

I am trying to create a subfolder in the htdocs and place some files I have been working on (in windows) in it.

As a windows user, I am used being able to drag a folder into another one and it's there. However, when I browse to the htdocs folder and try to drag a folder of the desktop in there it says permissions denied.

How do I overcome this? I am missing something real simple, obviously, but it's bugging me to no end that I can't create files in the folder.

Also, I somehow (no idea how) created a file in there and I want it gone, but I do not have permission to delete it either. How to I get full control over that folder?

Sounds like you might not have permissions to the files in the folder? Maybe the one time you added the file you did it as root. Easiest way I can think of is this:

Open a terminal window. type "su -" and then enter the root password. 

Then type "chmod -R 755 <path/to/whereveryourfilesare>"

This will make the directory and files in it have full permissions for the owner (7), and read/execute (5) permissions for other users in the owner's group and read/execute (5) for everyone else.

This will at least allow you to drag the files to your desktop because your account will be able to read them. If you want to ensure your user account owns those files so you can assign permissions as yourself and not have to be root or another user, do this by typing (again as root):

"chown -R <yourusername>:<yourgroupname> </path/to/whereveryourfilesare>"

Exit the terminal.

Now your user account will be able to control permissions, etc on those files/dirs. If this is not how you want those permissions to be assigned, then you can modify the permissions and ownership using these two commands until you are satisfied.

FYI most default Windows installs give the first user administrator access, which is why few people have permissions problems on their home PC. This is very bad from a security point of view.

Nightcrawler27

---

### Post by skrap1r0n on 2008-10-14
Awesome, this worked, with one little change I had to noodle out. I had to use

sudo chmod -R 755 /opt/lampp/htdocs/

not SU-

SU didn't work...

Now on to configuring my apache ini file to recognize include paths...

---

### Post by handydan918 on 2008-10-14
If you are doing any kind of admin stuff, you gotta get a handle on permissions. They are your greatest ally if you know them, and your worst nightmare if you don't.

[http://en.wikipedia.org/wiki/Unix_permissions](http://en.wikipedia.org/wiki/Unix_permissions)

---

### Post by akelsall on 2008-10-14
Based on my very similar experience, I believe nightcrawler27 is right on the mark. I had created a file as root, then tried to drag&drop files into that folder as another user (and of course, couldn't). If you follow nightcrawler27's suggestions, I think you'll be fine. 

Another alternative (albeit the brute force way) is to open a terminal window and enter " gksudo nautilus &". You'll be prompted to enter YOUR password (not the root password). You may see an error message in your term window, but after about 10 secs the Nautilus file browser will open.

[COLOR="Red"][B]*****************************************************************
A word of caution using the "gksudo nautilus &" method. This will open the Nautilus File Browser as root user. This means you can remove any and all files--meaning you can do serious damage if you're not paying attention to what you're moving or deleting using Nautilus. Use caution if you decide to go this route. The advantage is you'll be able to drag&drop files without any problem with permissions. 
*******************************************************************[/B][/COLOR]

Andy

---

### Post by stoogiebuncho on 2008-10-15
It's been a while since I did this, so maybe things have changed, but I remember from setting up Xampp on my machine that the htdocs folder needs to be owned by root in order for Xampp to function properly.

So once you have things set up and start coding, you may have to change the ownership of htdocs back to root before it will work for you.

I set up folders inside of htdocs that were owned by me, so I could edit and create them easily without being logged in as root, but the htdocs folder itself was owned by root so that it would work correctly.

---

### Post by bodhi.zazen on 2008-10-15
> **nightcrawler27 said:**
> Sounds like you might not have permissions to the files in the folder? Maybe the one time you added the file you did it as root. Easiest way I can think of is this:

Open a terminal window. type "su -" and then enter the root password. 

Then type "chmod -R 755 <path/to/whereveryourfilesare>"

This will make the directory and files in it have full permissions for the owner (7), and read/execute (5) permissions for other users in the owner's group and read/execute (5) for everyone else.

This will at least allow you to drag the files to your desktop because your account will be able to read them. If you want to ensure your user account owns those files so you can assign permissions as yourself and not have to be root or another user, do this by typing (again as root):

"chown -R <yourusername>:<yourgroupname> </path/to/whereveryourfilesare>"

Exit the terminal.

Now your user account will be able to control permissions, etc on those files/dirs. If this is not how you want those permissions to be assigned, then you can modify the permissions and ownership using these two commands until you are satisfied.

FYI most default Windows installs give the first user administrator access, which is why few people have permissions problems on their home PC. This is very bad from a security point of view.

Nightcrawler27

Sorry to burst you bubble(s) but, this is very bad advice.

First Ubuntu uses sudo , not su 

Furthermore, setting a root password is neither needed or supported on Ubuntu.

See this link : [uhelp]community/RootSudo[/uhelp]

And to make matters from bad to worse, Nightcrawler27 advises changing ownership of system files. This is the fastest way to break you system.

Even if "it works" Nightcrawler27's advice is also a serious breach of security and well is just wrong/bad advice.

I know it is frustrating to make the transition, but you really should take the time to learn how the system works. See the link handydan918 gave you re: permissions.

[uhelp]community/FilePermissions[/uhelp]

To run apache see this link :

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by skrap1r0n on 2008-10-15
I only used 

sudo chmod -R 755 /opt/lampp/htdocs/

and that allowed me to move the folder into the htdocs folder. I ran into another issue not having save (write?) permissions for the php.ini file. And it was getting late so I canned it for the night.

I never did set a root password when I installed it, AFAIK, I am the only user, is I am kind of confused as to why I need to have permissions when i am logged in. I will read up on permissions and figure it out.

---

### Post by bodhi.zazen on 2008-10-15
> **skrap1r0n said:**
> I am the only user, is I am kind of confused as to why I need to have permissions when i am logged in. I will read up on permissions and figure it out.

Permissions are a part of security on any OS, including Windows. The permissions are more robust on Linux.

---

### Post by nightcrawler27 on 2008-10-15
> Sorry to burst you bubble(s) but, this is very bad advice.

First Ubuntu uses sudo , not su 

Furthermore, setting a root password is neither needed or supported on Ubuntu.

See this link : [uhelp]community/RootSudo[/uhelp]



Sorry, I forgot that Ubuntu does this by default. Probably the first thing I do after I install Ubuntu is "uncripple" my root account. I'm sure many others do the same, especially if they are used to running that way from other distros. Sometimes it is just plain easier to do superuser tasks as root then to keep typing sudo before a bunch of commands all the time. Especially since the user needs to take as much care using sudo as they would if they actually had a root shell.

At the risk of threadjacking, may I ask how Ubuntu support responds to a user who has set their root password and uses a root shell for administration tasks from time to time? If this is "unsupported", does that mean that any Ubuntu user or sysadmin that calls for support after doing this is denied tech support?

> 

And to make matters from bad to worse, Nightcrawler27 advises changing ownership of system files. This is the fastest way to break you system.

Even if "it works" Nightcrawler27's advice is also a serious breach of security and well is just wrong/bad advice.



I did not specifically intend to have the user change ownership of system files, however I simply provided an example of how to change ownership of files if the user found the need to do that as well. The user apparently is familiar with the concept of file permissions and ownership, and an impression was made that the user knew the files he/she was working with and what he/she wanted to do with them. All I was trying to do was provide more information on how to assign rights and ownership to files. Maybe I should have made that more clear.

Nightcrawler27

---

### Post by bodhi.zazen on 2008-10-15
> **nightcrawler27 said:**
> At the risk of threadjacking, may I ask how Ubuntu support responds to a user who has set their root password and uses a root shell for administration tasks from time to time? If this is "unsupported", does that mean that any Ubuntu user or sysadmin that calls for support after doing this is denied tech support

Take a look at the link I gave you.

Ubuntu uses sudo

```
sudo -i
``` it the preferred way to obtain a root shell. Use gksu (kdesu for kde) for graphical applications.

For the rare time when setting a root password is required, it is supported.

And yes, it would be helpful if you would be more clear with your explanations. We have a lot of new users here and while you are free to run you system the way you like, we ask you to teach new users standard Ubuntu methodology while assisting on these forums. While I am sure you know what you are doing, you methodology can do a lot of potential damage.

My more expanded reasoning is here :

[http://ubuntuforums.org/showpost.php?p=5769207&postcount=77](http://ubuntuforums.org/showpost.php?p=5769207&postcount=77)

If typing "sudo -i" is such a hassle , why not set an alias.

alias su="sudo -i"

---

### Post by porchrat on 2008-10-15
OK so if sudo -i is the accepted way...why can't I use this:

```
sudo su
```

That is how I always do it.  Is that somehow wrong?...I have literally done it that way for ages.

---

### Post by bodhi.zazen on 2008-10-15
> **porchrat said:**
> OK so if sudo -i is the accepted way...why can't I use this:

```
sudo su
```That is how I always do it.  Is that somehow wrong?...I have literally done it that way for ages.

As I indicated there are several issues here.

First we are not taking a stance on how you chose to run your system. If you wish to sudo su or set a root password, and you know what you are doing, then by all means please do as you wish.

If, however, someone is asking for support we are asking that you teach them how to sysadmin in a standard, supported way. For example, please teach them about permissions rather then chmod 777 , etc.

What we object to more strongly is setting a root password. While that may work just fine for Fedora or Arch or any other OS, it can break Ubuntu and is not necessary. I mean really it seems silly to me that people are so stuck in their ways that they will not learn sudo. sudo is quite powerful and has a number of advantages over su and very few disadvantages. Not everyone will agree that sudo is *better* then su, and that is fine. While you may not agree, we are asking people to teach sudo on these forums and not set a root password unless there is no other option.

Our goals are very simple: teach proper system administration and prevent system breakage.

---

### Post by nightcrawler27 on 2008-10-16
> **bodhi.zazen said:**
> As I indicated there are several issues here.

While you may not agree, we are asking people to teach sudo on these forums and not set a root password unless there is no other option.

Our goals are very simple: teach proper system administration and prevent system breakage.


I definately see this point. I think alot of us "learned" Linux in part by exploring what we can do, sometimes breaking our systems and understanding what we did, why not to do that, how to fix it, etc. However I can also understand that getting new users to stick with Ubuntu may not be accomplished by saying what amounts to "You can use these commands to solve problem xyz. Try them out, you can change and control all sorts of things...here's an example, but you shoud really try to figure out how they can help you accomplish exactly what you want."

I will keep this in mind for the future.

Nightcrawler27

---

### Post by jerome1232 on 2008-10-16
I think sudo was a very good move by Ubuntu, and I can see why using sudo is so strongly encouraged on the forums. 

If it took the traditional route I could guarantee many people would be logged into X as root for their everyday tasks (browsing the web, checking email) and I think we can all agree that is not desired. (Just look around at threads complaining about 'how do I own my entire os? I don't care about security')

Some people don't realize that running as a limited user is a big part of the OS's security model.

---

### Post by bodhi.zazen on 2008-10-16
> **nightcrawler27 said:**
> I definately see this point. I think alot of us "learned" Linux in part by exploring what we can do, sometimes breaking our systems and understanding what we did, why not to do that, how to fix it, etc. However I can also understand that getting new users to stick with Ubuntu may not be accomplished by saying what amounts to "You can use these commands to solve problem xyz. Try them out, you can change and control all sorts of things...here's an example, but you shoud really try to figure out how they can help you accomplish exactly what you want."

I will keep this in mind for the future.

Nightcrawler27

Thank you very much, it is greatly appreciated. I agree that learning through breaking can be an effective method, and to some extent this is also how I learned.

Most people, however, probably prefer not to learn through breaking and this type of "education" is somewhat outdated. It is often less effective as breakage is frustrating, to say the least. In addition data loss can be devastating. It is bad enough to loose music one downloaded, but loss of family pictures or one's PhD thesis is entirely different.

The Ubuntu philosophy is different, kinder, gentler. For example data backup. Of course one should back up mission critical data, but we prefer to teach people to back up before a hard drive failure rather then after the failure. This is part of what makes these forums so popular for new users.

If one wishes to "test" new commands, I suggest using a live CD, virtualization, or a Test installation.

---

### Post by egalvan on 2008-10-16
> **nightcrawler27 said:**
> Open a terminal window. type "su -" and then enter the root password.

nightcrawler27, what is 

```
su -
```
 supposed to do?

On my system, I get the following:

```
ernest@hp-dv8135nr:~$ su -
Password: 
su: Authentication failure
ernest@hp-dv8135nr:~$
```

and yes, the password is my correct user password.

ErnestG

---

### Post by porchrat on 2008-10-16
> **egalvan said:**
> nightcrawler27, what is 

```
su -
```
 supposed to do?

On my system, I get the following:

```
ernest@hp-dv8135nr:~$ su -
Password: 
su: Authentication failure
ernest@hp-dv8135nr:~$
```

and yes, the password is my correct user password.

ErnestG

the su command makes you a super-user...basically it is like permanent sudo.

---

### Post by jerome1232 on 2008-10-16
Correction.

It stands for switch user, it's trying to switch to the root account which is disabled in Ubuntu, hence the authentication failure.

Use sudo -i to get a root shell (it's pretty much the same thing except it uses your password not roots)

---

### Post by egalvan on 2008-10-16
> **porchrat said:**
> the su command makes you a super-user...basically it is like permanent sudo.

OK, but
 "su"
 and
 "su -"

both fail on my system (Hardy)

Any ideas why it does not work?

Note, not trying to run as root all the time, just trying to learn what commands to use, and not to use, and why they fail on my system (hardy).

ErnestG

---

### Post by egalvan on 2008-10-16
> **jerome1232 said:**
> Correction.

**It stands for switch user, it's trying to switch to the root account which is disabled in Ubuntu, hence the authentication failure.**

Use sudo -i to get a root shell (it's pretty much the same thing except it uses your password not roots)

Many thanks.
Good explanation, and I have a little more knowledge added to my library of Linux.

ErnestG

:popcorn:

---

### Post by nightcrawler27 on 2008-10-16
> **egalvan said:**
> OK, but
 "su"
 and
 "su -"

both fail on my system (Hardy)

Any ideas why it does not work?

Note, not trying to run as root all the time, just trying to learn what commands to use, and not to use, and why they fail on my system (hardy).

ErnestG

As the forum staff was kind enough to explain, switching to superuser using su is not the way they want to encourage users to administrate their system.

However, the "su" command means "switch user". So if I need to become another user for some reason, rather than log out and log back in as that user, I might type "su <username>" to become that user. I would need to have that user's password to become that user. the "-" can be inserted or omitted in order to assume that user's environment, not just their rights/privileges. "su" or "su -" assumes the user wants to become root.

This kind of thing is a convenient way to do stuff as another user without logging off my current user account...i.e. I can be logged in as bob, but then open up an xterm and su to joe...but in the other window I am still bob.

The reason "su" (to root) does not work on many Ubuntu systems, as previously posted, is that Ubuntu is set up out of the box to prevent you from becoming root through su or logging in as root directly. Instead you perform administrative tasks using sudo, which allows you to execute an individual command with root privileges. This is to encourage users to not use administrative access all the time and therefore hose their systems.

If I remember correctly, a typical Windows install provides the first user with Administrator rights, which is one of the reasons why Windows is considered so insecure. Think about it...on your home Windows PC, have you ever had to enter an admin password to install software, apply patches, etc? Each home Windows PC user's account typically has rights over the whole box, which introduces the possibility of a user wrecking their system by doing something like opening an attachment with a virus or other malicious code that then executes with administrative privileges - allowing it to modify system files, configuration settings, etc. In Linux, especially Ubuntu, if something like this happens with an attachment, you are somewhat protected because your user account is not running with administrative privileges all the time. I believe this has changed in Windows Vista; the user really is a regular user by default.

Nightcrawler27

---

### Post by bodhi.zazen on 2008-10-16
Very small clarification.

su == switch user (or substitute user or what have you)

the "-" is a "flag" 

su , with no options, will default to root.

su bob will su to "bob"

su - => the - flag == log in shell. Basically a log in shell will act as if root had logged any will thus use root's environmental variables (ie /root/.bashrc, etc).

As always, when en question, try the man pages :twisted:

[http://linux.die.net/man/1/su](http://linux.die.net/man/1/su)

---

### Post by nightcrawler27 on 2008-10-16
> **bodhi.zazen said:**
> 
As always, when en question, try the man pages :twisted:

[http://linux.die.net/man/1/su](http://linux.die.net/man/1/su)


Yes, man pages are your friend! They can tell you all sorts of stuff about how to use specific commands, and what all their options and flags can do. Many questions about what a command does can be answered by the man pages, and usually much faster than asking someone in a forum and then have 30 morons come back and say "What r u a n00b??? N00b$ Sux0rS!!!" rather than try to help (except around here). :)

Nightcrawler27

---

### Post by egalvan on 2008-10-16
> **nightcrawler27 said:**
> As the forum staff was kind enough to explain, switching to superuser using su is not the way they want to encourage users to administrate their system.
Nightcrawler27

I totally agree, which is why I stated that I 

** not run as root all the time**
"not a good thing"

 **just trying to learn what commands to use,**
I need to learn linux

** and not to use,**
I want to learn what to stay away from, and why.


** and why they fail on my system (hardy).**
again, a need-to-learn.

I hit the 'man' pages often, but they rarely explain "WHY" one does it a certain way.

All these posts EXPLAINING what is going on have been VERY helpful.

bodhi.zazen has posted some excellent information.

---

### Post by bodhi.zazen on 2008-10-16
Well, IMO, learning to read the man pages is very helpful. I know, I know, they are written in techno-geek, but stay with it.

Now you know you are a geek when they start making sense, and you know you are in deep when you start writing man pages (I will spare you from that for the moment).

You *may* be interested in these links :

[http://articles.techrepublic.com.com/5100-10878_11-6102898.html](http://articles.techrepublic.com.com/5100-10878_11-6102898.html)

[http://spsneo.com/blog/2008/07/21/colourful-man-pages-in-ubuntu/](http://spsneo.com/blog/2008/07/21/colourful-man-pages-in-ubuntu/)

---

### Post by porchrat on 2008-10-17
> **bodhi.zazen said:**
> Well, IMO, learning to read the man pages is very helpful. I know, I know, they are written in techno-geek, but stay with it.

Now you know you are a geek when they start making sense, and you know you are in deep when you start writing man pages (I will spare you from that for the moment).

You *may* be interested in these links :

[http://articles.techrepublic.com.com/5100-10878_11-6102898.html](http://articles.techrepublic.com.com/5100-10878_11-6102898.html)

[http://spsneo.com/blog/2008/07/21/colourful-man-pages-in-ubuntu/](http://spsneo.com/blog/2008/07/21/colourful-man-pages-in-ubuntu/)

Also if the man pages are a little confusing (for example with the bloody "sed" man page!...sorry...no ranting...back under control) then you can always google the command and get a more easily understandable explanation.

---

### Post by dtommy79 on 2008-12-28
Hi,

I have the same problem as the thread starter. i've been reading through this thread and I'm a bit confused. So what's the best way to solve this premission problem?

Also, when i installed ubuntu I thought that I'm the root user when the installer asked for a username and password. How do i know what my root password is?

---

### Post by bodhi.zazen on 2008-12-28
> **dtommy79 said:**
> Hi,

I have the same problem as the thread starter. i've been reading through this thread and I'm a bit confused. So what's the best way to solve this premission problem?

Setting permissions are dependent on the file system. FAT and NTFS file systems are set when you mount. Linux native file systems (ext2/3, JFS, ReiserFS, etc) are set with chown/chmod.

See :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)


If you are having problems with this, please start a new thread. Be sure to tell us what file system you are talking about.

> Also, when i installed ubuntu I thought that I'm the root user when the installer asked for a username and password. How do i know what my root password is?As has been stated several times in this thread Ubuntu uses sudo.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by dtommy79 on 2008-12-28
ok, this one worked:

> sudo chmod a+w /opt/lampp/htdocs

---

### Post by bodhi.zazen on 2008-12-28
w00t :)

---

