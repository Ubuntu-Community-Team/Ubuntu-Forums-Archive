---
title: "Locking accounts"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by dotchristopher on 2012-08-22
Hi All,

Sorry to have to ask but I don't seem to be able to figure the behaviour from the documentation or anywhere else on line.

Basically, I have a few user accounts which are really only designed to run services- one runs (exclusively) a vmware version of windows, another runs (exclusively) a vmware machine of another operating system. The final one is for generic authenticated but effectively guest account access to various services- (moving downloaded files into their correct folders, screen sharing, opening up write access to samba/afp shares, etc). Let's call this last user account, to which many people have access in reality "user", the others vmware. One last account exists to provide access to git repositories and [the excellent] gitlab. It's called coderman.

"User" has to be a user (not system) account. Currently it's using lshell to restrict the powers of the user when working on VNC. Root gives it a desktop with the shell escape:
```
su user -c "vncsever" 
```
at boot. 

Similarly, with vmware and coderman, it's actually root, though cron or whatever, who starts the services and then drops them to the specified user privileges.

Thing is, I'm a little worried, what with all that exists on the box (my docs, pics, other's backups, etc) that these lesser used accounts could be abused to gain access to the system. If I locked the accounts, what would happen? Would root still be able to simply 'attach' the uid and guid to the process, whilst ensuring that no-one could log in, or obtain a shell, on the system?

If not, are there any sensible suggestions please? I'd hate to have sit down with the machine for a week and come up with a long list of commands that (say) vmware actually runs and add them to the permitted lshell configuration.

Thanks all for your help and suggestions in advance!

---

### Post by Lisiano on 2012-08-22
Am I understanding this correctly? You set up multiple accounts which you use for services which all get started by root but get dropped to the service account level? If so, you got nothing to worry about because there is no way to normally achieve root after dropping permissions. BUT there was an exploit that allowed someone to get a root prompt, don't remember when it was fixed (Was back in the the 2.6 kernel days). Anyway, as long as you make sure the applications are working under the service account you designate to them, then the applications ONLY have access to whatever that account has access to. By default, all accounts can see inside everyones home folder(s). If you don't want that, then you will need to set the home folders to 750(640). You can do this by issuing this command.
```
chmod -R u=rwX,g=rX,o= $HOME
```
What it does is, set all files under your home directory to the following permissions:
Owner - Can write, read and execute
Group - Can read and execute
Others - Can't do anything

Note on the options if you want to modify it a bit:
[LIST]
[*]1st argument
[LIST]
[*]u - User/Owner
[*]g - Group
[*]o - Others
[/LIST]
[*]2nd argument
[LIST]
[*]+ - add the following bits
[*]- - remove the following bits
[*]= - set to the following bits
[/LIST]
[*]3rd argument
[LIST]
[*]r - Read
[*]w - Write
[*]x - Execute/view directory
[*]X - Check the current execute bit and set to on in folders and keep the old bit on files
[/LIST]
[/LIST]

[COLOR="Red"]**Warning:**[/COLOR] Do ***_[COLOR="Red"]not[/COLOR]_*** run that command on /home directly. ***_[COLOR="Red"]Only[/COLOR]_*** run this command on the folders inside /home. Using the command directly on /home will result in that it will be ***_[COLOR="Red"]impossible[/COLOR]_*** to gain access to /home without using root.
If you do mess it up. Plese run this
```
sudo chmod u=rwX,g=rX,o=rX /home
```
You may also run it if you wish to revert back to letting others see what is in your home folder. Just substitute /home to $HOME or just type out where it is, eg: /home/user, also append -R so it will do it recursively.

---

