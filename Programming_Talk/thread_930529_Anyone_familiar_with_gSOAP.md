---
title: "Anyone familiar with gSOAP?"
date: 2008-09-26
forum: Programming Talk
---

### Post by bluedalmatian on 2008-09-26
Im trying to implement a SOAP client & server in C++ using gSOAP but the manual is very poorly written and the mailing list's only answer is RTFM.


The client bit looks fairly simple shouldnt be a problem but the server is posing more problematic.

Ive using a standalone server, as opposed to the CGI version, the main skeleton of the program I'v had working for a while but since adding the gSOAP bits it wont' compile giving strange errors about various variables and functions being redeclared.

At the moment I've just got one RPC function getVersionString() which simply returns a string to the client so I can check we're in business.

I've written a header file which I pass to soapcpp2 to generate the server skeletons & client stubs stubs, it consists solely of the line:

int xswitchtcs__getVersionString(std::string* result);

soapcpp2 seems to be happy with it and generates all the neccessary files.

I then take my p-threaded server skeleton (which at this point is working OK) and include soapH.h

and implement the getVersionString method as:

int xswitchtcs__getVersionString(struct soap *soap,std::string* result)
{
	result = "TCS 1.0";
	return SOAP_OK;
}

But when I compile the compiler trips up at the first few lines where the basic variable declarations are, saying I'm redefining them.

Does anyone know of a good tutorial on gSOAP or could offer any advice please?

Thanks

---

### Post by bluedalmatian on 2008-09-26
Am I right in thinking I only need to include soapH.h in my code. No other headers? Oh I should also add I've now removed the namespaces array and #incuded the .nsmap file instead

Again the manual is inconsistent with its examples of this, it appears you can do either?

Then I compile up soapServer.cpp & soapC.cpp into .o files
Then link the whole lot together with libgsoap++.a   ?

As I say its the inclusion of soapH.h that seems to be causing my code not to compile

---

### Post by Shin_Gouki2501 on 2008-09-26
maybe this works better for you? 
[http://ws.apache.org/axis/cpp/index.html](http://ws.apache.org/axis/cpp/index.html)

good luck :)

---

### Post by bluedalmatian on 2008-09-26
SOrted it it was a C++ namespace issue

I put all my code in its own namespace to fix it.

---

