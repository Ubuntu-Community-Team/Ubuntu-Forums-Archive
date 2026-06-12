---
title: "An Irssi script"
date: 2008-02-11
forum: Programming Talk
---

### Post by yannick_LM on 2008-02-11
```
# Print the country name and the local time in /WHOIS replies
# Based on : country.pl by Timo Sirainen

# This script uses the IP-to-Country Database
# provided by WebHosting.Info ([http://www.webhosting.info](http://www.webhosting.info)),
# available from [http://ip-to-country.webhosting.info](http://ip-to-country.webhosting.info).


# Install :
#     1. Get the latest ip-to-country database at :
#     [http://ip-to-country.webhosting.info/downloads/ip-to-country.csv.zip](http://ip-to-country.webhosting.info/downloads/ip-to-country.csv.zip)
#     and put it in ~/.irssi/scripts
#     2. Make a backup of your config files.
#     3. type (for instance):
#     /format whois {nick $0} {nickhost $1@$2}%:{whois country  $whois_country}%:{whois local $whois_local_time}%:{whois ircname $3}
#    4. Save the changes with /save

# Enjoy !

use strict;
use Irssi ;
use LWP::UserAgent;
use Socket;
#use Shell;

#my $sh=Shell->new;

use vars qw($VERSION %IRSSI);
$VERSION = "1.0.1";
%IRSSI = (
        authors         => "Yannick_LM",
        contact         => "yannicklm1337\@gmail.com",
        name            => "whois_local_time",
        description     => "Print the country name and the local time in /WHOIS replies",
        license         => "Public Domain",
        changed         => "Feb 24 2008"
        );


our $HOME_DIR = $ENV{HOME};
our $GEOFILE = "$HOME_DIR/.irssi/scripts/ip-to-country.csv";
our $URL="http://www.worldtimeserver.com/";

our $time = "";
our $country ="";


# The last version of the file can be obtained there:
# [http://ip-to-country.webhosting.info/downloads/ip-to-country.csv.zip](http://ip-to-country.webhosting.info/downloads/ip-to-country.csv.zip)

# Convert IP to number for use in the ip-to-country database.
sub ip_to_number {
    my $ip = shift;
    my (@octets, $ip_num);
    $ip =~ s/\n//g;
    @octets = split /\./, $ip;
    $ip_num = 0;
    foreach (@octets) {
        $ip_num <<= 8;
        $ip_num |= $_;
    }
    return $ip_num;
}

# Find the country name and code in the database
sub find_country {   
    my $ip=shift;
    $ip = &ip_to_number($ip);
    open GF, "<$GEOFILE" or die "Can't open $GEOFILE $!";
    while (<GF>){
        $_ =~ s/"//g;
        $_ =~ s/\n//;
        my ($start, $end, $CC, $CTRY);
        ($start, $end, $CC, $CTRY, $country) = split /,/, $_;
        if (($ip >= $start) and ($ip <= $end)){
            return "$CC";
            last;
        }
    }
    close GF;
    die "Country not found in database";
}



sub find_time {
    my $CC=shift;

# Queries worltimeserver.com
    my $ua = new LWP::UserAgent;
    $ua->agent("AgentName/0.1 " . $ua->agent);
    my $req = new HTTP::Request GET => "$URL/current_time_in_$CC.aspx";
    my $res = $ua->request($req);
    my $content = $res->content;
    my @lines = split("\n", $content);

# Parses the result
    foreach(@lines) {
        if ( $_ =~ /\s+(\d\d?:\d\d (A|P)M)/ ) {
            return $1;
        }
    }
}


# Redirect whois signal
sub sig_whois {
    my ($server, $data, $nick, $host) = @_;
    my ($me, $nick, $user, $host) = split(" ", $data);
    $host =~ s/^.*\@//;

    eval {
	
	# if it's a cloack, there is a slash in $host 
	if ($host =~ m,/,) {
	    die "$host is a cloak";
	}
	else {

	    my $packed_ip = gethostbyname("$host");
	    defined $packed_ip or die "gethostbyname failed";
	    my $ip_address = inet_ntoa($packed_ip);

	    # Find coutry and time
	    my $CC = &find_country($ip_address);
	    $time = &find_time($CC);
	}
    };

    if ($@) {
        $country="Not Found";
        $time="Unknown";
    }
}

# For use in the /format ligne
sub expando_whois_local_time {
    return $time;
}

sub expando_whois_country {
    return $country;
}


Irssi::signal_add_first('event 311', \&sig_whois);

Irssi::expando_create('whois_local_time', \&expando_whois_local_time,
        { 'event 311' => 'None' } );

Irssi::expando_create('whois_country', \&expando_whois_country,
        { 'event 311' => 'None' } );
```

Well, this is an irssi script that may be useful to you.
You can see if the people you're speaking to should be sleeping or not ;)

Any feedback would greatly be appreciated.

EDIT : fix a bug to take into account the cloaks.
make use of gethostbyname instead of shlel->ping().

---

### Post by Technoviking on 2008-03-24
County and local time are blank for me. Any extra programs needed for the script to work?

16:28 -!-  country  :  
16:28 -!-  local    : 

Mike

---

