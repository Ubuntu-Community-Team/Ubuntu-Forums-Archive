---
title: "Share folder on local network with ubuntu"
date: 2021-12-16
forum: New to Ubuntu
---

### Post by mkdahan on 2021-12-16
I try to share folder on ubuntu and connect to it through windows, currently know how to do it by these steps: [https://linuxhint.com/share-folder-on-local-network-with-ubuntu/](https://linuxhint.com/share-folder-on-local-network-with-ubuntu/)
but, since I have a lot of computers I need to do it on, I want to build a bash file that will do it automatically, I don't find on internet a way to share the folder with all the following checked by a Command Line Interface.
These are the steps I want to do using CLI:

[LIST=1]
[*]Choose the “Local Network Share” selection from the displayed list items: 
[https://i.stack.imgur.com/s78nw.png](https://i.stack.imgur.com/s78nw.png)
[*]check the boxes displayed in the following attached screenshot and then click on the “Create Share” button:

[https://i.stack.imgur.com/KGrF6.png](https://i.stack.imgur.com/KGrF6.png)
[/LIST]
Lets say I want to share the following folder: /home/mkdahan/Desktop/Shared_Folder
which terminal instruction can make this? No matter what thanks a lot!
I tried to built a bash script that will do that for me (based on [https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)! ):
```

sudo apt-get update
sudo apt-get install samba
sudo apt-get install smbclient


sudo cp /etc/samba/smb.conf ~/Desktop/backup




if sudo grep -Fxq '[Shared_Folder]'  /etc/samba/smb.conf
then
    # code if found
    echo the '[Shared_Folder] >> /etc/samba/smb.conf' exist at samba.conf
else


    echo [Shared_Folder] | sudo tee -a /etc/samba/smb.conf
    echo path =  /home/mkdahan/Desktop/Shared_Folder | sudo tee -a /etc/samba/smb.conf
    echo valid users =  mkdahan | sudo tee -a /etc/samba/smb.conf
    echo read only = no | sudo tee -a /etc/samba/smb.conf
fi


# Restart the samba
sudo service smbd restart
# check your smb.conf for any syntax errors
testparm


```

but, when i open the properties of this folder using the GUI of the ubuntu I see that this folder is still un-shared: [folder_unshared]("https://i.stack.imgur.com/4Bv99.png")
if I open /etc/samba/smb.conf, i see the new lines appear:
```

[Shared_Folder]
    path = /home/mkdahan/Desktop/Shared_Folder
    read only = No
    valid users = mkdahan





```
means after the reset of the samba it should be shared according to the smb.conf file.
few questions:

[LIST=1]
[*]Does the GUI aligned to what i execute using CLI (Does the sharing should be updated at the GUI also)?
[*]Do I miss something at my steps?
[/LIST]

---

### Post by Morbius1 on 2021-12-16
> but, when i open the properties of this folder using the GUI of the ubuntu I see that this folder is still un-shared: folder_unshared
Two different methods of creating a samba share.

Classic Shares have share definitions in /etc/samba/smb.conf.

UserShares ( created through the file manager ) have share definitions in /var/lib/samba/usershares.

You don't want to create a samba share of a given folder using both methods at the same time or samba will get confused.

---

### Post by TheFu on 2021-12-16
A few months ago, we were troubleshooting an issue that was caused because the user had setup a user-share in their HOME directory.  My advice is to NEVER, EVER, EVER, share any storage with other users from any HOME directory.  It caused all sorts of issues and 5 extremely experienced forum users weren't able to figure out the issue.
To share user HOME directories with that useid from other systems, there is a simple smb.conf config setup that works well. It will let each different userid access their HOME directory based on the connection credentials used. The stanza to be added to the bottom of the /etc/samba/smb.conf file is:

```
[homes]
  comment = Home Directories
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```
Add those lines and restart the smbd daemon.  May need to run **smbpasswd -a {username}** to create a new samba-userid on the system. This should match the Linux userid exactly.

---

### Post by DuckHook on 2021-12-17
Please don't post large graphics to the forums. This is very problematic for helpers with low speeds, who are on limited data plans, or are viewing from smartphones or small screens.

If you must post resource-intensive images, please post them as attachments using the paperclip icon in the *Adv Reply* toolbar.

For similar reasons, please do not use nonstandard fonts and styles in your posts, which can render poorly or illegibly in some browsers and on mobile devices.

---

### Post by ActionParsnip on 2021-12-17
You could share using NFS instead. Might be easier

---

### Post by Holger_Gehrke on 2021-12-17
You might want to take a look at the 'net' command from the package samba-common-bin, especially the 'usershare' sub-command. Basically you have to allow it in the '[GLOBAL]' section of the smb.conf, create a directory where the data about user shares is stored by the server, configure that directory in smb.conf, and then any user with write access to that directory can do 'net add usershare sharename path' to share path as sharename. There's more to it (much more, both to usershares and to the 'net' command) and you can find a lot of the details in the manual page (man 8 net).

Holger

---

### Post by Morbius1 on 2021-12-18
I actually think it would be better creating a share definition in smb.conf itself since it allows more adjustments but it will not create a "share" emblem on the shared folder in the file manager.

If that is a requirement then Holger_Gehrke's answer is a viable option.

I have a box here that I can use as an example:

I will create a guest accessible share of the Public folder in the user's home folder in a terminal with this command:
```
net usershare add Public /home/tester/Public "put comment here" everyone:f guest_ok=yes
```
I can verify the share creation with this command:
```
net usershare info --long
```
> tester@vub2004:~$ net usershare add Public /home/tester/Public "put comment here" everyone:f guest_ok=yes
tester@vub2004:~$ net usershare info --long
[Public]
path=/home/tester/Public
comment=put comment here
usershare_acl=Everyone:F,
guest_ok=y
It will in fact create a share emblem:
[ATTACH=CONFIG]289646[/ATTACH]

The only difference between doing this in a terminal and how the file manager does it is the file manager then prompts the user for authorization to change permissions of the shared folder to allow guest write access. You can accomplish the same thing I suppose with this:
```
net usershare add Public /home/tester/Public "put comment here" everyone:f guest_ok=yes && chmod 777 /home/tester/Public
```

For obvious reasons you wouldn't want to do this on the home folder itself ( /home/tester in this example ) but for all the subfolders it will work. That is what the samba usershare was designed to do. Allow an ordinary user the ability to create a samba share of anything he owns which pretty much limits him to the contents of his home folder..

---

