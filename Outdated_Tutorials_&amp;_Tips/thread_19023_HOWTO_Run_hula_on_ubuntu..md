---
title: "HOWTO: Run hula on ubuntu."
date: 2005-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by neom on 2005-03-10
I thought I would right a really quick step by step howto on installing hula on an ubuntu box.

For those who don't know, Hula is a calendar and mail server, it runs the novells NetMail backend, it's extremely versatile and fun!

You can find out more information here 
[http://hula-project.org/Hula_Server](http://hula-project.org/Hula_Server)


The first thing I would suggest you do if you don’t already have it is get subversion, it is available on the package manager. I went all out and also got python subversion and subversion tools. 

This is a terminal heavy install so I would suggest you have it open. 

First step is to create a hula directory in your home directory. 

> 
mkdir hula

Next, cd into hula and use subversion to acquire it. 

> 
cd hula/
svn checkout svn+ssh://anonymous@forgesvn1.novell.com/svn/hula/trunk/hula.

If it asks for a password, it’s anonymous.

The next step is to run the auto generator. The command is as follows:

> 
cd hula/hula/
./autogen.sh


You can use a prefix on this if you so wish, I however would recommend against it as it has to run as root anyway (you can use sudo for this). 

It’s also normal to get some errors at this point.

There may be a few dependencies you are missing, they are usually not too hard to find. I found all mine in the package manager.

Now it’s time for make! 

> 
make

And make install

> 
sudo make install


You have a bit of a choice now. Do you want to run hula as your main mail system, or do you have something existing you wish to leave in place? I was using it as my main mail system, so left most of the defaults install in tact. However, if you are installing along side something, you should probably add some prefixes to the next part.

You will need to find out what to use for dns, I would suggest you look that up in /etc/resolv.conf

> 
tail /etc/resolv.conf


I used the first nameserver.

For a near default install, use this command:

>  
cd /usr/local/sbin/
./hulasetup --domain=whatever.domain.tld --dns=nameserver


For domain, I was setting it up on my home box, so I used home.neom.ca for the domain, and my dns was 64.84.124.10 so I used that.

If you have other mail things running, you will need to use something like this

> 
cd /usr/local/sbin/
./hulasetup --domain=whatever.domain.tld --ldap=port --http=port --https=port --webadmin=port --webadmins=port --dns=nameserver


If you have something running on port 25, you will probably want to end that, I had postfix, so I just killed it.

Also note, this is an application that will stay running when you launch it, so put it in a terminal you can hide. I have mine skipping the taskbar on desktop 4. 

The final step is as follows

> 
sudo /usr/local/sbin/hulamanager


The only error I’ve experience at this point is bind errors, the rest can pretty much be ignored.

Don't forget to fwd your ports on your router.

Then just connect to [http://127.1.1.0:8080](http://127.1.1.0:8080)

And webadmin is at [http://127.1.1.0:89](http://127.1.1.0:89)

This is only what I have done, and I wouldn't say I'm a hula pro. If you need support I would suggest irc.freenode.net #hula

[IMG]http://home.neom.ca/hula.png[/IMG]

---

### Post by flightcrank on 2005-05-04
wow hula looks very nice, thanks for sharing, i didnt even know this existed. ill take a look when i have time.

 have you heard of wordpress. it bloging software.

heres mine [http://maximhome.no-ip.org/blog/](http://maximhome.no-ip.org/blog/) its sort of relevant so i thought id share that too :D

---

### Post by Avicus on 2005-05-18
OK< so i've got Hula running and I can log in as the admin... I have some problems...

1. What is the admin email address? I assume it is [email]admin@mydomain.com[/email], but nothing gets recieved when I try to send to it.

2. I'm not able to send email from this admin account. No errors, it just doesn't seem to reach the destination.

3. MX dns entries... what should they be? Is this a cause of my problems?

---

### Post by ericsp on 2005-08-23
Hi

got it up and running too using these instructions, but what is the way to login as admin?

Eric

---

### Post by ericsp on 2005-08-23
Sorry, had to look better before I asked. For the info: username is admin, password is hula. Then you can change this and create new users.

Eric

---

### Post by rosslaird on 2005-09-21
I'm having some difficulty. When I go to [http://127.1.1.0:8080](http://127.1.1.0:8080) in the browser, I get a "connection refused" message. This happens even when I run the browser as root.

Also, how do I know what I should specify for the "domain"? (I'm running this on my home box, called "ross", so for now I have entered "localhost.ross")

Ross

---

### Post by timmorrow on 2005-09-23
Note for anyone who encounters this error while running "autogen.sh":

> 
checking for openssl... Package openssl was not found in the pkg-config search path. Perhaps you should add the directory containing `openssl.pc' to the PKG_CONFIG_PATH environment variable No package 'openssl' found
configure: error: Library requirements (openssl) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


You'll need openssl and libssl-dev installed (available from Synaptic).

I already had openssl, but not libssl-dev.  It wasn't clear to me that this was where the "openssl.pc" file was located.

---

### Post by ounas on 2005-09-25
Got this error on making **hula**.

make[6]: Entering directory `/home/keys/hula/hula/import/libical/src/libicalss'
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -I../../src/libical -I../../src/libical     -g -O2 -MT icalssyacc.lo -MD -MP -MF ".deps/icalssyacc.Tpo" -c -o icalssyacc.lo icalssyacc.c; \
then mv -f ".deps/icalssyacc.Tpo" ".deps/icalssyacc.Plo"; else rm -f ".deps/icalssyacc.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -I../../src/libical -I../../src/libical -g -O2 -MT icalssyacc.lo -MD -MP -MF .deps/icalssyacc.Tpo -c icalssyacc.c  -fPIC -DPIC -o .libs/icalssyacc.o
icalssyacc.y: In function 'ssparse':
icalssyacc.y:67: error: 'yyclearin' undeclared (first use in this function)
icalssyacc.y:67: error: (Each undeclared identifier is reported only once
icalssyacc.y:67: error: for each function it appears in.)
icalssyacc.y:68: error: 'YYABORT' undeclared (first use in this function)
make[6]: *** [icalssyacc.lo] Error 1
make[6]: Leaving directory `/home/keys/hula/hula/import/libical/src/libicalss'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/keys/hula/hula/import/libical/src'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/keys/hula/hula/import/libical'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/keys/hula/hula/import/libical'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/keys/hula/hula/import'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keys/hula/hula'
make: *** [all] Error 2

Any idea?

Thanks Ounas ](*,)

---

### Post by ounas on 2005-09-26
> **ounas]Got this error on making **hula**.

make[6]: Entering directory `/home/keys/hula/hula/import/libical/src/libicalss'
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -I../../src/libical -I../../src/libical     -g -O2 -MT icalssyacc.lo -MD -MP -MF ".deps/icalssyacc.Tpo" -c -o icalssyacc.lo icalssyacc.c said:**
> (*,)

Solved problem by installing using the Debian version by adding this to the 
repostitory sources list [http://www.eurobob.eclipse.co.uk/hula/](http://www.eurobob.eclipse.co.uk/hula/) debs/ 
Then comment this out after installation.

-
Ounas:razz:

---

### Post by supergrapeman on 2005-09-27
[QUOTE=ounas]Solved problem by installing using the Debian version by adding this to the 
repostitory sources list [http://www.eurobob.eclipse.co.uk/hula/](http://www.eurobob.eclipse.co.uk/hula/) debs/ 
Then comment this out after installation.

-
Ounas:razz:[/QUOTE]

Are you running Warty, Hoary or Breezy? I'm running Hoary, and when I try the above, I get the following error, any clues? I'm very keen to try this out.

# apt-get install hula
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  hula: Depends: libhula0 (>= 0.1.0+svn366-1) but it is not going to be installed
        Depends: libsqlite3-0 (>= 3.2.1) but 3.0.8-3 is to be installed
E: Broken packages

---

### Post by briguy on 2005-10-20
[QUOTE=rosslaird]I'm having some difficulty. When I go to [http://127.1.1.0:8080](http://127.1.1.0:8080) in the browser, I get a "connection refused" message. This happens even when I run the browser as root.

Also, how do I know what I should specify for the "domain"? (I'm running this on my home box, called "ross", so for now I have entered "localhost.ross")

Ross[/QUOTE]
I had the same problem, it worked after a reboot.

---

### Post by gwfire on 2006-01-18
what about runlevel, boot-up and hula?? 

i've installed hula completely and it also runs without any problems. now i want, that hula starts with starting the system...! everytime i restart the system, i must manually start hula again - but that's not the thing i want..:!

i know, that i have to edit some files - but don't exactly which file and how. can anyone help??!!

EDIT: I'm running the newest Hula-Version!

Cheers GW

---

