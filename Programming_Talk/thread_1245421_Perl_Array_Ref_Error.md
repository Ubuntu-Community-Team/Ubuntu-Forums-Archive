---
title: "Perl Array Ref Error"
date: 2009-08-20
forum: Programming Talk
---

### Post by dellwood on 2009-08-20
Hi, 

In my program, the user specifies how many commands they want to run followed by the actual commands they will run in a config-type file, as shown below:

```

number     3
command1   adduser, 123.456.78.890, linux
command2   checkuser, 123.456.78.890, linux
command3   deluser, 123.456.78.890, linux

```

It is then read in using **Config::Simple** ([http://search.cpan.org/~sherzodr/Config-Simple-4.59/Simple.pm#MULTIPLE_VALUES](http://search.cpan.org/~sherzodr/Config-Simple-4.59/Simple.pm#MULTIPLE_VALUES)), and a hash is created holding the values like *"command1"=> [ "adduser", "123.456.78.890", "linux" ]*...at least in theory ](*,)

I'm getting the following error concerning the code ( shown below the error ):

```

Can't use string ("command1") as an ARRAY ref while "strict refs" in use at ConfigReader.pm line 196, <FH> line 32.

```

Code:
```

my $commandNumber = $Config{'number'};
my %commandHash = ();
my $x = 1;

#Create command hash
while( $x <= $commandNumber ) {
    @{"command$x"} = $cfg->param("command$x");
    $commandHash{$x} = @{"command$x"}  ;
    $x++;
}

```

I have googled the subject, but am having a hard time seeing how the other solutions fit in my scenario.

All help is appreciated.

-Josh

---

### Post by unutbu on 2009-08-20
Add this to the top of your script:
```
no strict "refs";	    
```

PS. Are you sure you want to do this? Why not just avoid the problem altogether?

```

while( $x <= $commandNumber ) {
    $commandHash{$x} = $cfg->param("command$x")
    $x++;
}
```

---

### Post by dellwood on 2009-08-20
Thanks, that cleared up the error, but it seems that it isn't correctly storing a) the values in the array and b) the arrays in the hash, as when I type *print "Command1: $commandHash{command1}\n";* it shows 'Command1: ' without anything after it.

---

### Post by unutbu on 2009-08-20
```
while( $x <= $commandNumber ) {
    @{"command$x"} = $cfg->param("command$x");
    $commandHash{$x} = \@{"command$x"};
    $x++;
}

print "Command1: ",join(",",@{"command1"}),"\n";
print "Command1: ",join(",",@{$commandHash{1}}),"\n";

```

---

### Post by dellwood on 2009-08-20
I figured it out.  I ended up using your shorter method for the while statement, and then to print it I did $commandHash{1}[0] $commandHash{1}[1], etc.  

Thanks for the help :)

-Josh

---

