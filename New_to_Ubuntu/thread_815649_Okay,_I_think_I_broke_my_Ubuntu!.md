---
title: "Okay, I think I broke my Ubuntu!"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by fishman78 on 2008-06-01
Hey All,

    So, I was trying to log into root priv.  But I keep getting "ubuntu is not in the sudoers file.  This incident will be reported."  When I try and go to user settings and unlock the properties, it tells me "Could not authenticate, an unexpected error has occurred."  Any thoughts on how to fix this?  I can't install anything or do anything that requires root access.  Thanks for all your help!

Kurt

---

### Post by SunnyRabbiera on 2008-06-01
you mean you wanted to do stuff under root right?
root access is disabled by default on Ubuntu, you can achieve most root commands by using sudo.
Did you try a guide by someone telling you to use root as opposed to sudo?

---

### Post by spiderbatdad on 2008-06-01
to get root privileges use ```
sudo -i
```From your user terminal and input your password.

---

### Post by fishman78 on 2008-06-01
Hi,

Thanks for the replies.  When I type sudo -i, I get the "ubuntu is not in the sudoers file.  This incident will be reported." message.  Ubuntu is the username.  Any ideas as to what might be causing this?  Thanks!

Kurt

---

### Post by SunnyRabbiera on 2008-06-01
did you modify ubuntu to use a root account?

---

### Post by fishman78 on 2008-06-01
> **SunnyRabbiera said:**
> did you modify ubuntu to use a root account?

I don't think so, but then I am quite new a linux, so maybe?

Can i fix it if I did.  When I go to user groups I get the other error stating unexpected error, could not authenticate.  Please help!

Kurt

---

### Post by fishman78 on 2008-06-01
Here is a screenie with my errors.  Thanks again!

---

### Post by majickmann on 2008-06-02
How did you install Ubuntu?  I've only seen the ubuntu userid on the live cd and vmplayer installs.  Are you sure this is the correct userid for you?

Have you used sudo commands prior to this incident?  If yes, what occurred prior to the commands failing?

It seems the sudoers file has been modified to exclude the userid ubuntu from certain or all sudo commands.  Or, the userid ubuntu has been removed from the admin group required for sudo access.

Otherwise, reinstall and create a userid for yourself when prompted.  Remember the login and password.  Use it with sudo.

HTH...
--majickmann

---

### Post by fishman78 on 2008-06-02
I have used the sudo command before with success, but now it doesn't work anymore.  
I made ubuntu my username....probably not smart...sorry.
I installed ubuntu on a standalone 250g sata drive.  (dual boot with vista)

I'd prefer not to reinstall ubuntu as I have spent hourse configuring to the way it is now.  But if that's the only solution then i'll try.  Thanks again.  Your help is greatly appreciated.

Kurt

---

### Post by jimrz on 2008-06-02
it would appear, since you have "ubuntu" as both the host name and user name , that you are using the "live cd" which is not going to give you root priviledges to it's system files. Apologies if you actually used these names on your actual install, if not then the instructions given for using "sudo' will work once you have an actual install in place.

---

### Post by johnl on 2008-06-02
If you don't want to reinstall you should be able to fix this as follows:

reboot your system.  At the GRUB menu, select the Ubuntu recovery option and hit enter to boot that.

It will boot up and dump you into a terminal as the root user.  Now you just need to add yourself to 1) the admin group or the sudoers file.  Let's try the admin group first.

```

usermod -a -G admin your-user-name

```

Now you should be able to reboot and use sudo as your user:

```

shutdown -r now

```

and boot into ubuntu normally.  Hopefully you should be able to use sudo now!

---

### Post by majickmann on 2008-06-02
Okay, so dual boot install; ubuntu is the userid you created.  Did you create other userids?

You have run commands with sudo prior...  Prior to what?  What happened between the time you could and the time you could not?

I suspect the userid ubuntu is no longer a member of the admin group. Run the id command.  You should see admin as at least one group for your userid.

For example:
majickmann@ubuntu7:/home/majickmann $ id
uid=1000(majickmann) gid=1000(majickmann) groups=1000(majickmann),115(admin)

---

### Post by majickmann on 2008-06-02
There's the missing link...  Following Johnl's instructions should get sudo access.  Presuming the problem is ubuntu mysteriously no longer belongs to the admin group.

Hopefully that is all.

:-)

---

### Post by Leit0 on 2008-06-02
> **johnl said:**
> If you don't want to reinstall you should be able to fix this as follows:

reboot your system.  At the GRUB menu, select the Ubuntu recovery option and hit enter to boot that.

It will boot up and dump you into a terminal as the root user.  Now you just need to add yourself to 1) the admin group or the sudoers file.  Let's try the admin group first.

```

usermod -a -G admin your-user-name

```

Now you should be able to reboot and use sudo as your user:

```

shutdown -r now

```

and boot into ubuntu normally.  Hopefully you should be able to use sudo now!
(Short for all the crap down there v: it worked and thanks.)


The longer version:

I'm a newbie, basically I got linux to appear geeky and smart. :D 

But yeah, dumb people shouldn't do that, I got a shady gray theme and I wasn't used to the difference between it's on/off positions on a trigger button. So basically instead of giving myself all administrative privileges I took them all away. xD

I don't know how what the shell is but I assumed that was the root and chose that after the repair. Then used the two command lines you supplied.

Yay, I'm admin. :D (I think I was better off without the privileges, now I'm gonna blow this thing up for sure).

---

### Post by fishman78 on 2008-06-02
Hi 

So I tried the command both in terminal and in the root shell off the login options.  I don't think it worked though.  Below is a copy and paste of the output I got.  Maybe I'm not typing something right?  I've attached another screenie of my accounts page.  When I look at the account I'm supposed to use none of the items are checked off.  Is that right?  Thanks again

Kurt

[COLOR="Blue"]ubuntu@ubuntu-PC:~$ usermod -a -g admin ubuntu
usermod: -a flag is ONLY allowed with the -G flag
Usage: usermod [options] LOGIN

Options:
  -c, --comment COMMENT		new value of the GECOS field
  -d, --home HOME_DIR		new home directory for the user account
  -e, --expiredate EXPIRE_DATE	set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE	set password inactive after expiration
				to INACTIVE
  -g, --gid GROUP		force use GROUP as new primary group
  -G, --groups GROUPS		new list of supplementary GROUPS
  -a, --append		append the user to the supplemental GROUPS
				mentioned by the -G option without removing
				him/her from other groups
  -h, --help			display this help message and exit
  -l, --login NEW_LOGIN		new value of the login name
  -L, --lock			lock the user account
  -m, --move-home		move contents of the home directory to the new
				location (use only with -d)
  -o, --non-unique		allow using duplicate (non-unique) UID
  -p, --password PASSWORD	use encrypted password for the new password
  -s, --shell SHELL		new login shell for the user account
  -u, --uid UID			new UID for the user account
  -U, --unlock			unlock the user account

ubuntu@ubuntu-PC:~$ [/COLOR]


> **johnl said:**
> If you don't want to reinstall you should be able to fix this as follows:

reboot your system.  At the GRUB menu, select the Ubuntu recovery option and hit enter to boot that.

It will boot up and dump you into a terminal as the root user.  Now you just need to add yourself to 1) the admin group or the sudoers file.  Let's try the admin group first.

```

usermod -a -G admin your-user-name

```

Now you should be able to reboot and use sudo as your user:

```

shutdown -r now

```

and boot into ubuntu normally.  Hopefully you should be able to use sudo now!

---

### Post by tom56 on 2008-06-02
Pay attention to the upper case G in the command (you typed a lowercase g).

---

### Post by arpanaut on 2008-06-02
The command you input is incorrect, commands in *nix are case sensitive... See the output from the terminal i.e. use the -G flag in the command.

---

### Post by Joeb454 on 2008-06-02
Case Sensitivity is something it took me a while to get over as well :p It still catches me out, when I miss an upper case letter :p

---

### Post by fishman78 on 2008-06-02
Well,   That seems to have worked well!  Thanks to all who helped!

Only thing now is that I'm the admin of the system.  That may not be a good thing as I don't know what I'm doing.  Will ubuntu still ask me for a password when i want to change the important stuff?  Thanks!!

Kurt

---

### Post by spiderbatdad on 2008-06-02
> **fishman78@live.ca said:**
> Well,   That seems to have worked well!  Thanks to all who helped!

Only thing now is that I'm the admin of the system.  That may not be a good thing as I don't know what I'm doing.  Will ubuntu still ask me for a password when i want to change the important stuff?  Thanks!!

Kurt

Changes to root owned file require 'sudo' to edit, so you will be asked for a password.

do: ```
id
``` check that you are user id 1000.

---

