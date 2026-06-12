---
title: "[SOLVED] C++ language quesion"
date: 2008-07-16
forum: Programming Talk
---

### Post by ceclauson on 2008-07-16
Hello!

I'm somewhat new to C++, and my main language for a bit has been Java.  I'm trying to figure out how visibility modifiers work in C++.

In Java, a static class method can call private methods of instances of that class.  For instance, if there was a class called TestClass, and it had a static method testMethod(TestClass testObject), it could call testObject.privateMethod(), even if private privateMethod() was private.  I'm trying to figure out if there's any way to do this in C++. I tried the following code:

```

#include <iostream>


class TestClass {


	public:

	TestClass* testObject;

	static void staticMethod() {
		std::cout << "staticMethod from TestClass called." << std::endl;
	}

	static void accessObject() {
		testObject->privateMethod();
	}


	private:
	void privateMethod() {
		std::cout << "privateMethod called." << std::endl;
	}

};

int main() {

	void (*smVar)();

	TestClass::staticMethod();

	smVar = TestClass::staticMethod;

	smVar();

	return 0;
}

```

and I got this compilation error:
```

staticmethodtest.cpp:9: error: invalid use of member &#8216;TestClass::testObject&#8217; in static member function
staticmethodtest.cpp:16: error: from this location

```

I'm not sure if this means that unlike Java, I can't call it because it's a private method, or if there's some other error here.

Thanks in advance.

Cooper

---

### Post by DavidBell on 2008-07-16
Your compile problem is that accessObject method is static, static methods don't have implied *this* pointer so it doesn't know where testObject comes from. It needs to be redone something like accessObject(TestClass*), from there not sure it will be able to call the private method, my guess is no.

DB

---

### Post by ceclauson on 2008-07-16
Thanks for the help! FYI, as it turns out, your guess was wrong, the following code compiled and ran:

```

#include <iostream>


class TestClass {


	public:

	static void staticMethod() {
		std::cout << "staticMethod from TestClass called." << std::endl;
	}

	static void accessObject(TestClass* testObject) {
		testObject->privateMethod();
	}

	private:
	void privateMethod() {
		std::cout << "privateMethod called." << std::endl;
	}

};

int main() {

	void (*smVar)();

	TestClass::staticMethod();

	smVar = TestClass::staticMethod;

	smVar();

	TestClass* testObject = new TestClass();
	TestClass::accessObject(testObject);

	return 0;
}

```

Thanks again,
Cooper

---

