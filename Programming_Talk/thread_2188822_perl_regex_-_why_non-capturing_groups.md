---
title: "perl regex - why non-capturing groups?"
date: 2013-11-19
forum: Programming Talk
---

### Post by Lars Noodén on 2013-11-19
I have two questions about the perl snippet below which prints out two lines.

[indent][i]CL/NZ 
US/AU/JP/MX[/i]
[/indent]

```

#!/usr/bin/perl                                                                 

my $txt="[CL/NZ propose; US/AU/JP/MX oppose: 2. Nothing in this Chapter ...";

print "$_\n" for  @match
    = $txt =~
    m/(?:(?:AU|BN|CA|CL|JP|MX|MY|NZ|PE|SG|US|VN)\/)+                            
         (?:AU|BN|CA|CL|JP|MX|MY|NZ|PE|SG|US|VN)/gx;

```

1) I understand the alternation and groupings, but why is the non-capturing (?:****) needed for the groups?

2) How would the *for  @match = $txt =~ m//gx* be grouped for readability with parenthesis or braces?

---

### Post by trent.josephsen on 2013-11-19
1) In list context, the /g modifier causes the pattern to return a list of all matches found. If the match has capturing subpatterns, each match will return a list and the result will be flattened, like this:
```
("12:foo, 42:bar;4:baz" =~ /(\d+):(\w*)/g) # => qw(12 foo 42 bar 4 baz)
```

The person who wrote that pattern didn't want that behavior, so he used only non-capturing groups so as to get the default behavior of capturing each match in its entirety. Apart from that, it's not a bad idea to use them all the time and only switch to capturing expressions when you really want to capture something; it saves counting parens to figure out which of $1, $2, $3, ... to use and it saves Perl the trouble of trying to store them somewhere.

As for 2) IMO there's no good way to split it as-is. I'd probably abstract out the common alternation:
```
$cc = 'AU|BN|CA|CL|JP|MX|MY|NZ|PE|SG|US|VN'; # "country code"
print "$_\n" for ($txt =~ m/(?:(?:$cc)\/)+(?:$cc)/gx);
```
Also notice that for/foreach provides array context, so there's no need to assign to @match unless you use @match for something else. But if this was more than a one-off (I saw it on Slashdot earlier, so I'm assuming not) I'd write it less concisely.

---

### Post by Lars Noodén on 2013-11-20
Thanks.  That's where I saw it, too.  I tend to write code more clearly, but perhaps even the original concise line was clear to that author at the time.  It was probably re-worked for publication.  I've seen map() used in a similar manner so I was also wondering if it was a new convention.  

The non-capturing and compact syntax were new to me.  The non-capturing basically (almost) does this:

```

   m/[color=red]([/color](?:(?:AU|BN|CA|CL|JP|MX|MY|NZ|PE|SG|US|VN)\/)+                           
         (?:AU|BN|CA|CL|JP|MX|MY|NZ|PE|SG|US|VN)[color=red])[/color]/gx;

```

---

