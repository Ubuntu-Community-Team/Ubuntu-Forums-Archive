---
title: "Quick perl question, greping a file"
date: 2009-03-28
forum: Programming Talk
---

### Post by Lorenzo1985 on 2009-03-28
I'm trying to customise a script in Perl but really I'struggling.

I have very little perl experience and this is driving me mental. It should be such a simple thing to do.

I need to grep a file for DBPassword. I'm having trouble with the fourth line. I cant figure out how to do what to do.
```

if ((length $dbpass) < 1) {
   if (-e "/etc/mythtv/mysql.txt") {
   #print "mysql.txt exists \n";
   $dbpass = < help required with this bit >
   print "!!!!!! Dbpass is: $dbpass !!!!!\n";
   }
}

```

I need to do something equivelant to the following unix command:
> grep DBPassword /etc/mythtv/mysql.txt


If anyone can help I'd be really grateful

---

### Post by Eisenwinter on 2009-03-28
```

open MYSQL, "file" or die "Can't open file\n";

my @lines;

while (my $line = <MYSQL>) { push(@lines, $line); }

@lines = grep { $_ eq "dbpass"; } @lines;

my $dbpass = $lines[0];

```

Try this way.

---

### Post by cardinals_fan on 2009-03-28
```
my $name = "/etc/mythtv/mysql.txt";

open( my $R, '<', $name ) or die "couldn't open $name \n";
while ( my $line = <$R> ) {
	if ( $line =~ /DBPassword/ ) {
		my $dbpass = $line;
	}
}
close $R;
```
Something like this might be useful...

---

### Post by Lorenzo1985 on 2009-03-28
Guys thanks very much for your help. Although that still doesn't seem to be working.

I currently have the following:
```

   if (-e "/etc/mythtv/mysql.txt") {
   print "mysql.txt exists \n";
   my $pass = '';
   my $name = "/etc/mythtv/mysql.txt";

   open( my $R, '<', $name ) or die "couldn't open $name \n";
   while ( my $line = <$R> ) {
        if ( $line =~ /DBPassword/ ) {
                #my $pass = $line;
            }
   }
close $R;

   print "!!!!!! LOZ Pass is: $pass!!!!!\n";
   }

```

This allways results in:
mysql.txt exists
!!!!!! LOZ Pass is: !!!!!

I can assure you there definetly is a line with DBPassword in it.

any ideas?

---

### Post by bapoumba on 2009-03-28
Moved to PT.

---

### Post by cardinals_fan on 2009-03-28
Setting a lexical variable (my $pass = $line) will only apply within the block in which it was created.  So you need to put the 'print "!!!! LOZ Pass is: $pass!!!!!\n"' directly underneath 'my $pass = $line' inside the blocks.

---

### Post by Lorenzo1985 on 2009-03-28
> **cardinals_fan said:**
> Setting a lexical variable (my $pass = $line) will only apply within the block in which it was created.  So you need to put the 'print "!!!! LOZ Pass is: $pass!!!!!\n"' directly underneath 'my $pass = $line' inside the blocks.

Oh so how do I get the value in $pass to be global/permanent?

The print is simply there to work out if the previous code has worked. But the value is actually a required for the rest of the script.

---

### Post by Lorenzo1985 on 2009-03-28
ignore this post

---

### Post by cardinals_fan on 2009-03-28
> **Lorenzo1985 said:**
> Oh so how do I get the value in $pass to be global/permanent?

The print is simply there to work out if the previous code has worked. But the value is actually a required for the rest of the script.
Well, you can set a global variable with 'our $whatever'.

EDIT: Does the DBPassword term appear more than once in the file?

---

### Post by Eisenwinter on 2009-03-28
You can also use "my $var" outside of a function (in this case, while()), to declare a global variable.

---

### Post by cardinals_fan on 2009-03-28
```
my $name = "/etc/mythtv/mysql.txt";
my @dbpass;

open( my $R, '<', $name ) or die "couldn't open $name \n";
while ( my $line = <$R> ) {
	if ( $line =~ /DBPassword/ ) {
		unshift(@dbpass, $line);
	}
}
print @dbpass;
close $R;
```
This ought to work nicely.  All the matching lines are now in the array @dbpass.

---

### Post by Lorenzo1985 on 2009-03-28
Ahh i get it, I didn't need the "my" on the $pass = $line bit as the re-defined the variable as a local within the function rather than using the one that was defined outside the function.

Thanks allot for all your help.

---

### Post by fredscripts on 2009-03-28
Equivalent of 

```
grep DBPassword /etc/mythtv/mysql.txt
```

is

```
perl -ne' print if /DBPassword/ ' /etc/mythtv/mysql.txt
```

---

### Post by apmcd47 on 2009-03-28
> **Lorenzo1985 said:**
> I'm trying to customise a script in Perl but really I'struggling.

I have very little perl experience and this is driving me mental. It should be such a simple thing to do.

I need to grep a file for DBPassword. I'm having trouble with the fourth line. I cant figure out how to do what to do.
```

if ((length $dbpass) < 1) {
   if (-e "/etc/mythtv/mysql.txt") {
   #print "mysql.txt exists \n";
   $dbpass = < help required with this bit >
   print "!!!!!! Dbpass is: $dbpass !!!!!\n";
   }
}

```

I need to do something equivelant to the following unix command:


If anyone can help I'd be really grateful

> **Eisenwinter said:**
> ```

open MYSQL, "file" or die "Can't open file\n";

my @lines;

while (my $line = <MYSQL>) { push(@lines, $line); }

@lines = grep { $_ eq "dbpass"; } @lines;

my $dbpass = $lines[0];

```

Try this way.
Slightly more obscure approach:
[PHP]
   our $dbpass;
   if ((length $dbpass) < 1) {
   if (-e "/etc/mythtv/mysql.txt") {
   #print "mysql.txt exists \n";
# read mysql.txt into @lines
   @lines = do { my (@ARGV = "/etc/mythtv/mysql.txt"; <> };
# get the line with DBPassword
   $line = grep (/DBPassword/, @lines);
# just the password
   ($dbpass = $line ) =~ s/DBPassword:\s+//;
   print "!!!!!! Dbpass is: $dbpass !!!!!\n";
   }
}
[/PHP]

Andrew

---

### Post by slavik on 2009-03-28
use Config;

:)

---

