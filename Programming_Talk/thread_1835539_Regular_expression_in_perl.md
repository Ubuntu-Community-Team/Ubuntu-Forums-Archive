---
title: "Regular expression in perl"
date: 2011-08-29
forum: Programming Talk
---

### Post by raac on 2011-08-29
I've got a question guys, I need to match the string that contains exactly two "pp" matches.

What I'm thinking about is doing this

/$.*?pp.*?pp[something]           <--- don't know how to say NOT pp here because I only                                                     want exactly two matches.


"?" is saying not greedy, and ".*" is any character 0 or more times

Thanks a lot guys

---

### Post by sisco311 on 2011-08-29
.*[^p]p{2}[^p].*

---

### Post by raac on 2011-08-29
Thanks for the reply cisco311,
is that ever going to match?, "^" is for the beginning of the string, so the second ^p will never be true, right?

---

### Post by sisco311 on 2011-08-29
Nope, in this context, ^ is used for negation. [a-z] matches a lowercase ascii. [^a-z] matches any character but a lowecase ascii. [^p] matches any character but a p:
[http://perldoc.perl.org/perlrecharclass.html#Bracketed-Character-Classes](http://perldoc.perl.org/perlrecharclass.html#Bracketed-Character-Classes)

---

### Post by raac on 2011-08-29
Thanks .

So, actually it needs to be [^pp] right?

because "p" is fine, making it like this...

.*[^pp]pp{2}[^pp].* 	

what about if I added this to my original...

.*?pp.*?pp.*?[^pp]

---

### Post by sisco311 on 2011-08-29
Could you post some examples. I'm not sure if I understand correctly what I you trying to do.

---

### Post by raac on 2011-08-29
for instance
 
ppxppy         (true) because it has two "pp"
 
ppxppyfpp     (false) because it has three "pp" instead of two
 
asdpperdspp  (true) because it has two "pp"
 
asp               (false) because it does not have two "pp"
 
aspp            (false) because it does not have two "pp", it has only one

---

### Post by sisco311 on 2011-08-29
how about?

aspppas
apppasspp
asppppass

---

### Post by raac on 2011-08-29
aspppas               false
apppasspp           true
asppppass            true

---

### Post by paxxus on 2011-08-29
```
if ( /^(.*)pp.*pp/ and $1 !~ /pp/ ) {
  print "TRUE\n";
} else {
  print "FALSE\n";
}
```Not that elegant but I couldn't find a solution with just one regular expression.

---

### Post by stylishpants on 2011-08-29
You could also count the number of times that your entire regex matches the string, and just take action if that count is 2.

One way to do that would be a manual count of matches by m//:
```

bob@cob:/tmp$ cat test.txt
ppxppy (true) because it has two
ppxppyfpp (false) because it has three instead of two
asdpperdspp (true) because it has two
asp (false) because it does not have two
aspp (false) because it does not have two, it has only one
aspppas false
apppasspp true
asppppass true
aspppppass true
asppppppass false

bob@cob:/tmp$ perl -ne '$c=0; $c++ while $_ =~ /pp/g; print "$c\t$_";' test.txt
2	ppxppy (true) because it has two
3	ppxppyfpp (false) because it has three instead of two
2	asdpperdspp (true) because it has two
0	asp (false) because it does not have two
1	aspp (false) because it does not have two, it has only one
1	aspppas false
2	apppasspp true
2	asppppass true
2	aspppppass true
3	asppppppass false


```

Another approach would be to use the s/// operator to do a substitution, because s/// returns a count of the actions performed.  

```
bob@cob:/tmp$ perl -ne 'print s/pp/pp/g; print "\t$_"' test.txt
2	ppxppy (true) because it has two
3	ppxppyfpp (false) because it has three instead of two
2	asdpperdspp (true) because it has two
	asp (false) because it does not have two
1	aspp (false) because it does not have two, it has only one
1	aspppas false
2	apppasspp true
2	asppppass true
2	aspppppass true
3	asppppppass false

```
s/// seems to start its subsequent matches after the previous ones, so if you replace a string with itself you will not run into a problem where portions of previous matches are merged into later characters to form new matches.

---

### Post by shawnhcorey on 2011-08-29
Try:

```
#!/usr/bin/env perl

use strict;
use warnings;

while( <DATA> ){
  my ( $word, $should_be ) = split;

  my @pp = $word =~ m{ ( pp ) }gmsx;
  if( @pp == 2 ){
    print "$word is true, should be $should_be\n";
  }else{
    print "$word is false, should be $should_be\n";
  }
}

__DATA__
ppxppy true
ppxppyfpp false
asdpperdspp true
asp false
aspp false
aspppas false
apppasspp true
asppppass true

```

---

### Post by kurum! on 2011-08-30
I don't use Perl, 

```

$ for text in ppxppy ppxppyfpp asdpperdspp  asp aspp aspppas apppasspp asppppass ; 
>do 
> echo $text | ruby -ne 'chomp;puts ($_.split(/[^p]/).grep(/.*pp.*/).size == 2) ? "#{$_} match" : "#{$_} not   match" '
>done
ppxppy match
ppxppyfpp not match
asdpperdspp match
asp not match
aspp not match
aspppas not match
apppasspp match
asppppass not match


```

In the above Ruby statement, the split(/[^p]/) will get rid of all other characters except "p" and put them in array. So  "apppassppp" will split to become ["", "ppp", "", "", "ppp"]. Then all you have to do it count the number of items that have "pp" pattern..in this case, 2... 
All of these can be translated  to Perl, since Perl has the split function as well as grep....

---

