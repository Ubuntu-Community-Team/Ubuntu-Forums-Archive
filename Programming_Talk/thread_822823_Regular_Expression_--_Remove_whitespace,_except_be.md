---
title: "Regular Expression -- Remove whitespace, except between &lt;PRE&gt;&lt;/PRE&gt; tags"
date: 2008-06-08
forum: Programming Talk
---

### Post by WallabyWannabe on 2008-06-08
Hello!

I am writing a perl script to optimize html files.

One of the things I am trying to implement is to remove whitespace that is not needed.

For example:

this             is a           sentence

Should become:

this is a sentence

The reason it is removed is that in html the extra whitespace is still interpreted as a single space.

This isn't particularly difficult to do with switch and a regular expression, except that if the same sentence was surrounded by <PRE> ... </PRE> tags the whitespace becomes meaningful and I must preserve it.

My difficulty is I don't know how to make my regular expression turn itself off when looking inside the <PRE> </PRE> tags.

Thanks for any advice you can offer :).

---

### Post by rye_ on 2008-06-08
I'm afraid I'm not a perl programmer. but in ruby I guess you want to something like the following?

ruby -i.bak -pe '$_ = $_.gsub!(/\s/,' ') unless $_ =~ <PRE>' file.html

running this will save a copy of the original file.txt as file.txt.bak (just in case)

EDIT: I JUST WROTE THIS AS A QUICK EXAMPLE, IT MAKES THE ASSUMPTION THAT ALL <PRE></PRE> tags exist on one line, though with a bit of thought a multiline version shouldn't be too tricky.

---

### Post by odyniec on 2008-06-10
You might also build a simple HTML parser for this purpose:

```
#!/usr/bin/perl

use HTML::Parser;

my $preserve = 0;

sub process_tag
{
    my ($tag, $text) = @_;
    
    if ($tag eq 'pre') {
        $preserve = 1;
    }
    elsif ($tag eq '/pre') {
        $preserve = 0;
    }
    
    print $text;
}

sub process_default
{
    my ($text) = @_;
    
    $text =~ s/[ ]+/ /g unless $preserve;
    print $text;
}

undef $/;
$_ = <STDIN>;

my $p = HTML::Parser->new(
    start_h => [\&process_tag, 'tag,text'],
    end_h => [\&process_tag, 'tag,text'],
    default_h => [\&process_default, 'text']
);
    
$p->parse($_);
```

---

