---
title: "Sed And Perl"
date: 2010-05-20
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-05-20
What's Up Home Boy?

But seriously, I'm making a small perl script that gets some text from a html page and stores it in a variable, But I'm new to both sed and perl, The only thing left to do is parse the text from the html. I've gotten the sed syntax but are unsure on how to use it within perl.

The html gets printed to the console (Also in variable $content), I have the sed command which I think works :(  sed -n 's/.*<dd>\([^<]*\)<\/dd>.*/\1/p'  Text is inbetween two <dd> tags.

Anyone know?

See Ya!

---

### Post by ja660k on 2010-05-20
backticks...
my $result = `sed ... ... `

that will put the output of sed in $result

also i dont know why your using sed,
when perl is known for its awesome regex

---

### Post by Some Penguin on 2010-05-20
Perl substitution is quite similar.

```

$value_that_gets_changed =~ s/foo/bar/;

```

('man perlre' or 'perldoc perlop' for details)

---

### Post by trent.josephsen on 2010-05-20
> **ja660k said:**
> also i dont know why your using sed,
when perl is known for its awesome regex
Because the regex is not massively complicated, and the OP doesn't need all Perl's libraries and functionality -- he merely needs a **s**tream **ed**itor.  Hence, sed.

Forgive me, though -- don't you want the -e flag before the s/regex/repl/ statement?  And is it ever possible that you will encounter a newline in the <dd> tag, or might there be more than one in a file?  Either of those might throw off your script.

However, I'm not really certain if you're asking a question -- because it looks like a statement with a question mark after it.  In other words, I can't tell whether you are having a problem, or you just want someone to verify you're doing it right.  If the code works, then great.  If it doesn't work, then tell us what it gives you and how that differs from what you were expecting.  If you haven't tested it, then don't ask us to tell you if it works or not -- test it yourself!

---

### Post by Chamillionaire2 on 2010-05-21
Once I've finished I'm going to be compiling it to .executable format for windows, Didn't think about trying to invoke SED on windows won't really work. So what's the regex equivalent?

---

### Post by trent.josephsen on 2010-05-21
I think I misunderstood you.  I didn't realize you were using Perl to call sed -- that doesn't make much sense, because there's no point in calling out to another program when you have all the power of Perl at your fingertips, so to speak.

The regex formats are very similar.  I think in this case they're identical, except that Perl parentheses don't need to be escaped for grouping.  So the regex you used in the original post (with the parens unescaped) will match the content of the **last** <dd> element in the string, provided it is surrounded by **exactly** <dd> and </dd> (no spaces or attributes allowed), is **entirely** on the first line of the string (no newlines between <dd> and </dd>), and contains **no other elements** (can't have any embedded <a> or <em> elements, for instance).

If you can post your code in its entirety, we can probably suggest a better way to go about this.

---

### Post by shawnhcorey on 2010-05-21
Don't use a regex to parse HTML; use a module from [CPAN]("http://search.cpan.org/").  If you are downloading the page from the web use [WWW::Mechanize]("http://search.cpan.org/~petdance/WWW-Mechanize-1.62/lib/WWW/Mechanize.pm").  If you have it locally, use [HTML::TreeBuilder]("http://search.cpan.org/~petek/HTML-Tree-3.23/lib/HTML/TreeBuilder.pm") to parse it.  (HTML::TreeBuilder comes with WWW::Mechanize.)

---

### Post by Chamillionaire2 on 2010-05-21
> **trent.josephsen said:**
> I think I misunderstood you.  I didn't realize you were using Perl to call sed -- that doesn't make much sense, because there's no point in calling out to another program when you have all the power of Perl at your fingertips, so to speak.

The regex formats are very similar.  I think in this case they're identical, except that Perl parentheses don't need to be escaped for grouping.  So the regex you used in the original post (with the parens unescaped) will match the content of the **last** <dd> element in the string, provided it is surrounded by **exactly** <dd> and </dd> (no spaces or attributes allowed), is **entirely** on the first line of the string (no newlines between <dd> and </dd>), and contains **no other elements** (can't have any embedded <a> or <em> elements, for instance).

If you can post your code in its entirety, we can probably suggest a better way to go about this.

Here's the appropriate part of the script ```
my $url = 'http://0161.t35.com/html.html; 
my $content = get $url;
die "Couldn't get $url" unless defined $content;

print $content; 
```
So as you can see the content of the webpage is stored in the $content variable, But how could we get the text in side of the custom <get> tags?

---

### Post by lostinxlation on 2010-05-22
> **Chamillionaire2 said:**
> Here's the appropriate part of the script ```
my $url = 'http://0161.t35.com/html.html; 
my $content = get $url;
die "Couldn't get $url" unless defined $content;
 
print $content; 
```
So as you can see the content of the webpage is stored in the $content variable, But how could we get the text in side of the custom <get> tags?
I think it won't be super clean solution if there're unknown number of <tag> - </tag> combination. Off the top of my head, here is what I got.
@a=split(/<tag>/, $content);
shift(@a);
foreach (@a){
s/</tag>.*$//;
push(@b, $_);
}
 
Each element of @b contains the texts between <tag> and </tag>
 
you might be able to do the same with map function in place of foreach above.
 
 
I'd guess your code is related to another question you asked to extact the texts between tags. I'm not sure why you want to use an infinite loop, but I'll keep it and modify your code as below.
 
```

#!/usr/bin/perl
 
use LWP::Simple;
use Sys::Hostname;
 
 
while (1)
{{
my $url = 'http://www.website.com/html.html';
my $content = get $url;
 
[COLOR=red]my @b=();[/COLOR]
[COLOR=red]my @a=split(/<tag>/, $content);   # split the contents with <tag> delimiter[/COLOR]
[COLOR=red]shift(@a);                                    # The first element discarded.[/COLOR]
[COLOR=red]foreach (@a){[/COLOR]
[COLOR=red] s/</tag>.*$//;                           # truncate </tag> and subsequent text.[/COLOR]
[COLOR=red] push(@b, $_);[/COLOR]
[COLOR=red]}[/COLOR]
 
[COLOR=red]foreach (@b){[/COLOR]
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

