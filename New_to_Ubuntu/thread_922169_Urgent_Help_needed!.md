---
title: "Urgent Help needed!"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by JimVicious on 2008-09-17
Hey everyone, I just fired up one of the computers that I got built for me a month or two ago and I don't know how to do anything. Can someone tell me how to install a .bz2 file.

---

### Post by crazypenguin2008 on 2008-09-17
type in tar xvjf filename.tar.bz2 to extract the files out of it

thn open a terminal and type ./configure

that should work off the top of my head but ill look to be sure

btw what is the file your trying to install??

---

### Post by JimVicious on 2008-09-17
where would i type that?
and the file is vuze.

thanks

---

### Post by Ryadt on 2008-09-17
Type it in the terminal. Application > Accessories > Terminal.

---

### Post by crazypenguin2008 on 2008-09-17
i should have mentioned that,sorry about that. 2"30am and im trying to do too many things at once lol

---

### Post by JimVicious on 2008-09-17
REQUIREMENTS:
Azureus requires Sun Java 1.5.x or newer to run.
JRE 1.6 (6.0 series) is highly recommended.
[http://java.sun.com](http://java.sun.com)

RUNNING:
1. Extract the contents of this .tar.bz2 file.
2. Change to the 'azureus' directory where the files were extracted.
3. Start Azureus by running the script named 'azureus'; ex. "./azureus"

NOTE:
If you have the Java JRE installed somewhere unusual (or not in your PATH),
use the JAVA_PROGRAM_DIR option in the script.



Thats what the readme says. I right clicked the .bz2 and pressed extract. Now its on my desktop. What do i do now?

---

### Post by Ryadt on 2008-09-17
> **JimVicious said:**
> REQUIREMENTS:
Azureus requires Sun Java 1.5.x or newer to run.
JRE 1.6 (6.0 series) is highly recommended.
[http://java.sun.com](http://java.sun.com)

RUNNING:
1. Extract the contents of this .tar.bz2 file.
2. Change to the 'azureus' directory where the files were extracted.
3. Start Azureus by running the script named 'azureus'; ex. "./azureus"

NOTE:
If you have the Java JRE installed somewhere unusual (or not in your PATH),
use the JAVA_PROGRAM_DIR option in the script.



Thats what the readme says. I right clicked the .bz2 and pressed extract. Now its on my desktop. What do i do now?
Why don't you just install the one in the repos?
Just type in terminal```
sudo apt-get install azureus
```
and you are done.

---

### Post by northern lights on 2008-09-17
Applications > Accessories > Terminal, alternatively 'Alt+F2 > gnome-terminal'

```
cd ~/Desktop/vuze
```assuming that there's a folder on the desktop called that

The next step may or may not be necessary```
sudo chmod 770 azureus
```
Run the installer```
./azureus
```

---

### Post by JimVicious on 2008-09-17
peter@peter-desktop:~$ sudo apt-gett install azureus
[sudo] password for peter:
peter@peter-desktop:~$ sudo apt-gett install azureus
peter@peter-desktop:~$ sudo apt-gett install azureus
peter@peter-desktop:~$ sudo apt-gett install azureus


:@ I cant do this ****. Kill Me!

why does it hate me.
I typed it in. It asked for the password, I entered the password and nothing happened

---

### Post by tangibleorange on 2008-09-17
for the most part, installing software on ubuntu is not like installing on windows. instead of downloading a file from the manufacturer's website, you can install a pre-compiled version that is known to work with ubuntu. to do this, you can either type a command like was issued above, or use "Add/Remove Applications", which can be found at Applications -> Add/Remove Programs.

This link may also be of use: [https://help.ubuntu.com/community/InstallingSoftware]("https://help.ubuntu.com/community/InstallingSoftware")

good luck!

EDIT: it's:
```
sudo apt-get install azureus
```
not 'apt-gett'

---

### Post by northern lights on 2008-09-17
If it's in the repos this obviously easier.

It's 'apt-get', i.e.```
sudo apt-get install azureus
```

Plus, you need to have the [universe]("http://packages.ubuntu.com/search?keywords=azureus&searchon=names&suite=hardy&section=all") repository enabled. Check under "System > Administration > Software Sources".

[EDIT]
Ryadt had put one 't' only also...
[/EDIT]

---

### Post by JimVicious on 2008-09-17
Sorry about all of this. Im a complete noob!.
i put in the password that i enter at the start after my username and it says :[sudo] password for peter:
Sorry, try again.
[sudo] password for peter:
peter@peter-desktop:~$

---

### Post by tangibleorange on 2008-09-17
> **JimVicious said:**
> Sorry about all of this. Im a complete noob!.
i put in the password that i enter at the start after my username and it says :[sudo] password for peter:
Sorry, try again.
[sudo] password for peter:
peter@peter-desktop:~$

well when it asks for a sudo: password you just type your normal password (that you login with). if you type it correctly it should run the command...

---

### Post by northern lights on 2008-09-17
Your user's regular password is what is asked for.

If a single 't' doesn't do the trick, enable universe (see above).

---

### Post by JimVicious on 2008-09-17
> **northern lights said:**
> If it's in the repos this obviously easier.

It's 'apt-get', i.e.```
sudo apt-get install azureus
```

Plus, you need to have the [universe]("http://packages.ubuntu.com/search?keywords=azureus&searchon=names&suite=hardy&section=all") repository enabled. Check under "System > Administration > Software Sources".

[EDIT]
Ryadt had put one 't' only also...
[/EDIT]

under system > administration ive only got : keyring manager, network tools, printing, system log, system moniter and update log

---

### Post by JimVicious on 2008-09-17
i did this:

peter@peter-desktop:~$ cd ~/Desktop/vuze
peter@peter-desktop:~/Desktop/vuze$ sudo chmod 770 azureus
[sudo] password for peter:
peter@peter-desktop:~/Desktop/vuze$ ./azureus
Starting Azureus...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Java exec found in PATH. Verifying...
find: /home/peter/.azureus/plugins: No such file or directory
Passing startup args to already-running Vuze java process listening on [127.0.0.1: 6880]
peter@peter-desktop:~/Desktop/vuze$

---

### Post by tangibleorange on 2008-09-17
> **JimVicious said:**
> under system > administration ive only got : keyring manager, network tools, printing, system log, system moniter and update log

ah i guess you are not in the sudoers group (can not gain admin rights). are you the only user of that computer - there should be an account with sudo ability that belongs to the user that first installed ubuntu. you need to find that account.

---

### Post by JimVicious on 2008-09-17
im the only user that i know of.
Is there any way i can change it?

---

### Post by northern lights on 2008-09-17
> **JimVicious said:**
> peter@peter-desktop:~$ cd ~/Desktop/vuze
peter@peter-desktop:~/Desktop/vuze$ sudo chmod 770 azureus
[sudo] password for peter:
peter@peter-desktop:~/Desktop/vuze$ ./azureus
Starting Azureus...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Java exec found in PATH. Verifying...
*find: /home/peter/.azureus/plugins: No such file or directory*
Passing startup args to already-running Vuze java process listening on [127.0.0.1: 6880]
peter@peter-desktop:~/Desktop/vuze$In theory, it appears the binary is supposed to be ran from the home folder. So moving it there either by hand or by```
mv ~/Desktop/vuze/ ~/
```might be of help.

However, I have to concur with tangibleorange. You appear to only be in the user group.

---

### Post by northern lights on 2008-09-17
> **JimVicious said:**
> im the only user that i know of.
Is there any way i can change it?
If this is your personal machine you can change it via Recovery Mode. However if you set up the system yourself and did not change your username you should be in sudoers. Can you please post the output of ```
cat /etc/sudoers
```

---

### Post by JimVicious on 2008-09-17
i didn't set this up myself. A friend did it for me and hes away without a way to contact him.

This is the effect:

peter@peter-desktop:~$ cat /etc/sudoers
cat: /etc/sudoers: Permission denied
peter@peter-desktop:~$

---

### Post by northern lights on 2008-09-17
Mkey, this was a bit daft on my behalf. sudoers can't even be viewed without root rights.

Can you instead post ```
groups USER
```where USER is your username?

---

### Post by JimVicious on 2008-09-17
peter@peter-desktop:~$ groups peter
peter : powerdev adm dialout fax cdrom floppy tape audio dip plugdev scanner fuse
peter@peter-desktop:~$ 

thanks

---

### Post by northern lights on 2008-09-17
Okay, you're for sure not equipped with root rights. You should be in 'admin'.

Under the premise, that, physically, this is your machine, do the following:

Reboot and in the GRUB menu choose "Recovery Mode". If the GRUB menu doesn't show at boot, hit 'ESC' when it says "GRUB loading - stage 1.5".
Drop to a root shell and run ```
cat /etc/sudoers
```and make sure the line in italics exists```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

[I]# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
[/I]
```
Then add yourself to 'admin'```
usermod -g admin peter
```

---

### Post by fullmetalgerbil on 2008-09-17
If you can't get Vuse in, which I'm unsure whether you did or didn't, then you really should just install Azureus (It's the pre Vuse version, but myself I like it better anyways and it has basically the same function i.e. Bit Torrent client) from the repositorys as others have suggested. Just go to System>Administration>Synaptic Package Manager, click search, type in Azureus, mark for installation and hit apply.
Of course this could be perfectly useless if you've already found a way to install Vuse.
And don't sweat the n00b thing, you'll do fine just stick with it.

---

### Post by northern lights on 2008-09-17
> **fullmetalgerbil said:**
> If you can't get Vuse in, which I'm unsure whether you did or didn't, then you really should just install Azureus (It's the pre Vuse version, but myself I like it better anyways and it has basically the same function i.e. Bit Torrent client) from the repositorys as others have suggested. Just go to System>Administration>Synaptic Package Manager, click search, type in Azureus, mark for installation and hit apply.
Of course this could be perfectly useless if you've already found a way to install Vuse.
And don't sweat the n00b thing, you'll do fine just stick with it.While inherently, none of what you suggest is anywhere near faulty, Synaptic will also only work if you're in %admin and is not shown in the OP's menu.

It is advisable to more than the first post of a thread once in a while...
;)

---

### Post by JimVicious on 2008-09-17
guys i cant do this.
can someone help me get windows xp on this?

---

### Post by northern lights on 2008-09-17
> **northern lights said:**
> Okay, you're for sure not equipped with root rights. You should be in 'admin'.

Under the premise, that, physically, this is your machine, do the following:

Reboot and in the GRUB menu choose "Recovery Mode". If the GRUB menu doesn't show at boot, hit 'ESC' when it says "GRUB loading - stage 1.5".
Drop to a root shell and run ```
cat /etc/sudoers
```and make sure the line in italics exists```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

[I]# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
[/I]
```
Then add yourself to 'admin'```
usermod -g admin peter
```
Exactly at what point do you get stuck?

---

### Post by JimVicious on 2008-09-17
when i pressed escape at the point where the screen read "Press esc in 2, 1, 0" and it did nothing

---

### Post by JimVicious on 2008-09-17
oh hang on
i just got it going 
so ill copy that stuff that you wrote onto paper and ill work it out

---

### Post by Bucky Ball on 2008-09-17
If you get to the desktop and you have a wired internet connection, good chance it will work. Login on the Ubuntu computer as it will be easier to go to 'Applications->Internet->Firefox WebBrowser' and continue posting from there. Then you can just copy and paste what is here straight to the terminal without having to scribble it all down. :)

Don't forget to breathe, JimVicious ... ;)

---

### Post by northern lights on 2008-09-17
> **Bucky Ball said:**
> If you get to the desktop and you have a wired internet connection, good chance it will work. Login on the Ubuntu computer as it will be easier to go to 'Applications->Internet->Firefox WebBrowser' and continue posting from there. Then you can just copy and paste what is here straight to the terminal without having to scribble it all down.

The OP is on an Ubuntu machine. Recovery Mode is CLI.

---

### Post by Bucky Ball on 2008-09-17
Gotcha. :-? Scribbling it is then.

---

### Post by JimVicious on 2008-09-17
alright i got most of it
just after the :

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL



i dont know how to do the admin thing
i wrote in "usermod -g admin peter"
and it said unrecognized command

---

### Post by Ryadt on 2008-09-17
It seems that you can use sudo then.
Try to update```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by JimVicious on 2008-09-17
peter@peter-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for peter:
peter is not in the sudoers file.  This incident will be reported.
peter@peter-desktop:~$

---

### Post by Ryadt on 2008-09-17
> **JimVicious said:**
> peter@peter-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for peter:
peter is not in the sudoers file.  This incident will be reported.
peter@peter-desktop:~$

Boot in recovery mode.
Then type
```
sudo adduser peter admin
```
then reboot and login.

---

### Post by northern lights on 2008-09-17
Recovery Mode is the only instance of Ubuntu where the root account is enabled by default. The prefix sudo is thus irrelevant.

Won't 'assuser'/'useradd' create a new account? It trifles me why 'usermod' would not work.

---

