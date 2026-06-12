---
title: "how to fix home permissions so I can log in again"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by streamsanddragonflies on 2008-09-27
ok have asked this in launchpad but I want to be assured of an answer since my combined errors cost me two whole days!  I was told to use the rescue component of the alternated dvd for my ubuntu studio since I changed my /home permissions wrong and cannot log in anymore!  I was told to use the command line but no furthur instructions so my question is are the appropriate steps included on the cd and if not what are they?
I know it has to do with chmod 644...since "$HOME/.dmrc file is being ignored) must be fixed.  

Also for the future reference
for /home
 if I sudo nautilus what is the right: 

owner: is it my username? create and delete?
group: users or root? create and delete?
others: access files only?

and if I don't want other new users to see my home files can others: be left -----?

I'm tired of mucking around and making things worse!
Thanks in adv.
Note:  I figured I post here cause file permissions errors...I feel like a noob!
:confused:

---

### Post by aysiu on 2008-09-27
Boot into recovery mode (if you don't know how to do this, check out the first half of [this tutorial](http://www.psychocats.net/ubuntu/resetpassword))

Then type ```
chmod 644 /home/*username*/.dmrc
exit
``` where *username* is your username.


P.S. Please don't ever do *sudo nautilus*

More details here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by gossrock on 2008-09-27
looks like for me that the owner of my "/home/username" is "username" and the group is also "username"  the owner can "create and delete" and the group can "access" others can also access.  

the "/home" folder itself is owned by root and the group is root. root can do everything (read, write and exicute) everyone else can read and exicute

This I believe is default.

---

### Post by gossrock on 2008-09-27
(edit: pretty much ignore me since I miss read the original post. ... sorry)


If you are able to get to a "recovery mode" command line then you can use the "chown" command to change the user and groups of a file or directory and you can use "chmod" to change the permissions that the user, group and everyone else can do.  When you are in "recovery mode" you are root and you will not need to sudo.  If you were doing this from a terminal as your normal user then you would need to use sudo

chown user:group filename

so for the home directory for you user you can use

chown username:username /home/username/

to set the proper permisions for the directory you can do the following to bring it back to default:

chmod 644 /home/username/

the octal permision code of 644 is not intitive to me but it is equivalent to the following 3 commands at once

chmod u=rwx /home/username/
chmod g=rx /home/username/
chmod o=rx /home/username/

were u stands for user, g stands for group o stands for others, r stands for read w stands for write x stands for exicute.

if you don't want others to see your home directory then you can set the permisions this way

chmod o= /home/username/

where you leave it blank.  This will not affect what root can do since root can do anything.

---

### Post by aysiu on 2008-09-27
Not everything in your /home/*username* (or ~/) directory is supposed to be chmoded to 644.

In this case, it's best to just fixed the affected file (.dmrc) and change it 644.

---

### Post by streamsanddragonflies on 2008-10-04
> **gossrock said:**
> looks like for me that the owner of my "/home/username" is "username" and the group is also "username"  the owner can "create and delete" and the group can "access" others can also access.  

the "/home" folder itself is owned by root and the group is root. root can do everything (read, write and exicute) everyone else can read and exicute

This I believe is default.


Hi, after I've been away for a bit, I tried to change the permission for the .dmrc file in recovery mode, as Aysiu recommended, but my "HOME/.dmrc file is being ignored" still! when I try to login. (What is .dmrc for anyways?)  From the live CD, (in nautilus- always via gksudo! thanks Aysiu-)
and later from failsafe gnome terminal, I reset my owner, group and permissions as Gossrock said, but to no avail!  These are the error messages as I tried to login in regular and in failsafe mode:  

"...This prevented default session and language from being saved.  File should be owned by user and have 644 permissions.  User's Home directory must be owner by user and not writable by other users. 

The Gnome session manager was unable to lock the file /home/username/Ice authority.
Pls. report this as a Gnome bug.
Sometimes this error may occur if the file's directory is unwritable, you could try logging in via the failsafe session and ensuring that it is."
  
 from username&place: ls -l
my home entry was:
drwxrwxr-x  5 username users 4096 2008-09-27  13:10  home
I changed it to
drwxrwxr-x   5 root    root  4098 2008-10-03     ?    home  
 
I would like to find a link for a good 'how-to' for related file administration in linux/ubuntu...      
Here are more of my error messages when I tried to login in failsafe gnome (not terminal):
 
"Pls. contact your system administrator to resolve the following problem: 
Could not resolve the address "xml.readwrite:/home/username/.gconf" in the configuration file "etc/gconf/2/path":Failed:could not make directory '/home/username/g.conf':Permission denied

in details:
(seahorse-agent 7809)libgnomevfs-warning* unable to create ~/.gnome2directory:Permission denied could not create per-user gnome configuration directory 'home/username/.gnome2/':Permission denied."


So even though I will re-install, I have an aside question: 

Although I did the included media check of my ubuntu install dvd, I did not do a md5sum check and now I can't access any linux OS!  When I first entered the hardy desktop, the default "taskbar" and layout had less items than gutsy.  Is this  correct for hardy or could I actually have some corrupt files on my installation disk which is linked to my difficulties with fixing my login???  Just wondering since I don't have the patience to wait for another ISO download, I will count on my media being ok....

  And bear with me, lastly, to recap on folder/partition permissions:  if my /home folder is on a separate partition, are there any differences with permissions etc... that I should be aware of vs when all of ubuntu is on one partition?  Also, being /home, are the permissions to be approached differently than for my ext3 data partition? 

We shall see how it goes...

---

### Post by Francewhoa on 2009-10-08
Tutorial to fix this can be found at [http://swiss.ubuntuforums.org/showthread.php?t=976610](http://swiss.ubuntuforums.org/showthread.php?t=976610)

---

