---
title: "Script to parse info between tags"
date: 2009-09-16
forum: Programming Talk
---

### Post by MrBoxes on 2009-09-16
Hi, I'm trying to write a script to parse the info between tags.
I don't care what I need to use to do this (awk, sed, python) I'd like to try python but have no idea how to do that.

Here is the file I want to parse
```

<?xml version="1.0" encoding="UTF-8"?>
<feed version="0.3" xmlns="http://purl.org/atom/ns#">
<title>yo - woof 'thisthing' for some.guy@aplace.com</title>
<tagline>word stuff junk 'thisthing' label</tagline>
<fullcount>10</fullcount>
<link rel="alternate" href="http://somewebsite.com/stuff" type="text/html" />
<modified>2009-09-16T17:45:58Z</modified>
<entry>
<title>Hey from Someone [(123) 456-789]</title>
<summary>why you what are you doing? -- Some stuff https://www.some.com/stuff</summary>
<link rel="alternate" href="http://mail.some.com/mail?account_id=some.guy%40woof.com&amp;message_id=123423418&amp;view=conv&amp;extsrc=atom" type="text/html" />
<modified>2009-09-14T17:41:04Z</modified>
<issued>2009-09-14T17:41:04Z</issued>
<id>tag:some.stuff.com,2004:1313813366812914712</id>
<author>
<name>Someone(who)</name>
<email>123456789.123456789.XPKeexjS2T@stuff.junk.place.com</email>
</author>
</entry>
</feed>

```

output I want to have
```

Hey from Someone [(123) 456-789]
Message: why you what are you doing?

```

the first line is from one of the title tags and the 2nd line is from the summary tag.

What I tried was this
```
cat "/home/somedude/Documents/sourcefile"|awk '/<title>/','/<\/title>/' '/home/somedude/Documents/outputfile"
```
to try and get just what was between the title tags to start with and the output I got was just my source file unchanged. =/ All help is welcome.

---

### Post by scragar on 2009-09-16
parser.pl```
use XML::Simple;
my $xml = XMLin(shift);
print $xml->{entry}->{title}, "\n", $xml->{entry}->{summary}, "\n";
```
Usage:```
perl parser.pl /home/somedude/Documents/sourcefile
```

Edit: more advanced version to handle multiple entry elements:
```
use XML::Simple;
my $xml = XMLin(shift, forcearray => 1);

foreach ( @{$xml->{entry}} ) {
  print $_->{title}->[0];
  print "\n"; // line separator, just new line here.
  print $_->{summary}->[0];
  print "\n\n";// separator between entries, two lines is my default.
}
```

---

### Post by MrBoxes on 2009-09-16
```

somedude@betabox:~$ perl /home/somedude/Documents/parser.pl /home/somedude/Documents/sourcefile
Can't locate XML/Simple.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/mrboxes/Documents/parser.pl line 1.
BEGIN failed--compilation aborted at /home/somedudes/Documents/parser.pl line 1.
somedude@betabox:~$ 

```
I r noob. Sorry could you possibly help me not be a scrub by telling me how to fix this error?

Do i just need to install XML simple?

---

### Post by scragar on 2009-09-16
Sorry, install the library.
```
sudo apt-get install libxml-simple-perl
```

---

### Post by MrBoxes on 2009-09-16
>.> It's telling me my file does not exist.

```
File does not exist: /home/somedude/Documents/outputfile at parser.pl line 2
```

Sorry I require so much help

Oh wait... I think I can do this one lol

---

### Post by lswb on 2009-09-16
cat yourfile|sed -n  's/<title>\(.*\)<\/title>\|<summary>\(.*\)<\/summary>/\1\2/p'

---

### Post by scragar on 2009-09-16
The argument is your input file, not the output file. I should have made that clear:
```
perl parser.pl inputfile [color=red]>outputfile[/color]
```The last part can be left off, it's completely optional, without it the stripped content will be displayed on screen rather than recorded to file.

---

### Post by scragar on 2009-09-16
> **lswb said:**
> cat yourfile|sed -n  's/<title>\(.*\)<\/title>\|<summary>\(.*\)<\/summary>/\1\2/p'

I tried that, but he has <title> tags outside of his entry tags, which he wants to ignore. That's why I wrote the simple perl version to avoid the problems.

---

### Post by MrBoxes on 2009-09-16
> **scragar said:**
> The argument is your input file, not the output file. I should have made that clear:
```
perl parser.pl inputfile [color=red]>outputfile[/color]
```The last part can be left off, it's completely optional, without it the stripped content will be displayed on screen rather than recorded to file.

Both of them just keep giving me file does not exist error =/

Yea the file is exactly where its supposed to be so idk.

Scratch that I'm a scrub.... It works (keep forgetting case sensitive) >.<

---

### Post by MrBoxes on 2009-09-16
Amazing! they both actually work exactly like I wanted them.

Here's my output
```

Hey from Someone [(123) 456-789]
why you what are you doing? -- Some stuff https://www.some.com/stuff

```

Is there a way I could turn that output into

```

Hey from Someone [(123) 456-789]
why you what are you doing?

```

Basically remove the " -- Some stuff https://www.some.com/stuff" from the message because that part is always there very annoying.

Thank's for the help.

Also I was wondering why "<title>yo - woof 'thisthing' for [email]some.guy@aplace.com[/email]</title>" isn't in the output (I don't want it to be there, but I'm unsure as to why it's not.)

---

### Post by scragar on 2009-09-16
```
  print $_->{summary}->[0];
```
Remove that and in it's place put:
```
$_->{summary}->[0] =~ m/^(.*)--/;
print $1;
```

---

### Post by MrBoxes on 2009-09-16
> **scragar said:**
> ```
  print $_->{summary}->[0];
```
Remove that and in it's place put:
```
$_->{summary}->[0] =~ m/^(.*)--/;
print $1;
```

```

someone@betabox:~/Documents$ perl parser.pl /home/someone/Documents/GValert >/home/someone/Documents/outputfile2
Bareword found where operator expected at parser.pl line 6, near "// line"
    (Missing operator before line?)
Bareword found where operator expected at parser.pl line 8, near "// separator"
    (Missing operator before separator?)
syntax error at parser.pl line 6, near "// line separator"
syntax error at parser.pl line 8, near "// separator between "
No such class default at parser.pl line 8, near "is my default"
Execution of parser.pl aborted due to compilation errors.

```

Those are the error's I got.

when i take out what you had after // on the 2 lines you had notes in your code it runs.

---

### Post by scragar on 2009-09-16
That's really strange, it works perfectly for me:
```

[scragar @ sbox working in ~/Desktop/test]
**$** cat parser
use XML::Simple;

my $xml = XMLin(shift, forcearray => 1);


foreach ( @{$xml->{entry}} ) {
  print $_->{title}->[0];
  print "\n";
  $_->{summary}->[0] =~ m/^(.*)--/;
  print $1;
  print "\n\n";
}
[scragar @ sbox working in ~/Desktop/test]
**$** perl parser source
Hey from Someone [(123) 456-789]
why you what are you doing? 

[scragar @ sbox working in ~/Desktop/test]
**$** 
```

---

### Post by MrBoxes on 2009-09-16
the code you originally pasted.
```

use XML::Simple;
my $xml = XMLin(shift, forcearray => 1);

foreach ( @{$xml->{entry}} ) {
  print $_->{title}->[0];
  print "\n"; // line separator, just new line here.
  print $_->{summary}->[0];
  print "\n\n";// separator between entries, two lines is my default.
}

```

what I had to change it to.
```

use XML::Simple;
my $xml = XMLin(shift, forcearray => 1);

foreach ( @{$xml->{entry}} ) {
  print $_->{title}->[0];
  print "\n";
  print $_->{summary}->[0];
  print "\n\n";
}

```

I see in your post your code has it without the "//ect" it was my fault for not seeing the error before trying the code.

Any ways now it does exactly what I wanted it to do =) thank you once again. You've solved my problems for a while but I'd like to actually learn how write scripts in pearl, python, or awk, sed ect. I'm mostly interested in pearl and python though. Do you have any suggested reading?

---

### Post by scragar on 2009-09-16
Erm, not really, I'd learn python though, perl is an amazing powerfull and versitile language, but as you've probably seen it's not exactly the easiest to write and understand, simple things can cause errors that don't make sense,(there are 4 different methods of having an array(a normal array, a reference to an array, a hashed array, a reference to a hashed array), which causes a lot of confusion).

Personally I learn more by taking what other people have written and attempting to understand it, once you understand most of a project try to clone the project, see how far you can get, what trips you up etc, then google it.
If you do decide to learn perl(why?) you should remember to check CPAN.org for any libraries you're having difficulty with.

---

### Post by MrBoxes on 2009-09-16
> **scragar said:**
> Erm, not really, I'd learn python though, perl is an amazing powerfull and versitile language, but as you've probably seen it's not exactly the easiest to write and understand, simple things can cause errors that don't make sense,(there are 4 different methods of having an array(a normal array, a reference to an array, a hashed array, a reference to a hashed array), which causes a lot of confusion).

Personally I learn more by taking what other people have written and attempting to understand it, once you understand most of a project try to clone the project, see how far you can get, what trips you up etc, then google it.
If you do decide to learn perl(why?) you should remember to check CPAN.org for any libraries you're having difficulty with.

I learn better by taking what other people write too. Though pearl looks a bit complicated to do that (for me I guess) without a reference.

---

### Post by scragar on 2009-09-16
> **MrBoxes said:**
> I learn better by taking what other people write too. Though pearl looks a bit complicated to do that (for me I guess) without a reference.

It's a matter of finding a well documented project, personally I found checkgmail to be a fairly easy one to understand for some things(testing which libraries are available and throwing errors or warning based on what we need and what just makes it easier to use being the most important), it was also a big hand to me learning how to display notification icons and mess about with GTK. I also found myself looking through the source code to some libraries for clues on how to best approach tasks without loading whole libraries.

---

### Post by ghostdog74 on 2009-09-16
```

awk '/<entry>/{f=1}
f&&/<title>|<summary>/{
    gsub(/<title>|<summary>/,"")
    gsub(/<\/title>|<\/summary>/,"")
    gsub(/--.*/,"")
    print
}' file

```
output
```

# ./shell.sh
Hey from Someone [(123) 456-789]
why you what are you doing?

```

---

