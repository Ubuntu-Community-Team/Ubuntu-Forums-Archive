---
title: "i dissabled password but still getting a password promt"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by rishiar4 on 2012-08-02
Im using ubuntu - 10.10 . i want to remove password to login, so i went to system settings  >  User Accounts , then i clicked on password and then selected the option of 'dissabling the password for login' .
                   But now when i use 'sudo -su' its asking the password . I tried using the old password but its not working.... :(
                   plzz help me asap!!!
thanks in advance

---

### Post by NikTh on 2012-08-02
Hi , 
press Ctrl+alt+F2 and login with username & password. Can you login there ? (maybe password not needed) 

If you login successfully , then give this commands with order 
```
sudo service gdm stop
sudo passwd

``` 
it will ask you for new password , write it twice and then 
```
sudo service gdm start
``` 

Thanks

---

### Post by rishiar4 on 2012-08-02
:( its asking me a password for executing any commmand......

---

### Post by TheFu on 2012-08-02
I don't know how to solve this issue in the current state - you can't change system settings like userids without sudo, but you can't sudo since there isn't a password.

Bare with me as I think aloud.

I think you need enable a password on the account (seems you may have a chicken/egg problem there since sudo needs a password), then you can change the settings in the sudoers file to not require a password - 'man sudo' explains how.

But, you are stuck.  Did you make another login as a backup? Does it have sudo capabilities? If so, use that account.

The only other method I could guess would be to boot from other media, mount the partition with /etc and manually edit the /etc/shadow file.  I think the 2nd field will have an "!" and you want that to be an encrypted password. 

A little more searching found this solution [http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)  .  I haven't tried this method, but it should work. Set a password for your account using the method inside that link, then look up the NOPASSWD options for sudo.  The fact that it is so easy to get root without any credentials really concerns me.  Here is a more detailed step-by-step explanation [http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

However, I believe that not having a password for a login is a very dangerous thing for Linux systems. Unlike on Windows, Linux passwords protect against remote access too.  In Windows, remote access or file sharing have to be explicitly enabled. On Linux, if you or some other dependent package installs any tool capable of remote access, then you've left your PC while open ... unless you also run with very tight firewall settings.

In a multi-user OS, passwords are a way of life.

---

### Post by NikTh on 2012-08-02
> **rishiar4 said:**
> :( its asking me a password for executing any commmand......

OK, then. 

You can go through recovery mode. 
Boot from recovery mode and click "root" . 
Then write below commands with order
```
mount -o rw,remount /
passwd <username>
``` 

username = Your username. 

Reboot and see if fixed. 

Thanks

---

### Post by Paqman on 2012-08-02
> **rishiar4 said:**
> Im using ubuntu - 10.10 . i want to remove password to login, so i went to system settings  >  User Accounts , then i clicked on password and then selected the option of 'dissabling the password for login' .

Doing this doesn't disable your password, it just means you won't be prompted for it when you *first* log in. You will still need it whenever you open an admin tool or if you want to use sudo on the command line.

> 
I tried using the old password but its not working.... :(

Try it again, your password won't have changed.

---

### Post by rishiar4 on 2012-08-02
> **Paqman said:**
> Doing this doesn't disable your password, it just means you won't be prompted for it when you *first* log in. You will still need it whenever you open an admin tool or if you want to use sudo on the command line.



Try it again, your password won't have changed.

I've tried it again but its saying "Sorry, try again" .
Actually even i want to remove password  just for logging in and not for opening admin tool or for executing sudo on the command line.

---

### Post by critin on 2012-08-02
> I've tried it again but its saying "Sorry, try again" .

Check your Caps Lock.  You may be using capitals or not using capitals as required by the password.  It's happened to me.

---

### Post by Paqman on 2012-08-03
> **critin said:**
> Check your Caps Lock.

Or Number Lock, especially if you're on a laptop. Happens to me all the time.

---

### Post by Ubun2to on 2012-08-03
> **TheFu said:**
> The fact that it is so easy to get root without any credentials really concerns me.  Here is a more detailed step-by-step explanation [http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

Well, it doesn't concern me too much. I have a good root password, so even if someone steals my computer and knows how to enable logging in as root, they probably won't even be able to get into the root shell, unless they were looking over my shoulder when I set the password.
Also, that article was made for 8.04. Does it work for 12.04? I'm just curious.

---

### Post by TheFu on 2012-08-03
> **Ubun2to said:**
> Well, it doesn't concern me too much. I have a good root password, so even if someone steals my computer and knows how to enable logging in as root, they probably won't even be able to get into the root shell, unless they were looking over my shoulder when I set the password.
Also, that article was made for 8.04. Does it work for 12.04? I'm just curious.

I don't know if it still works, but I can't see why it wouldn't.  

Whatever your root password is doesn't matter using this method. It will never come up.

Physical access to any device means they can hack it, but the fact that Linux (this is a Linux thing, not ubuntu specific), has a built-in bypass is a little concerning.  The only way to fix this is to put an access password on grub, but anyone that can boot from alternate media will still easily bypass any local password.  

The only way to avoid having your data viewed or your PC booted without proper credentials is to use whole drive encryption.  This is a good idea for portable devices anyway, but the hassle in doing it on a desktop is just a little more than many people, myself included, would want.  I do encrypt my laptop completely - there is simply too much to risk otherwise between personal and corporate data.  **Whenever encryption is used, excellent backups become mandatory.**

I hope the OP found that link, followed it and read through my initial post. Sorry it was so complex and convoluted. I figured that sharing my thought process might trigger someone else's more elegant solution.

---

### Post by Ubun2to on 2012-08-03
> **TheFu said:**
> I don't know if it still works, but I can't see why it wouldn't.  

Whatever your root password is doesn't matter using this method. It will never come up.

Physical access to any device means they can hack it, but the fact that Linux (this is a Linux thing, not ubuntu specific), has a built-in bypass is a little concerning.  The only way to fix this is to put an access password on grub, but anyone that can boot from alternate media will still easily bypass any local password.  

The only way to avoid having your data viewed or your PC booted without proper credentials is to use whole drive encryption.  This is a good idea for portable devices anyway, but the hassle in doing it on a desktop is just a little more than many people, myself included, would want.  I do encrypt my laptop completely - there is simply too much to risk otherwise between personal and corporate data.  **Whenever encryption is used, excellent backups become mandatory.**

I hope the OP found that link, followed it and read through my initial post. Sorry it was so complex and convoluted. I figured that sharing my thought process might trigger someone else's more elegant solution.

If I ever drop to the root shell in Recovery Mode, I am always prompted for my root password. Maybe that's because I actually SET a root password, which is something not everybody will do.

---

