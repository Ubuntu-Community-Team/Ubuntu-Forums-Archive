---
title: "PERL - creating usernames and passwords + add to /etc/sudoers"
date: 2007-08-20
forum: Programming Talk
---

### Post by misconfiguration on 2007-08-20
Ok all here is what I'm trying to accomplish. 

I'm pretty darn new to PERL, well I guess we could say programming in general. I have to create 50 + usernames on about 20 different servers, I need to initially setup the UID's, GID's and the special sudoers group.

```
#!/usr/bin/perl -w
# Script for adding new users, giving a generic passwd
# and setting them up appropriately in /etc/sudoers
# Sudoers for the DBA's
#
# ***Declare Variables***
#
        print "Please enter a username to create\n";
my $username = <STDIN>;
        chomp ($username);
#
        print "Please enter the users Real Name\n";
my $realname = <STDIN>;
        chomp ($realname);
# ***End Variables***
# Setup hashes
#
my %useraddcmd = (
        useradd => "/usr/sbin/useradd $username -g users -c \"$realname\"",
        passwd => "/sbin/passwd \"$username\"",
);

# End hashes
# Now on to add the actual username
#
        print "Do you want to create $username Y/n?\n";
$_ = <STDIN>;
chomp;
$_ = "Y" if (length($_) == 0);
# add user
if ($_ =~ /[Yy]/) {
        print "Adding user $username...\n";
        system ($useraddcmd {'useradd'});
        system ($useraddcmd {'passwd'});
}
else {
        print "Can't create user\n";
}

```

I'm having issues when trying to create the password after the user is created, I've chmoded the script and I'm invoking this VIA sudo, any ideas?

This is the output of the script so far. 
```

[misconfig@fakebox ~]$ sudo perl useradd1.pl
Password:
Please enter a username to create
misconfigtest
Please enter the users Real Name
Fake Name
Do you want to create misconfigtest Y/n?
y
Adding user misconfigtest...
sh: /sbin/passwd: No such file or directory

```

The UID is created, I'm thinking I have the wrong path for passwd, albeit when I run it VIA root or straight from the shell I have no issues. 

```
[misconfig@fakebox ~]$ cat /etc/passwd | grep misconfigtest
misconfigtest:x:10011:100:Fake Name:/home/misconfigtest:/bin/bash

```

---

### Post by christhemonkey on 2007-08-20
Your using the path /sbin/passwd in the program and 'cat'ing /etc/passwd.

So maybe you mean /etc/ instead of /sbin/?

---

### Post by misconfiguration on 2007-08-20
I cat'd /etc/passwd to show the UID was being created.

The program stalls and gives me permission denied once the command should create the passwd for $username. 

I'm actually trying to invoke passwd and take my <STDIN> for $username and make a generic password. 

Sorry for any confusion.

---

### Post by McNils on 2007-08-20
Use the -p option to useradd to set the password instead of using passwd.
useradd => "/usr/sbin/useradd $username -g users -c \"$realname\" -p ${username}123 
Sets password to username followed by 123

---

### Post by misconfiguration on 2007-08-20
Thanks for the quick solution, I was trying to find what was wrong in the environment so this issue could be better understood.

The -p option worked I just didn't want to alter any code. Thanks a lot!

---

### Post by stickboy2642 on 2007-08-21
The path to the passwd command should be: 
```
/usr/bin/passwd
```

Give that a shot.  And a quick tip:  You can use the which command to find the path to a command or application in your path.

```
root@server1:/usr/bin# which passwd
/usr/bin/passwd
```

Hope this helps!

---

### Post by misconfiguration on 2007-08-21
That's exactly what I needed Stick, thank you very much!

Sometimes you just need a fresh set of eyes.

---

### Post by misconfiguration on 2007-08-21
Ok guys I have another issue, this one is tellnig me I'm missing a right curly bracket at line 68. This happens to be the last line on the current bit of the script.

I still have a lot more to go before this is completed but can anyone see anything, I've even commented that out, I don't see anything wrong with the script ATM.

Any help is appreciated!

```
#!/usr/bin/perl -w
# Script for adding new users, giving a generic passwd
# and setting them up appropriately in /etc/sudoers
# Sudoers for the DBA's
#
# ***Declare Variables***
#
        print "Please enter a username to create\n";
	my $username = <STDIN>;
        	chomp ($username);
#
        	print "Please enter the users Real Name\n";
	my $realname = <STDIN>;
        	chomp ($realname);
# ***End Variables***
# Setup hashes
#
	my %useraddcmd = 
	(
        	useradd => "/usr/sbin/useradd $username -g users -c \"$realname\"",
	        passwd => "/sbin/passwd \"$username\"",
		groupadd => "/usr/sbin/groupadd -f dba",
	
	);

# End hashes
# Now on to add the actual username
#
      		  print "Do you want to create $username Y/n?\n";
	$_ = <STDIN>;
		chomp;
	$_ = "Y" if (length($_) == 0);
# Check to see if user exists.
#
	open PASSWD, "/etc/passwd" || die "Can't open passwd file, check permissions ($!)";

		while (<PASSWD>) {
		chomp;
		if (/^$username:/) { # $username exists
			warn "$username already exists in /etc/passwd";
	}
	}

# add user
	if ($_ =~ /[Yy]/) {
       		 print "Adding user $username...\n";
        	system ($useraddcmd {'useradd'});
        	system ($useraddcmd {'passwd'});
	}
	else {
        	print "Can't create user\n";
	}
		print "Checking to see if the group dba exists\n";
	open GROUPS, "/etc/group" || die "Can't open /etc/group ($!)";

	while (<GROUPS>) {
		chomp;
	if (/^dba:/) { # check to see if dba is there
		warn "Group exists!";
		print "Press </ENTER> to exit the script\n";
		<>;
	}
	elsif (/^dba:/ eq "") {
		system ($useraddcmd {'groupadd'});
	}
	else {  	
	
	 	warn "Some weird issue is going down, I'm stumped!";
	exit
	}		
```

---

### Post by misconfiguration on 2007-08-22
The above issue is fixed!

---

### Post by rahul_11d on 2011-08-23
> **misconfiguration said:**
> The above issue is fixed!
I am learning perl scripting and not an expert in writing big scripts. I like to bring a point here about the option "-p" with the useradd cmd.
I tried the following on redhat and believe it would be the same on ubuntu.

#!/usr/bin/perl

$USER = <STDIN>;
chomp($USER);
`useradd -d /home/$USER -s /bin/bash -p ${USER}123 -m $USER`;
print "user $USER has been added to the server and password is set to username itself";

The script ran without an error, but when I tried to take ssh it was not accepting the users password. I checked the password status of the user as root and found this.
[root@localhost perl_scripts]# passwd userxyz -S
userxyz PS 2011-08-24 0 99999 7 -1 (Password set, DES crypt.)

After changing the password of the user as root the password status changed to this
[root@localhost perl_scripts]# passwd userxyz -S
userxyz PS 2011-08-24 0 99999 7 -1 (Password set, MD5 crypt.)

This time I am able to login with the new password. I am not sure what the difference of DES and MD5 crypt. Can anyone give a clarity on this please.

---

### Post by Iowan on 2011-08-23
From the Code of Conduct:

> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

