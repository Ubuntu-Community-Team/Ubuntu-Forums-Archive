---
title: "Help with perl hashes"
date: 2010-08-17
forum: Programming Talk
---

### Post by nebu on 2010-08-17
I am trying the following 

```


my %x;

while(<INPUT>)
{
$x{$_} = {
name => 'test',
list => []
};
}

for my $someValue(keys %x)
{
my %y = {val1=>"sasda",val2=>"sjxj");
push(@{$x{$someValue}{list}},%y);
}


```

nothing is being added into the list if i do this?
what is going wrong?

---

### Post by trent.josephsen on 2010-08-17
For starters, you have a mismatched { with ) on line 13.

Also, your code doesn't open INPUT anywhere, so either you're reading a filehandle that doesn't exist (which will probably be interpreted as a bareword name-of-file, if my Perl-fu is correct) or you're holding out on us.  Show complete code, please.

---

### Post by nebu on 2010-08-17
you asked for it!! :P

i am using this code to process the output of exuberant ctags to get a basic layout of the code in xml.... the implementation of the thing to output is not coming!

the input file can be obtained by just going into a perl project folder and typing

```
ctags -R -x * > ctags_ouput.proc
```

here is the actual perl code
```

#!/usr/bin/env perl

#read perl codes easily

use strict;

open IN_FILE, "<", "ctags_output.proc";

my @lines = <IN_FILE>;
close(IN_FILE);

my %project;

#Process CTAGS file
for my $i (@lines)
{
        #Process package names
        if($i =~ /([a-zA-Z0-9:]*)\s+package\s+([\d]*)\s+([a-zA-z\/.0-9]*)\s+package\s+([.]*)/)
        {
                my $packageName = $1;
                my $lineNo = $2;
                my $fileName = $3;
                my $parent = "";
                my $count = 0;
                print STDOUT "Got package $packageName @ $lineNo in $fileName\n";
                for my $key (keys %project)
                {
                        if($packageName =~ /^$key/)
                        {
                                if(length($parent)<length($key))
                                {
                                        $parent = $key;
                                }
                        }
                }
                print STDOUT "Found parent of $packageName -> $parent\n";
                if(exists $project{$packageName})
                {}
                else
                {
                        $project{$packageName} = {
                                'path'         => "$fileName",
                                'lineNo'       => "$lineNo",
                                'super'        => "$parent",
                                'subrountines' => []
                        };
                }
                next;
        }
        #Process Function names
        if($i =~ /([a-zA-Z0-9:_]*)\s+subroutine\s+([\d]*)\s+([a-zA-z\/.0-9]*)\s+sub\s+([.]*)/)
        {
                my $subName = $1;
                my $lineNo = $2;
                my $fileName = $3;
                for my $key (keys %project)
                {
                        if($fileName eq $project{$key}{'path'})
                        {
                                print STDOUT "Got subroutine $subName of $key @ $lineNo in $fileName\n";
                                my %sub = {'name'=>"$subName",'nu'=>"$lineNo"};
                                push($project{$key}{'subroutines'},{%sub});
                        }
                }
        }
}

#Write output to XML file
open OUT_FILE, "+>", "project_parsed.xml";

use XML::DOM;
my $doc = XML::DOM::Document->new();
my $decl = $doc->createXMLDecl('1.0');
print OUT_FILE $decl->toString; 

my $xml = $doc->createElement("project");
for my $i (keys %project)
{
        my $package = $doc->createElement("package");
        $package->setAttribute('name',$i);
        $package->setAttribute('path',$project{$i}{'path'});
        $package->setAttribute('lineNo',$project{$i}{'lineNo'});
        my $len = scalar @{$project{$i}{'subroutines'}};
        for(my $j=0;$j<$len;$j++)
        {
                my $subroutine = $doc->createElement("subroutine");
                print STDOUT $project{$i}{'subroutine'}[$j]{'name'};
                $subroutine->setAttribute('name',$project{$i}{'subroutine'}[$j]{'name'});
                $subroutine->setAttribute('lineNo',$project{$i}{'subroutine'}[$j]{'nu'});
                $package->appendChild($subroutine);
        }
        $xml->appendChild($package);
}

print OUT_FILE $xml->toString;

close OUT_FILE;

if(!($ARGV[0] eq 'silent'))
{
        print map { "$_ =>\n\tpath=$project{$_}{'path'}\n\tlineNo=$project{$_}{'lineNo'}\n\tsuper=$project{$_}{'super'}\n\tsubroutines=join('',$project{$_}{'subroutines'})\n\n\n" } keys %project;
}


```


edit:
i forgot to mention that the error is in and around line 62

---

### Post by dv3500ea on 2010-08-17
Line 62: ```
push($project{$key}{'subroutines'},{%sub});
```
looks a bit off with using '{%sub}'. 

Try rewriting line 62:
```
push($project{$key}{'subroutines'},\%sub);
```

---

### Post by nebu on 2010-08-17
i tried that... originally line 62 read something like....
```

push(@{$project{$key}{'subroutines'}},\%sub);

```

but then i got the error
```

Can't use an undefined value as an ARRAY reference at ./parseCTAGS.pl line 83.

```

so i assumed the thing wasnt being pushed into the array correctly!

---

### Post by trent.josephsen on 2010-08-18
> **nebu said:**
> i tried that... originally line 62 read something like....
```

push(@{$project{$key}{'subroutines'}},\%sub);

```

but then i got the error
```

Can't use an undefined value as an ARRAY reference at ./parseCTAGS.pl line 83.

```

so i assumed the thing wasnt being pushed into the array correctly!
So why did you change the first element to a scalar?  You can't push anything into a scalar.

You're using some pretty odd conventions here -- really long lines are one problem, but I'm also wondering about
```
                if(exists $project{$packageName})
                {}
                else
```
Why not just 'unless ($project{packageName})'?  Better yet, combine it with the assignment:
```
				$project{$packageName} ||= { ...
```

You're also doing a lot of print STDOUT, which seems a little odd.

Line 45 misspells 'subroutines', which is probably a pretty big problem.

```
my %sub = {'name'=>"$subName",'nu'=>"$lineNo"};
```
(line 61) seems unusual for a few reasons: notably, you're assigning a hashref to a hash; you're using double-quote interpolation when none is needed; and you're not taking advantage of auto-quoting of barewords in front of the =>.

Your indexing is odd, but I can't quite put my finger on why.

This little snippet rather has me wondering:
```
        my $len = scalar @{$project{$i}{'subroutines'}};
        for(my $j=0;$j<$len;$j++)
        {
                my $subroutine = $doc->createElement("subroutine");
                print STDOUT $project{$i}{'subroutine'}[$j]{'name'};
                $subroutine->setAttribute('name',$project{$i}{'subroutine'}[$j]{'name'});
                $subroutine->setAttribute('lineNo',$project{$i}{'subroutine'}[$j]{'nu'});
                $package->appendChild($subroutine);
        }
```
Why not 'foreach (@{$project{$i}{'subroutines'}}) { ... }'?

You use 'for my $key (keys %hash)' a lot; are you unaware of 'while (my ($key, $value) = each %hash)'?  Hiding the hash access within the loop control prevents having to chain your indexing all over the place like in the previous code.

I'm also wondering why you didn't use warnings as well as strict.

I apologize for somewhat playing the Style Police, but these are some pretty heavy things for me to wade through before I can actually help you out.  Honestly, I'm not sure what of the several things I mentioned here are problems and which ones are just unusual.  I can't test it right now, but I'll try it later.  In the meantime you could try fixing some of the issues I've already pointed out.

Tip:  Use Data::Dumper to inspect the contents of complex data structures and make sure they contain what you think they do.

---

### Post by shawnhcorey on 2010-08-18
Change:

```
my %sub = {'name'=>"$subName",'nu'=>"$lineNo"};
```

to:
```
my %sub = ( name => $subName, nu => $lineNo );
```

---

### Post by nebu on 2010-08-18
**@trent:** ya.... im kind of used to c/c++ code.... so i try to keep my perl as close to c/c++ code as possible! i have had experience that it does not sit very well with perl developers.... so just bear with me

**@shawnhcorey**: ya... i did that now i know that the hash %project is getting the required data
i made ur change and made the following change where i was accessing the data.... the dump produces the right output but when i try to access the data... i get null values!
eg---- $_{'name'}

 ```
       foreach (@{$project{$i}{'subroutines'}})
        {   
                my $subroutine = $doc->createElement("subroutine");
                use Data::Dumper;
                print "$_---->";
                print Dumper($_);
                print "$_{'name'},$_{'nu'}\n";
                $subroutine->setAttribute('name',$_{'name'});
                $subroutine->setAttribute('lineNo',$_{'nu'});
                $package->appendChild($subroutine);
        }
```

---

### Post by gmargo on 2010-08-18
The problem is almost entirely due to mixing up the spelling of the key 'subroutines'.  Here's a minimal unified diff to your code that makes it work:

```

--- proc1.pl    2010-08-18 08:30:16.000000000 -0700
+++ proc3.pl    2010-08-18 09:24:08.000000000 -0700
@@ -42,7 +42,7 @@
                                 'path'         => "$fileName",
                                 'lineNo'       => "$lineNo",
                                 'super'        => "$parent",
-                                'subrountines' => []
+                                'subroutines'  => []
                         };
                 }
                 next;
@@ -58,8 +58,8 @@
                         if($fileName eq $project{$key}{'path'})
                         {
                                 print STDOUT "Got subroutine $subName of $key @ $lineNo in $fileName\n";
-                                my %sub = {'name'=>"$subName",'nu'=>"$lineNo"};
-                                push($project{$key}{'subroutines'},{%sub});
+                                my $sub = {'name'=>"$subName",'nu'=>"$lineNo"};
+                                push @{$project{$key}{'subroutines'}}, $sub;
                         }
                 }
         }
@@ -84,9 +84,9 @@
         for(my $j=0;$j<$len;$j++)
         {
                 my $subroutine = $doc->createElement("subroutine");
-                print STDOUT $project{$i}{'subroutine'}[$j]{'name'};
-                $subroutine->setAttribute('name',$project{$i}{'subroutine'}[$j]{'name'});
-                $subroutine->setAttribute('lineNo',$project{$i}{'subroutine'}[$j]{'nu'});
+                print STDOUT $project{$i}->{'subroutines'}[$j]{'name'};
+                $subroutine->setAttribute('name',$project{$i}{'subroutines'}[$j]{'name'});
+                $subroutine->setAttribute('lineNo',$project{$i}{'subroutines'}[$j]{'nu'});
                 $package->appendChild($subroutine);
         }
         $xml->appendChild($package);

```

---

### Post by nebu on 2010-08-18
hey.... i fixed most of the changes.... here is the latest code


the spelling thing was a humongous mistake... i fixed it up.... "cleaned up" the code a little bit.... however the thing still does not work! (check my previous post for exactly where)
 
```

#!/usr/bin/env perl

use strict;

#use warnings;

open IN_FILE, "<",  "ctags_output.proc";
open LOG_STD, "+>", "parseCTAGS.log";

my @lines = <IN_FILE>;
close(IN_FILE);

my $projectFolder = $ARGV[0];

my %project;

#Process CTAGS file
for my $i (@lines) {

    #Process package names
    if ( $i =~ /([a-zA-Z0-9:]*)\s+package\s+([\d]*)\s+([a-zA-z\/.0-9]*)\s+package\s+([.]*)/ )
    {
        my $packageName = $1;
        my $lineNo      = $2;
        my $fileName    = $3;
        my $parent      = "";
        my $count       = 0;
        print LOG_STD "Got package $packageName @ $lineNo in $fileName\n";
        for my $key ( keys %project ) {
            if ( $packageName =~ /^$key/ ) {
                if ( length($parent) < length($key) ) {
                    $parent = $key;
                }
            }
        }
        print LOG_STD "Found parent of $packageName -> $parent\n";
        unless ( $project{$packageName} ) {
            $project{$packageName} = {
                'path'         => "$fileName",
                'lineNo'       => "$lineNo",
                'super'        => "$parent",
                'subrountines' => ()
            };
        }
        next;
    }

    #Process Function names
    if ( $i =~ /([a-zA-Z0-9:_]*)\s+subroutine\s+([\d]*)\s+([a-zA-z\/.0-9]*)\s+sub\s+([.]*)/ )
    {
        my $subName  = $1;
        my $lineNo   = $2;
        my $fileName = $3;
        for my $key ( keys %project ) {
            if ( $fileName eq $project{$key}{'path'} ) {
                print LOG_STD
                  "Got subroutine $subName of $key @ $lineNo in $fileName\n";
                my %sub = ( 'name', "$subName", 'nu', "$lineNo" );
                push( @{ $project{$key}{'subroutines'} }, \%sub );

                #use Data::Dumper;
                #print "func[$subName, $lineNo, $key, $fileName] -->\n";
                #print Dumper(@{$project{$key}{'subroutines'}});
                #print "\n\n\n";

            }
        }
    }
}

#Write output to XML file
open OUT_FILE, "+>", "project_parsed.xml";

use XML::DOM;
my $doc  = XML::DOM::Document->new();
my $decl = $doc->createXMLDecl('1.0');
print OUT_FILE $decl->toString;

my $xml = $doc->createElement("project");
for my $i ( keys %project ) {
    #Write package details
    my $package = $doc->createElement("package");
    $package->setAttribute( 'name',   $i );
    $package->setAttribute( 'path',   $project{$i}{'path'} );
    $package->setAttribute( 'lineNo', $project{$i}{'lineNo'} );
    open PERL_FILE, "<", "$projectFolder/$project{$i}{'path'}";
    my @file = <PERL_FILE>;

    #Write uses
    for my $line (@file) {
        if ( $line =~ /^use\s+([A-Za-z0-9:]*)[.]*;/ ) {
            print LOG_STD "\tUsing $1 in $i\n";
            my $calls = $doc->createElement("calls");
            $calls->setAttribute( "name", $1 );
            $package->appendChild($calls);
        }
    }
    close(PERL_FILE);

    #Write subroutines
    foreach ( @{ $project{$i}{'subroutines'} } ) {
        my $subroutine = $doc->createElement("subroutine");
        use Data::Dumper;
        print "$_---->";
        print Dumper($_);
        print "$_{'name'},$_{'nu'}\n";
        $subroutine->setAttribute( 'name',   $_{'name'} );
        $subroutine->setAttribute( 'lineNo', $_{'nu'} );
        $package->appendChild($subroutine);
    }
    $xml->appendChild($package);
}

print OUT_FILE $xml->toString;

close OUT_FILE;
close LOG_STD;

```

---

### Post by gmargo on 2010-08-18
You're not dereferencing enough.  Following is a patch.  And please, always turn on the warnings!  And check your "open"s for failure.

```

--- proc4.pl    2010-08-18 09:53:02.000000000 -0700
+++ proc5.pl    2010-08-18 10:06:41.000000000 -0700
@@ -2,7 +2,7 @@
 
 use strict;
 
-#use warnings;
+use warnings;
 
 open IN_FILE, "<",  "ctags_output.proc";
 open LOG_STD, "+>", "parseCTAGS.log";
@@ -10,7 +10,7 @@
 my @lines = <IN_FILE>;
 close(IN_FILE);
 
-my $projectFolder = $ARGV[0];
+my $projectFolder = $ARGV[0] || ".";
 
 my %project;
 
@@ -39,7 +39,7 @@
                 'path'         => "$fileName",
                 'lineNo'       => "$lineNo",
                 'super'        => "$parent",
-                'subrountines' => ()
+                'subroutines'  => [],
             };
         }
         next;
@@ -83,7 +83,8 @@
     $package->setAttribute( 'name',   $i );
     $package->setAttribute( 'path',   $project{$i}{'path'} );
     $package->setAttribute( 'lineNo', $project{$i}{'lineNo'} );
-    open PERL_FILE, "<", "$projectFolder/$project{$i}{'path'}";
+    if (open PERL_FILE, "<", "$projectFolder/$project{$i}{'path'}")
+    {
     my @file = <PERL_FILE>;
 
     #Write uses
@@ -96,6 +97,7 @@
         }
     }
     close(PERL_FILE);
+    }
 
     #Write subroutines
     foreach ( @{ $project{$i}{'subroutines'} } ) {
@@ -103,9 +105,9 @@
         use Data::Dumper;
         print "$_---->";
         print Dumper($_);
-        print "$_{'name'},$_{'nu'}\n";
-        $subroutine->setAttribute( 'name',   $_{'name'} );
-        $subroutine->setAttribute( 'lineNo', $_{'nu'} );
+        print "$_->{'name'},$_->{'nu'}\n";
+        $subroutine->setAttribute( 'name',   $_->{'name'} );
+        $subroutine->setAttribute( 'lineNo', $_->{'nu'} );
         $package->appendChild($subroutine);
     }
     $xml->appendChild($package);

```

---

### Post by trent.josephsen on 2010-08-18
> **nebu said:**
> **@trent:** ya.... im kind of used to c/c++ code.... so i try to keep my perl as close to c/c++ code as possible! i have had experience that it does not sit very well with perl developers.... so just bear with me
Well, I'm used to English, but I don't try to make my Perl code look like English!  It's all very well to say "just bear with me", but when you're asking for help, you'll get the best help when your code is readable to the people who can help.

That beside the point, did you even read my entire post?  I pointed out two issues that were definitely mistakes and not stylistic in nature.  In fact, I just noticed that if you had followed my advice about avoiding multiple levels of indexing, another mistake could have been avoided.  But you're apparently too happy copy-n-pasting $project{$i}{'subroutine'}[$j] to consider replacing it with $_.  One of the other mistakes still hasn't been fixed.  And you've introduced a new one (at the same line, no less).

(Edit:  gmargo's patch took care of that.)

---

### Post by gmargo on 2010-08-18
I think there may be an error in your main input loop.  Trying to process both packages and subroutines in the same loop relies on an expectation of sorted input, since the subroutine processing relys on a package definition.  I did a test with two loops, processing the input just for packages first, then subroutines, and the output was different, slightly larger for the project I used for testing.

---

### Post by nebu on 2010-08-19
@gmargo: i assume the iput comes from a sorted ctags file!

@trent: i shall look into the problems.... thnaks for the input! :D

thanks everyone.... the problem is solved

---

