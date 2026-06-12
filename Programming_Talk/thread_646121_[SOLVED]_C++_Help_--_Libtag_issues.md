---
title: "[SOLVED] C++ Help -- Libtag issues"
date: 2007-12-20
forum: Programming Talk
---

### Post by t3hi3x on 2007-12-20
I am having some issues. I am using the libtag library for reading tags

this code is acting weird. the example programs show cout-ing the tags using the operator "->"

This part of code throws weird errors:

[PHP]
      file_title = tag->title();
      file_artist = tag->artist();
      file_album = tag->album();
      file_year = tag->year();
      file_comment = tag->comment();
      file_track = tag->track();
      file_genre = tag->genre();
[/PHP]

Errors:
```

apbresh@pluto:~/teraTunes$ g++ -I/usr/include/mysql -I/usr/include/mysql++ -c ttaddone.cpp `taglib-config --cflags --libs` -o ttadd -ltag -lmysql++
ttaddone.cpp: In function ‘int main(int, char**)’:
ttaddone.cpp:35: error: no match for ‘operator=’ in ‘file_title = #‘obj_type_ref’ not supported by dump_expr#<expression error>()’
/usr/include/c++/4.1.3/bits/basic_string.h:485: note: candidates are: std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(const std::basic_string<_CharT, _Traits, _Alloc>&) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
/usr/include/c++/4.1.3/bits/basic_string.h:493: note:                 std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(const _CharT*) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
/usr/include/c++/4.1.3/bits/basic_string.h:504: note:                 std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(_CharT) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
ttaddone.cpp:36: error: no match for ‘operator=’ in ‘file_artist = #‘obj_type_ref’ not supported by dump_expr#<expression error>()’
/usr/include/c++/4.1.3/bits/basic_string.h:485: note: candidates are: std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(const std::basic_string<_CharT, _Traits, _Alloc>&) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
/usr/include/c++/4.1.3/bits/basic_string.h:493: note:                 std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(const _CharT*) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
/usr/include/c++/4.1.3/bits/basic_string.h:504: note:                 std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(_CharT) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
ttaddone.cpp:37: error: no match for ‘operator=’ in ‘file_album = #‘obj_type_ref’ not supported by dump_expr#<expression error>()’
/usr/include/c++/4.1.3/bits/basic_string.h:485: note: candidates are: std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(const std::basic_string<_CharT, _Traits, _Alloc>&) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
/usr/include/c++/4.1.3/bits/basic_string.h:493: note:                 std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(const _CharT*) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
/usr/include/c++/4.1.3/bits/basic_string.h:504: note:                 std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(_CharT) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
ttaddone.cpp:39: error: no match for ‘operator=’ in ‘file_comment = #‘obj_type_ref’ not supported by dump_expr#<expression error>()’
/usr/include/c++/4.1.3/bits/basic_string.h:485: note: candidates are: std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(const std::basic_string<_CharT, _Traits, _Alloc>&) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
/usr/include/c++/4.1.3/bits/basic_string.h:493: note:                 std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(const _CharT*) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
/usr/include/c++/4.1.3/bits/basic_string.h:504: note:                 std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(_CharT) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
ttaddone.cpp:41: error: no match for ‘operator=’ in ‘file_genre = #‘obj_type_ref’ not supported by dump_expr#<expression error>()’
/usr/include/c++/4.1.3/bits/basic_string.h:485: note: candidates are: std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(const std::basic_string<_CharT, _Traits, _Alloc>&) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
/usr/include/c++/4.1.3/bits/basic_string.h:493: note:                 std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(const _CharT*) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
/usr/include/c++/4.1.3/bits/basic_string.h:504: note:                 std::basic_string<_CharT, _Traits, _Alloc>& std::basic_string<_CharT, _Traits, _Alloc>::operator=(_CharT) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]

```
The code compiles fine without that code, but this still there code:

[PHP]      cout << "title   - \"" << tag->title()   << "\"" << endl;
      cout << "artist  - \"" << tag->artist()  << "\"" << endl;
      cout << "album   - \"" << tag->album()   << "\"" << endl;
      cout << "year    - \"" << tag->year()    << "\"" << endl;
      cout << "comment - \"" << tag->comment() << "\"" << endl;
      cout << "track   - \"" << tag->track()   << "\"" << endl;
      cout << "genre   - \"" << tag->genre()   << "\"" << endl;[/PHP]

I don't understand the difference between cout-ing the thing and storing them in declared strings. Also note that year and track DO NOT show up on the error list.

I know I missing something fundamental, but I am not sure exactly what that is.

Anybody know?

---

### Post by revanthedarth on 2007-12-21
std::string cannot convert ints to strings. You should do something like:

```
string toString(T t)
{
    stringstream out;
    out << t;
    return out.str();
}
```

Then,  file_year = toString(tag->year()) should work.
Cout has overloaded operator for int, double, float, etc. But String doesnt have one. So, it's not about Libtag, it's about STL.

---

### Post by t3hi3x on 2007-12-22
Thanks. I was actually thinking of something like that, but I didn't know that class existed. 

Did exactly what I needed. Converted Taglib::String to std::String.

---

### Post by Jessehk on 2007-12-22
> **revanthedarth said:**
> 
Cout has overloaded operator for int, double, float, etc. But String doesnt have one. So, it's not about Libtag, it's about STL.

Huh?

```

#include <iostream>
#include <string>

int main() {
    std::string str( "hello" );
    
    std::cout << str << std::endl;
}

```

```

$ ./example 
hello

```

---

### Post by revanthedarth on 2007-12-22
You got it wrong. cout has overloaded operator for int, float, string, char, char* etc.

```

int hey = 16;
float h2=3.86;
string str = "HELLO";
cout << hey << h2 << str;

```
But string doesn't have one.
```

string str;
int a = 16;
str = "a is " + a;

```

So, i meant that
cout has operator<<(int), but string doesnt have operator+(int).  So, you need to use stringstreams.

```

#include <fstream>
#include <string>
#include <iostream>
using namespace std;
int main()
{
	int a=66;
	string str = "HELLO";
	str += a;
	cout << str << "\n";
}

```
```

 ./a.out
HELLOB

```
HELLOB, because 66 is 'B'. But if you want HELLO66 for your string, you have to use stringstreams.

---

### Post by Jessehk on 2007-12-22
> **revanthedarth said:**
> You got it wrong

So, i meant that
cout has operator<<(int), but string doesnt have operator+(int).  So, you need to use stringstreams.


That's not what you said in your previous post at all.

You said, and I quote:
> 
Cout has overloaded operator for int, double, float, etc. But String doesnt have one. So, it's not about Libtag, it's about STL.


I think you are responsible for the misunderstanding as to me, that reads "std::cout is not overloaded for std::string".

---

### Post by t3hi3x on 2007-12-23
> 
HELLOB, because 66 is 'B'. But if you want HELLO66 for your string, you have to use stringstreams.

This was very helpful in me understanding the basics behind std::string.

Thanks.

---

### Post by revanthedarth on 2007-12-23
I said, "Cout has overloaded operator for int, double, float, etc. But String doesnt have one. So, it's not about Libtag, it's about STL.". What i meant was, cout has overloaded operator<< for int, double, float. But String doesn't have overloaded operator+ or operator= for int, double, float. 

cout HAS overloaded operator<< for string, yes. But i didn't (try to) mean that or otherwise.

---

### Post by t3hi3x on 2007-12-23
I understand what you meant due to the fact I was already on the right track to figure out what the prob was. I also do understand how it could have been confusing, and it was good to clear that up and go deeper to what is happening in those functions.

---

### Post by t3hi3x on 2007-12-23
I also wanted to clear up that Taglib has its own type:

Taglib::String

The problem was trying to convert Taglib::string to std::string. The function I made as follows:

[PHP]using namespace std;

string to_string(TagLib::String s)
{
	stringstream string_out;
	string_out << s;
	return string_out.str();
}[/PHP]

Would this be the most efficient way to process the strings?

---

### Post by revanthedarth on 2007-12-23
Hmm... I googled for TagLib::String, and here is what i've found:

It has a toCString(bool) function, returning a const char*. That would be better. I never used it, but it seems to work like std::string::c_str() function. You may have to free the returining value of that function, i do not know. But toCString function would be a better way, i guess. 

And, know that ostringstream doesn't have a overloaded operator<< for TagLib::String. TagLib::String has overloaded operator<< for ostringstream. So, if you think of making a container and you'd like to print its members, you may overload operator<< for ostringstream.

The link is [http://developer.kde.org/~wheeler/taglib/api/classTagLib_1_1String.html](http://developer.kde.org/~wheeler/taglib/api/classTagLib_1_1String.html)

By the way, use templates for that kind of function, you won't need to overload for another type even if you need to:
```

using namespace std;
template <typename T>
string toString(T s)
{
    stringstream string_out;
    string_out << s;
    return string_out.str();
}

```

---

