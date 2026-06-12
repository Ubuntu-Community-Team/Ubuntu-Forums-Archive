---
title: "Possible to hide files in Samba to certain users?"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by xolo80 on 2012-10-31
Hello,
 I have set up my home server (Ubuntu), and I have set up a samba shared folder publicly. But, what I'm trying to figure out is how to set up a personal folder for each user they can only see and have access to.

For example, have 2 folders one named "Mom" and "Dad". When Mom logs on to Windows 7, she will automatically see a drive that I map with both the Shared folder (for all users), and the one titled Mom. She will not see nor have access to my Dads. 

I've been trying to research something like this for the past few days, but I'm so new to Linux I'm finding myself a bit over my head, so any help is appreciated. Thank you in advance

---

### Post by redmk2 on 2012-11-01
> **xolo80 said:**
> Hello,
 I have set up my home server (Ubuntu), and I have set up a samba shared folder publicly. But, what I'm trying to figure out is how to set up a personal folder for each user they can only see and have access to.

For example, have 2 folders one named "Mom" and "Dad". When Mom logs on to Windows 7, she will automatically see a drive that I map with both the Shared folder (for all users), and the one titled Mom. She will not see nor have access to my Dads. 

I've been trying to research something like this for the past few days, but I'm so new to Linux I'm finding myself a bit over my head, so any help is appreciated. Thank you in advance

What you are looking for is called a [homes] share in Samba.  You only need to configure the [homes] share once.  As a user logs in, their personal [homes] share is configured.  It can be non-browsable (hidden).  To access it each user could use: *[COLOR="DarkSlateGray"]**nautilus smb://SERVER/username**[/COLOR]* to find the share.  More info available [&btnG=Go!#hl=en&sclient=psy-ab&q=samba+[homes]+share&oq=samba+[homes]+share&gs_l=serp.3..0j0i30l3.40466.41794.0.43101.6.6.0.0.0.0.145.843.0j6.6.0.les%3B..0.0...1c.1.kJ22CF7GnE0&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=b834a242fa531d3a&bpcl=37189454&biw=1192&bih=665"]**_[COLOR="Blue"]here[/COLOR]_**]("https://www.google.com/search?q=samba+[homes).

---

### Post by xolo80 on 2012-11-01
> **redmk2 said:**
> What you are looking for is called a [homes] share in Samba.  You only need to configure the [homes] share once.  As a user logs in, their personal [homes] share is configured.  It can be non-browsable (hidden).  To access it each user could use: *[COLOR="DarkSlateGray"]**nautilus smb://SERVER/username**[/COLOR]* to find the share.  More info available [&btnG=Go!#hl=en&sclient=psy-ab&q=samba+[homes]+share&oq=samba+[homes]+share&gs_l=serp.3..0j0i30l3.40466.41794.0.43101.6.6.0.0.0.0.145.843.0j6.6.0.les%3B..0.0...1c.1.kJ22CF7GnE0&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=b834a242fa531d3a&bpcl=37189454&biw=1192&bih=665"]**_[COLOR="Blue"]here[/COLOR]_**]("https://www.google.com/search?q=samba+[homes).

Thank you, I wrote my own smb.conf file, following tutorials and I bet that is how I lost the [homes] file. I will try to work on this, I appreciate your help

---

### Post by redmk2 on 2012-11-01
> **xolo80 said:**
> Thank you, I wrote my own smb.conf file, following tutorials and I bet that is how I lost the [homes] file. I will try to work on this, I appreciate your help

Here is the section on the [homes] share from the original smb.conf file```
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

```

---

### Post by xolo80 on 2012-11-01
Thank you, so if I'm understanding this correctly I will set up the homes share like you were discussing.

Then, I restart the services and from the terminal I will use the commands

    useradd -m <username>
    passwd <username>
    smbpasswd -a <same username>

And finally, that will set up the user to log into \servername\homes    where they will be asked for user/password verification?

---

### Post by redmk2 on 2012-11-01
> **xolo80 said:**
> Thank you, so if I'm understanding this correctly I will set up the homes share like you were discussing.

Then, I restart the services and from the terminal I will use the commands

    useradd -m <username>
    passwd <username>
    smbpasswd -a <same username>

And finally, that will set up the user to log into \servername\homes    where they will be asked for user/password verification?

I can't vouch for the method of adding the Linux user, but it looks correct.  There are multiple ways of adding a user from the CLI.  The Samba user is correct.  If all goes well the user can map a drive to this [COLOR="Red"]**//SERVER**[/COLOR]**[COLOR="Blue"]/user_name[/COLOR]**.  The slashes used are dependant upon whether the user is using a Win or Linux client.  Samba will understand both ways I believe.  The [homes] share is really a redirection to the logged in users home dir. This means you will never map a the share directly to [homes].  You map the share to the users login name.  That's what this means ```
# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S
```

On the other hand if you are using a Windows machine should map the share using the Windows GUI.  You will not be able to browse to the share unless you make all of the shares visible.

---

### Post by xolo80 on 2012-11-01
I am trying to map it to a Windows client. I will try it later tonight when I get home. Thank you again for your help.

---

### Post by xolo80 on 2012-11-02
Well I've been trying to map it. I have it successfully (maybe?) logging into my profile. For example I map it to \\server\username from the map network drive in Windows. 

But, when I do that it takes me inside a username folder where I have things listed like cache, .ssh, and .vim folders along with other files I'm assuming have to do with my profile, because theres no Share or homes folder inside

---

### Post by redmk2 on 2012-11-02
> **xolo80 said:**
> Well I've been trying to map it. I have it successfully (maybe?) logging into my profile. For example I map it to \\server\username from the map network drive in Windows. 

But, when I do that it takes me inside a username folder where I have things listed like cache, .ssh, and .vim folders along with other files I'm assuming have to do with my profile, because theres no Share or homes folder inside

Those sound like the hidden files in the users home directory.  The file starts with a dot (.).  They are user specific and setup various applications.

There is no share folder or homes folder you are at the root directory of the user (i.e.  /home/<user_name>.  Create a file or directory in that share and then look at it from the Ubuntu machine.  You will find the directory you just created at [COLOR="DarkGreen"]*/home/<user_name>/new_dir*[/COLOR].  If you just create a file it would be [COLOR="Blue"]*/home/<user_name>/new_file*[/COLOR].

---

### Post by xolo80 on 2012-11-02
> **redmk2 said:**
> Those sound like the hidden files in the users home directory.  The file starts with a dot (.).  They are user specific and setup various applications.

There is no share folder or homes folder you are at the root directory of the user (i.e.  /home/<user_name>.  Create a file or directory in that share and then look at it from the Ubuntu machine.  You will find the directory you just created at [COLOR="DarkGreen"]*/home/<user_name>/new_dir*[/COLOR].  If you just create a file it would be [COLOR="Blue"]*/home/<user_name>/new_file*[/COLOR].

I think that's why I'm confused because I can map to my shares file, and I thought (from documentation I'm reading) that when I log into my server a homes folder is automatically made?

---

### Post by xolo80 on 2012-11-02
I've pasted my config file below, I'm thinking I'm doing something wrong in this thing because I've put it together myself based on tutorials. Please let me know if I did, if you don't mind


[global]
	workgroup = DANGERSERVER
	netbios name = Danger
	Server String = Samba Server
	name resolve order = hosts lmhosts
	printcap name = cups
	security = user
	printing = cups
	printcap name = cups
	show add printer wizard = yes
	load printers = yes
[homes]
	comment = Home Directories
	#path = \\server\username
	browseable = no
	create mask = 0600
	directory mask = 0700 
	#Make sure that only "username" can connect to \\server\ustername
	valid users = %S
	writable = yes
[share]
	path = /srv/samba/sharedfiles
	comment = Share for all users
	public = yes
	guest ok = yes
	read only = no
	writeable = yes
	browseable = yes

[Music]
	path = /srv/samba/sharedfiles/Music
	comment = Music for all users
	public = yes
	guest ok = yes
	read only = no
	writeable = yes
	browseable = yes

[Programs]
	path = /srv/samba/sharedfiles/Programs
	comment = Various Programs & Executables
	public = yes
	guest ok = yes
	read only = no
	writeable = yes
	browseable = yes

[Movies]
	path = /srv/samba/sharedfiles/Movies
	comment = Movies for all users
	public = yes
	guest ok = yes
	writeable = yes
	browseable = yes

[printers]
	comment = All Printers
	browseable = yes
	path = /var/temp
	printable = yes
	public = yes
	guest ok = yes
	writable = no
	create mode = 0700
	use client driver = yes

#[print$]
#	comment = Printer Drivers Download Area
#	path = /var/lib/samba/printers
#	browsable = yes
#	read only = yes
#	guest ok = yes
#	write list = @samba-printers, root

---

### Post by redmk2 on 2012-11-02
> **xolo80 said:**
> I think that's why I'm confused because I can map to my shares file, and I thought (from documentation I'm reading) that when I log into my server a homes folder is automatically made? 
All the documentation for the smb.conf parameters is available [**[COLOR="Blue"]here[/COLOR]**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") or at ```
man smb.conf
```

The *homes* share does not create a homes folder to share.  The *homes* share automagically shares the users /home/$USER folder.  Just as you have seen it.  As you also saw there is no path to a folder declared. Samba, on the fly knows to use the users path to their home directory. To summarize: No HOMES folder is created.  Instead, the [homes] share shares the users home directory.> 

I'm thinking I'm doing something wrong in this thing because I've put it together myself based on tutorials. Please let me know if I did, if you don't mind


It all looks okay to me.  I think you are over thinking the whole thing.  Remember that a [homes] share is NOT the same as a home directory.  It shares the EXISTING home directory.  What makes it unique is that the one [homes] share will work with all users (Joe, John, Tony, Jane, Lois, etc.).

---

### Post by xolo80 on 2012-11-03
Ok once again thank you, it looks like I am getting into my /home/%u file correctly. It's just when I follow that path in Linux I have those files inside that I told you about.

I was under the assumption that I'd get a brand new directory that is empty, similar to how my /srv/samba directory looked. I had to make new folders inside of there to share. I'm just going to play around with these setting now that I know I have them correct. Again Thank you very much

---

