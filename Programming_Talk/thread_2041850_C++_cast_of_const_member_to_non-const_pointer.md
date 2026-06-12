---
title: "C++ cast of const member to non-const pointer"
date: 2012-08-13
forum: Programming Talk
---

### Post by PaulM1985 on 2012-08-13
Hi

Sorry for the rather odd post title, I found some behaviour and I wondered if this is a compiler bug or something.  Below is the code:

Test.h
```

#pragma once

class Base
{
public:
	int number;
	
	Base() { number = 1; }
	
	int GetNumber() const { return number; }
	void SetNumber(int newNumber) { number = newNumber; }
};

class Derived : public Base
{

};

class Test
{
public:
	Derived mMember;

	void DoSomething() const
	{
	//	The line below won't compile because we are
	//	calling a non-const function on a const member
	//	mMember.SetNumber(3);

	//	Why are these two lines allowed?  I can now 
	//	make changes to the object.
		Base *pMember = (Base*) &mMember;
		pMember->SetNumber(3);
	}
};

```

Test.cpp
```

#include "Test.h"

#include <iostream>

int main()
{

	Test test;
	std::cout << test.mMember.GetNumber() << std::endl;

	test.DoSomething();

	std::cout << test.mMember.GetNumber() << std::endl;

	return 0;
}

```

Compile with:
g++ Test.cpp -o Test

I expected that the cast in the Test::DoSomething function would fail since we are casting a const member to a non-const pointer, but it seems to be allowed.  Any ideas why?

Paul

---

### Post by durdenstationer on 2012-08-13
It's not a compile error because C-style casts basically do an end run around the type system. They are not checked by the compiler.

---

### Post by GeneralZod on 2012-08-13
A C-style cast is basically a wrecking-ball approach to casting - it will quite happily cast away constness, amongst other things.

---

### Post by PaulM1985 on 2012-08-13
Thanks for the quick replies.  Solved.

Paul

---

### Post by durdenstationer on 2012-08-13
You're welcome. Just remember, if you want compiler-checked casts use static_cast. If you want what is closet to C-style casts but not allow const to be removed and have them easier to search for in the code, use reinterpret_cast.

---

