---
title: "Trying to understand some Perl 5 regexp I found in a book by breaking the code down"
date: 2012-12-25
forum: Programming Talk
---

### Post by s3a on 2012-12-25
I am trying to analyze some syntax I found in a book by breaking it down and making code that uses a subset of those special characters but, I have not been able to manage to get anything running successfully.

Here is the syntax I found in the book.:
```
#!/usr/bin/perl

@lines = `perldoc -u -f atan2`;
foreach (@lines) {
	s/\w<([^>]+)>/\U$1/g; #This is the line that I am most confused about.
	print;
}
```

For example, here is my failed attempt to modify the above code sample so that it simply converts all the letters to uppercase letters.:
```
#!/usr/bin/perl

#@lines = `perldoc -u -f atan2`;
@lines = "one\ntwo\n";
foreach (@lines) {
	#s/\w<([^>]+)>/\U$1/g; #This is the line that I am most confused about.
	s/\U$1/g;
	print;
}
```

When I attempt to run this code, I get the following error message.:
> Substitution replacement not terminated at /tmp/testperlfile.pl line 7.

What must I do differently in order to make my broken-down code work as intended?

Any help in successfully breaking down what I found in the book in order to fully understand it would be greatly appreciated!

---

### Post by steeldriver on 2012-12-25
Well I don't speak perl but I would think that [FONT=Courier New]s/\U$1/g[/FONT] is only half of a substitution - it needs to be in the form [FONT=Courier New]s/**thing to match**/**thing to replace it with**/g[/FONT] 

To replace all characters, you still need to specify a thing to match, I think - but it can be .* (any number of any characters) i.e.

```
$ echo "something<or other>" | perl -e 'while (<>) { s/(.*)/\U$1/g; print }'
SOMETHING<OR OTHER>
```or (since you don't really need the grouping) you can use $& to replace the whole match

```
$ echo "something<or other>" | perl -e 'while (<>) { s/.*/\U$&/g; print }'
SOMETHING<OR OTHER>
```

---

### Post by kevinharper on 2012-12-25
This page has an explanation of what steeldriver is talking about:

"Changing case with regex"
[http://vim.wikia.com/wiki/Changing_case_with_regular_expressions](http://vim.wikia.com/wiki/Changing_case_with_regular_expressions)

---

### Post by foobantu on 2012-12-26
Hi,

Here's one way to try it:

```
#!/usr/bin/perl
use warnings;
use strict;
my @lines = "one\ntwo\n";

foreach (@lines) {
	
	s/($_)/\U$1/g;
	print;
}
```

The line - s/($_)[COLOR="Red"]**/**[/COLOR]\U$1/g; was missing the / (highlighted in red). That's because, the part before the / is what will be Substituted with the part AFTER the /. the () around $_ enable the $1 to sort of capture it.

The $_ is Perl's default.

I dont clearly remember, but looks like this is from the first few pages of Learning Perl Book. Its an awesome book. Correct me if I am wrong, but it looks like you jumped off straight to the chapter on Regular Expressions. What I would suggest is learn the same was as the chapters progress. Meaning Chapter 1 first, then 2nd and then 3rd and so on. 

Also, please include "use warnings" and "use strict" as it will save you a lot of trouble.

Hope this helps. My sincere request would be to try out each and every exercise given at the end of the chapters. :)

---

### Post by spjackson on 2012-12-26
> 
#@lines = `perldoc -u -f atan2`;
@lines = "one\ntwo\n";

Apart from the regex issues, I just want to point out that the original creates an array with many elements, but the replacement creates an array with precisely one element. So the subsequent loop is executed once, i.e. you don't really need a loop.

Of course, simply to translate everything to uppercase, it makes no functional difference whether you process line by line or all at once, but for other regex patterns it might.

If you wanted something more like the original then you might do:
```

my @lines = ("one\n", "two\n");

```

Furthermore, if all you want to do is convert to uppercase, you don't even need a regex. Simply:
```

foreach (@lines) {
	print uc;
}

```
This is Perl: there's more than one way to do it ;-)

---

### Post by foobantu on 2012-12-26
+1 @spjackson for that one. :)

---

