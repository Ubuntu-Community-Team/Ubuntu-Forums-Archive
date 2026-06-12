---
title: "anyone know what's wrong with this perl code?"
date: 2009-06-12
forum: Programming Talk
---

### Post by Mateo on 2009-06-12
i'm new to perl so be gentle.  it should print off the first 2 titles in this RSS feed.  but it just prints the first title twice. I'm not sure why.  It moves the index forward... so it doesn't make too much sense to me.


```
#!/usr/bin/perl

use LWP::Simple;

sub KillCData {
	my($str) = @_;
	$findex = index($str,"<![CDATA[")+9;
	$str = substr($str,$findex);
	# The number 3 is the length of the ending part "]]>"
	$end = length($str)-3;
	$str = substr($str,0,$end);
	return $str;
}

# Usage: &GetField(String, Index, StartString, EndString)
sub GetField {
	my($wstr, $start, $bstr, $estr) = @_;
	$bindex = index($wstr,$bstr,$start)+length($bstr);
	$eindex = index($wstr,$estr,$start);
	$field = substr($wstr,$bindex,$eindex-$bindex);
	return &KillCData($field);
}

$link = "http://louisville.craigslist.org/apa/index.rss";
$xml = get($link);

$iitem = index($xml,"<item");


$title = &GetField($xml, $iitem, "<title>", "</title>");
$newtitle = &GetField($xml, $iitem+length($title), "<title>", "</title>");
print $title."\n".$newtitle."\n";

```

---

### Post by unutbu on 2009-06-12
Save $xml to a file. 
Use print statements to figure out the value of $iitem.
Find where $iitem+length($title) is in $xml. 

What you'll find is this:

```
$iitem    $iitem+length($title)           $bindex       $eindex
1214      ~1300                           9444          9517
<item                                     <title>       </title>

```
So $iitem+length($title) is too small. Starting the search for $title at $iitem
and starting the search at ($iitem+length($title)) yield the same result.

Here is some code which fixes the immediate problem; I've marked in red where I've made significant changes.
```

#!/usr/bin/perl 
use strict;
use warnings;

use LWP::Simple;

sub KillCData {
	my($str) = @_;
	my $findex = index($str,"<![CDATA[")+9;
	$str = substr($str,$findex);
	# The number 3 is the length of the ending part "]]>"
	my $end = length($str)-3;
	$str = substr($str,0,$end);
	return $str;
}

# Usage: &GetField(String, Index, StartString, EndString)
sub GetField {
	my ($wstr, $start, $bstr, $estr) = @_;
# 	print "args: ($start, $bstr, $estr)\n";
	my $bindex = index($wstr,$bstr,$start)+length($bstr);
	my $eindex = index($wstr,$estr,**[COLOR="Red"]$bindex[/COLOR]**);
	my $field = substr($wstr,$bindex,$eindex-$bindex);
# 	print "indices: $bindex,$eindex,$field\n";
	return (&KillCData($field),**[COLOR="Red"]$eindex[/COLOR]**);
}

my $link = "http://louisville.craigslist.org/apa/index.rss";
my $xml = get($link);
# print "$xml\n";

my $iitem = index($xml,"<item");
# print "iitem=$iitem\n";

my ($title,**[COLOR="Red"]$next[/COLOR]**) = &GetField($xml, $iitem, "<title>", "</title>");
# print "title: $title\n";
# print "next: $next\n";
(my $newtitle,$next) = &GetField($xml, **[COLOR="Red"]$next[/COLOR]**, "<title>", "</title>");
# print "newtitle: $newtitle\n";
# print "next: $next\n";

print $title."\n".$newtitle."\n";
```



Note that there are perhaps better ways to achieve your goal.
If you plan on doing more xml scrapers, it will pay to learn how to use a proper xml parser. 

If you choose not to use an xml parser, another strategy you could use is to
split $xml into a list: 
```
@lines=split(/<title><![CDATA[/,$xml)
```
That way, you are automatically guaranteed to have a new title pretty much at the beginning of each element in the list. You won't have to rely so heavily on index'ing and substr'ing, or my dirty hack to obtain $next.

---

### Post by slavik on 2009-06-12
see XML::Simple

---

### Post by Mateo on 2009-06-13
thanks so much unutbu.  i think i'll give split a try, break apart the items and then grab what i want from each one on the list.  i appreciate your help.

---

