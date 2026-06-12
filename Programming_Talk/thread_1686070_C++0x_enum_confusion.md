---
title: "C++0x enum confusion"
date: 2011-02-11
forum: Programming Talk
---

### Post by worksofcraft on 2011-02-11
I'm trying to use to use the new C++ enum extensions to extend an existing enum class with more symbolic constants, but can't get it  to compile with -std=c++0x compile switch :(
Keeping in mind that the extended enum will eventually be part of some other class or module, does anyone here know how the following should be done?
[php]
// g++ -std=c++0x enums.cpp
#include <cstdio>

int main() {
	enum base_enum: char { eSOI = '\xD8' };

	// extend the above list of codes with some more
	enum derived_enum: base_enum { eDHT = '\xC4' };

	return !printf("SOI=%X, DHT=%X\n", eSOI, eDHT);
}
[/php]

The error I get is
```

$ g++ -std=c++0x enums.cpp
enums.cpp: In function &#8216;int main()&#8217;:
enums.cpp:8: error: underlying type &#8216;main()::base_enum&#8217; of &#8216;main()::derived_enum&#8217; must be an integral type

```

... but I thought base_enum **IS** an integral type :confused:

---

### Post by MadCow108 on 2011-02-11
the new enum class are not really classes just scoped strongly typed enums. there is no inheritance (at least I can't find any reference to it in the standard).

also you are using unscoped enums. scoped enums have the additional class tag:
[PHP]enum class base_enum: char { eSOI = '\xD8' };

printf("SOI=%X\n", eSOI, eDHT); // error
printf("SOI=%X\n", base_enum::eSOI); // ok
[/PHP]

---

### Post by worksofcraft on 2011-02-11
> **MadCow108 said:**
> the new enum class are not really classes just scoped strongly typed enums. there is no inheritance (at least I can't find any reference to it in the standard).

also you are using unscoped enums. This scoped enums have the additional class tag:
[PHP]enum class base_enum: char { eSOI = '\xD8' };

printf("SOI=%X\n", eSOI, eDHT); // error
printf("SOI=%X\n", base_enum::eSOI); // ok
[/PHP]

Oh... that's a shame :(
So it's no use for what I want then?

Mind you it does seem to let me inherit base_enum from char but not derived_enum from base_enum :confused: Another case of poorly thought out standard designed by committee IMO :P

---

### Post by MadCow108 on 2011-02-11
yes its very unfortunate syntax
the class does not mean class and the inheritance operator : does not mean inheritance ...
very confusing, but unavoidable when one wants to keep backward compatibility and not introduce new keywords.

---

