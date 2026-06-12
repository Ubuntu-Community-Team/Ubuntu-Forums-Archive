---
title: "Perl: Help with Net::Nslookup script"
date: 2013-06-13
forum: Programming Talk
---

### Post by 98cwitr on 2013-06-13
It returns the same IP over and over. This is my first perl script ever :D

> 
use Net::Nslookup;
open (FILE, 'list.txt');
open (MYFILE, '>>dnsResults.csv');
foreach $record (<FILE>) {
        my $r = null;
	my $r  = nslookup "$record";
	print MYFILE "$record,$r \n";
}
close  (MYFILE, 'dnsResults.csv');


---

### Post by 98cwitr on 2013-06-14
inside test.txt I have

[www.google.com]("http://www.google.com")
[www.yahoo.com]("http://www.yahoo.com")
127.0.0.1

Only thing returned is 127.0.0.1

nameserver in resolv.conf is 8.8.8.8...bash works fine :(

use Net::Ping;
open (FILE, 'test.txt');
foreach $record (<FILE>) {
    #print "ping $record \t";
    $p=Net::Ping->new();
    my $ping = $p->ping($record, 2);
    if($ping) {print $record;    };
}

---

### Post by Habitual on 2013-06-14
a post at [here]("http://www.perlmonks.org/?node_id=5968") says [Just a warning: per Paul Vixie, nslookup is broken. Use dig]("http://www.perlmonks.org/?node_id=6148")
having spent ALL day banging on dns and zone edits, I banged this script out.

```
vi checkdns.pl
``` and add
```
#!/usr/bin/perl
$file=$ARGV[0];   
chomp($file);
@list = `cat $file`;

$filedns=$ARGV[1]; 
chomp($filedns);
@listdns = `cat $filedns`;

foreach $dns(@listdns) {
chomp($dns);
print "\n--------------\n$dns\n";

for ($count = 2; $count >= 1; $count--) {
        foreach $domain(@list) {
                chomp($domain);
                $ns = `dig $domain +short`;
                chomp($ns);
                $ns =~s/\n/\t/g;
                print "$domain\t$ns\n";
        }

}

}
```

Save it and exit the editor. make it executable using ```
chmod 700 checkdns.pl
```

Put a list of the domains in domains.txt. 
Save and exit domains.txt
Put a list of dns servers in dnsservers.txt to check against (I used IPs in case RDNS is NOT set...) 
save and exit dnsservers.txt

Now the Magic:
```
**checkdns.pl domains.txt dnsservers.txt**
```

I didn't author it, I found it and modified it (I removed "$dns" in[COLOR=#ff0000]** $ns = `dig $dns  $domain +short`;**[/COLOR]) because I only wanted the host and the A Record from all the nameservers.

I really hope this alternative can benefit you as it did me.

---

### Post by trent.josephsen on 2013-06-14
Habitual, the post you linked to is from 2000.

I tried to install Net::Nslookup from CPAN to see if I could replicate the problem, but the automated tests seem to depend on [www.boston.com](www.boston.com) being found somewhere it isn't (at least not for me). I don't have the patience to fiddle with CPAN tonight, but I'll toss some advice your (OP's) way anyway:

1_ Always use strict and use warnings. Your first attempt has several problems that one or both of these would complain about. I don't think any of those problems are what you're actually wondering about here, but it can't hurt.

2_ Put code in [code] tags when you post it on this forum -- just makes it easier to read.

3_ It's normally better to use while instead of for(each) to iterate over a file in Perl. Not a big deal but you might want to get into the habit. [Explanation](http://stackoverflow.com/questions/585341/whats-the-difference-between-it)

4_ Have you done `perldoc Net::Nslookup` and are you sure you're using it the right way? Most of the online examples I found seemed to call it with keyword arguments (e.g. domain => "google.com", not just "google.com").

Also note that Google doesn't always respond to plain pinging -- not sure why that is but it's true. If you use Net:: Ping you may want to use other domains for testing purposes. Universities are usually good.

---

### Post by drmrgd on 2013-06-15
I tried playing with Net::Nslookup and couldn't get it to install either.  Seems there's an issue with this module.  However, there's another one that might do what you're trying to do, Net::DNS::Nslookup.  I just scribbled together this quickie that might do what you want:

```

#!/usr/bin/perl


use warnings;
use strict;
use Net::DNS::Nslookup;


my $outfile = "dnsResults.csv";
open( OUTPUT, ">", $outfile ) || die "Can't open file '$outfile' for writing: $!";                                                   
                                                                                                                                     
my $infile = $ARGV[0] || die "Need to enter a file with a list of IP Addresses";                                                     
open( INFILE, "<", $infile ) || die "Can't open the input file '$infile' for reading: $!";                                           
while (<INFILE>) {                                                                                                                   
        chomp;                                                                                                                       
        my $dnsLookup = Net::DNS::Nslookup->get_ips( $_ );                                                                           
        print OUTPUT "$dnsLookup\n";                                                                                                 
}                                                                                                                                    
close( OUTPUT );                                                                                                                     
close( INFILE );
```

If you run it with:

```
perl nslookup.pl <file_with_sitenames>
```

the output will be (written to a file called dnsResults.csv):

```

www.google.com,173.194.73.147
www.google.com,173.194.73.105
www.google.com,173.194.73.106
www.google.com,173.194.73.99
www.google.com,173.194.73.103
www.google.com,173.194.73.104
www.ubuntuforums.org,91.189.94.12
www.cnn.com,157.166.240.13
www.cnet.com,64.30.224.103
www.perl.org,207.171.7.51
www.perl.org,207.171.7.41
```

I think that at least should give you a starting point.

---

### Post by trent.josephsen on 2013-06-17
I submitted a bug report on CPAN and Net::Nslookup has been fixed now.

The only other thing that I noticed after trying to use the module myself is that you have to chomp the input -- "www.google.com\n" won't resolve.

---

