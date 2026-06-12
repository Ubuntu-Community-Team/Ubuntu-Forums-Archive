---
title: "Perl: parsing data from xml in a single-lined string variable"
date: 2009-10-16
forum: Programming Talk
---

### Post by qmqmqm on 2009-10-16
Hi

In Perl, I have the following xml text stored in a variable “$xml_string”.

<result>
<inventory>
 <total>1204</total>
 <in>804</in>
 <out>400</out>
 </inventory>
<inventory>
 <total>484</total>
 <in>324</in>
 <out>160</out>
 <type>product1</type>
 </inventory>
<inventory>
 <total>240</total>
 <in>160</in>
 <out>80</out>
 <type>product2</type>
 </inventory>
<inventory>
 <total>240</total>
 <in>160</in>
 <out>80</out>
 <type>product3</type>
 </inventory>
 </result>

The variable does not contain newline characters, in other words the above xml text is stored in a single line of string. I need to make use of the values of “total”, “in”, and “out” for each type of product. What is the best way to parse these numbers out?

I searched online and I found some Perl XML parsers but they all read from disk files instead of arrays (including the one on the CPAN website).

Could anyone please advise what is the best way (wither an existing library or an efficient algorithm that I can implement) to get the values out from the single-lined string?

Thanks a lot.

Tom

---

### Post by unutbu on 2009-10-16
If $xml_string is complicated, then you probably should use an XML parser, 
but for a simple job maybe this will suffice:
[PHP]
#!/usr/bin/perl 
use strict;
use warnings;

my $xml_string="<result>
<inventory>
<total>1204</total>
<in>804</in>
<out>400</out>
</inventory>
<inventory>
<total>484</total>
<in>324</in>
<out>160</out>
<type>product1</type>
</inventory>
<inventory>
<total>240</total>
<in>160</in>
<out>80</out>
<type>product2</type>
</inventory>
<inventory>
<total>240</total>
<in>160</in>
<out>80</out>
<type>product3</type>
</inventory>
</result>

";

foreach my $chunk (split(/<\/inventory>/,$xml_string)) {
    my ($total,$in,$out)=($chunk=~m|<total>(.*)</total>\s*<in>(.*)</in>\s*<out>(.*)</out>|);
    if ($total and $in and $out) {
	print "$total,$in,$out\n";
    }
}
[/PHP]

---

### Post by A_Fiachra on 2009-10-16
Looking at [XML::Parser]("http://cpan.uwinnipeg.ca/htdocs/XML-Parser/XML/Parser.html#parse_SOURCE_OPT_gt_OPT_VALUE") on CPAN, I see:

"
parse(SOURCE [, OPT => OPT_VALUE [...]]) 		The SOURCE parameter should either be a string containing the whole XML document, or it should be an open IO::Handle.
"

So it seems to fit the bill


```

#!  /usr/bin/perl -w

use strict;
use XML::Parser;

my $xml_string = qq{<result>
<inventory>
<total>1204</total>
<in>804</in>
<out>400</out>
</inventory>
<inventory>
<total>484</total>
<in>324</in>
<out>160</out>
<type>product1</type>
</inventory>
<inventory>
<total>240</total>
<in>160</in>
<out>80</out>
<type>product2</type>
</inventory>
<inventory>
<total>240</total>
<in>160</in>
<out>80</out>
<type>product3</type>
</inventory>
</result>};



my $p1 = new XML::Parser(Style => 'Debug');
$p1->parse($xml_string);



```

---

### Post by ghostdog74 on 2009-10-16
here's a feasible algorithm
```

my $s=qq(<result>
<inventory>
<total>1204</total>
<in>804</in>
<out>400</out>
</inventory>
<inventory>
<total>484</total>
<in>324</in>
<out>160</out>
<type>product1</type>
</inventory>
<inventory>
<total>240</total>
<in>160</in>
<out>80</out>
<type>product2</type>
</inventory>
<inventory>
<total>240</total>
<in>160</in>
<out>80</out>
<type>product3</type>
</inventory>
</result>);

@s = split /<\/inventory/, $s; #split on </inventory> since each record ends with it
print Dumper(@s);
# go thru the array and replace all <>
foreach my $i ( @s) { 
    $i =~ s/<.*?>//g;
    print "$i\n";
    # now you left with "total" "in" and "out" with some garbage left.
    # i leave it to you to remove them.
}




```

---

