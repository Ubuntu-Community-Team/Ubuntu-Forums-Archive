---
title: "PERL help me out plz."
date: 2009-08-17
forum: Programming Talk
---

### Post by librisje on 2009-08-17
Hi all, i'm programming 2 scripts in perl, to communicatie with each other. It needs to be a authentication system Steps it takes:

startup server ---> client sents login to the server ---> server checks if the login is in the database with enough licenses ---> server needs to send back if the client is allowed to run or to die. So, i got it working with 2 sockets. But i want it all running over 1 socket. I'm started with it, and tried today everything but does not work. What do i have now? I have my server running, when the client connects the server gets the info. Now my server needs to send back if the client is allows by sending "nietgelukt" if he's not allowed and sending the clientid out of the db when the client is allowed to run. But this aint working. It IS but the clients receives it when i'm shutting down my server. I don't know why and looking for someone who can see the bug in my code. So i don't want to shutdown my server to receive if the client is allowed, it needs to keep on running. Heres the code:

Server:
```

#! /usr/bin/perl

use IO::Socket;
use threads();
use DBI();
use warnings;

my $dbh = DBI->connect("DBI:mysql:database=test;host=localhost", "root", "###", {'RaiseError' => 1 });

$sock = new IO::Socket::INET (
							LocalHost => 'localhost',
							LocalPort => '8050',
							Proto => 'tcp',
							Listen => SOMAXXCON,
							Reuse => 1,
						);
die "Could not create socket: $!\n" unless $sock;
while(1){
  $new_sock = $sock->accept();
	while(<$new_sock>) {
	my $dbh = DBI->connect("DBI:mysql:database=test;host=localhost", "root", "###", {'RaiseError' => 1 });
	$ontvangen = $_;
	print $_;
$new_sock->autoflush(1);
$sockthread = threads->new(\&behandelclient,$new_sock);
$sockthread->detach;

}
}
sub behandelclient {
	my $new_sock = $_[0];
	my $dbh = DBI->connect("DBI:mysql:database=test;host=localhost", "root", "###", {'RaiseError' => 1 });
	if($ontvangen =~ m/^\d+/) {
	my $sth = $dbh->prepare('DELETE FROM `connections` WHERE id='.$_ .'');
	  $sth->execute();
	  $sth->finish;	
	} else {
	@dbgegevens = split(/;/, $ontvangen);
	$password = @dbgegevens[1];
	$username = @dbgegevens[0];
	$clientip = @dbgegevens[2];
	chomp($username);
	chomp($password);
	print "username gekregen: " . @dbgegevens[0] . "\n" ;
	print "pw gekregen: " . $password . "\n" ;
	my $sth = $dbh->prepare('SELECT * FROM `customers` WHERE username="' . @dbgegevens[0] . '"');
	  $sth->execute();
	 
	  while (my $ref = $sth->fetchrow_hashref()) {
	  print "FOUND DB username $ref->{'username'} password $ref->{'password'} licenses: $ref->{'licenses'}\n";
	   my $sth = $dbh->prepare('INSERT INTO `test`.`connections` (`username` ,`ip`)VALUES ("'.$username.'", "'.$clientip.'")');
	  $sth->execute();
	  $sth->finish;
	   my $sth = $dbh->prepare('SELECT COUNT(*) FROM `connections` WHERE username="'.$username.'"');
	  $sth->execute();
	  $runningconnections = $sth->fetchrow;
	  $sth->finish;
		  
	  if($ref->{'username'} eq $username and $ref->{'password'} eq $password and $ref->{'licenses'} >= $runningconnections) {
	  sleep 1;
	
	  my $sth = $dbh->prepare('SELECT id FROM connections ORDER BY id DESC LIMIT 1');
	  $sth->execute();
	  $clientid = $sth->fetchrow;
	  print $new_sock $clientid;
	  close($new_sock);

	  print "CLIENT ID =" . $clientid;
	  
	  $sth->finish;
	  }else{
	  
	  sleep 1;
	 
	  print $new_sock "nietgelukt";
	   print "SENDING NIET GELUKT.........\n";
	  close($new_sock);

	  }

  }
	 $sth->finish;

}

}


```

CLIENT:

```

#! /usr/bin/perl

use IO::Socket;
use Sys::HostIP;
use warnings;

my $ip_address = Sys::HostIP->ip;
$SIG{'INT'}='mijn_int_routine';
$SIG{'TERM'}='mijn_int_routine';
$SIG{'HUP'}='mijn_int_routine';
$sig_int = 0;
 
if($#ARGV != 1) {
die "Usage: licensie_usr.pl <USERNAME> <PASSWORD>"
}

my $sock = new IO::Socket::INET (
						PeerAddr => 'localhost',
						PeerPort => '8050',
						Proto => 'tcp',
						);
die "Cannot connect to the server: $!\n" unless $sock;
print $sock $ARGV[0] . ";" . $ARGV[1] . ";" . $ip_address . "\n";
			$response = <$sock>;
			print $response;
			if($response eq "nietgelukt") {
			die "Authentication to the server failed. Wrong username or password or you are using all your licenses";
			} else {
			$clientid = $response;
			}

sub mijn_int_routine
{
        $sig_int=1;
		if ($sig_int) {
		print "Afgebroken via Control-C\n";
		print $sock $clientid;
		exit;
		}
		close($sock);
}

while(1 == 1)
{ 
print $clientid;
}
close($sock);

```

I think the problem is in the client at this part:

```
$response = <$sock>;
``` but if so, i still don't know how to fix it. Someone who can help . Thanks!

---

