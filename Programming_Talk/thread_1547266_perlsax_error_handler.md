---
title: "perl::sax error handler"
date: 2010-08-06
forum: Programming Talk
---

### Post by badperson on 2010-08-06
Hi,
I was getting my feet wet with a sax parser the other day, and I was good up until I tried to create an error handler.

I had the subs for the error stuff in the same .pm file as the regular handler (start_element, end_element, characters, etc)

the code runs, but it just ignores my error code. 
I googled and couldn't find any examples of an error handler. 

I create the parser like so:

```
my $factory = new XML::SAX::ParserFactory( Required_features => { 
	'http://xml.org/sax/features/validation' => 1,
	'http://xml.org/sax/features/namespaces'  => 1 }
	);



my $handler = new JWHandler;
my $errorHandler = new JWHandler;
my $parser = $factory->parser( Handler=>$handler, ErrorHandler => $errorHandler );

```

and an example of the fatal_error sub (I didn't see any examples of this, so I wasn't sure how to deal with the exception)

```
sub fatal_error{
my $test = shift;
	print Dumper($test);
print "FATAL ERROR: at path\n", getElementPath(), "\nfollowing text: $previousText\n";

}
```

any ideas?
thanks!
bp

---

