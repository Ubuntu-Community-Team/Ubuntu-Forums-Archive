---
title: "Confusing C++ Documentation"
date: 2008-02-12
forum: Programming Talk
---

### Post by shaggy999 on 2008-02-12
I'm very conused by some C++ documentation. I'm using the Xerces C++ libraries and I was reading about how to initialize the setup. The documentation gives this command to be called:

```
static void XMLPlatformUtils::Initialize  	(  	const char *const    	 locale = XMLUni::fgXercescDefaultLocale,
		const char *const   	nlsHome = 0,
		PanicHandler *const   	panicHandler = 0,
		MemoryManager *const   	memoryManager = 0,
		bool  	toInitStatics = false	 
	) 			[static]

Perform per-process parser initialization.

Initialization must be called first in any client code.

The locale is set iff the Initialize() is invoked for the very first time, to ensure that each and every message loaders, in the process space, share the same locale.

All subsequent invocations of Initialize(), with a different locale, have no effect on the message loaders, either instantiated, or to be instantiated.

To set to a different locale, client application needs to Terminate() (or multiple Terminate() in the case where multiple Initialize() have been invoked before), followed by Initialize(new_locale).

The default locale is "en_US".

nlsHome: user specified location where MsgLoader retrieves error message files. the discussion above with regard to locale, applies to this nlsHome as well.

panicHandler: application's panic handler, application owns this handler. Application shall make sure that the plugged panic handler persists through the call to XMLPlatformUtils::terminate().

memoryManager: plugged-in memory manager which is owned by user applications. Applications must make sure that the plugged-in memory manager persist through the call to XMLPlatformUtils::terminate() 
```

The problem is EVERY example code I see, which DOES compile calls ::Initialize() with no arguments! From looking at the API I don't see any reason for this to be the case, so how in the world do I trust the documentation?

---

### Post by shaggy999 on 2008-02-12
Oh gosh. I think I have my answer. In the function definition it says

```
vartype var = value
``` for every variable... I'm guessing this means those are default values and you can omit them if you want to? Maybe that's it. Can this only be done in an all or nothing fashion (meaning either omit them all or define them all) or can I define some and not others without causing the compiler to blow up because it doesn't know what function to call due to overloaded definitions?

Forgive me, I'm used to Java. :D

---

### Post by shaggy999 on 2008-02-12
New problem!! I found this statement in example code:

```
#include <xercesc/dom/DOM.hpp>
```

Only problem is... the documentation doesn't list DOM.hpp!!! I am really confused.

---

### Post by shaggy999 on 2008-02-12
Nevermind... if I had actually read the programming guide DOM.hpp is just a redirector that includes all the various DOM headers.... I suck.

---

