---
title: "my first look at Perl"
date: 2007-12-16
forum: Programming Talk
---

### Post by DouglasAWh on 2007-12-16
Ok, I found [http://www.linuxjournal.com/article/2026](http://www.linuxjournal.com/article/2026) and thought things were going to be relatively simple, then I took a look at the full code below. 

[php]
Listing 1

#!/usr/bin/perl -w
# checklinks -- Check Hypertext
# Links on a Web Page
# Usage:  See POD below

#------------------------------------
# Copyright (C) 1996  Jim Weirich.
# All rights reserved. Permission
# is granted for free use or
# modification.
#------------------------------------

use HTML::LinkExtor;
use HTTP::Request;
use LWP::UserAgent;
use LWP::Simple;
use URI::URL;

use Getopt::Std;
$version = '1.0';

# Usage
#-------------------------------------
# Display the usage message by scanning
# the POD documentation for the
# usage statement.

sub Usage {
    while (<DATA>) {
   if (/^B<[-A-Za-z0-9_.]+>/) {
       s/[BI]<([^>]*)>/$1/g;
       print "Usage: $_";
       last;
   }
    }
    exit 0;
}


# ManPage
#------------------------------------
# Display the man page by invoking the
# pod2man (or pod2text) script on
# self.

sub ManPage {
    my($pager) = 'more';
    $pager = $ENV{'PAGER'} if $ENV{'PAGER'};
    if ($ENV{'TERM'} =~ /^(dumb|emacs)$/) {
   system ("pod2text $0");
    } else {
   system ("pod2man $0 | nroff -man | $pager");
    }
    exit 0;
}


# HandleParsedLink
#---------------------------------
# HandleParsedLink is a callback
#provided for parsing handling HTML
# links found during parsing.  $tag
# is the HTML tag where the link was
# found. %links is a hash that contains
# the keyword/value pairs from
# the link that contain URLs. For
# example, if an HTML anchor was
# found, the $tag would be "a"
# and %links would be (href=>"url").

# We check each URL in %links. We make
# sure the URL is absolute
# rather than relative. URLs that don't
# begin with "http:" or "file:"
# are ignored. Bookmarks following a "#"
# character are removed.
# If we have not seen this URL yet, we
# add it to the list of URLs to
# be checked. Finally, we note where
# the URL was found it its list of
# references.

sub HandleParsedLink {
      my ($tag, %links) = @_;
      for $url (values %links) {
         my $urlobj = new URI::URL $url, $currentUrl;
           $url = $urlobj->abs;
           next if $url !~ /^(http|file):/;
     $url =~ s/#.*$//;
     if (!$refs{$url}) {
         $refs{$url} = [];
         push (@tobeChecked, $url);
   }
     push (@{$refs{$url}}, $currentUrl);
    }
    1;
}

# HandleDocChunk
#--------------------------------
# HandleDocChunk is called by the
# UserAgent as the web document is
# fetched. As each chunk of the
# document is retrieved, it is passed
# to the HTML parser object for further
# processing (which in this
# case, means extracting the links).

sub HandleDocChunk {
    my ($data, $response, $protocol) = @_;
    $parser->parse ($data);
}


# ScanUrl
# ------------------------------
# We have a URL that needs to be
# scanned for further references to
# other URLs. We create a request to
# fetch the document and give that
# request to the UserAgent responsible
# for doing the fetch.

sub ScanUrl {
    my($url) = @_;
    $currentUrl = $url;
    push (@isScanned, $url);
    print "Scanning $url\n";
    $request  = new HTTP::Request (GET => $url);
    $response = $agent->request \
    ($request, \&HandleDocChunk);
    if ($response-7gt;is_error) {
   die "Can't Fetch URL $url\n";
    }
    $parser->eof;
}

# CheckUrl
# ------------------------------
# We have a URL that needs to be
# checked and validated. We attempt
# to get the header of the document
# using the head() function. If this
# fails, we add the URL to our list
# of bad URLs. If we do get the
# header, the URL is added to our
# good URL list. If the good URL
# is part of our local web site
#(i.e. it begins with the local
# prefix), then we want to scan
# this URL for more references.

sub CheckUrl {
    my($url) = @_;
    print "    Checking $url\n" if $verbose;
    if (!head ($url)) {
           push (@badUrls, $url);
    } else {
      push (@goodUrls, $url);
      if ($doRecurse && $url =~ /\.html?/ \
              && $url =~ /^$localprefix/) {
            push (@tobeScanned, $url);
   }
    }
}

# Main Program
#---------------------------------

use vars qw ($opt_h $opt_H $opt_V);

getopts('hHpruvV') || die "Command aborted.\n";
$verbose   = ($opt_v ? $opt_v : 0);
$printUrls = ($opt_u ? $opt_u : 0);
$doRecurse = ($opt_r ? $opt_r : 0);

die "Version $version\n" if $opt_V;
ManPage() if $opt_H;
Usage() if $opt_h || @ARGV==0;

# Initialize our bookkeeping arrays

@tobeScanned = ();
# list of URLs to be scanned
@goodUrls    = ();
# list of good URLs
@badUrls     = ();
# list of bad URLs
@isScanned   = ();
# list of scanned URLs
%refs        = ();
# reference lists

# Use the first URL as the model
# for the local prefix. We remove the
# trailing file name of the URL and
# retain the prefix. Any URL that
# begins with this prefix will be
#considered a local URL and available
# for further scanning.

$localprefix = ($opt_p ? $opt_p : $ARGV[0]);
$localprefix =~ s%[^/]*$%%;
print "Local Prefix = $localprefix\n" if $verbose;
if ($doRecurse && !$localprefix) {
    die "A local prefix is required i\
       to restrict recursive fetching\n";
}

# Put each command line arg on the
# list of files to scan. If the
# argument is a file name, convert
# it to a URL by prepending a "file:"
# to it.

for $arg (@ARGV) {
    if (-e $arg) {
   $arg = "file:" . $arg;
    }
    push (@tobeScanned, $arg);
}

# Create the global parser and
# user agent.

$parser = new HTML::LinkExtor
   (\&HandleParsedLink);
$agent  = new LWP::UserAgent;

# Keep Scanning and Checking until
# there are no more URLs

while (@tobeScanned || @tobeChecked) {
    while (@tobeChecked) {
   my $url = shift @tobeChecked;
   CheckUrl ($url);
    }

    if (@tobeScanned) {
   my $url = shift @tobeScanned;
   ScanUrl ($url);
    }
}

# Print the results.

if ($printUrls) {
    print "Scanned URLs: ", join (" ",
        sort @isScanned), "\n";
    print "\n";
    print "Good URLs: ", join (" ",
        sort @goodUrls), "\n";
    print "\n";
    print "Bad URLs: ", join (" ",
        sort @badUrls), "\n";
}

print "\n";
for $url (sort @badUrls) {
    print "BAD URL $url referenced in ...\n";
    for $ref (sort @{$refs{$url}}) {
   print "... $ref\n";
    }
    print "\n";
}

print int (@isScanned), " URLs Scanned\n";
print int (keys %refs), " URLs checked\n";
print int (@goodUrls), " good URLs found\n";
print int (@badUrls),  " bad  URLs found\n";

__END__

=head1 NAME

checklinks - Check Hypertext
 Links on a Web Page

=head1 SYNOPSIS

B<checklinks> [B<-hHpruvV>] I<urls>...

=head1 DESCRIPTION

I<checklinks> will scan a web site
 for bad HTML links.

=head1 OPTIONS

=over 6

=item B<-h> (help)

Display a usage message.

=item B<-H> (HELP ... man page)

Display the man page.

=item B<-p> I<prefix> (local prefix)

Specify the local prefix to be used
when testing for local URLs.  If
this option is not specified when
using the B<-r> option, then a local
prefix is calculated from the first URL
 on the command line.

=item B<-r> (recurse)

Normally, only the URLs listed on the
 command line are scanned.  If
this option is specified, local URLs
 (as defined by the local prefix)
found within documents are fetched and scanned.

=item B<-u> (print URL lists)

The complete lists of good, bad and
scanned URLs will be printed in
addition to the normally printed information.

=item B<-v> (verbose mode)

Display "Checking" messages
as well as "Scanning" messaegs.

=item I<urls>

List of urls to be scanned. If the URLs
is a filename, then a "file:"
is prepended to the filename (this allows
 local files to be scanned
like other URLs).

=back

=head1 AUTHOR

Jim Weirich <C<jweirich@one.net>>

=head1 LIMITATIONS

When recursive scanning URLs
option B<-r>), a local prefix is
calculated from the first URL on the
command line by removing the last
file name in the URL path. If the
URL specifies a directory, the
calculated prefix may be incorrect.
Always specify the complete URL
or use the B<-p> prefix
option to directly specify a local prefix.

=head1 SEE ALSO

See also related man pages for
HTML::LinkExtor, HTTP::Request,
LWP::UserAgent, LWP::Simple, and URI::URL.

=cut


[/php]

I'm a little lost on all of that.  The tutorial page uses

[php]
$req = new HTTP::Request GET,
 'http://w3.one.net/~jweirich';
[/php]

but the real code uses 

[php]
$url =~ s/#.*$//;
[/php]

in 

[php]
sub HandleParsedLink {
      my ($tag, %links) = @_;
      for $url (values %links) {
         my $urlobj = new URI::URL $url, $currentUrl;
           $url = $urlobj->abs;
           next if $url !~ /^(http|file):/;
     $url =~ s/#.*$//;
     if (!$refs{$url}) {
         $refs{$url} = [];
         push (@tobeChecked, $url);
   }
     push (@{$refs{$url}}, $currentUrl);
    }
    1;
}
[/php]

I don't understand that syntax.  Am I looking in the wrong place?

I've never used Perl before, so sorry if this is an easy question.  I'll continue reading up!  THANKS!

---

### Post by slavik on 2007-12-16
some urls look like "http://blah.com/somepage.html#blah" ... that s/#.*$// substitutes a # (hash/pound) followed by any characters followed by an end of the string with nothing (thereby removing everything after and including the hash sign.)

---

### Post by pmasiar on 2007-12-16
I am not sure what you want to accomplish - but I am almost sure that in Python it would be more readable. ASPN recipes are great for this!

---

### Post by slavik on 2007-12-16
how can python make regex (and regex substitution) more readable???

How can you be sure of the outcome if you do not understand what is being done?

---

### Post by operator207 on 2007-12-16
When working with Perl, I have always remembered these two quotes:

Perl is better for impressing the ladies. They think you're
really smart when you can understand something that looks like line noise.
--Jeremy Nixon, SuperNews

Perl is the succesful experiment of making a braindump executeable
--Unknown


Not that the above help much. I am a good doer, not a good teacher. But they may give you a laugh.

---

### Post by nhandler on 2007-12-16
Are you trying to learn perl? Or are you just interested in running the script?
If you intend to learn perl, I suggest starting with something a lot more simple and working your way up.

Here is a good perl tutorial that should get you started:
[http://www.sthomas.net/oldpages/roberts-perl-tutorial.htm](http://www.sthomas.net/oldpages/roberts-perl-tutorial.htm)

---

### Post by DouglasAWh on 2007-12-16
> **Cheater said:**
> Are you trying to learn perl? Or are you just interested in running the script?
If you intend to learn perl, I suggest starting with something a lot more simple and working your way up.

Here is a good perl tutorial that should get you started:
[http://www.sthomas.net/oldpages/roberts-perl-tutorial.htm](http://www.sthomas.net/oldpages/roberts-perl-tutorial.htm)

Mostly just the script.  It doesn't need to be in Perl by any stretch, but I'm trying to do something outside of PHP so I do force myself to learn a little something.

I do understand regular expressions and I thought that's what was happening with that line, but I guess I don't understand how I run the script on the beginning URL.  Doesn't that URL need to be put in the code somewhere or is that a parameter somewhere I am missing?

---

### Post by Majorix on 2007-12-16
What happened to my post here? It didn't contain offensive stuff or anything? :confused:

---

### Post by LaRoza on 2007-12-16
> **Majorix said:**
> What happened to my post here? It didn't contain offensive stuff or anything? :confused:

It was [flamebait]("http://en.wikipedia.org/wiki/Flamebait"), wasn't it?

It had nothing to do with the OP's question, or the thread, and would instigate a very off topic and pointless discussion with strong emotions and no purpose.

---

### Post by Majorix on 2007-12-16
I don't think it was. Even if it was, that is not a reason enough to delete someone's post.

---

### Post by LaRoza on 2007-12-16
> **Majorix said:**
> I don't think it was. Even if it was, that is not a reason enough to delete someone's post.

Yes it was, and yes it is.

Take it up in the forum feedback and help section, under "Resultion Centre", don't discuss it here.

---

### Post by Majorix on 2007-12-16
OK anyways I hadn't seen my PM's just saw them.

---

### Post by slavik on 2007-12-16
[php]sub HandleParsedLink {
      my ($tag, %links) = @_;
      for $url (values %links) {
         my $urlobj = new URI::URL $url, $currentUrl; [/php]

in perl, @_ is a flattened array of the arguments to the function. %links is a hash (php's associative array). for $url line takes all the values from the hash (discards the keys) and during each iteration of the loop $url gets a value from the list of values, then each time, an object gets created with the $url (so for every url processed, an object is created) ...

---

### Post by ghostdog74 on 2007-12-16
> **slavik said:**
> how can python make regex (and regex substitution) more readable???


in Python, here's one way how it can be made more readable (taken frow HOWTO)
```

pat = re.compile(r"""
 \s*                 # Skip leading whitespace
 (?P<header>[^:]+)   # Header name
 \s* :               # Whitespace, and a colon
 (?P<value>.*?)      # The header's value -- *? used to
                     # lose the following trailing whitespace
 \s*$                # Trailing whitespace to end-of-line
""", re.VERBOSE)

```
In Perl, just make some comments about what your regexp is doing, should be fine in most cases.

---

### Post by pmasiar on 2007-12-16
> **slavik said:**
> how can python make regex (and regex substitution) more readable???

By not using regex at all? Python has ie astring.startswith(), 

So instead "if $url !~ /^(http|file):/" you can use 
```

if not url.startswith("http:") or not url.startswith("file:"):

```
which is longer, but more readable for everyone but Perl expert like you of course.

> How can you be sure of the outcome if you do not understand what is being done?

by having extreme mad skilz in ESP? :-)  Or maybe by been there, done that, having scars to prove it?

I have no problem if OP decides to learn Perl anyway. But if Perl is not hard requirement, IMNSHO Python is easier to learn and code in. YMMV. If OP likes Python, fine. If not, it's loss for him :-) IMHO

Perl is deservedly called "executable line noise" and "write-only language". Python is "executable pseudocode", and even people who don't grok it can read it. :-)

---

### Post by slavik on 2007-12-17
we never discussed strings that start with anything ...

you have a url that includes a hash sign and stuff after, without using regex, in a simple and readable way, how do you remove the hash sign and everything after it?

as for starts with, I can implement that in C in like the time it takes me to type it, is that your point?

---

### Post by ghostdog74 on 2007-12-17
> **slavik said:**
> 
you have a url that includes a hash sign and stuff after, without using regex, in a simple and readable way, how do you remove the hash sign and everything after it?


In Python, one way ( depending on how your url definition looks like):
```

>>> url = "blah#blahblah"
>>> url = "blah#blah1blah2end" #assume only 1 hash
>>> startindex = url.index("#")  # get the position of where "#" is
>>> startindex
4
>>> print url[startindex:]
#blah1blah2end
>>> print url[startindex+1:] # get substring.
blah1blah2end

```
In Python, substrings can be easily performed, by string  indexing.
In Perl, to get substring, substr() is used to perform the same task.

---

### Post by Majorix on 2007-12-17
> **slavik said:**
> you have a url that includes a hash sign and stuff after, without using regex, in a simple and readable way, how do you remove the hash sign and everything after it?

[PHP]print "foo#andmoo".split("#")[0][/PHP]

would print foo.

I have a feeling someone is belittling Python? :popcorn:

---

### Post by ghostdog74 on 2007-12-17
> **slavik said:**
> 
as for starts with, I can implement that in C in like the time it takes me to type it, is that your point?

not really necessary. Python's startswith() is equivalent to /^word/ 
eg
```

>>> s=" test"
>>> s.startswith("test")
False
>>> s.startswith(" test")
True

```
in Perl, you can do a function to simulate that. (without the use of the easier regexp  )
```

sub startswith {
        my($pattern, $mystring) = @_;
        $len = length($pattern);
        my $substring = substr($mystring, 0, $len) ;
        if ( $substring eq $pattern ){
                return 1
        }
        else {
                return 0
        }
     }
my $string = "word from here";
if ( startswith("word",$string) ) {
        print "yes\n";
}

```

---

### Post by ghostdog74 on 2007-12-17
> **Majorix said:**
> [PHP]
I have a feeling someone is belittling Python? :popcorn:
```

my $s = "foo#andmoo";
my @array = split(/#/,$s);
print $array[0]."\n";

```

---

### Post by slavik on 2007-12-17
> **ghostdog74 said:**
> ```

my $s = "foo#andmoo";
my @array = split(/#/,$s);
print $array[0]."\n";

```
why do that when you can just do:
[php]$s = s/#.*$//;[/php]

saves the cpu/memory of creating an array (doubly linked circular list)

---

### Post by ghostdog74 on 2007-12-17
> **slavik said:**
> why do that when you can just do:
[php]$s = s/#.*$//;[/php]

saves the cpu/memory of creating an array (doubly linked circular list)
i know it can be done like that.  if you look at that post close enough, i am merely showing Major the equivalence of the split  function in both Perl/Python.

---

### Post by pmasiar on 2007-12-17
> **Majorix said:**
> I have a feeling someone is belittling Python? 

You obviously do not know Perl enough to know how minimal Perl expressions can be, if written by a master. Slavik is skilled in the perl-fu, I bet he could run circles around beginner's Python. But that is irrelevant to my point.

I agree that Perl is superior Python, if all you need it to do some pattern-matching trick in least number of characters typed, and I have no problem with that.

Python is superior to Perl when couple months later you need to read and change your terse Perl code, or some Perl beginner needs to make some changes in a program written by Perl expert:-)

Perl is terse, Python is concise.

I don't want to discourage OP from learning Perl, if Perl is what he wants. But if all OP needs is to parse some text, Perl is not the only solution, and IMHO not  the simplest/easier to learn solution, that's all.

> 
DAGOBAH -- DAY
With Yoda strapped to his back, Luke climbs up one of the many thick vines that grow in the swamp until he reaches the Dagobah statistics lab. Panting heavily, he continues his exercises -- grepping, installing new packages, logging in as root, and writing replacements for two-year-old shell scripts in Python.

YODA: Code!  Yes.  A programmer's strength flows from code maintainability. But beware of Perl.  Terse syntax... more than one way to do it... default variables.  The dark side of code maintainability are they. Easily they flow, quick to join you when code you write.  If once you start down the dark path, forever will it dominate your destiny, consume you it will.

LUKE: Is Perl better than Python?

YODA: No... no... no.  Quicker, easier, more seductive.

LUKE: But how will I know why Python is better than Perl?

YODA: You will know.  When your code you try to read six months from now.

:-)

---

### Post by tyoc on 2007-12-17
Readability of code is only tied to programmer skills, and prior work reading other people code.

Sure it help to have a "nice sintax", but a good programmer can't be beat by the lang being more or less "readable" to other people feelings.


Simple as there are persons that can read & UNDERSTAND x-open source code, and there are others that not.

---

### Post by slavik on 2007-12-17
the thing is that given two programs (one written in Perl, another in Python) that use the same algorithm to accomplish the same thing the Perl code could be at least half the length og Python code but to read it you will still need the same amount of time as for the Python code.

As for Perl one-liners and weird syntax, I don't always write it this way (especially if I know that the code might have to be maintaned). I do have a Perl script that is pretty much just regex matching and uses strict (which forces declaration of variables).

the default variables are there as a convenience to the coder, not for any style or symantic.

---

### Post by pmasiar on 2007-12-17
> **slavik said:**
> I do have a Perl script that is pretty much just regex matching and uses strict 

wait a minute! So you admit in public that you don't "use strict;" in some of your programs? oh the heresy - don't tell perlmonks, or you will be excommunicated! :-)

---

### Post by bobrocks on 2007-12-17
Why are you guys turning this into a pissing match between python and all other languages. And arguing about built in string methods; startswith and indexof are like 3 line functions, if you want them and they aren't there then write them.

From what I gather the original poster asked a question about an already written program and his advice was to write it again in python.  Not from all I know, some explained the program very well.

The way I understand his question he only wants to know how to run the program, but maybe I am wrong on that one.  To run the program save it in a file called checklinks.pl and in the command prompt type:

```
perl checklinks.pl
```

it will give you the options available to you then you can use what options you need, eg -

```
perl checklinks.pl -r http://asite
```

for example as the tutorial says near the end.  You may not need the word perl but that is not an important point.

When the tutorial said 
[PHP]$req = new HTTP::Request GET,
 'http://w3.one.net/~jweirich'; [/PHP]
it was just telling you how you could use the library yourself separate from the script.  But you don't have to modify the script as far as I can see.

I can't actually test any of this on my current machine.
I have used a different program to spider our company sites to find dead links but I can't remember the name of it, I will have a look for you later.  Though I don't see why this wouldn't do the job.

---

### Post by slavik on 2007-12-17
> **bobrocks said:**
> Why are you guys turning this into a pissing match between python and all other languages. And arguing about built in string methods; startswith and indexof are like 3 line functions, if you want them and they aren't there then write them. ...

Unfortunately there are people who believe that Python is the answer to everything.

---

