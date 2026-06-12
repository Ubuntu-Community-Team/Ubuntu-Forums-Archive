---
title: "really stupid perl question...logical or"
date: 2008-12-09
forum: Programming Talk
---

### Post by badperson on 2008-12-09
Hi, 

Is there a shorter way to write the if statement in this script? 
```
print "enter a number: ";
chomp (my $val = <STDIN>);


	if( $val == 4 || $val == 25 || $val == 324){
	print "$val is matched\n";
	} else {
	print "$val is not enumerated\n";
	}
```

something along the lines of 
```
if($val == (4||25||324))
```

I've tried both the single and double bar operators; the single bar doesn't match any, and the double only matches the first one. 

Makes me realize I'm not fully understanding how precedence works, also the difference between logical and bitwise or. 
thanks,
bp

---

### Post by rbprogrammer on 2008-12-09
> **badperson said:**
> Hi, 

Is there a shorter way to write the if statement in this script? 
```
print "enter a number: ";
chomp (my $val = <STDIN>);


	if( $val == 4 || $val == 25 || $val == 324){
	print "$val is matched\n";
	} else {
	print "$val is not enumerated\n";
	}
```

something along the lines of 
```
if($val == (4||25||324))
```

I've tried both the single and double bar operators; the single bar doesn't match any, and the double only matches the first one. 

Makes me realize I'm not fully understanding how precedence works, also the difference between logical and bitwise or. 
thanks,
bp

As far as my understanding of Perl is, that double bars || means "boolean or", while single bars | means "bitwise or".  Secondly, you cannot compress the boolean "or" line.  That's just the way it is.

---

### Post by gjoellee on 2008-12-09
PLEASE: No questions are stupid, except for the following question: "Is this question stupid?"

---

### Post by Reiger on 2008-12-09
Not being very knowledgeable about Perl but in this case you can compress the expression *slightly* by using a regex instead (of course it doesn't improve readability nor performance of your code, but hey: it's perl! :p)

```

if($val =~ /^(25)|((32)?4)$/)

```

But really that's overkill

---

### Post by Martin Witte on 2008-12-09
Something like this might do:

```
my @list = qw(4 25 324);
if ( grep(  /^$val$/, @list) )
{
        print "Found\n";
}
```

---

### Post by badperson on 2008-12-09
that makes sense...
I'm wondering, why doesn't the boolean or work there? (4||25||324) 

I mean, that is a boolean evaluation, right? 
bp

---

### Post by Reiger on 2008-12-09
Well that is a litteral value ;)

4 is a constant
so is 25
and 324.

So the result we'd get is 4 || 25 || 324 which if I'm not mistaken would evaluate to (from casting to booleans, if Perl does this) true || true || true which renders true.

Now what do we have left then?

if($val == true)

---

