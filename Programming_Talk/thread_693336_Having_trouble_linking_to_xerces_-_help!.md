---
title: "Having trouble linking to xerces - help!"
date: 2008-02-10
forum: Programming Talk
---

### Post by shaggy999 on 2008-02-10
Ok, so I copied the code for a quick tester app to see if I can get xerces linked in properly.

```

#include <xercesc/util/PlatformUtils.hpp>


XERCES_CPP_NAMESPACE_USE

int main(int argc, char* argv[])
{
	try {
		XMLPlatformUtils::Initialize();
	}
	catch (const XMLException& toCatch) {
		return 1;
	}

	XMLPlatformUtils::Terminate();

	return 0;
}

```

Then I run the command:

```
g++ xmltest.cpp -lxerces
```

...and I get this:
```
/usr/bin/ld: cannot find -lxerces
collect2: ld returned 1 exit status
```

Anybody have any idea what I'm doing wrong?

To confirm I have libxerces27 and libxerces27-dev installed.

**SOLUTION:** *-lxerces* should be *-lxerces-c*. he he

---

### Post by sehriyar on 2008-10-25
Hi,

It's been a long time but can you explain how you installed xercesc. I tried with

configure
make
make install 

commands but I get lots of undefined reference errors when I compile a program.

---

### Post by shaggy999 on 2008-10-28
Xerces should be in the repositories.

The package 'libxerces28' provides the runtime and 'libxerces28-dev' provides the .h files needed to compile against. :)

---

### Post by mark0978 on 2010-03-12
I ran into this too, even after installing from the repositories.

When linking, it should be -lxerces-c

(At least for version 2.8)

---

