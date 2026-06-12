---
title: "Need help with a perl script"
date: 2006-12-03
forum: Programming Talk
---

### Post by shingalated on 2006-12-03
I'm trying to make a perl script that can be used to add new users for my ftp server.  Could anyone tell me why the script isn't working?

#!/usr/bin/perl -w
print ("Enter Username:");
$name = <STDIN>;
print ("Enter Password:");
$pass = <STDIN>;
print ("Retype Password:");
$pass2 = <STDIN>;
system ("/usr/sbin/useradd -G ftp $name");
open (PASSWD, "| passwd");
print PASSWD "$pass";
print PASSWD "$pass2";
close(PASSWD);

When I try to run it this is what I get:

chris@Linus:/media/CHRIS' USB$ sudo perl New\ User.pl 
Enter Username:mark
Enter Password:password
Retype Password:password
Enter new UNIX password: Retype new UNIX password: Sorry, passwords do not match
passwd: Authentication information cannot be recovered
passwd: password unchanged

---

### Post by shingalated on 2006-12-03
yeah, and it's still not working.

---

### Post by jayemef on 2006-12-04
I believe you need to let the passwd utility know to read from stdin. Try
```

if ($pass == $pass2) {
    system ("echo $pass | passwd --stdin $name");
}

```

---

### Post by shingalated on 2006-12-04
my version of passwd does not support stdin

---

### Post by bradleyd on 2006-12-06
I think the best thing to do is let passwd ask for the passwd itself. Maybe not what you were looking for, but try this.

#!/usr/bin/perl -w
print ("Enter Username:");
$name = <STDIN>;

system ("sudo /usr/sbin/useradd -G ftp $name");

system('sudo passwd $name');

I did find a perl script from "wicked cool perl scripts" that has everything and the kitchen sink. go here [http://www.nostarch.com/frameset.php?startat=wcps]("http://www.nostarch.com/frameset.php?startat=wcps")
download the code from book. It is under chapter6 directory. The script is called add_user.pl.
I hope that helps.

---

### Post by DaveBorealis on 2006-12-06
> **shingalated said:**
> I'm trying to make a perl script that can be used to add new users for my ftp server.

Hello,

If you don't mind my asking, I'm curious if you're just playing around at writing a script, or are you trying to do something specific with your script that useradd doesn't do?  (I can't see a difference.)

Best regards,
Dave

---

### Post by johnnymac on 2006-12-07
Only suggestion I have is that you issue a:

```

chomp($variable_from_stdin);

```

After every time you grab STDIN from user.  Otherwise you get the extra newline character.

---

### Post by bradleyd on 2006-12-07
> **johnnymac said:**
> Only suggestion I have is that you issue a:

```

chomp($variable_from_stdin);

```

After every time you grab STDIN from user.  Otherwise you get the extra newline character.

you are correct. I have been playing with Python lately and forgot chomp!

#!/usr/bin/perl -w
print ("Enter Username:");
$name = <STDIN>;
chomp($name);
system ("sudo /usr/sbin/useradd -G ftp $name");
system("sudo passwd $name");

---

