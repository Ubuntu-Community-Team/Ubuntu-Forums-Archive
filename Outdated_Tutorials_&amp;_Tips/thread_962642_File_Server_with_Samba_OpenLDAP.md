---
title: "File Server with Samba OpenLDAP"
date: 2008-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by gabrielvargas7 on 2008-10-29
We are going create a server that work like a window 2003 domain controller and active directory. 
With a files server. 


First you need to setup Samba+openLDAP Domain Controller
all the instruction are on the next link after you finish it, you can return here to continue. 
(Samba+openLDAP Domain Controller )
([http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760))

**Backup Server **

Now, after setup your Domain Controller and Active directory, that first thing is create a backup CD, if something happen

Install Remastersys Backup and create and ISO image then burn on a CD 


**Create Groups **
In this case We are going to create 2 group 
call grouppublic, groupadmin

sudo smbldap-groupadd groupoublic
sudo smbldap-groupadd groupadmin

To see your user and group,  you can you phpldapadmi.  (note; before to use phpldapadmin, you mush install itin  your server)
[http://10.10.1.15/phpldapadmin](http://10.10.1.15/phpldapadmin)

**Create Users **
Now I am going to create some user
assistant1
media 
customersupport
customerservices
support 
editor


sudo smbldap-useradd -a -m assistant1 
sudo smbldap-useradd -a -m media 
sudo smbldap-useradd -a -m customersupport
sudo smbldap-useradd -a -m customerservices
sudo smbldap-useradd -a -m support
sudo smbldap-useradd -a -m editor

-a	is a Windows User (otherwise, Posix stuff only)

 -m	creates home directory and copies /etc/skel


now we setup the passwords for each user

smbldap-passwd “username”

in my case all password is going to be the same, “password”
(Note: in windows xp, the user can change the password with Ctr+atl+Del,)
(Note: If you can not change the password from windows, change to “NO" that following line on smb.conf
   unix password sync = no 
)


sudo smbldap-passwd assistant1 
sudo smbldap-passwd media ....
do the same for all the user 
      [B]
Add User to group [/B]
now we are going to add users to the groups
for admin group, we are going to add 
	support
	customersupport
	customerservices

for public group, we add all the users
(note: this is a security, we add al ther user for the public so only people that is a user can get in to the public, not guess, or other)

smbldap-usermod -G “groupname1,groupname2...” username 

sudo smbldap-usermod -G grouppublic,groupadmin support
sudo smbldap-usermod -G grouppublic,groupadmin customersupport
sudo smbldap-usermod -G grouppublic,groupadmin customerservices

sudo smbldap-usermod -G grouppublic media
sudo smbldap-usermod -G grouppublic editor
sudo smbldap-usermod -G grouppublic assistant1

so, if you want you can refresh phpldapadmin and see all group and users


**Create Folder **
So now, we are going to create 2 folder 
public folder and admin folder on home/samba  directory

sudo mkdir  /home/samba/public
sudo mkdir  /home/samba/admin

if you need to delete a folder use
sudo rm -r pathfolder

Change Permitions 
sudo chmod 770 public
sudo chmod 770 admin



 
**Add Group to the folder **
sudo chgrp grouppublic /home/samba/public
sudo chgrp groupadmin /home/samba/admin

so with this all the user of the admin group can getting to the admin folder and
all the user for the public group can getting to to public folder 
but fist we need to add it to samba configuration

**Add Share Folder On Samba **
open smb.conf

sudo gedit  /etc/samba/smb.conf

and add this lines

# ADMIN share definition

[admin]

path = /home/samba/admin

public = yes

writeable = yes

browseable = yes

directory mode = 0700

create mode = 0660

valid users = @groupadmin



# PUBLIC share definition

[public]

path = /home/samba/public

public = yes

writeable = yes

browseable = yes

directory mode = 0700

create mode = 0660

valid users = @grouppublic


save the file, close it and stop samba and start it

sudo /etc/init.d/samba stop
sudo /etc/init.d/samba start

**Join to the Domain **
now you can join one windows computer to the domain 
go to Start->MyComputer right click and properties

go to computer tap and click on the button Change 

On Member Off change to domain and type the domain name 
in my case are 

dlinux.local 

then click Ok. type the user name and password 

so restart the computer and login with any user that we create 
(Note; The computer must have a windows XP professional)

**Get in to the Share folder **

Ok we login with one user 
we can go to run and type the \\servername\ 
in my case my server name is 
\\DC01 

and in is going to show you all the folder that are share

if user have right to the folder, you should get in.

I hope this instruction help you.

---

