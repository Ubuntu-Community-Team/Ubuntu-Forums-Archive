---
title: "C++ what instance is thrown?"
date: 2010-10-24
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-24
Ok it's important to get the basics right and so I wanna throw differnt class of error for different packages (and potentially derive from them for sub classes of errors).
However essentially I want them all to do the same thing... like print an error message and exit if when they aren't explicitly caught.

[php]
// g++ my_error.cpp -lX11
#include <stdio.h>
#include <stdarg.h> // for exit with error message: "fatal"
#include <stdlib.h> // exit
#include <exception>

// base class for exceptions from different packages
// the derived class is to identify which one
struct my_error: std::exception {
	char aErrorText[100]; // a short description of the error
	// the throw here says it can't throw another error
	virtual const char* what() const throw() { return aErrorText; }
	// format the error message then exit
	void fatal(const char *pFmt, ...) {
		va_list L;
		va_start(L, pFmt);
		vsnprintf(aErrorText, sizeof(aErrorText), pFmt, L);
		va_end(L);
		throw *this; // more versatile than exit(EXIT_FAILURE);
	}
};

struct bug1class: my_error {
} gBug1; // global instance

int main(int argc, char *argv[] ) {
	gBug1.fatal("argc=%d invalid\n", argc);
	return !printf("exits normally\n");
}
[/php]

as yo can see I'm throwing gBug1 which is an instance of bug1class, but how to stop it from reporting it as instance of my_error base class from which universal "fatal" method gets inherited :confused:

```

$> ./a.out
terminate called after throwing an instance of 'my_error'
  what():  argc=1 invalid

Aborted

```

---

### Post by Queue29 on 2010-10-24
> Ok it's important to get the basics right ...

Well if that's true then first you should stop using C libraries where C++ libraries exist.

---

### Post by worksofcraft on 2010-10-24
> **Queue29 said:**
> Well if that's true then first you should stop using C libraries where C++ libraries exist.

Using #include <cstdarg> instead of #include <stdarg.h> makes absolutely no difference :P

p.s. and incase you woonder why I don't use new (or malloc) to create these things... then consider the case where my short error message reads "out of memory" ;)

---

### Post by psusi on 2010-10-25
Throw instantiates a new object.  Since you give it *this, it creates a new object from this and initializes it to a copy of *this, which is a my_error.  In other words, you can't do that, but you're doing it wrong anyhow.

Drop the fatal function, and just throw bug1class.  Do not pre-create a global instance of it.

throw bug1class("argc=%d invalid\n", argc);

---

### Post by worksofcraft on 2010-10-25
> **psusi said:**
> Throw instantiates a new object.  Since you give it *this, it creates a new object from this and initializes it to a copy of *this, which is a my_error.  In other words, you can't do that, but you're doing it wrong anyhow.

Drop the fatal function, and just throw bug1class.  Do not pre-create a global instance of it.

throw bug1class("argc=%d invalid\n", argc);

Yes at first I tried throwing the pointer this but that also was converted to a my_error pointer.

Your idea of passing the message details to the error class constructor is quite neat :) However it means having to create variadic constructors for every class just to format that "what() error  message text :(

Isn't there some way to inherit the message formatting from a base class so that all my exception classes can be very simple?

[php]
struct x11wrapper_error: my_error {
	// this one is the base for my x11 wrappers
};

struct x11tryagain: x11wrapper_error {
	// catch this to let user change incorrect input
};

struct x11fatal: x11wrapper_error {
	// don't bother catching, this is irrecoverable
};

// and then somewhere in a totally different package:
struct glib_wrapper_error: my_error {
};
// ... etcetera

      // then somehow something like
      throw x11tryagain() << format(...);
[/php]

---

### Post by worksofcraft on 2010-10-25
lol - ok that was easy to solve...
[php]
// g++ my_error.cpp -lX11
#include <stdio.h> // vsnprintf
#include <cstdarg> // for fail message generator
#include <stdlib.h> // exit
#include <exception> // common base class for exceptions


// form exception message
struct my_error: std::exception {
	static char aErrorText[100]; // a short description of the error
	virtual const char* what() const throw() { return &aErrorText[0]; }
	// format the error message then exit
	static bool fail(const char *pFmt, ...) {
		va_list L;
		va_start(L, pFmt);
		vsnprintf(aErrorText, sizeof(aErrorText), pFmt, L);
		va_end(L);
		return false;
	}
};

char my_error::aErrorText[]; // a short description of the error

struct x11wrapper_error: my_error {
	// this one is the base for my x11 wrappers
};

struct x11tryagain: x11wrapper_error {
	// catch this to let user change incorrect input
};

struct x11fatal: x11wrapper_error {
	// don't bother catching, this is irrecorverable
};

// and then somewhere in a totally different package:
struct glib_wrapper_error: my_error {
};
// ... etcetera

int main(int argc, char *argv[]) {
	if (argc <= 1) {
		my_error::fail("this %s %s business", "is", "serious");
		throw x11tryagain();
	}
	// or we can include it in a Prolog style expression
	else if (
		argc <= 2 &&
		!my_error::fail("invalid argc=%d", argc)
	) throw x11fatal();
	else {
		my_error::fail("and now for something completely different");
		throw glib_wrapper_error();
	}
	return 0; // some people don't like printf
}
[/php]

now it gives me the right class AND the formatted message without me having to code anything in the derived error classes or even catch the error!

Thanks psusi that was really insightful :)

```

$ ./a.out 2010
terminate called after throwing an instance of 'x11fatal'
  what():  invalid argc=2
Aborted

```

---

### Post by nvteighen on 2010-10-25
???

It's pretty simple to do... In your "worksofcraft::exception", create a method to be called in "catch" blocks... Of course, you have to manage to create a well-planned interface for your own "base class" so that all needed information is available for the "base output" method. Then, use C++ polymorphism features to create versions that might require specific stuff.

About stdarg.h: In C++ classes, you shouldn't use variadic argument lists... You can overload methods to work with different signatures. It's much more practical to do it that way, really. And of you need an indeterminate amount of data, use a std::vector or something like that, but having a variadically parametrized exception seems a bad idea to me: error handling should be simple, predictable and output only the relevant information.

---

### Post by worksofcraft on 2010-10-25
> **nvteighen said:**
> ???

It's pretty simple to do... In your "worksofcraft::exception", create a method to be called in "catch" blocks... Of course, you have to manage to create a well-planned interface for your own "base class" so that all needed information is available for the "base output" method. Then, use C++ polymorphism features to create versions that might require specific stuff.


ooh ... yes there is an idea too :)
So it's like a kind of call back from the catch to findout more about what it's caught ?!

My original was to exit the program with a message on stderr and I wanted it to retain that as default. What I don't know is the parameters I might need to express in the error message, hence the variadic function.

For some exceptions the application program can take remedial action and then I **don't** want to output anything. Alas from within my wrapper object libraries I have no idea of what said program is going to catch and handle, hence the use of standard exception class with "what()" method: When the exception is caught the handler can display it or ignore it or do something completely different.

See now I can integrate say the FT (freetype) library and include exception classes for that with practically no code at all...
[php]
// ^my_error ... as above

struct ft_problem: my_error {};

int main() {
    try {
        if (!my_error::fail("this fails!")) throw ft_problem();
    }
    catch (ft_problem &P) {
         printf("I'm ignoring %s  :P\n", P.what());
    }
    return !"yes";
}
[/php]

---

### Post by psusi on 2010-10-25
> **worksofcraft said:**
> 
Your idea of passing the message details to the error class constructor is quite neat :) However it means having to create variadic constructors for every class just to format that "what() error  message text :(

Generally your exception class should be specific enough that it should just take the required arguments and format it correctly, rather than accept an arbitrary printf format string.

---

### Post by worksofcraft on 2010-10-25
> **psusi said:**
> Generally your exception class should be specific enough that it should just take the required arguments and format it correctly, rather than accept an arbitrary printf format string.

You mean like this?
[php]
#include <stdio.h> // vsnprintf
#include <cstdarg> // for fail message generator
#include <stdlib.h> // exit
#include <exception> // common base class for exceptions


// form exception message
struct my_error: std::exception {
	const char * pErrorMessage; // actuall message
	my_error(const char *pSetMessage): pErrorMessage(pSetMessage) {}
	virtual const char* what() const throw() { return pErrorMessage; }
};

struct ft_problem: my_error {
	ft_problem(const char *pMsg): my_error(pMsg) {};
};

struct ft_filenotfound: ft_problem {
	ft_filenotfound(const char *pFileName): ft_problem(pFileName) {}
};

int main(int argc, char *argv[]) {
	// for sake of argument imagine that argv[0] is the
	// freetype font face library we wanted but we fail to open it
	throw ft_filenotfound(argv[0]);
	return !printf("exits normally\n");
}
[/php]

Failing to catch it gives:
```

$> g++ my_err2.cpp
$> ./a.out
terminate called after throwing an instance of 'ft_filenotfound'
  what():  ./a.out
Aborted

```

I suppose given a reasonable error class name it's almost intelligible :)

Yet to me it seems preferable to format a string saying "unable to find %s font file". Especially when it comes to making it translatable into other locales for users who don't speak English.

OTOH I don't want to write that to stderr from my library code because the application using it might catch said error and try a different file location.

---

### Post by psusi on 2010-10-25
No, I mean if you have a "can not find file" exception, then its ctor should take the name of the file as the argument, and format that into the string you want.

---

### Post by worksofcraft on 2010-10-25
> **psusi said:**
> No, I mean if you have a "can not find file" exception, then its ctor should take the name of the file as the argument, and format that into the string you want.

Good idea,I'll combine both facilities then :)
[php]
#include <stdio.h> // vsnprintf
#include <cstdarg> // for fail message generator
#include <stdlib.h> // exit
#include <exception> // common base class for exceptions

// form exception message
struct my_error: std::exception {
	// error message for std::exception
	const char * pErrorMessage; // actual message
	virtual const char* what() const throw() { return pErrorMessage; }

	// facility to format a short "last error" message
	static char aErrorText[100]; // default short description of the error
	static bool fail(const char *pFmt, ...) {
		va_list L;
		va_start(L, pFmt);
		vsnprintf(aErrorText, sizeof(aErrorText), pFmt, L);
		va_end(L);
		return false;
	}
	// by default point to what was prepared with most recent call to fail
	my_error(): pErrorMessage(&aErrorText[0]) {}
};

// default last error message
char my_error::aErrorText[] = "no error message supplied";

// base class for all ft_library problems
struct ft_problem: my_error {}; // can thus catch them as a group

// a specific ft_library error class, might catch this to
// try a differnt path or font file name.
struct ft_fontnotfound: ft_problem {
	ft_fontnotfound(const char *pFileName) {
		fail("unable to open %s font file", pFileName);
	}
};

int main(int argc, char *argv[]) {
	// for sake of argument imagine that argv[0] is the
	// freetype font face library we wanted but we fail to open it
	throw ft_fontnotfound(argv[0]);
	return !printf("exits normally\n");
}
[/php]

---

### Post by psusi on 2010-10-25
Good, now get rid of the redundant fail() function and the *printf C-ism.  Change the error string from char * to std::string, then the ctor just needs to errstring << "unable to open" << filename << "font file".

---

### Post by worksofcraft on 2010-10-25
> **psusi said:**
> Good, now get rid of the redundant fail() function and the *printf C-ism.  Change the error string from char * to std::string, then the ctor just needs to errstring << "unable to open" << filename << "font file".

[LIST]
[*]I prefer using Glib::ustring so it will handle utf-8 correctly. However I would still be concerned about it's function when there is an out-of-memory error.

[*]Stream manipulators for rendering things like hexadecimal with leading zeros along with say floating point with two decimal places is simply painful.

[*]Attempting to translate fragmented sentences interspersed with parameters is an internationalization nightmare.
[/LIST]

Some parts of good old C are simply too good to sacrifice on that altar of OO-ism ;)

---

### Post by worksofcraft on 2010-10-25
Anyway I decided not to be swayed by my own preconceptions... so following this page in [Glib reference manual]("http://library.gnome.org/devel/glibmm/2.23/classGlib_1_1ustring.html#a231dbca90eb151d43ac3c8062e089cba") it should be able to write it in real C++ but I can't get it to compile :confused:

[php]
//g++ -Wall err_str.cpp `pkg-config gtkmm-2.4 --cflags`
#include <glibmm/ustring.h>
#include <exception> // common base class for exceptions
#include <iostream>
#include <iomanip>

// try to make the syntax a bit less painful
using namespace std;

struct my_error: exception {
	Glib::ustring sErrorMessage;
	virtual const char* what() const throw() { return sErrorMessage.c_str(); }
};

// base class for all ft_library problems
struct ft_problem: my_error {}; // can thus catch them as a group

// show invalid rgb color mask in hex
struct ft_colormaskfail: ft_problem {
	ft_colormaskfail(unsigned rgb_mask) {
		sErrorMessage = Glib::ustring::format(
			"rgb mask ", setbase(16), setw(8), setfill('0'), rgb_mask, " is not value");
	}
};

int main() {
	throw ft_colormaskfail(0x1000000);
	cout << "exits normally" << endl;
	return 0;
}
[/php]

---

### Post by nvteighen on 2010-10-26
Well, for instance, you're not linking against the library. Use:

```

g++ -Wall -Werror -pedantic err_str.cpp `pkg-config gtkmm-2.4 --cflags **--libs**` 

```

Now, even adding --libs, the whole thing blows up into several cryptic compiler errors.

---

### Post by worksofcraft on 2010-10-26
> **nvteighen said:**
> Well, for instance, you're not linking against the library. Use:

```

g++ -Wall -Werror -pedantic err_str.cpp `pkg-config gtkmm-2.4 --cflags **--libs**` 

```

Now, even adding --libs, the whole thing blows up into several cryptic compiler errors.

Indeed it never gets to linking the libraries :( When I quit programming, main stream C++ compilers simply didn't support exception handling so I hadn't used it before and my simple "fail" function would exit the application. That's sorted now, but we do see it's not easy to then carry on and replace old C style strings with advanced C++ string classes:

Here I attempt to instruct the compiler to pick a template based on the number of parameters supplied.

Behind the scenes the compiler is then expected to generate a special and dedicated function for the exact types of those parameters in this particular spot here.

According to the documentation, somehow inside said function it is allegedly going to be invoking standard i/o stream manipulator instances to manipulate conversions of a number into a string for concatenation into it's ustring container class even though there isn't an actual i/o stream in sight :shock:

Even if it did work and ignoring the practical points mentioned earlier, my mind just boggles at such style of coding and I ask myself how intelligible it would be to other programmers?

---

