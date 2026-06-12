---
title: "PERL: how to get reply from dns server"
date: 2008-11-18
forum: Programming Talk
---

### Post by shafi on 2008-11-18
Dear all,
I have write a part of code in perl which send a dns request to the dns server.
The question is how to get the reply from the dns server, I want this part of code to act like the dig unix command, a sooner reply appreciated, thank you.
[HTML]
#!/usr/bin/perl
use IO::Socket;
	&dnsQueryPacket($ARGV[0],$ARGV[1]);

sub dnsQueryPacket{
my $hostname = $_[0];
# my @labels = split(/\./, $hostname) ; my $n = scalar(@labels) ; my $question = pack("(C/a*)$n C n2", @labels, 0, 1, 1) ; 
my @labels;
my $nlabels = 0;

for (split /\./, $hostname) {
    push @labels, length, $_;
    $nlabels++;
}
my $n = scalar(@labels);

my $question = pack("(C/a*)$n C n2", @labels, 0, 1, 1) ;
print '$question: ', join("", unpack("(C/a*)$n C n2", $question) ), "\n";
#Hexadecimal format of the Query Part!
print '$question: ', join(" ", unpack("(H2)*", $question) ), "\n";
}
}
[/HTML]
to run the source code:
[HTML]perl script.pl www.google.com A[/HTML]

---

### Post by pdwerryhouse on 2008-11-18
You probably want to look at perl's Net::DNS module.

It will handle all the network operations for you.

---

### Post by slavik on 2008-11-18
ok, first off, that is horrible Perl code ... keeping manual count of number of elements in an array and then call scalar on it to get the same? No wrapper functions for packing/unpacking? that whole for loop needs to go ...

second of all, once you have a socket open, say $sock ...

$request = "give me A record for blah"; # or some such
print $sock $request; #send query
$reply = <$sock>; #receive query

---

### Post by shafi on 2008-11-19
I have brought some changes to the code but still I am not able to get the reply.
I need to do this manually I can not use NET: DNS module, I need help please:

[HTML]
#!/usr/bin/perl
use IO::Socket;
	&dnsQueryPacket($ARGV[0],$ARGV[1]);

sub dnsQueryPacket{
	my $hostname = $_[0];
	# my @labels = split(/\./, $hostname) ; my $n = scalar(@labels) ; my $question = pack("(C/a*)$n C n2", @labels, 0, 1, 1) ; 
	my @labels;
	my $nlabels = 0;

	my @labels = split(/\./, $hostname) ;
	my $n = scalar(@labels) ;
	my $question = pack("(C/a*)$n C n2", @labels, 0, 1, 1) ;

	$header1 = &dnsheader;
	$server = '130.149.2.12';
	$sock = new IO::Socket::INET (PeerAddr=>$server,PeerPort=>'53',Proto=>'udp') or die "Can't Connect";
	#sending request
	$sock->send($header1.$question);
	#receiveing request
	$sock->recv($buf,512);
	
	close($sock);
	}

	sub dnsheader{
		$id = 1000;
		$qr_Opcode_aa_tc_rd = '00000000';
		$ra_Z_Rcode = '00000000';
		$Qdcount = 1;
		$Ancount = 0;
		$Nscount = 0;
		$Arcount = 0;
		$header = pack("n,b8,b8,n4",$id++,
					 "$qr_Opcode_aa_tc_rd",#qr,opcode,aa,tc,rd fields
					 "$ra_Z_Rcode",#ra,Z,Rcode fields 
					 "$Qdcount",#one question(Qdcount)
					 "$Ancount",#no answers (ancount)
					 "$Nscount",#no ns records in authority section(nscount)
					 "$Arcount");#no addtl rr's
		return $header;
	}

[/HTML]

---

### Post by shafi on 2008-11-19
any one?

---

### Post by slavik on 2008-11-19
do you get any errors or something?

---

### Post by shafi on 2008-11-19
> **slavik said:**
> do you get any errors or something?

No I am not getting error, I dont have out put,
here I am sending the request and I think I am also getting the reply back
[HTML]
$sock->send($header1.$question);
	#receiveing request
	$sock->recv($buf,512)
[/HTML]
I think I have the packed reply now in the $buf but I don't know how to unpack it?

---

