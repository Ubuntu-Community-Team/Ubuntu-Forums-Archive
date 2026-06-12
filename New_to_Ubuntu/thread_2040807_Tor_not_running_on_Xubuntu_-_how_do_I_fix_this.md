---
title: "Tor not running on Xubuntu - how do I fix this?"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by WiredTired on 2012-08-11
Hi, I'm new here.

I decided to install Xubuntu, because I have an older PC, I heard that the new Gnome 3 is kinda awful, and then I heard that Xfce is looking a lot like old Gnome anyway (kinda mac-like but no-nonsense and organized sounded appealing, as it has been so far).

Anyway, I've had a hard time following some of the help threads, which tend to ignore Xfce users in favor of Gnome. Specifically, I'm trying to get Tor working (with the graphical Vidalia UI), and the first thing I did was download the Linux-specific bundle from the website (yeah I know, probably not the best way to do Linux). After unpacking the files, I found an executable file for Vidalia (the executable for Tor was unresponsive), which launched a graphic window, but with the error that Tor had stopped. Like I said, it's hard to find a help page online for Tor under Xfce, and I know there are different operational programs to call (if not different file structures too). 

Has anyone been successful running Tor under Xubuntu, and can anyone help me get it running on mine? I'd be most grateful.

---

### Post by uRock on 2012-08-11
> **WiredTired said:**
> Hi, I'm new here.

I decided to install Xubuntu, because I have an older PC, I heard that the new Gnome 3 is kinda awful, and then I heard that Xfce is looking a lot like old Gnome anyway (kinda mac-like but no-nonsense and organized sounded appealing, as it has been so far).

Anyway, I've had a hard time following some of the help threads, which tend to ignore Xfce users in favor of Gnome. Specifically, I'm trying to get Tor working (with the graphical Vidalia UI), and the first thing I did was download the Linux-specific bundle from the website (yeah I know, probably not the best way to do Linux). After unpacking the files, I found an executable file for Vidalia (the executable for Tor was unresponsive), which launched a graphic window, but with the error that Tor had stopped. Like I said, it's hard to find a help page online for Tor under Xfce, and I know there are different operational programs to call (if not different file structures too). 

Has anyone been successful running Tor under Xubuntu, and can anyone help me get it running on mine? I'd be most grateful.Installing and running Tor is the same for all *ubuntu installs. From another thread,> **uRock said:**
> 
I was having the same problem with Vidalia and Tor. I had to chown to do the following via the terminal,```
cd /var/run/tor
sudo chown username:username control.authcookie
```The above command made the user(insert your username into the command) the owner of the control.authcookie so that it can run properly. After doing this, I used the terminal to launch the downloaded Tor browser, which is located in my Downloads folder,```
cd Downloads/tor-browser_en-US/ && ./start-tor-browser
```You may first need to make the start-tor-browser executable which is done by **cd**ing to the directory holding the file, then using the **chmod +x** command.

I changed the title of the thread in hopes of answering your question instad of arguing over frustrations.

---

### Post by WiredTired on 2012-08-11
> **uRock said:**
> Installing and running Tor is the same for all *ubuntu installs. From another thread,
I'll give this a try.

What I was trying to do was start "clean", and follow a tutorial (which I've lost track of after a couple of browser reboots) which involved **gedit, **something which I know is not installed by default on Xubuntu. By the time I figured out that the program which replaced gedit for Xfce was named for a leaf (leafpad?????), and that the file which that tutorial called for me to edit didn't really exist on my system, I was getting kinda frustrated!

---

### Post by WiredTired on 2012-08-11
> **uRock said:**
> Installing and running Tor is the same for all *ubuntu installs. From another thread,
Not doing so well. I got a "permission denied" error just for trying to move to that directory per the first command!  I'm the only permitted user on my PC, so what may be causing that?

I'm also getting a real hard time from this site specifically -  it won't allow me to quote most of what I intended to, and I did remove all script restrictions for ubuntu forums.

The problem I have in following your helpful instructions is that my system won't even permit me to enter folder on MY computer

cd /var/run/tor

and then I am completely locked out of any right-click options to change the permissions for this one!  So before I decide that this whole system is just too weird for anybody who didn't design it himself (or could have), I hope somebody can help me out of this situation too - please! Can't imagine what I may have done to get locked out of anything on my own system - I feel violated!

---

### Post by JKyleOKC on 2012-08-11
> **WiredTired said:**
> Not doing so well. I got a "permission denied" error just for trying to move to that directory per the first command!  I'm the only permitted user on my PC, so what may be causing that?

I'm also getting a real hard time from this site specifically -  it won't allow me to quote most of what I intended to, and I did remove all script restrictions for ubuntu forums.

The problem I have in following your helpful instructions is that my system won't even permit me to enter folder on MY computer

cd /var/run/tor

and then I am completely locked out of any right-click options to change the permissions for this one!  So before I decide that this whole system is just too weird for anybody who didn't design it himself (or could have), I hope somebody can help me out of this situation too - please! Can't imagine what I may have done to get locked out of anything on my own system - I feel violated!I fully understand your frustration; perhaps a bit of overviewing will help you comprehend what is happening and reduce the level of frustration.

For starters, you are **NOT** the only user authorized on your system. My system has 39 users defined, but only one of them is human. The other 38 exist to partition what individual parts of the system are permitted to do "behind the curtain." For instance, user "bind" is only permitted to handle specific areas that deal with my local DNS server -- and nobody BUT "bind" is allowed to change critical parts of those areas. You may have more or less than my 39; some of them, like my example "bind," are created only if their associated software is installed.

However one very critical user, named "root," is present in every system. This is the "super user" which can do almost anything, anywhere, and many if not most of the critical system files are owned by root but do have read-only access for everyone. A few of the most critical, though, prohibit access by anyone other than "root" and it sounds as if this is the case for your /var/run/tor directory. The /var directory does have read access for everyone, as does its /var/run subdirectory. Since the "tor" subdirectory does not exist until tor has been installed, and I don't have tor on my system, I can't check its permissions.

However, if you issue the command "ls -l /var/run" from a terminal window, that should show you the ownership of all the subdirectories and also their permissions. I would expect permissions to appear as "drwxr-xr-x" for all directories shown. If one shows as "drwx------" then only the owner (the first user name on the same line) can do anything with it. Most owners in this area should show as "root" but the second name on each line may vary from one to the next. You can direct the output to a text file in your home directory by typing "ls -l /var/run > VarRun" (that's a little L, not the figure 1) and can then attach the VarRun file to a message here if you need more help interpreting it -- and it won't give away any personal information; it just lists each directory or file in that directory, its size, date, permissions, and owner.

Changing ownership and permissions can be quite dangerous to your system. In many cases, giving permissions to everyone for a system file or directory may make it impossible to boot the machine again. This whole business of multi-level permissions and multiple "users" that are really just system programs is intended to provide better security. While you're perfectly free to make any change you want to your own system, some changes have serious unexpected consequences.

I hope this helps reduce your level of frustration. It will take a while to become really comfortable with such detailed security precautions, but most of us do get there pretty rapidly...

---

### Post by cortman on 2012-08-11
Frankly I would just install it from the repositories:

```
sudo apt-get install tor vidalia
```

I use tor all the time for IRC, never had any problem with it that simply restarting the daemon didn't fix. (to do that- 

```
sudo service tor restart
```
)

---

