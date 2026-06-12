---
title: "G++ help."
date: 2006-01-09
forum: Programming Talk
---

### Post by Jimmey on 2006-01-09
Simple, hello world: 
```
Include <iostream>

using namespace std;

int main(){
                cout << "Hello world.";
                cin.get;
}


```

With G++:

> g++ /home/james/programming/hello.cpp

Returns: 

> /usr/include/c++/4.0.2/bits/locale_facets.tcc:2648: error: ‘mbstate_t’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2648: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2649: error: ‘mbstate_t’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2649: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2649: error: template-id ‘use_facet<<expression error> >’ for ‘const int& std::use_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2705: error: ‘mbstate_t’ was not declared in this scope
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2705: error: template argument 3 is invalid
/usr/include/c++/4.0.2/bits/locale_facets.tcc:2705: error: template-id ‘has_facet<<expression error> >’ for ‘bool std::has_facet(const std::locale&)’ does not match any template declaration
/usr/include/c++/4.0.2/ostream: In instantiation of ‘std::basic_ostream<char, std::char_traits<char> >’:
/usr/include/c++/4.0.2/bits/ostream.tcc:680:   instantiated from here
/usr/include/c++/4.0.2/ostream:64: error: no type named ‘off_type’ in ‘struct std::char_traits<char>’
/usr/include/c++/4.0.2/bits/ostream.tcc:451: error: no type named ‘off_type’ in ‘struct std::char_traits<char>’
/usr/include/c++/4.0.2/ostream: In instantiation of ‘std::basic_ostream<wchar_t, std::char_traits<wchar_t> >’:
/usr/include/c++/4.0.2/bits/ostream.tcc:692:   instantiated from here
/usr/include/c++/4.0.2/ostream:62: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/ostream:64: error: no type named ‘off_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/bits/ostream.tcc:451: error: no type named ‘off_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream: In instantiation of ‘std::basic_istream<char, std::char_traits<char> >’:
/usr/include/c++/4.0.2/istream:580:   instantiated from here
/usr/include/c++/4.0.2/istream:65: error: no type named ‘off_type’ in ‘struct std::char_traits<char>’
/usr/include/c++/4.0.2/istream:569: error: no type named ‘off_type’ in ‘struct std::char_traits<char>’
/usr/include/c++/4.0.2/istream: In instantiation of ‘std::basic_istream<wchar_t, std::char_traits<wchar_t> >’:
/usr/include/c++/4.0.2/istream:596:   instantiated from here
/usr/include/c++/4.0.2/istream:63: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream:65: error: no type named ‘off_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream:272: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream:427: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream:438: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream:569: error: no type named ‘off_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream: In instantiation of ‘std::basic_iostream<char, std::char_traits<char> >’:
/usr/include/c++/4.0.2/bits/istream.tcc:1273:   instantiated from here
/usr/include/c++/4.0.2/istream:757: error: no type named ‘off_type’ in ‘struct std::char_traits<char>’
/usr/include/c++/4.0.2/istream: In instantiation of ‘std::basic_istream<wchar_t, std::char_traits<wchar_t> >::sentry’:
/usr/include/c++/4.0.2/bits/istream.tcc:1276:   instantiated from here
/usr/include/c++/4.0.2/istream:630: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream: In instantiation of ‘std::basic_iostream<wchar_t, std::char_traits<wchar_t> >’:
/usr/include/c++/4.0.2/bits/istream.tcc:1281:   instantiated from here
/usr/include/c++/4.0.2/istream:755: error: no type named ‘int_type’ in ‘struct std::char_traits<wchar_t>’
/usr/include/c++/4.0.2/istream:757: error: no type named ‘off_type’ in ‘struct std::char_traits<wchar_t>’
james@ubuntu:~$

Ehrm...Help?

---

### Post by mostwanted on 2006-01-09
```
#include <iostream>

using namespace std;

int main()
{
	cout << "Hello world.";
	cin.get();
	return 0;
}
```

You forgot # and c++ is not case-insensitive, so it's #include. cin.get() is a method, remember parantheses, they're not optional either. Also, remember to return 0 at the end of your function, otherwise declare it void instead of int if you don't want to return anything.

---

### Post by m87 on 2006-01-09
[quote=Jimmey]Simple, hello world: 
```
Include <iostream>

using namespace std;

int main(){
                cout << "Hello world.";
                cin.get;
}


``` 

Ehrm...Help?[/quote]
to "include" you should use a preprocessor directive (which starts with #), which is #include (lowercase).
then, get() is a method, therefore you should put cin.get () (with the brackets), but here it's useless because it does nothing but getting stuff and exiting :)

~marco

---

### Post by Jimmey on 2006-01-09
Yeah, I already had 
```
#include <iostream>
```, I just spelled it wrong, so that's not the problem :(
Here's a copied + pasted version
```
#include <iostream>

using namespace std;

int main(){
	cout << "Hello, world!";
	cin.get();
	return 0;

}

```

---

### Post by Jimmey on 2006-01-09
Shouldn't really be bumping, but I'd like to screw around with C++.

---

### Post by Adrian on 2006-01-09
[QUOTE=Jimmey]Shouldn't really be bumping, but I'd like to screw around with C++.[/QUOTE] Well, I copied your code and compiled it on my computer. No problems at all. I have no idea :/

---

### Post by Jimmey on 2006-01-09
Hahaha, that's well harsh!

What could be the problem?

I'll try like, un and re installing. See what that does.

Might it be anything to do with GCC?

---

### Post by kperkins on 2006-01-09
Strange, it compiles fine for me. 
doing g++ helloworld.cpp -o helloworld

---

### Post by Jimmey on 2006-01-09
Naw, it's getting beyond unfair now, when I tried compiling something from source earlier....

> james@ubuntu:~/Desktop/tmsnc-0.3.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


---

### Post by coredump on 2006-01-09
That's the second time I've seen the error message "C compiler cannot create executables".  If there's a way to search the forums, that'd be worth looking for.

---

### Post by kperkins on 2006-01-09
do you have build-essentials, linux-kernel-headers, and glibc-dev installed?

---

