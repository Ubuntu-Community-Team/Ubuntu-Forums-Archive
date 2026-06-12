---
title: "New to programming"
date: 2010-08-20
forum: Programming Talk
---

### Post by angliski on 2010-08-20
Hi, I have installed C++ from synaptic, but can't find it under applications. Can someone tell me how to get started learning C++ please.

I have never compiled or done anything like that before, I just download from Update manager or synaptic so am not very experienced in Linux.

Cheers

Steve

---

### Post by SpinningAround on 2010-08-20
I don't think you need to install C++ since C++ is a language. First you write some code in c++ then you open a shell and use "gcc" (with file) to compile your code. gcc is a compiler that "transform" your code into machine code that the cpu can understand. This transformed code is stored in a output file from gcc (usually a.out). To run your new program go to the folder where your compiled code is stored and type ./a.out

For guides in c++ see the sticky post in this forum.

---

### Post by worksofcraft on 2010-08-20
create a new text file called hi2.cc on your Desktop and paste the following code in it
```

#include <stdio.h>

struct HelloApp {
	const char *nature;
	HelloApp(const char *n) { nature = n; }
	~HelloApp() {
		printf("Goodbye from %s\n", nature);
	}
	virtual int sayHi() = 0;
};

struct GirlApp: HelloApp {
	GirlApp(): HelloApp("pretty and pink") {}
	int sayHi() {
		return printf("%s girl application says Hello\n", nature);
	}
};

struct BoyApp: HelloApp {
	BoyApp(): HelloApp("cool and blue") {}
	int sayHi() {
		return printf("Hi from the %s boy application\n", nature);
	}
};

int hi(HelloApp *h) { return h->sayHi(); }

int main(int argc, char *argv[]) {
	return hi(&BoyApp()) + hi(&GirlApp());
}

```

open a terminal window and do following commands:
```

cd ~/Desktop
g++ hi2.cc
./a.out

```

You should get two warnings from the compiler.
The program demonstrates object polymorphism and temporary anonymous variables.

---

### Post by nvteighen on 2010-08-20
> **angliski said:**
> Hi, I have installed C++ from synaptic, but can't find it under applications. Can someone tell me how to get started learning C++ please.

I have never compiled or done anything like that before, I just download from Update manager or synaptic so am not very experienced in Linux.

Cheers

Steve

Look at the stickies to find tutorials on C++. Although, I'd suggest you to start learning Python instead of C++, because well... C++ is a language that even experienced people have troubles with.

But anyway, for C++, check that you've installed the build-essentials package. Then, your write some code in a text editor (or in a full-fledged IDE), like this one:

```

#include <iostream>

int main()
{
    std::cout << "Hello world!" << std::endl;

    return 0;
}

```

Save it as hello.cpp and then in a terminal, do this (-Wall, -Wextra and -pedantic turn on a lot of useful checks; -o is used to specify the generated executable's name):
```

g++ -o hello hello.cpp -Wall -Wextra -pedantic

```

And then execute it:
```

./hello

```

Of course, this example doesn't do anything exciting, but if it worked, it means that you've set up everything correctly. Then you may search for tools that might be a bit more advanced that automate this process and have other stuff that might help you in managing your code and etc. But again, the essential thing is what you see here.

P.S.: worksofcraft... no, please no #include <stdio.h>!!!

---

### Post by surfer on 2010-08-20
a smoother way into c++ programming may be to start with python. you'll quickly learn to do nice and fun stuff and you are pretty close to c++ (you'll have to learn a few additional concepts, but as python is built on c++, you are pretty close already for many things).

---

### Post by angliski on 2010-08-20
Thanks everyone, That gives me a place to start. I'm off to write a programme for the international space station now, :lolflag:

Steve

---

### Post by rakete on 2010-08-20
a nice way to make first steps, could be netbeans ide for c++. It manages all the compiler things for you. You just have to make yourself comfortable with netbeans, but that should be no problem.

---

### Post by GeneralZod on 2010-08-20
Make worksofcraft's example a bit more C++-ish (and get rid of the warnings) :

```

#include <iostream>

using namespace std;

class HelloApp {
protected:
    const char *nature; // "char*" isn't very C++-ish (std::string is usually used), but we can forgive it here, I guess.
public:
    HelloApp(const char *n) { nature = n; }
    virtual ~HelloApp() {
            cout << "Goodbye from " << nature << endl;
    }
    virtual void sayHi() const = 0;
};

class GirlApp: public HelloApp {
public:
    GirlApp(): HelloApp("pretty and pink") {}
    void sayHi() const {
            cout << nature << " girl application says Hello" << endl;
    }
};

class BoyApp: public HelloApp {
public:
    BoyApp(): HelloApp("cool and blue") {}
    void sayHi() const {
            cout << "Hi from the " << nature << " boy application" << endl;
    }
};

void hi(const HelloApp &h) { h.sayHi(); }

int main() {
    hi(BoyApp()), hi(GirlApp());
    return 0; 
}

```

I think this should work in pretty much the same as his, except that it doesn't return the number of characters printed by the BoyApp() or GirlApp() (assuming that the print operations were successful, of course).

---

### Post by worksofcraft on 2010-08-20
> **GeneralZod said:**
> Make worksofcraft's example a bit more C++-ish (and get rid of the warnings)

Lol, nice one GeneralZod :)

Now for those who wish to test their progress in understand C++...
try answering some of these:
[LIST]
[*] why GeneralZod's version doesn't give warnings (the clue is in the warning)
[*] the use of private: and public: (your clue is in the use of struct vs. class)
[*] how did the right sayHi method get called when function hi just expects a basic HelloApp. For those that method was set to zero
[*]... well that's just suggestions to trigger your curiosity, but if you know the answers you are well on your way to being a C++ guru ;)
[/LIST]

p.s. Exercise: replace sayHi() method with an overloaded << operator so you can use these HelloApp objects in an output stream and don't forget to internationalize with gettext so you can use it on that international space station :lolflag:

---

### Post by KdotJ on 2010-08-20
> **angliski said:**
> Thanks everyone, That gives me a place to start. I'm off to write a programme for the international space station now, :lolflag:

Steve

Don't forget about those who showed you the way! haha

---

