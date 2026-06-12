---
title: "Sharing a folder to everyone"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by kc5hwb on 2013-02-27
Hi Folks
I just installed a new HDD Raid in my Ubuntu 12.04 box, and that went fine.  But I am trying to share this drive, which is mounted at /mnt/data, to my entire network, and it is giving me errors when trying to write to the directory.

I followed the steps here:
[https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

and my folder is setup exactly as above, but I can't write it to.  I can see the folder from other windows machines in my network, and I can read the contents, but I can't create a new folder, or copy files to it.

Basically I want to share this folder openly to anyone on my network.

Thanks.

---

### Post by TheFu on 2013-02-27
Which client OSes need to read it?

What sort of data does it have?

Any programs?

---

### Post by kc5hwb on 2013-02-28
> **TheFu said:**
> Which client OSes need to read it?

What sort of data does it have?

Any programs?

I have other Ubuntu boxes, and a couple of Windows 7 boxes.

Mostly videos, but some documents too.

No programs.

---

### Post by Morbius1 on 2013-02-28
Make the following change:
> 
[share]
     comment = Ubuntu File Server Share     
path = /srv/samba/share     
browsable = yes 
    guest ok = yes     
read only = no
    [COLOR=#0000ff]**force user = nobody**[/COLOR]     
create mask = 0755
Restart samba:
```
sudo service smbd restart
```
Wait a few minutes for the network to settle down then see if you can write to the share.

If that doesn't fix it post the output of the following command:
```
ls -dl /srv/samba/share
```

---

### Post by TheFu on 2013-02-28
> **kc5hwb said:**
> I have other Ubuntu boxes, and a couple of Windows 7 boxes.
Mostly videos, but some documents too.
No programs.

Ok, perfect for samba.  Those instructions are to share files read-only. It seems to be working.
For read-write access there are 2 additional things.
* smbpasswd
* correct file/group permissions on the Linux side.
So, every userid that you want to have with read-write access will need to be in the same Linux group (/etc/groups) AND each userid will need to have a passwd set using smbpasswd.

For documents, it is often best to place those under each user's HOME and use the special [homes] section.
For media, I prefer to have 1 read-write account and all the others are read-only.  This way other members of the household don't accidentally delete everything. It is also easier to setup since you don't need to setup groups, since "other" permissions will be sufficient.

```
$ man smbpasswd 
$ man smb.conf
$ man groups 
``` will explain more - perhaps everything.

Of course, your specific needs could be more complex than my current needs.  If you are stuck, post these:
* ls -al /path/to/dir
* relevant parts of /etc/samba/smb.conf
* explain which users and groups you want AND which sort of access they should have.

Testing from Linux will tell us if it is a Win7 specific issue or not.  **smbtree **is a great tool for that.

BTW, I do not have ****any** **experience with Samba4, but plan to in the next year.

---

### Post by TheFu on 2013-02-28
So the 
    [COLOR=#0000ff]**force user = nobody**[/COLOR]
part is just scary to me.  Anyone on the network will have read-write access to the share without any real audit abilities.
I'd prefer to use **chmod g+s** to force group perms than to have everyone's access through a single account. Maybe this is overkill for a home network.

---

### Post by Morbius1 on 2013-02-28
> **TheFu said:**
> Ok, perfect for samba.  Those instructions are to share files read-only. It seems to be working.
Just the opposite is true. It's designed to allow everyone on the network to write to the share.

The problem is it will only work if you [COLOR=#0000cd]**never**[/COLOR] create a samba user ( smbpasswd ) or have one created for you ( libpam-smbpass ) because the permissions on the target folder are set to nobody:nogroup.

It's a bad HowTo and one that couldn't possibly have passed peer review. "force user = nobody" fixes it for this problem and in the future when the user wants to create a private share on another folder.

[COLOR=#0000cd]**EDIT**[/COLOR]: There is another alternative of course and that to set the folder to 777:
```
sudo chmod 777 /srv/samba/share
```

---

### Post by kc5hwb on 2013-02-28
> **TheFu said:**
> So the 
    [COLOR=#0000ff]**force user = nobody**[/COLOR]
part is just scary to me.  Anyone on the network will have read-write access to the share without any real audit abilities.
I'd prefer to use **chmod g+s** to force group perms than to have everyone's access through a single account. Maybe this is overkill for a home network.

Well to clarify, when I say "anyone on the network" I really mean any other machine that I myself am using on the network.  My wife and I live alone, and she doesn't do much on the computer except browse Facebook, so really it is just me wanting access to this share from my other Ubuntu and Windows boxes.

I have setup share in the past with using (smbpasswd ), and I should have written down how I did it, but unfortunately I didn't.  I do remember using some command similar to **CHMOD RWA+UGA** or some-such, but I can't remember exactly what I did.  Once I find the solution this time, I will make a note of it for future uses.

---

### Post by Morbius1 on 2013-02-28
> **kc5hwb said:**
> Well to clarify, when I say "anyone on the network" I really mean any other machine that I myself am using on the network.  My wife and I live alone, and she doesn't do much on the computer except browse Facebook, so really it is just me wanting access to this share from my other Ubuntu and Windows boxes..
Well, if this is just another box on the network and one you log into yourself then I would make the following changes:
Change permissions from nobody:nogroup to you:
```
sudo chown kc5hwb /srv/samba/share
```
Then change the share to this:
> [share]
     comment = Ubuntu File Server Share     
path = /srv/samba/share     
browsable = yes 
    guest ok = yes     
read only = no
    [COLOR=#0000ff]**force user = **[/COLOR][COLOR=#0000cd]**kc5hwb**[/COLOR]
create mask = 0755                      


If this isn't a true Server with a capital "S" then "force user = nobody" won't do you much good since when you are logged into the machine itself you won't be able to write to it locally as you are not "nobody"

---

### Post by kc5hwb on 2013-02-28
The **force user = nobody** worked for writing to the share from another machine.  But you are correct, I can't write to it locally.

Changing the ownership to my user account seemed to work too, but when I use my wife's Windows 7 machine, while logged in with her account, it also lets me write to it over the network.  So it is working as I want, but I am not sure why it still lets me write from my wife's account after CHOWNing the folder to my account.

---

### Post by TheFu on 2013-02-28
> **kc5hwb said:**
> The **force user = nobody** worked for writing to the share from another machine.  But you are correct, I can't write to it locally.

Changing the ownership to my user account seemed to work too, but when I use my wife's Windows 7 machine, while logged in with her account, it also lets me write to it over the network.  So it is working as I want, but I am not sure why it still lets me write from my wife's account after CHOWNing the folder to my account.

force user 

Scary.  The only thing that is scarier to me is the chmod 777 !!!!! THAT is crazy.  I take it that you've never been hacked?  Someone gets with an extremely low permission account ... er ... nobody.  Yet they can wipe every file out. Nice.

I've been hacked twice over the years, last time was 2000. I'm paranoid.  Paranoid about file permissions, network permissions and internet connections.

---

### Post by Morbius1 on 2013-02-28
> **kc5hwb said:**
> The **force user = nobody** worked for writing to the share from another machine.  But you are correct, I can't write to it locally.

Changing the ownership to my user account seemed to work too, but when I use my wife's Windows 7 machine, while logged in with her account, it also lets me write to it over the network.  So it is working as I want, but I am not sure why it still lets me write from my wife's account after CHOWNing the folder to my account.
All users on your network will be converted to [COLOR=#000000]kc5hwb[/COLOR] which is now the owner of the directory. Depending on what else you've done as far as smbpasswd and such and depending on what OS the client is using a samba client will come across one of two ways: as nobody ( the original HowTo depended on it ) or as somebody ( that's what broke the original HowTo ). After Samba allows the user access his/her identity is converted to kc5hwb when reading or writing files - for that particular share anyway.

---

