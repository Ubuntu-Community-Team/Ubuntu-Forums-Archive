---
title: "Perl: Printing Text From HTML"
date: 2010-05-22
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-05-22
What's Up?

OK So my first Perl script is under way, I'm not sure what's going wrong with it any more, Have a look if you dare, Here's what I'm hoping to try and do, get the source of a HTML file, Take some text out of some tags, And then print it whilst in a constant loop (three second timeout), However, If the second time around the text that we've grabbed from in between the tags is the same as last time, Then not to print them.

Here's my attempt (AiiiiEEeee!!!)
```
#!/usr/bin/perl

use LWP::Simple;
use Sys::Hostname;

while (1)
{{
my $url = 'http://www.website.com/html.html';
my $content = get $url;
if ( $content =~ m#<(tag)>(.*)</\1># ) {
$shell = $2;
}
if ($shell eq $check) {
print "Same";
goto Bypass;
} 
else
{
print "Not same";
system($shell);
$check = $shell;
}

Bypass:
my $timeout = 3;
$timeout -= sleep $timeout while $timeout > 0;
}}
```

OK you can look from behind the sofa if you please. But with that out of the way, Is it possible to fix and use that code? Or is there a fresher better way of going about this?

Thanks Bye!

---

### Post by lostinxlation on 2010-05-22
I guess it's because you are assigning the same thing to $url and $content at every loop, so you repeat the same operation all over again. At least, you have to take $content assignment to before while loop, but that's not enough if you want to process multiple tags because $content evaluation(if statement) you have only checks the 1st one that maches the pattern. The rest won't be checked.
 
There are many ways to do what you are trying to do, but the straightforward way is just open the file, and read each line every loop and check the pattern match.
Something like(assuming a single tag part don't go across multiple lines),
 
```

 
open(F, 'html file') || die 'file open failed';
 
while(<F>){
   chomp;
   $content = $_;
   if($content =~ m#.....) {
        .......
   }
   .....
   .....
 
}
close(F);

```

---

### Post by shawnhcorey on 2010-05-22
You should use a HTML parser to parse HTML.  This code extracts all the cells from all tables in a page using [HTML::TreeBuilder]("http://search.cpan.org/~petek/HTML-Tree-3.23/lib/HTML/TreeBuilder.pm"):
```
#!/usr/bin/perl

use strict;
use warnings;

use LWP::Simple;
use HTML::TreeBuilder;

my $url = 'http://some.site/page.html';
my $content = get $url;

my $html_tree = HTML::TreeBuilder->new();
$html_tree->parse( $content );

# get all cells of all tables
my @cells = $html_tree->look_down( '_tag', 'td' );

# now display them
for my $cell ( @cells ){
  print $cell->as_text(), "\n";
}

```

---

### Post by lostinxlation on 2010-05-23
I believe this gives what you want.
 
```

#!/usr/bin/perl
 
use LWP::Simple;
use Sys::Hostname;
 
 
while (1)
{{
my $url = 'http://www.website.com/html.html';
my $content = get $url;
 
[COLOR=red]my @a=split(/<tag>/, $content);   # split the contents with <tag> delimiter[/COLOR]
[COLOR=red]shift(@a);                                    # The first element discarded.[/COLOR]
[COLOR=red]map(do{s/</tag>.*$//}, @a);       # truncate </tag> and subsequent texts[/COLOR]
 
[COLOR=red]foreach (@a){[/COLOR]
[COLOR=red] my $shell = $_;[/COLOR]
 
   if ($shell eq $check) {
      print "Same";
      goto Bypass;
   } 
   else
  {
      print "Not same";
      system($shell);
      $check = $shell;
   }
 
   Bypass:
   my $timeout = 3;
   $timeout -= sleep $timeout while $timeout > 0;
 
}}

```

---

### Post by tgalati4 on 2010-05-23
man curl

---

