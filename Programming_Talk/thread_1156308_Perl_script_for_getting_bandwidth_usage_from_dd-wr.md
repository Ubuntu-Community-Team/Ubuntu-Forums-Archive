---
title: "Perl script for getting bandwidth usage from dd-wrt"
date: 2009-05-11
forum: Programming Talk
---

### Post by exutable on 2009-05-11
Hey guys,

I am writing a perl script that pulls the monthly bandwidth usage off of dd-wrt and puts it into conky.

I have gotten to the point where the source is stored in a variable but don't know how to get to a certain line and get the characters that I need.

Here is the code I have:
```

#!/usr/bin/perl
# ===========================

use LWP::UserAgent;
$ua = new LWP::UserAgent;
my $req = HTTP::Headers->new;

$req = HTTP::Request->new(GET => 'http://********.homelinux.com:8080/Status_Internet.asp');
$req->authorization_basic('*******', '********');
print "Content-type: text/html\n\n";
my $response = $ua->request($req);
my $html = $response->content;

```

---

### Post by gmatt on 2009-05-11
I can't answer this in perl, because I haven't worked in Perl for a long while, but here is how you can do something similar using the sed tool in linux. 

The sed tool has a -n option which will not print anything, unless you force it to, which is exactly what you want to extract information from a command. 

So lets take a simple example. Suppose I have the command

```

matt@ubuntu:~$ ls -l
total 29520
-rw-r--r--  1 matt matt 28675179 2009-05-08 02:00 bg.xwd
-rw-r--r--  1 matt matt   972170 2009-05-08 02:22 capture.png
-rw-r--r--  1 matt matt   398276 2009-04-08 12:37 conference-ornate-20min.en.pdf
drwxr-xr-x  3 matt matt     4096 2009-04-05 12:41 cs313
drwxr-xr-x  3 matt matt     4096 2009-04-09 01:37 cs425
drwxr-xr-x  2 matt matt     4096 2009-04-08 12:40 Desktop
drwxr-xr-x 10 matt matt     4096 2009-05-07 22:36 Documents
drwxr-xr-x  3 matt matt     4096 2009-05-10 02:48 Downloads
drwxr-sr-x  9 matt matt     4096 2009-05-10 17:49 eclipse
-rw-r--r--  1 matt matt    25318 2009-04-28 00:56 funny-dog-pictures-doin-today.jpg
-rw-r--r--  1 matt matt      415 2009-04-12 21:58 game.pgn
drwxr-xr-x  5 matt matt     4096 2009-04-13 14:47 gtk-gnutella-downloads
drwxr-xr-x  6 matt matt     4096 2009-03-24 00:43 jazz
drwxr-xr-x  5 matt matt     4096 2009-04-13 14:54 LimeWire
drwxr-xr-x  2 matt matt     4096 2009-04-22 00:50 math419
drwxr-xr-x  2 matt matt     4096 2009-03-23 11:57 Music
-rw-r--r--  1 matt matt      375 2009-04-10 00:40 peer-eval
-rw-r--r--  1 matt matt    16960 2009-04-10 00:40 peer-eval.pdf
drwxr-xr-x  2 matt matt     4096 2009-03-23 23:02 Pictures
-rw-r--r--  1 matt matt      529 2009-04-08 19:22 plugin_stack.trace
drwxr-xr-x  2 matt matt     4096 2009-03-23 11:57 Public
drwxr-xr-x 14 matt matt     4096 2009-05-08 16:57 sandbox
drwxr-xr-x  9 matt matt     4096 2009-03-25 20:02 sawcode
drwxr-xr-x  2 matt matt     4096 2009-03-23 11:57 Templates
drwxr-xr-x  2 matt matt     4096 2009-03-23 11:57 Videos
drwxr-xr-x  4 matt matt     4096 2009-05-09 01:29 workspace

```

now, lets say that you want to extract the permissions of the game.pgn file (chess game.) Then the command 

```

matt@ubuntu:~$ ls -l | sed -n "s/\(.\{10,10\}\).*game.pgn/\1/p"
-rw-r--r--

```
Matches this. Note that the syntax of sed is slightly different than Perl for reg exp. I'll assume you know your Perl reg exp and I'll explain the differences. The \( and \) are just like ( ) in Perl. The \1 is just like $1 in perl--that is \1 prints whatever was matched in \( \). The \{n,m\} are just like {n,m} in perl, That is we match between n and m characters. So what this does is it prints out the very first 10 characters of the line with game.pgn on it.

I hope this helps. 


Edit: you can use backquotes (`ls`) in Perl I believe to execute a shell command and store its output. I don't know if that will help you but its useful information.

---

### Post by ghostdog74 on 2009-05-11
> **exutable said:**
> Hey guys,

I am writing a perl script that pulls the monthly bandwidth usage off of dd-wrt and puts it into conky.

I have gotten to the point where the source is stored in a variable but don't know how to get to a certain line and get the characters that I need.

Here is the code I have:
```

#!/usr/bin/perl
# ===========================

use LWP::UserAgent;
$ua = new LWP::UserAgent;
my $req = HTTP::Headers->new;

$req = HTTP::Request->new(GET => 'http://********.homelinux.com:8080/Status_Internet.asp');
$req->authorization_basic('*******', '********');
print "Content-type: text/html\n\n";
my $response = $ua->request($req);
my $html = $response->content;

```

1) split your $html variable on newlines, or <br> (if any), all results will be stored in array. go through the array with a for loop, then search for the things you need. 
2) use a regex on multiline string eg  =~ /mystring/gms
look at the perldoc perlretut or perldoc perlre for how to use regular expresion.

---

### Post by ghostdog74 on 2009-05-11
> **gmatt said:**
> 
Edit: you can use backquotes (`ls`) in Perl I believe to execute a shell command and store its output. 
i consider this "bad" habit. its not portable and Perl has opendir(), readdir() to list directory contents.

---

### Post by KyleBrandt on 2009-05-12
I would not recommend using regular expressions to parse html. 

If you do chose to parse the web page, I would use HTML::TreeBuilder and something like

```
use strict;
use warnings;

use HTML::TreeBuilder;

my $tree = HTML::TreeBuilder->new();
$tree->parse_file('Status_Internet.asp.html');
for my $span ($tree->find_by_tag_name('span')) {
    my $spanID = $span->attr('id') || next;
    if ($spanID =~ /ttraff_in/) {
        print $span->content_list();
    }
} 
```

SNMP would probably be best, but I don't see an OID that correlates to what the webpage shows.

-Kyle

---

### Post by exutable on 2009-05-12
Very helpful Kyle Brandt!

Although your code makes a lot of sense and seems to be almost perfect, it's not returning anything? Not even an error.

Here is my current code:

```
#!/usr/bin/perl
# ===========================

use LWP::UserAgent;
$ua = new LWP::UserAgent;
my $req = HTTP::Headers->new;

$req = HTTP::Request->new(GET => 'http://********.homelinux.com:8080/Status_Internet.asp');
$req->authorization_basic('*********', '**********');
print "Content-type: text/html\n\n";
my $response = $ua->request($req);
my $html = $response->content;


use strict;
use HTML::TreeBuilder 3;

my $root = HTML::TreeBuilder->new;
$root->parse($html);

for my $span ($root->find_by_tag_name('span')) {
    my $spanID = $root->attr('id') || next;
    if ($spanID =~ /ttraff_in/) {
        print $root->content_list();
    }
}

#$root->eof( );  # done parsing for this tree
#$root->dump;   # print( ) a representation of the tree
#$root->delete; # erase this tree because we're done with it
```

---

### Post by KyleBrandt on 2009-05-13
Have you tried printing $html to make sure there is a span tag with an id attribute of ttraff_in, and that tag has some data inside of it?

Other than that I would try maybe taking out the if statement and printing all the content of all the span tags to make sure that much works.

---

### Post by exutable on 2009-05-13
Yeah,

there actually is a span tag that has that id, that's why I was so surprised that you got it spot on.

I'm clearly not any good at perl, I can't even print all the span tags, here is my attempt at the code.  It tries to print out the arrays but not the content?


```

#!/usr/bin/perl
# ===========================

use LWP::UserAgent;
$ua = new LWP::UserAgent;
my $req = HTTP::Headers->new;

$req = HTTP::Request->new(GET => 'http://*******.homelinux.com:8080/Status_Internet.asp');
$req->authorization_basic('********', '******');
print "Content-type: text/html\n\n";
my $response = $ua->request($req);
my $html = $response->content;


#print $html;

use strict;
use HTML::TreeBuilder;

my $root = HTML::TreeBuilder->new;
$root->parse($html);


for my $span ($root->find_by_tag_name('span')) {
    print $root->content;
}

$root->eof( );  # done parsing for this tree
$root->dump;   # print( ) a representation of the tree
$root->delete; # erase this tree because we're done with it
```

---

### Post by KyleBrandt on 2009-05-13
I think you want this:

> 
for my $span ($tree->find_by_tag_name('span')) {
   my $spanID = $span->attr('id') || next;
   print $spanID, ':', $span->content_list, "\n";
   #if ($spanID =~ /ttraff_in/) {
   #   print $span->content_list();
   #}
}


Note the span->content_list instead of the root->content .  I think you were just getting content from the wrong HTML::Element object , not entirely sure -- I am not an expert either :P

---

### Post by exutable on 2009-05-13
NICE!!!


Totally got it working, I really appreciate the help!

Now just getting it into conky :)


Here is my final code:

```

#!/usr/bin/perl
# ===========================

use LWP::UserAgent;
$ua = new LWP::UserAgent;
my $req = HTTP::Headers->new;

$req = HTTP::Request->new(GET => 'http://*********.homelinux.com:8080/Status_Internet.asp');
$req->authorization_basic('*******', '*********');
my $response = $ua->request($req);
my $html = $response->content;


#print $html;

use strict;
use HTML::TreeBuilder;

my $root = HTML::TreeBuilder->new;
$root->parse($html);

for my $span ($root->find_by_tag_name('span')) {
    my $spanID = $span->attr('id') || next;
    if ($spanID =~ /ttraff_in/) {
	print "Incoming: ";
        print $span->content_list;
	print "\n"
    }
    if ($spanID =~ /ttraff_out/) {
	print "Outgoing: ";        
	print $span->content_list;
	print "\n"
    }
}


$root->eof( );  # done parsing for this tree
#$root->dump;   # print( ) a representation of the tree
$root->delete; # erase this tree because we're done with it


```

---

### Post by exutable on 2009-05-13
I actually do have one quick question, do you know how to make it so that the result is in gbs not mbs?

I tried making the mb a variable and using this

$temp = $temp/10;

but that just return 1


Thanks,

Exutable

---

### Post by KyleBrandt on 2009-05-14
I don't see anything wrong with that off hand, can you post more of the code?

---

### Post by exutable on 2009-05-14
Here is the code:

```

#!/usr/bin/perl
# ===========================
#Written by Dane Shea with the help of KyleBrandt of Ubuntuforums.org, this script is free to alter and redistribute without giving credit


#Import libraries
use LWP::UserAgent;
$ua = new LWP::UserAgent;
my $req = HTTP::Headers->new;

#Specify the address of your remote management, for example: "test.homelinux.org";
$ADDRESS = 'http://******.homelinux.com';

#Specify the port of your remote management client, standard http port is 80
$PORT = '8080';

#Specify username for router login
$USER = '*********';

#Specify password for router login
$PASS = '**********';

#Creating the actual request and logging in to fetch the source
$req = HTTP::Request->new(GET => "$ADDRESS:$PORT/Status_Internet.asp");
$req->authorization_basic($USER, $PASS);
my $response = $ua->request($req);
my $html = $response->content;


#Import parsing libraries
use strict;
use HTML::TreeBuilder;

#Start the parsing by creating the root treebuilder
my $root = HTML::TreeBuilder->new;
$root->parse($html);

#Go through all the span tags and look for the id traff_in to retrieve the traffic in tag
for my $span ($root->find_by_tag_name('span')) {
    my $spanID = $span->attr('id') || next;
    if ($spanID =~ /ttraff_in/) {
	#print "Incoming: ";
	my $temp = $span->content_list();
	$temp = $temp/10;
	print $temp;
	print "\n"
    }
}


$root->eof( );  # done parsing for this tree
$root->delete; # erase this tree because we're done with it


```

---

### Post by KyleBrandt on 2009-05-14
One of the tougher things with perl is context.  The two main contexts in Perl are scalar and list context (these can be thought of as singular and plural).  When you put ```
my $temp = $span->content_list();
``` you are telling Perl to evaluate the list that the content_list method call returns in scalar context. When a list is evaluated in scalar content, you get the number of elements in the array.

So instead I think you want something like:
```

for my $span ($root->find_by_tag_name('span')) {
    my $spanID = $span->attr('id') || next;
    if ($spanID =~ /ttraff_in/) {
        if (@temp = $span->content_list()) {
	    my $in = $temp[0] / 10;
	    print $in, "\n";
        }
    }
}

```

---

