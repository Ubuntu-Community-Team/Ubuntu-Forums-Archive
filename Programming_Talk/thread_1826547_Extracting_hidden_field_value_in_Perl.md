---
title: "Extracting hidden field value in Perl"
date: 2011-08-16
forum: Programming Talk
---

### Post by Crikat on 2011-08-16
Hello,

I need to extract the value of a hidden feld in html. I can get get the html content no problem. I've tried HTML::Form, HTML::TagParser etc, but they never seem to give me the value, but the tag name, or input name instead.

```
<input type="hidden" name="login" value="22 length string expected">
```

What I want in a scalar is the 22 len string generated.

thanks in advance.

---

### Post by myrtle1908 on 2011-08-16
I'm sure you can adapt the following crude example as necessary.  The example doesn't account for many things eg. multiline tags etc.

```
use strict;
use warnings;

while(<DATA>) {
  /value="(.*?)"/i && print $1, "\n";
}

__DATA__
<html>
 ...
 <input type="hidden" name="login" value="22 length string expected">
 <input type="hidden" name="aaa" value="22 length string expected">
 <input type="hidden" name="bbb" value="22 length string expected">
</html>
```


However ... you should learn to use a parser if you need more control.  Are you sure you've read the docco for those modules you mention?  To illustrate, the HTML::TagParser docs says:

```
$attr = $elem->attributes();

This method returns a hash of $elem's all attributes.
$value = $elem->getAttribute( $key );

This method returns the value of $elem's attributes which name is $key.
```

So you can use those to retrieve the value attrib of your hidden INPUTs.

---

### Post by Crikat on 2011-08-17
Thanks for your help.

I managed to get it working by using the API in the HTML::TagParser module. I am not at home right now, so when I get back I'll post my solution. But it wasn't as tidy as I wanted it. Had to use a foreach loop to cycle through the values until I found the loginid.

later.

---

### Post by Crikat on 2011-08-17
```
sub loginid {
    my $loginid = "";
    my $html = HTML::TagParser->new( "http://www.spinchat.com/" );
    my @list = $html->getElementsByTagName("input");
    foreach my $elem (@list) {
        my $att = $elem->attributes;
        foreach my $key (sort keys %$att) {
            if($key eq "value") {
                if(length($att->{$key}) == 22) {
                    $loginid = $att->{$key};
                    last;
                }  
            }
        }
    }
  return ($loginid);
}
```

It works anyway..

---

