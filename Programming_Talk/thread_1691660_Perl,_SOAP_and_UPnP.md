---
title: "Perl, SOAP and UPnP"
date: 2011-02-20
forum: Programming Talk
---

### Post by jobsonandrew on 2011-02-20
Hi,
I'm developing a small UPnP library in Perl that I can use to determine my external IP address and possibly map/unmap ports (likely by cron job). This is my first journey into OOP with Perl, so I'm looking to make something reusable

My question involves SOAP with Perl, and passing parameters to SOAP methods on my Netgear DG834. I can use SOAP to determine the External IP of the router, because its a very simple method call:
```

#method of 'Gateway' class
sub getExternalIP(){
	my($self)=@_;
	my $r = SOAP::Lite
		->uri($self->{serviceType})
		->proxy($self->{baseURL}.$self->{controlURL})
		->GetExternalIPAddress();
	return $r->result();
}
```
very neat. However, the 'AddPortMapping' method on UPnP routers takes some parameters:
[LIST]
[*]NewRemoteHost
[*]NewExternalPort
[*]NewProtocol
[*]NewInternalPort
[*]NewInternalClient
[*]NewEnabled
[*]NewPortMappingDescription
[*]NewLeaseDuration
[/LIST]
so that means I need to provide this info.. but how? Because I don't know which order the method is expecting the parameters, or exactly how to do this with Perl.. I tried something like this:
```
#addPortMapping(extport, intport, intclient, proto, description)
sub addPortMapping{
	my($self)=@_;
	print "adding portmapping\n";
	my $res = SOAP::Lite
		->uri($self->{serviceType})
		->proxy($self->{baseURL}.$self->{controlURL})
		->addPortMapping(
			NewRemoteHost=>"",
			NewExternalPort=>shift,
			NewInternalPort=>shift,
			NewInternalClient=>shift,
			NewProtocol=>shift,
			NewPortMappingDescription=>shift);
	return $res->result();
}
```
But that didn't work... I did this in Java but there I actually built up the SOAP XML header that the router expects to see.. so this is a bit confusing.. How do I know what order the parameters should be.. or can I specify whats what similar to the above?

Attached is the source for anyone interested. See the code for apt-get commands to install required libraries

UPnP specification for WANIPConnection (one of the port forwarding services): [http://upnp.org/specs/gw/UPnP-gw-WANIPConnection-Service.pdf]("http://upnp.org/specs/gw/UPnP-gw-WANIPConnection-Service.pdf") (page 49)

Cheers for any interest/response

---

### Post by jobsonandrew on 2011-02-20
Just replying to say I figured this out.
Method now looks like this:
```

#addPortMapping(extport, intport, intclient, proto, description)
sub addPortMapping{
	my($self)=shift;
	SOAP::Lite
		->uri($self->{serviceType})
		->proxy($self->{baseURL}.$self->{controlURL})
		->AddPortMapping(
			SOAP::Data->name('NewRemoteHost')->type(string=>""),
			SOAP::Data->name('NewExternalPort')->type(string=>shift),
			SOAP::Data->name('NewInternalPort')->type(string=>shift),
			SOAP::Data->name('NewInternalClient')->type(string=>shift),
			SOAP::Data->name('NewProtocol')->type(string=>shift),
			SOAP::Data->name('NewPortMappingDescription')->type(string=>shift),
			SOAP::Data->name('NewEnabled')->type(string=>"1"),
			SOAP::Data->name('NewLeaseTime')->type(string=>"0"));
}
```

Updated source code is attached for those interested

Cheers

---

