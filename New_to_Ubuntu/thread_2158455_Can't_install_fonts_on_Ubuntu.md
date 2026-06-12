---
title: "Can't install fonts on Ubuntu"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by Datzy on 2013-06-29
I'm dualbooting Ubuntu 12.04 LTS on a Windows-based laptop, and I can't seem to install fonts.

Every time I attempt to install a font, it comes up with "Install Failed", and I can't manually place them in the file system because the administrator account doesn't have root permissions.

Help?

---

### Post by cub on 2013-06-29
Which kind of font are you trying to install?

---

### Post by Datzy on 2013-06-29
> **cub said:**
> which kind of font are you trying to install?

otf.

---

### Post by buzzingrobot on 2013-06-29
> **Datzy said:**
> I'm dualbooting Ubuntu 12.04 LTS on a Windows-based laptop, and I can't seem to install fonts.

Every time I attempt to install a font, it comes up with "Install Failed", and I can't manually place them in the file system because the administrator account doesn't have root permissions.

Help?

Are you unable to use sudo in Ubuntu? If so, something's wrong.

System fonts are located in /usr/share/fonts. A "sudo cp -R <MyFontFolder> /usr/share/fonts"  will do the trick.  Follow up with "fc-cache -fv", and "sudo fc-cache -fv" for system-wide enabling. Fonts can also be stashed in ~/.fonts, ie., a .fonts directory in your ./home folder.

---

### Post by grahammechanical on 2013-06-29
If I remember correctly, when I was using 12.04 that also happened to me. Try opening Libreoffice Writer. You may see that font as one of the listed fonts. If so then it is installed despite the message saying it is not.

If the administrator account does not have root privileges, then it is not the administrator account. You do not need administrator privileges to create a .font folder in your home folder.

Open the file manager and in the View menu select Show Hidden files. Then when you open your home folder you will see all the hidden files and folders. They will have a dot ( . ) in front of the name. That is what hides them from normal view. Right click the window background and select New Folder. Rename it to .fonts and stick that font in there.

Regards.

---

### Post by Datzy on 2013-06-29
I did what both of you said, and nothing's working. Should I just do a clean reinstall?

---

### Post by buzzingrobot on 2013-06-30
Have you checked the directory you placed the files in to make sure they are actually there?

Did you run the "fc-cache -fv" commands? Did they produce screen output?

What is displaying that "Install Failed" message?  I've never seen that when I install fonts.  It's not a message that the shell would display.

When you open a terminal and prefaced one of those commands with "sudo", were you prompted for your password, and did the command run to completion?  If so, then you ran the command with administrative privileges.

I'm not sure what you mean by "administrator account" in Ubuntu.  Ubuntu does not enable switching to root via su. The default user, the one created during the install, is allowed to use sudo, instead.

---

### Post by Datzy on 2013-06-30
> **buzzingrobot said:**
> Have you checked the directory you placed the files in to make sure they are actually there?

Did you run the "fc-cache -fv" commands? Did they produce screen output?

What is displaying that "Install Failed" message?  I've never seen that when I install fonts.  It's not a message that the shell would display.

When you open a terminal and prefaced one of those commands with "sudo", were you prompted for your password, and did the command run to completion?  If so, then you ran the command with administrative privileges.

I'm not sure what you mean by "administrator account" in Ubuntu.  Ubuntu does not enable switching to root via su. The default user, the one created during the install, is allowed to use sudo, instead.

I ran fc-cache -fv, it produced screen output.

I know how to use sudo, and yes, I was prompted for my password. 

What I mean is that I can't manually move things to the /___/ filesystem, like /usr/share/fonts.

I'm assuming it was an installation error since it should be working as far as I know, I don't have anything important. After I do the clean reinstall I'll come back to you.

---

### Post by newb85 on 2013-06-30
> **buzzingrobot said:**
> I'm not sure what you mean by "administrator account" in Ubuntu.  Ubuntu does not enable switching to root via su. The default user, the one created during the install, is allowed to use sudo, instead.

Actually, in the terminal, one can switch to root with
```
sudo su
```
but it's usually better practice to simply preface the commands requiring superuser privileges with sudo.

Also, Ubuntu *does* differentiate between Standard and Administrator accounts.  Administrator accounts may use sudo.  Standard accounts may not.  Neither are superuser or root by default.

---

### Post by buzzingrobot on 2013-06-30
> **newb85 said:**
> 
```
sudo su
```


I always use "sudo -i" when I have a lot of things to run off in succession.  Think it sets up a slightly different environment than "sudo su", so the difference might be important on occasion.

In other distros, I usually edit sudoers so I can play fast and loose without the password prompt.  I agree, sort of, with Ubuntu's premise that forcing use of sudo and a password can enhance security.  It doesn't, though, stop people from running dangerous commands.

---

### Post by Frogs Hair on 2013-06-30
To work with items in the file to the file system try the following which is better for graphical applications . Excuse me if I misunderstood.   ```
gksudo nautilus
```

---

### Post by newb85 on 2013-06-30
> **buzzingrobot said:**
> I always use "sudo -i" when I have a lot of things to run off in succession.  Think it sets up a slightly different environment than "sudo su", so the difference might be important on occasion.

Different in the sense that you're acting as root in root's home directory instead of your own home directory.

> **buzzingrobot said:**
> In other distros, I usually edit sudoers so I can play fast and loose without the password prompt.  I agree, sort of, with Ubuntu's premise that forcing use of sudo and a password can enhance security.  It doesn't, though, stop people from running dangerous commands.

You're certainly free to "play fast and loose" on your system.  Please do not advise others to do so, especially in Absolute Beginners.  From the forums' Code of Conduct:

> Remember to do things the Ubuntu way. Often there is more than one solution to a problem. Choose the one you think will be the easiest for the user and the method most commonly used in Ubuntu.

---

### Post by buzzingrobot on 2013-06-30
> **newb85 said:**
> Different in the sense that you're acting as root in root's home directory instead of your own home directory.

You're certainly free to "play fast and loose" on your system.  Please do not advise others to do so, especially in Absolute Beginners.  From the forums' Code of Conduct:

True indeed!  Thanks for the reminder. (Altho it wasn't offered as advice.)

Friends, do not try that at home. 

(But, seriously, the security implications of using "sudo -i" or "sudo su" in Ubuntu, which allows you to run an indefinite number of commands as root until you log out, versus editing sudoers in Fedora/Slackware/OpenSuse/etc to be able to do "sudo <command> without the password prompt, seem to me pretty equivalent.)

---

### Post by newb85 on 2013-06-30
> **buzzingrobot said:**
> 
(But, seriously, the security implications of using "sudo -i" or "sudo su" in Ubuntu, which allows you to run an indefinite number of commands as root until you log out, versus editing sudoers in Fedora/Slackware/OpenSuse/etc to be able to do "sudo <command> without the password prompt, seem to me pretty equivalent.)

True.  A good reason to simply instruct the use of sudo for each individual command requiring superuser privileges, or at least to instruct them to log out after they've run commands in a sudo su or sudo -i environment.  The idea behind Ubuntu's setup is to minimize the time spent running with scissors.

---

### Post by deadflowr on 2013-06-30
The difference between running sudo -i/sudo su and editing the sudoers file is that you can exit the sudo -i/sudo su commands, so they run temporary, where as the edit is for life, so to speak.

---

### Post by Dennis N on 2013-06-30
@Datzy

If you are still about, it's not clear if you ever tried to just put the font file into **~/.fonts** as was suggested. That does not require any elevated privileges.

Just open a file manager window to **~/.fonts** (create the folder if necessary) and then drag and drop the font file in there.

It's installed (for you, anyway).

Later, you can put another copy of the font file into **/usr/share/fonts** for the benefit of any other users of your machine.

---

