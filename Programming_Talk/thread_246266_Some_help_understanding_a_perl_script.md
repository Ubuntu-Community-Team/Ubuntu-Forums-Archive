---
title: "Some help understanding a perl script"
date: 2006-08-29
forum: Programming Talk
---

### Post by Rasitiln on 2006-08-29
I recently took up learning perl (its been easy so far) but when I went to play with arrays I made a program to keep two arrays one of names the other of phone numbers. I found calling the proper element in each array based on user input to be rather tedious (lots of if elsif etc). So I asked a guy on IRC to take a look at it he sent me back this which is much nicer but has no comments. I'd like to know what exactly hes doing to get this accomplished So if someone could take a look at the following code and comment it or just explain exactly whats being done it would be much appriciated. ;) 

```
#!/usr/bin/perl -w

@people = qw(Adam Jeremy Landon);

@number = qw(555-555-5555 555-555-555 555-555-5555);



print "Please enter a name\n:";

chomp ($name = <STDIN>);



my $found;

for my $i (0 .. $#people) {

    if ($name eq $people[$i]) {

        print "Name: $people[$i]\nNumber: $number[$i]\n";

        $found++;

    } 

}

unless($found) {

    print "name not found\n" 

}
```

---

### Post by Woei on 2006-08-29
> **Rasitiln said:**
> 
```
#!/usr/bin/perl -w
```
Turn on warnings. You should always run your scripts with -w when developing them, and only leave it off when distributing them.
```

@people = qw(Adam Jeremy Landon);

@number = qw(555-555-5555 555-555-555 555-555-5555);



print "Please enter a name\n:";

chomp ($name = <STDIN>);



my $found;

```
All pretty standard. chomp will chop the end off of a string, if it's a newline character. See 'perldoc -f chomp'. STDIN is an automatic variable which will return standard input. It will give you back a single line, as it's executed in scalar context (the scalar on the left hand side makes it so).
```

for my $i (0 .. $#people) {

```
For any given array @foo, $#foo will give you the last index element. So, if @foo has 5 elements, $#foo will return 4.
```

    if ($name eq $people[$i]) {

        print "Name: $people[$i]\nNumber: $number[$i]\n";

        $found++;

    } 

}

unless($found) {

    print "name not found\n" 

}
```

Basic. 'unless' is simply a fancier way of writing if (!condition).

This code works, but what you really want is a hash instead of using 2 arrays which will horribly get out of sync in a larger program. 

Also, pick up "Learning Perl" by Randal Schwartz, also known as 'the Llama book'. It's the quintessential intro to the world of Perl, written in an entertaining manner. It's a bit light if you're an experienced programmer with some awk experience. For them, 'Programming Perl', written by the creator of Perl himself is better suited.

Also, Perl comes with quite a bit of good documentation already. apt-get install perl-doc. Then start reading: 'perldoc perlintro', 'perldoc perl'.

---

