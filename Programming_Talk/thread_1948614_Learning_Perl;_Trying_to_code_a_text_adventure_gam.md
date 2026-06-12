---
title: "Learning Perl; Trying to code a text adventure game"
date: 2012-03-28
forum: Programming Talk
---

### Post by Rhemat on 2012-03-28
Heya all,

I'm trying to expand my knowledge of Perl, and I figured that coding a text adventure game would be the easiest way to do it.  The first thing I am tackling is being able to "look" at the environment.  I do know how to call up values of both arrays, and hashes, but I am still puzzled on how to keep the location of the player current, rather than statically coded in.  Here are the two ways I've tried it so far:

With hashes:
```

#!/usr/bin/perl -w

#Define world HASH
@world = (
	[ "", "", "" ],
	[ "town", "Town", "You see several run-down buildings, and a few citizens meandering about.\n" ],
	[ "forest", "Ancient Forest", "You are surrounded by tall, ancient trees.\n" ],
);


action();

#sub for getting player action

sub action {
	print "What would you like to do? ";
	$act = <STDIN>;
	if ($act eq "look") {
		look();
		print $look;
		print "\n";		
		};
	};

#sub for getting look info
	#take contents of %world, put into $look
	#print look

sub look {
	$look = $world[1][2];
	print $look;
	};

```

With Arrays:
```

#!/usr/bin/perl -w

#Define world HASH
%world = (
	"town" => "Town\nYou see several run-down buildings, and a few citizens meandering about.\n",
	"forest" => "Ancient Forest\n You are surrounded by tall, ancient trees.\n",
);

$look = "";

action();

#sub for getting player action

sub action {
	print "What would you like to do? ";
	$act = <STDIN>;
	print "\n";
	if ($act eq "look") {
		look();
		print $look;
		print "\n";
		};
	};

#sub for getting look info
	#take contents of %world, put into $look
	#print look

sub look {
	$look = $world{"town"};
	};

```

Also, this code does not print the contents of $look for some reason, so I'm obviously doing something wrong there.  Any hints?

Thanks in advance.

---

### Post by nutrapi on 2012-03-29
> **Rhemat said:**
> Heya all,

I'm trying to expand my knowledge of Perl, and I figured that coding a text adventure game would be the easiest way to do it.  The first thing I am tackling is being able to "look" at the environment.  I do know how to call up values of both arrays, and hashes, but I am still puzzled on how to keep the location of the player current, rather than statically coded in.  Here are the two ways I've tried it so far:

With hashes:
```

#!/usr/bin/perl -w

#Define world HASH
@world = (
	[ "", "", "" ],
	[ "town", "Town", "You see several run-down buildings, and a few citizens meandering about.\n" ],
	[ "forest", "Ancient Forest", "You are surrounded by tall, ancient trees.\n" ],
);


action();

#sub for getting player action

sub action {
	print "What would you like to do? ";
	$act = <STDIN>;
	if ($act eq "look") {
		look();
		print $look;
		print "\n";		
		};
	};

#sub for getting look info
	#take contents of %world, put into $look
	#print look

sub look {
	$look = $world[1][2];
	print $look;
	};

```

With Arrays:
```

#!/usr/bin/perl -w

#Define world HASH
%world = (
	"town" => "Town\nYou see several run-down buildings, and a few citizens meandering about.\n",
	"forest" => "Ancient Forest\n You are surrounded by tall, ancient trees.\n",
);

$look = "";

action();

#sub for getting player action

sub action {
	print "What would you like to do? ";
	$act = <STDIN>;
	print "\n";
	if ($act eq "look") {
		look();
		print $look;
		print "\n";
		};
	};

#sub for getting look info
	#take contents of %world, put into $look
	#print look

sub look {
	$look = $world{"town"};
	};

```

Also, this code does not print the contents of $look for some reason, so I'm obviously doing something wrong there.  Any hints?

Thanks in advance.

you have to chomp that CR.

---

### Post by nutrapi on 2012-03-29
You have your hashes and arrays mixed up as well...

chomp:
chomp(my $act = <STDIN>);

[http://perldoc.perl.org/functions/chomp.html](http://perldoc.perl.org/functions/chomp.html)

Might want to take a look at this book:
[http://www.learning-perl.com/](http://www.learning-perl.com/)

It's a great beginner's resource and is quite inexpensive in its ebook form. DRM-free ebook available in multiple formats.

---

### Post by Rhemat on 2012-03-29
> **nutrapi said:**
> You have your hashes and arrays mixed up as well...

chomp:
chomp(my $act = <STDIN>);

[http://perldoc.perl.org/functions/chomp.html](http://perldoc.perl.org/functions/chomp.html)

Might want to take a look at this book:
[http://www.learning-perl.com/](http://www.learning-perl.com/)

It's a great beginner's resource and is quite inexpensive in its ebook form. DRM-free ebook available in multiple formats.


Thank you, I had forgotten all about chomp.  I am also taking a look at the website, and seeing some interesting articles.

---

