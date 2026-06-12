---
title: "Is this a C++ bug?"
date: 2010-01-03
forum: Programming Talk
---

### Post by kahumba on 2010-01-03
Hi,
this compiles fine but yields a runtime error:
```

#include <iostream>
#include <locale>
using namespace std;
 
int main() {
	// Change to French/France
	locale loc("french");
	cout.imbue(loc);
}

```

> 
terminate called after throwing an instance of 'std::runtime_error'
  what():  locale::facet::_S_create_c_locale name not valid
Aborted

The issue - can't set French locale.
I saw a bug on launchpad from 2007 which is still "undecided", same issue. So is this a bug at all?

---

### Post by Axos on 2010-01-03
I'm extremely non-expert at this but it looks like you have to use one of the locale names listed by the command:

 locale -a

I modified your program to pass argv[1] to the locale constructor so I could try various things. The only ones which worked were ones which exactly matched the output of the above command.

For example, on my system the output of locale -a is:

C
en_AG
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

Passing "en_US" alone does **not** work. Only if I pass "en_US.utf8" does it work.

---

### Post by mmix on 2010-01-03
sound like you haven't generated those locale.

---

### Post by SledgeHammer_999 on 2010-01-03
I think "locale loc()" is throwing an exception, but your code doesn't handle exceptions, so the program aborts execution.

---

### Post by iharrold on 2010-01-05
> **SledgeHammer_999 said:**
> I think "locale loc()" is throwing an exception, but your code doesn't handle exceptions, so the program aborts execution.

Correct...

[http://www.cplusplus.com/reference/std/locale/locale/locale/](http://www.cplusplus.com/reference/std/locale/locale/locale/)

> C-string with a standard C locale name.
When it is the only parameter, the resulting locale implements all the semantics associated with that name.
When it is the second parameter, only the categories specified in cats are used in the resulting locale, taking the rest from parameter other's locale.
**If this argument is not valid, runtime_error is thrown.** 


Also note locale's are system specific so if it doesn't exist on your system it will throw an exception.

[https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)

---

