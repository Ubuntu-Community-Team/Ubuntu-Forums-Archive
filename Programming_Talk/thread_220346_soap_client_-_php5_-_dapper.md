---
title: "soap client - php5 - dapper"
date: 2006-07-21
forum: Programming Talk
---

### Post by robinharvey on 2006-07-21
Hi.

I'm having some problems with the PHP5 Soap libs on Ubuntu Dapper.  What is happening is that the SoapClient is not encoding it's data properly, leading to errors on the SoapServer side.  The code i'm running works fine on a regular php install (i.e. compiled from source - same version (5.1.2)), which leads me to think this is an Ubuntu specific problem.
When the SoapClient sends it's request, it is supposed to convert the data you pass it into an XML document, which lists the types of each data item.  By logging the soap envelope which is sent I can see that these data types are missed off the ubuntu-encoded version, which means that the SoapServer interprets the data as an object, instead of an array (for example).  Here is a listing of the XML which is produced in each case:

```

<!-- This is the ubuntu version -->
<SOAP-ENV:Envelope 
	xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" 
	xmlns:ns1="http://myns.com/" 
	xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
	xmlns:ns2="http://xml.apache.org/xml-soap" 
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
	xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/" 
	SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
	<ns1:status>
		<param0>
			<item>
				<key>client_id</key>
				<value>99228700</value>
			</item>
			<item>
				<key>password</key>
				<value>da-password</value>
			</item>
			<item>
				<key>reference</key>
				<value>1000030</value>
			</item>
			<item>
				<key>psp</key>
				<value>MOMGateway</value>
			</item>
		</param0>
	</ns1:status>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>

```

```

<!-- This is the compiled version -->
<SOAP-ENV:Envelope 
	xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" 
	xmlns:ns1="http://myns.com/" 
	xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
	xmlns:ns2="http://xml.apache.org/xml-soap" 
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
	xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/" 
	SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<SOAP-ENV:Body>
	<ns1:status>
		<param0 xsi:type="ns2:Map">
			<item>
				<key xsi:type="xsd:string">client_id</key>
				<value xsi:type="xsd:string">99228700</value>
			</item>
			<item>
				<key xsi:type="xsd:string">password</key>
				<value xsi:type="xsd:string">da-password</value>
			</item>
			<item>
				<key xsi:type="xsd:string">reference</key>
				<value xsi:type="xsd:string">1000031</value>
			</item>
			<item>
				<key xsi:type="xsd:string">psp</key>
				<value xsi:type="xsd:string">MOMGateway</value>
			</item>
		</param0>
	</ns1:status>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>

```

See the xsi:type attributes are missing from the Ubuntu version?  This is what I think the error may be.
The Script I'm running is in non-wsld mode, and i've tried all combinations of options in teh contructor.

Has anyone else come accross this problem??  If not, I think i'll report this as a bug.

TIA,
--Robin

---

### Post by robinharvey on 2006-07-27
OK, I found the problem so here's the solution, FTI.

First, there is a bug report at php.net for this:

[http://bugs.php.net/bug.php?id=37790](http://bugs.php.net/bug.php?id=37790)

(There is also an ubuntu bug report, but i lost the link).  So, the short story is that the PHP version in dapper is broken WRT Soap.  The solution is to build it yourself, and i found a nice way to do this:

1) apt-get build-dep php5 (downloads and installs php5 dependancies)
2) apt-get install checkinstall
3) remove ALL php5 packages (use dpkg --purge to loos config files as well)
4) grab php5.2beta from php.net
5) ./configure (w your options), make on php5 source.
6) sudo checkinstall -D --pkgname="whatever-you-like"

Checkinstall shells the 'make install' of your PHP source, but creates a .deb packages instead of copying files directly to the filesystem.
(AMD64 users: make sure you change the architecture to amd64 (not X86_64) in the last option (8 IIRC)).

You'll have to plumb the new version of php in to your apache config - that's not too hard!

This way you can use a working php version untill such time as one appears in the dapper repos, at which time you can easily remove your hand built package.

hth
--Robin

---

