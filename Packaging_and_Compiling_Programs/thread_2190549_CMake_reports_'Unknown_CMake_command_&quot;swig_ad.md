---
title: "CMake reports: 'Unknown CMake command &quot;swig_add_module&quot;.'"
date: 2013-11-27
forum: Packaging and Compiling Programs
---

### Post by PyrexKidd on 2013-11-27
Hello All,

I'm attempting to compile some obscure [Perl module]("https://svn.apache.org/repos/asf/qpid/trunk/qpid/cpp/bindings/qpid/perl/") for qpid, but instructions are scarce.

When I run cmake on CMakeLists.txt I get the error:

```

root@qpid:~/qpid# cmake CMakeLists.txtCMake Error at CMakeLists.txt:31 (swig_add_module):
  Unknown CMake command "swig_add_module".




-- Configuring incomplete, errors occurred!

```

According to the [CMake Docs]("http://www.cmake.org/Wiki/CMake_FAQ#How_do_I_use_CMake_to_generate_SWIG_wrapper_libraries.3F"), cmake defines two macros for swig generation, one of them being "swig_add_module".

And I think I'm using cmake version > 2.0.

```

root@qpid:~/qpid# cmake --versioncmake version 2.8.11.2

```

Any thoughts?  Thanks for your help.

---

### Post by drmrgd on 2013-11-27
I'm not sure that's the right method.  I think you must use Makefile.PL like this:

```

perl Makefile.PL
make
make test #optional if you want to make sure everything's working right before proceeding

```

---

### Post by PyrexKidd on 2013-11-27
Thanks for the reply.

Under normal circumstances, you'd be absolutely correct.  

I get the following error when trying to write the make file:

```

root@qpid:~/qpid# perl Makefile.PL
perl.i:22: Error: Unable to find 'qpid/swig_perl_typemaps.i'
perl.i:34: Error: Unable to find 'qpid/qpid.i'
Writing Makefile for cqpid_perl
Writing MYMETA.yml

```

Of course given that writing the Makefile fails, 

```

root@qpid:~/qpid# make
cp lib/qpid/messaging/Address.pm blib/lib/qpid/messaging/Address.pm
cp lib/qpid/messaging/Duration.pm blib/lib/qpid/messaging/Duration.pm
cp lib/qpid/messaging.pm blib/lib/qpid/messaging.pm
cp lib/qpid/messaging/Connection.pm blib/lib/qpid/messaging/Connection.pm
cp lib/qpid/messaging/Message.pm blib/lib/qpid/messaging/Message.pm
cp lib/qpid.pm blib/lib/qpid.pm
cp lib/qpid/messaging/Sender.pm blib/lib/qpid/messaging/Sender.pm
cp lib/qpid_messaging.pm blib/lib/qpid_messaging.pm
cp lib/qpid/messaging/Receiver.pm blib/lib/qpid/messaging/Receiver.pm
cp lib/qpid/messaging/Session.pm blib/lib/qpid/messaging/Session.pm
Running Mkbootstrap for cqpid_perl ()
chmod 644 cqpid_perl.bs
rm -f blib/arch/auto/cqpid_perl/cqpid_perl.so
cc  -shared -L/usr/local/lib -fstack-protector cqpid_perl.o  -o blib/arch/auto/cqpid_perl/cqpid_perl.so     \
           -lqpidmessaging -lqpidtypes          \


cc: error: cqpid_perl.o: No such file or directory
make: *** [blib/arch/auto/cqpid_perl/cqpid_perl.so] Error 1

```

I'm pretty sure cmake is able to generate the swig interface files which is why I am attempting to run cmake.  (At least... according to the docs it should be able to...)

---

### Post by drmrgd on 2013-11-27
Hmmmm...you might be right.  Started digging around the link you provided (wanted to see what was in the Makefile...pretty lean and paths are a little wonky).  Found some docs here, which I *think* are relevant:

[https://svn.apache.org/repos/asf/qpid/trunk/qpid/cpp/INSTALL](https://svn.apache.org/repos/asf/qpid/trunk/qpid/cpp/INSTALL)

According to this, you indeed should be using cmake.  And according to this, you should be running cmake from the 'bld' dir under qpid:

```

In the cpp distribution directory (<qpid>/cpp), build the code with:

 # mkdir bld       # This is just a suggested name for the build directory
 # cd bld
 # cmake ..        # ".." is the path to the distribution directory

 # make all

```

From what you posted above, looks like you were running cmake from /qpid?

---

### Post by PyrexKidd on 2013-11-27
Heh, what a novel idea "taking my blinders off and looking around".  Thanks for this!

I'm guessing, I can build everything, then hopefully be able to run my Makefile.PL, etc.

the worst part is, there is a libqpid-perl package, but it's incomplete.  It doesn't include the "qpid.pm" portion of the module (cqpid_something.pm does come with it though...

I'll give this a try and let you know how it goes.  I'm "logged out" for the night at this point so that's a task for tomorrow.

Thanks for all your help!

---

### Post by PyrexKidd on 2013-11-28
So that didn't work...  I built everything (but didn't install) and running Makefile.PL or cmake MakeLists.txt both fail with the same errors.  Actually, cmake gives me a dev warning too:

```

root@qpid:~/qpid/cpp/bindings/qpid/perl# cmake CMakeLists.txt
CMake Error at CMakeLists.txt:31 (swig_add_module):
  Unknown CMake command "swig_add_module".




CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as


    cmake_minimum_required(VERSION 2.8)


  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.


-- Configuring incomplete, errors occurred!

```

So, on a hunch I tried to search for the swig files and found them in: qpid/cpp/include/qpid/

Copying that directory to the perl directory and rerunning the MakeFile.PL produces more, new, errors:

```
root@qpid:~/qpid/cpp/bindings/qpid/perl# perl Makefile.PLqpid/messaging/Address.h:131: Warning 362: operator= ignored
qpid/messaging/Message.h:51: Warning 362: operator= ignored
qpid/messaging/Receiver.h:51: Warning 362: operator= ignored
qpid/messaging/Sender.h:50: Warning 362: operator= ignored
qpid/messaging/Session.h:55: Warning 362: operator= ignored
qpid/messaging/Connection.h:96: Warning 362: operator= ignored
qpid/messaging/Message.h:206: Warning 401: Nothing known about base class 'qpid::types::Exception'. Ignored.
qpid/messaging/Receiver.h:45: Warning 401: Nothing known about base class 'qpid::messaging::Handle< ReceiverImpl >'. Ignored.
qpid/messaging/Receiver.h:45: Warning 401: Maybe you forgot to instantiate 'qpid::messaging::Handle< ReceiverImpl >' using %template.
qpid/messaging/Sender.h:44: Warning 401: Nothing known about base class 'qpid::messaging::Handle< SenderImpl >'. Ignored.
qpid/messaging/Sender.h:44: Warning 401: Maybe you forgot to instantiate 'qpid::messaging::Handle< SenderImpl >' using %template.
qpid/messaging/Session.h:49: Warning 401: Nothing known about base class 'qpid::messaging::Handle< SessionImpl >'. Ignored.
qpid/messaging/Session.h:49: Warning 401: Maybe you forgot to instantiate 'qpid::messaging::Handle< SessionImpl >' using %template.
qpid/messaging/Connection.h:45: Warning 401: Nothing known about base class 'qpid::messaging::Handle< ConnectionImpl >'. Ignored.
qpid/messaging/Connection.h:45: Warning 401: Maybe you forgot to instantiate 'qpid::messaging::Handle< ConnectionImpl >' using %template.
qpid/messaging/Address.h:152: Warning 503: Can't wrap 'operator bool' unless renamed to a valid identifier.
qpid/messaging/Message.h:45: Warning 467: Overloaded method qpid::messaging::Message::Message(qpid::types::Variant &) not supported (no type checking rule for 'qpid::types::Variant &').
qpid/messaging/Message.h:222: Warning 467: Overloaded method qpid::messaging::decode(qpid::messaging::Message const &,qpid::types::Variant::Map &) not supported (no type checking rule for 'qpid::types::Variant::Map &').
qpid/messaging/Message.h:234: Warning 467: Overloaded method qpid::messaging::decode(qpid::messaging::Message const &,qpid::types::Variant::List &,std::string const &) not supported (no type checking rule for 'qpid::types::Variant::List &').
qpid/messaging/Message.h:246: Warning 467: Overloaded method qpid::messaging::encode(qpid::types::Variant::Map const &,qpid::messaging::Message &) not supported (no type checking rule for 'qpid::types::Variant::Map const &').
qpid/messaging/Message.h:258: Warning 467: Overloaded method qpid::messaging::encode(qpid::types::Variant::List const &,qpid::messaging::Message &,std::string const &) not supported (no type checking rule for 'qpid::types::Variant::List const &').
qpid/messaging/Connection.h:87: Warning 467: Overloaded method qpid::messaging::Connection::Connection(std::string const &,qpid::types::Variant::Map const &) not supported (no type checking rule for 'qpid::types::Variant::Map const &').
Writing Makefile for cqpid_perl
Writing MYMETA.yml

```

And just for S&Gs here's the error from make:

```

root@qpid:~/qpid/cpp/bindings/qpid/perl# make
cp lib/qpid/messaging/Address.pm blib/lib/qpid/messaging/Address.pm
cp lib/qpid/messaging/Duration.pm blib/lib/qpid/messaging/Duration.pm
cp cqpid_perl.pm blib/lib/cqpid_perl.pm
cp lib/qpid/messaging.pm blib/lib/qpid/messaging.pm
cp lib/qpid/messaging/Connection.pm blib/lib/qpid/messaging/Connection.pm
cp lib/qpid/messaging/Message.pm blib/lib/qpid/messaging/Message.pm
cp lib/qpid.pm blib/lib/qpid.pm
cp lib/qpid/messaging/Sender.pm blib/lib/qpid/messaging/Sender.pm
cp lib/qpid_messaging.pm blib/lib/qpid_messaging.pm
cp lib/qpid/messaging/Receiver.pm blib/lib/qpid/messaging/Receiver.pm
cp lib/qpid/messaging/Session.pm blib/lib/qpid/messaging/Session.pm
cc -c   -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fstack-protector -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"\" -DXS_VERSION=\"\" -fPIC "-I/usr/lib/perl/5.14/CORE"   cqpid_perl.cpp
cqpid_perl.cpp:1568:39: fatal error: qpid/messaging/exceptions.h: No such file or directory
 #include <qpid/messaging/exceptions.h>
                                       ^
compilation terminated.
make: *** [cqpid_perl.o] Error 1

```

Which certainly does exist:

```

root@qpid:~/qpid/cpp/bindings/qpid/perl# ls qpid/messaging/exceptions.h
qpid/messaging/exceptions.h

```




And for completeness here's what I was talking about that the libqpid-perl package is incomplete:

```

root@qpid:~/qpid/cpp/bindings/qpid/perl# apt-file list libqpid-perl
libqpid-perl: /usr/lib/perl5/auto/cqpid_perl/cqpid_perl.bs
libqpid-perl: /usr/lib/perl5/auto/cqpid_perl/cqpid_perl.so
libqpid-perl: /usr/lib/perl5/cqpid_perl.pm
libqpid-perl: /usr/share/doc/libqpid-perl/changelog.Debian.gz
libqpid-perl: /usr/share/doc/libqpid-perl/copyright

```

(These are the libraries I would expect to be generated with a successful cmake run...  but I'm guessing)

I think ultimately, the problem is that cmake doesn't understand swig...  but it's supposed to... (At least, according to the FAQ)... So I'm puzzled how I'm the only person to find the version WITHOUT swig_add_module...

EDIT:  Oh, I forgot to mention, tests pass... mostly. (which means they fail) which confuses me totally as to why cqpid_perl is even required...

```

root@qpid:~/qpid/cpp/bindings/qpid/perl# prove -It -Ilib
t/Address.t ... ok
t/Duration.t .. 1/?
#   Failed test 'Multiplying by a factor returns a new Duration with that period'
#   at t/Duration.t line 73.


#   Failed test 'Never unequal to an equal instance'
#   at t/Duration.t line 117.
# Looks like you failed 2 tests of 19.
t/Duration.t .. Dubious, test returned 2 (wstat 512, 0x200)
Failed 2/19 subtests
t/Message.t ... 1/? TypeError in method 'Message_setPriority', argument 2 of type 'uint8_t' at /root/qpid/cpp/bindings/qpid/perl/lib/qpid/messaging/Message.pm line 345.
# Looks like your test exited with 255 just after 24.
t/Message.t ... Dubious, test returned 255 (wstat 65280, 0xff00)
All 24 subtests passed


Test Summary Report
-------------------
t/Duration.t (Wstat: 512 Tests: 19 Failed: 2)
  Failed tests:  9, 18
  Non-zero exit status: 2
t/Message.t (Wstat: 65280 Tests: 24 Failed: 0)
  Non-zero exit status: 255
Files=3, Tests=59,  0 wallclock secs ( 0.02 usr  0.00 sys +  0.09 cusr  0.01 csys =  0.12 CPU)
Result: FAIL

```


EDIT2:  Also, I can't run any of the test scripts, so I'm fairly certain that I need to build this library as opposed to just copying it.

```

root@qpid:~/qpid/cpp/bindings/qpid/perl# for i in hello_world.pl client.pl server.pl spout.pl drain.pl; do perl -Ilib $i ; done
2013-11-28 11:18:36 warning Closing connection due to internal-error: Sasl error: SASL(-4): no mechanism available: No worthy mechs found (qpid/SaslFactory.cpp:280)
internal-error: Sasl error: SASL(-4): no mechanism available: No worthy mechs found (qpid/SaslFactory.cpp:280) at lib/qpid/messaging/Connection.pm line 120.
2013-11-28 11:18:36 warning Closing connection due to internal-error: Sasl error: SASL(-4): no mechanism available: No worthy mechs found (qpid/SaslFactory.cpp:280)
internal-error: Sasl error: SASL(-4): no mechanism available: No worthy mechs found (qpid/SaslFactory.cpp:280) at lib/qpid/messaging/Connection.pm line 120.
2013-11-28 11:18:36 warning Closing connection due to internal-error: Sasl error: SASL(-4): no mechanism available: No worthy mechs found (qpid/SaslFactory.cpp:280)
internal-error: Sasl error: SASL(-4): no mechanism available: No worthy mechs found (qpid/SaslFactory.cpp:280) at lib/qpid/messaging/Connection.pm line 120.
2013-11-28 11:18:36 warning Closing connection due to internal-error: Sasl error: SASL(-4): no mechanism available: No worthy mechs found (qpid/SaslFactory.cpp:280)
internal-error: Sasl error: SASL(-4): no mechanism available: No worthy mechs found (qpid/SaslFactory.cpp:280) at lib/qpid/messaging/Connection.pm line 120.
2013-11-28 11:18:36 warning Closing connection due to internal-error: Sasl error: SASL(-4): no mechanism available: No worthy mechs found (qpid/SaslFactory.cpp:280)
internal-error: Sasl error: SASL(-4): no mechanism available: No worthy mechs found (qpid/SaslFactory.cpp:280) at lib/qpid/messaging/Connection.pm line 120.

```
[CODE]

---

