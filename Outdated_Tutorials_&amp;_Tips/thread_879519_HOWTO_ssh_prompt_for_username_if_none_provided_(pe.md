---
title: "HOWTO: ssh prompt for username if none provided (perl script)"
date: 2008-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by HeWhoE on 2008-08-04
The perl script that follows will intercept your ssh command and check it to see whether you've provided a username followed by an *at* symbol (@), like so.

$ ssh username@address

If a username is provided, the script will call ssh as usual.

If only the address is provided (no ampersand is found in the command argument), then the script will prompt you for your username.

1.  Edit the .bashrc file with your choice of editor. In the following examples, I use vi.
```
$ vi ~/.bashrc
```

2.  Add the following line to the file.
```
export PATH=$HOME/bin:$PATH
```

3.  Update your settings:
```
$ source ~/.bashrc
```

4.  Create a bin directory in your home directory.
```
$ mkdir ~/bin
```

5.  Create a file named ssh in your bin directory.
```
$ vi ~/bin/ssh
```

6.  Put the following in the new file.
```

#!/usr/bin/perl

my $user_at_address = $ARGV[0];
my @u_a = split(/@/, $user_at_address);

if (defined $u_a[1])
{
    if ( $^O == 'linux' )
    {
        exec ("/usr/bin/ssh $u_a[0]\@$u_a[1]");
    }
    if ( $^O == 'solaris' )
    {
        exec ("/usr/local/bin/ssh $u_a[0]\@$u_a[1]");
    }
}
else
{
    print "Enter your username: ";
    my $username = <STDIN>;
    chomp ( $username );
    if ( $^O == 'linux' )
    {
        exec ("/usr/bin/ssh $username\@$u_a[0]");
    }
    if ( $^O == 'solaris' )
    {
        exec ("/usr/local/bin/ssh $username\@$u_a[0]");
    }
}

```

7.  Save the file.

8.  Make the file executable.
```
$ chmod +x ~/bin/ssh
```

---

### Post by HeWhoE on 2008-08-15
I use the same script for sftp.

1.  Create the script to call sftp.
```
$ vi ~/bin/sftp
```

2.  Add the following to the script.
```

#!/usr/bin/perl

my $user_at_address = $ARGV[0];
my @u_a = split(/@/, $user_at_address);

if (defined $u_a[1])
{
    if ( $^O == 'linux' )
    {
        exec ("/usr/bin/sftp $u_a[0]\@$u_a[1]");
    }
    if ( $^O == 'solaris' )
    {
        exec ("/usr/local/bin/sftp $u_a[0]\@$u_a[1]");
    }
}
else
{
    print "Enter your username: ";
    my $username = <STDIN>;
    chomp ( $username );
    if ( $^O == 'linux' )
    {
        exec ("/usr/bin/sftp $username\@$u_a[0]");
    }
    if ( $^O == 'solaris' )
    {
        exec ("/usr/local/bin/sftp $username\@$u_a[0]");
    }
}

```

3.  Make the script executable.
```
$ chmod +x ~/bin/sftp
```

---

### Post by bhp0528 on 2009-07-08
Very nice. Thanks for the scripts ... three years later.

---

### Post by wideyes on 2010-01-04
Thanks for these! I did lots of searching on this subject, and these seemed the best-written solutions!

---

