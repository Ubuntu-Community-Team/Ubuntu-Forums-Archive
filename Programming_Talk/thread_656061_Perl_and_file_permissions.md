---
title: "Perl and file permissions"
date: 2008-01-02
forum: Programming Talk
---

### Post by wislon32 on 2008-01-02
As a newcomer to Perl under Linux (as opposed to Windows), I'm still flummoxed at times as to who / what requires permissions.  The following small script (df.pl) fails with message such as  '/home permission denied' or '$dir is not a directory'.  The script has permissions to execute, and I would have expected Perl to have them too:

```
#!/usr/bin/perl -w
use strict;
use warnings;
use Filesys::DiskSpace;

# file system /home or /dev/sda5

my $dir = '/home';

my ($fs_type, $fs_desc, $used, $avail, $fused, $favail) = df $dir;

# calculate free space in %
my $df_free = (($avail) / ($avail+$used)) * 100.0;

# display message;
my $out = sprintf("Disk space on $dir == %0.2fn",$df_free);print $out;

```

I've tried double and single quotes and backtick, all to no avail.  I thought at first it was the IDE I was using (geany), but the same thing happens in a command box

What am I doing wrong?

---

### Post by meatpan on 2008-01-02
After recreating your issue, I don't think there is a problem with the permissions.

As far as I can tell, Perl's Filesys::DiskSpace module appears to be old, and does not support the ext3 filesystem which is standard with ubuntu.   I determined this after inspecting the file: /usr/share/perl5/Filesys/DiskSpace.pm.  I find it hard to believe that a module available for download out of the debian/ubuntu repository would not support an ext3 fs, so please be cautious with my suggestions.

I made your script behave as expected by switching to the Filesys::Df module, and changing some of the code.  I also corrected the newline and added a % symbol in the output (I thought the output message was misleading and needed to specify that it was a percentage).

Here it is:

```

#!/usr/bin/perl -w
use strict;
use warnings;
use Filesys::Df;

# file system /home or /dev/sda5

my $dir = '/home';

my $fs_info = df($dir, 1);
my $avail = $fs_info->{bavail};
my $used = $fs_info->{used};

# calculate free space in %
my $df_free = (($avail) / ($avail+$used)) * 100.0;

# display message;
my $out = sprintf("Disk space on $dir == %0.2f%%\n",$df_free);print $out;


```

Does this help?

---

### Post by wislon32 on 2008-01-03
Yes and No!  Thank you for the assistance, but I have one minor problem here, and it's more general in that the Df Module is not on my machine. 

 I've worked out how to download the module from CPAN, (using cpan) but I'm having problems with the install.  They fail with:
```
mkdir /usr/local/lib/perl: Permission denied at /usr/share/perl/5.8/ExtUtils/Install.pm line 112
```
which is the target directory: the line in effect reads:
```
mkdir /usr/local/lib/perl 
```
and fails with permission denied.  The perl subfolder does not exist. I can create it manually using chmod and mkdir, but perl still does not have permissions to create it.  How do I give perl permissions to carry on with the make?

---

### Post by wislon32 on 2008-01-03
Simple when you know how.  Start cpan with sudo:
```
sudo cpan
``` and away we go.

Many thanks to Llamakc at
Simple when you know how.  Start cpan with sudo:
```
sudo cpan
``` and away we go.

**[COLOR="Red"]Many thanks to Llamakc[/COLOR]** at
[http://ubuntuforums.org/showthread.php?t=641414&highlight=perl+permissions"]http://ubuntuforums.org/showthread.php?t=641414&highlight=perl+permissions](http://ubuntuforums.org/showthread.php?t=641414&highlight=perl+permissions"]http://ubuntuforums.org/showthread.php?t=641414&highlight=perl+permissions)
for the obvious solution.

---

### Post by evymetal on 2008-01-03
> **wislon32 said:**
> 
```

my $dir = '/home';

```


(I haven't used either of these modules so this may not be useful)

Does it work if you sudo the command to run the script?

If so, does it work if /home is replaced with "~" (i.e. /home/[username] ? Don't know about the security for perl's df, but you wouldn't be able to write to /home from a standard user.

---

### Post by meatpan on 2008-01-03
The perl modules that you want to install are relatively common.  As such, a stable version is likely to exist in the debian/ubuntu repositories.  Installing via the repository managers is nice because ubuntu will automatically manage dependencies, updates, and security vulnerability patches.  CPAN is still useful, especially if you need a relatively recent package, but you don't get the ubuntu support.

Browse through the repository via:
```

sudu apt-get update
sudo apt-cache search filesys | grep -i perl

```

These two look like potential matches (fetched via default package lists for ubuntu 7.04 on 1/3/2008):
libfilesys-df-perl - Module to obtain filesystem disk space information
libfilesys-diskspace-perl - fetch filesystem size and usage information from Perl

Check to see if you have them installed:
```

 dpkg -l libfilesys-diskspace-perl
 dpkg -l libfilesys-df-perl

```

Install if necessary:
```

sudo apt-get install libfilesys-diskspace-perl libfilesys-df-perl

```

Like I said above, this is simply an alternative method to semi-manual install with CPAN.

---

