---
title: "perl Modules"
date: 2007-04-13
forum: Programming Talk
---

### Post by cascader on 2007-04-13
I am having problems getting my **[COLOR=Red]perl Modules[/COLOR]** working. As far as I can see, and after following directions posted to this forum, I have the Modules installed. At least, I have followed installation instructions and it appeared to go thru the process of installation.

The following is my test code, lifted directly from the **[COLOR=Red]CPAN[/COLOR]** site, [COLOR=SeaGreen][here]("http://search.cpan.org/dist/String-Tokenizer/lib/String/Tokenizer.pm")[/COLOR].

[INDENT] [COLOR=Navy]#!/usr/bin/perl[/COLOR]
[COLOR=Navy]use IO::File;[/COLOR]
[COLOR=Navy]use strict;[/COLOR]
[COLOR=Navy]use String::Tokenizer;[/COLOR]
[COLOR=Navy]use warnings qw(all);[/COLOR]
[COLOR=Navy]# system("clear");[/COLOR]

[COLOR=Navy]# create the tokenizer and tokenize input[/COLOR]
[COLOR=Navy]  my $tokenizer = String::Tokenizer->new();[/COLOR]
[COLOR=Navy]  [/COLOR]
[COLOR=Navy]  $tokenizer->tokenize("((5 + 5) - 10)", '()');[/COLOR]
[COLOR=Navy]  [/COLOR]
[COLOR=Navy]  # will print '(, (, 5, +, 5, ), -, 10, )'[/COLOR]
[COLOR=Navy]  print join ", " => $tokenizer->getTokens();[/COLOR]
[COLOR=Navy]  [/COLOR]
[/INDENT]And, the following is what gets sent to the term. This is done from a **[COLOR=Red]root[/COLOR]** shell.

[INDENT][COLOR=DarkSlateBlue]cpan shell -- CPAN exploration and modules installation (v1.8802)[/COLOR]
[COLOR=DarkSlateBlue]ReadLine support enabled[/COLOR]

[COLOR=DarkSlateBlue]                                                                                Can't ioctl TIOCGETP: Invalid argument[/COLOR]
[COLOR=DarkSlateBlue]Consider installing Term::ReadKey from CPAN site nearby[/COLOR]
[COLOR=DarkSlateBlue]        at [http://www.perl.com/CPAN](http://www.perl.com/CPAN)[/COLOR]
[COLOR=DarkSlateBlue]Or use[/COLOR]
[COLOR=DarkSlateBlue]        perl -MCPAN -e shell[/COLOR]
[COLOR=DarkSlateBlue]to reach CPAN. Falling back to 'stty'.[/COLOR]
[COLOR=DarkSlateBlue]        If you do not want to see this warning, set PERL_READLINE_NOWARN[/COLOR]
[COLOR=DarkSlateBlue]in your environment.[/COLOR]
[COLOR=DarkSlateBlue]cpan[1]> install Term::ReadKey[/COLOR]
[COLOR=DarkSlateBlue]CPAN: Storable loaded ok[/COLOR]
[COLOR=DarkSlateBlue]Going to read /root/.cpan/Metadata[/COLOR]
[COLOR=DarkSlateBlue]  Database was generated on Thu, 29 Mar 2007 10:09:36 GMT[/COLOR]
[COLOR=DarkSlateBlue]Going to read /root/.cpan/sources/authors/01mailrc.txt.gz[/COLOR]
[COLOR=DarkSlateBlue]CPAN: LWP::UserAgent loaded ok[/COLOR]
[COLOR=DarkSlateBlue]Fetching with LWP:[/COLOR]
[COLOR=DarkSlateBlue]  [http://www.perl.org/CPAN/modules/02packages.details.txt.gz](http://www.perl.org/CPAN/modules/02packages.details.txt.gz)[/COLOR]
[COLOR=DarkSlateBlue]Going to read /root/.cpan/sources/modules/02packages.details.txt.gz[/COLOR]
[COLOR=DarkSlateBlue]Undefined subroutine &Compress::Zlib::gzopen called at /usr/local/share/perl/5.8.8/CPAN/Tarzip.pm line 102.[/COLOR]
[COLOR=DarkSlateBlue]Going to read /root/.cpan/sources/authors/01mailrc.txt.gz[/COLOR]
[COLOR=DarkSlateBlue]Lockfile removed.[/COLOR]
[COLOR=DarkSlateBlue]Undefined subroutine &Compress::Zlib::gzopen called at /usr/local/share/perl/5.8.8/CPAN/Tarzip.pm line 102.[/COLOR]
[COLOR=DarkSlateBlue]root@cascade-desktop:~# [/COLOR]
[/INDENT]
There is something I am just not getting about this process.

**[COLOR=YellowGreen]Any feedback would be appreciated . . .[/COLOR]**

---

### Post by phossal on 2007-04-14
You downloaded this module from where? CPAN? or the *'buntu repositories?* What might you be using this for?

---

### Post by cascader on 2007-04-14
Downloaded and installed via **[COLOR=Red]cpan[/COLOR]**.

I am trying to use the '**[COLOR=Red]String::Tokenizer[/COLOR]**' perl module to tokenise Strings (lines) I have read in from a txt file. I then want the '**[COLOR=Red]Tokenizer[/COLOR]**' to print to stdout the words within those lines.

Thanks for the reply.

---

### Post by phossal on 2007-04-14
What's significant about the module? Can't you just split the words on space into an array and then print them out as you want?

For example:

```
#!/usr/bin/perl

#Open a file
$file_to_read = "file.txt";  		#Or substitute $ARGV[0]
open (INF, "< $file_to_read") or die "Can't open file: $!\n";


@file_contents = <INF>; 		#Pull all the lines.
close(INF);				#Close the file.

foreach $line (@file_contents) { 	#For each line...
	@words = split(" ",$line); 	#create a list of words.
	foreach $word (@words) { 	#For each word...
		print $word.",\n"; 	#print the word to stdout
	}
}
```

I'm working in Windows, so I can't check out the module to see if I can make it work.

---

### Post by phossal on 2007-04-14
Or you could do it by character, printing on a single line: 

```
#!/usr/bin/perl

$file_to_read = "$ARGV[0]";  		
open (INF, "< $file_to_read") or die "Can't open file: $!\n";


@file_contents = <INF>; 		
close(INF);				         

foreach $line (@file_contents) { 	
	chomp($line);
	$line =~ s/\s+//ig;

	@words = split(//, $line);
	foreach $word (@words) {
		print $word.", "; 	
	}
}
```

There are cleaner ways to do this, but this is simple enough that you could modify it however you need?

---

### Post by cascader on 2007-04-16
Thanks very much for the reply and the code, **[COLOR=Red]phossal[/COLOR]**.

I have about **[COLOR=Green]three[/COLOR]** projects going at once at the moment - got to earn my keep ! As soon as I can I will test and possibly implement your code, or some variation thereof. Of course, if I do use any code from other ppl I will credit it accordingly.

Still pretty frustrated by this module implementation problem I just don't seem to be getting. Whenever I can I try not to use modules when coding in perl, then I don't have to worry whether it'll work if run on another 'puter. But this code is for my use only (so far) so at least I could know that the software will run on my machine.

---

