---
title: "Perl problem. Variable value does not change"
date: 2009-08-25
forum: Programming Talk
---

### Post by Gediminas2 on 2009-08-25
Hello everyone.
I  started learning perl only a few hours ago, so I'm very inexperienced.
Now without further empty talk here's the code 
```

#!/usr/bin/perl

use warnings;
use strict;

use File::stat;
use Tie::File;
use LWP::Simple;
use LWP::UserAgent;
use HTTP::Request;
use HTTP::Response;
use HTML::LinkExtor; 

use Encode;

my $site1 = "http://www.info.lt/index.php?Nuo="; # Full url like 
my $category="&page=imones&action=ieskoti&veikla_id=";
my $veikla="100209494";

my $start1 = 0;
my $end1 = 1000;
my $contents1;
my $email;
#my $i;
my $url;

my $browser1 = LWP::UserAgent->new();
$browser1->timeout(10);
my $request1;
my $response1;

my $count;
for ($count=$start1; $count<=$end1; $count+=20) {
  $url = $site1  . $count . $category . $veikla . "&Kiek=20";
  printf "Downloading %s\n", $url;

  # Method 2
 
  $request1 = HTTP::Request->new(GET => $url);
  $response1 = $browser1->request($request1);
  if ($response1->is_error()) {
    printf "%s\n", $response1->status_line;
  }
  $contents1 = $response1->decoded_content();

 $email ="";
 #for($i=1; $i<100; $i++)
 {
    if ($contents1 =~  /mailto:(.*)\?sub(.*)/g | $contents1 =~ /mailto:(.*)\>(.*)/g ) 
    {
     $email = "$1";
	`echo $1 >> ~/Logs/email.log`;
	printf "Found:%s\n" ,$email;
    }
 }
}


```Basically what it should do is: Go to a certain website and gather emails (My employer told me to send some offers to them by hand and i thought it would be faster if I made a script for getting the emails).

Now, it only gets a single one (the last one in the page). And does not change it into a new one EVER.

In my opinion the problem lies here:
```
 $email ="";
 
    if ($contents1 =~  /mailto:(.*)\?sub(.*)/g | $contents1 =~ /mailto:(.*)\>(.*)/g ) 
    {
     $email = "$1";
	`echo $1 >> ~/Logs/email.log`;
	printf "Found:%s\n" ,$email;

```

I have thought a way that might help, but am unable to write it in perl. Pseudocode:
```

foreach $line in $contents
  if($line contains email)`echo $1 >> ~/Logs/email.log`;

```

can anyone help me with this? I might be terribly wrong here as I'm not used to perl. Have been googling for answers and tutorials, but now I don't even know what to search. Thanks in advance.

Gedas

after a few hours of googling I found out that i need this line:
  s/[^[:ascii:]]+//g;  # get rid of non-ASCII characters

---

### Post by unutbu on 2009-08-25
Perhaps this will help:
```
  my @lines=split(/\n/,$contents1);
  foreach (@lines) {
      if (/mailto:(.*)\?sub/ | /mailto:(.*)\>/) {
	  ...
      }
  }
```

---

