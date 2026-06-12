---
title: "Perl, Mechanize, TreeBuilder help"
date: 2013-01-04
forum: Programming Talk
---

### Post by playoffspc on 2013-01-04
I have built a simple test website to practice some basic HTML parsing, collecting data, following links and continuing.


Sample Website is laid out like this

index.html (contains simple table, with links to s1.html, s2.html, s3.html)
--> s1.html (contains single h1 tag, "s1 page!")
--> s2.html (contains single h1 tag, "s2 page!")
--> s3.html (contains single h1 tag, "s3 page!")


I try and code a perl script to read index.html, works nicely. I can loop through the table and print out attributes and content of the links, the table rows and cells, etc. No problem.

I can build the links to the next pages, and they print OK. But when I follow a link, say going from index.html to s1.html, my program crashes.


```

!/usr/bin/perl

use WWW::Mechanize;
use WWW::Mechanize::TreeBuilder;

my $mech = WWW::Mechanize->new();
WWW::Mechanize::TreeBuilder->meta->apply($mech);

my $path = "/home/example/path/";
my $url = $path . "index.html";

$mech->get($url);
die "Cannot open file: ", $mech->response->status_line
    unless $mech->success;


# build list of links that are on index.html
# index.html contains a table, each row has a link (<a href="...">....</a>) and
# some other stuff, mostly text right now for testing
my @list = $mech->look_down(_tag => "a", class => "links");


# loop through each link, print some data about each
# ultimately I want to loop my program, table row by row, store some
# data from each row, and if certain conditions are met, follow some links,
# if other conditions are NOT met, skip those rows
foreach (@list) {
  # create the path to file, ie: /home/example/path/s1.html
  $url = $path . $_->attr('href');

  # I would like to go to next page, gather some data
  $mech->get($url);

  # and come back. but after leaving page, I have troubles on next loop
  # iteration. It it is like it loses the previous values of @list, or so it feels like
  $mech->back();

}

```


Sorry if this was too long, I tried to explain it as best I could.

---

