---
title: "class library for numbers - printing to string?"
date: 2009-06-05
forum: Programming Talk
---

### Post by Bulletbeast on 2009-06-05
Hi. Does anyone familiar with the CLN library know how can I convert an integer (cl_I) to a string, in the manner of sprintf and the like? The documentation article says a lot about printing to ostreams, and a bit on the internal representation, but nothing about simply printing a number to a string...

---

### Post by Habbit on 2009-06-05
If you can print it to a ostream, then you can print it to a string, just use a stringstream.

---

### Post by MadCow108 on 2009-06-05
I haven't got it installed so I can't test.
but the following should work:

edit: have tested it now, works.
note that you have to include <cln/*type*_io.h> where type is for example integer or real.
stringstream is included in <sstream>
editend

```

std::stringstream ss;
cl_I integer = 5;
//declaration of fprint: fprint (std::ostream& stream, const type& x)
fprint (ss, integer)
std::cout << ss.str() << std::endl;

```

according to documentation it should even have overloaded the << operator:
[http://www.ginac.de/CLN/cln_5.html#SEC47](http://www.ginac.de/CLN/cln_5.html#SEC47)
   std::ostream& operator<< (std::ostream& stream, const type& x)

so this should work to:
```

std::stringstream ss;
cl_I integer = 5;
cl_R real = 5.34253;
ss << integer << " - " << real;
std::cout << ss.str() << std::endl;

```
(str() returns the c++ string of the stringstream)
[http://www.cplusplus.com/reference/iostream/stringstream/](http://www.cplusplus.com/reference/iostream/stringstream/)

also note following in the docu:
> The output may depend on the global printer settings in the variable default_print_flags. **The ostream flags and settings (flags, width and locale) are ignored.**

---

### Post by Bulletbeast on 2009-06-05
Great, thanks. So ss.str().cstring() should work for me I guess.

---

### Post by Bulletbeast on 2009-06-05
What I copied from cplusplus.com's article on stringstream's constructor, namely

stringstream smess (stringstream::in | stringstream::out);

results in:

variable `std::stringstream smess' has initializer but incomplete type
incomplete type `std::stringstream' used in nested name specifier

Why?

---

### Post by MadCow108 on 2009-06-05
have you included sstream?
#include <sstream>

btw get the cstring from a c++ string is c_str() not cstring()
but generally you should avoid c strings if possible in c++ the string class is more flexible and saver.

---

### Post by Bulletbeast on 2009-06-05
I thought so, but I hadn't. I added it, and that error went away, however:

fprintdecimal(smess,total_mass);
sprintf(mess,"Total mass: %s",smess.str.c_str());

==>>

insufficient contextual information to determine type

edit: huh, did I write cstring()? wtf. I know it's c_str()...

---

### Post by MadCow108 on 2009-06-05
if your using streams you don't need to use the c printf functions.
Just do this:

smess <<"Total mass: "<< total_mass;

or 
smess << "Total mass: ";
fprintdecimal(smess,total_mass);

the problem with your code is that str is missing its brackets
sprintf(mess,"Total mass: %s",smess.str**()**.c_str());

you also shouldn't use sprintf, use the better snprintf function. (if you really need to use c code)

---

### Post by Bulletbeast on 2009-06-05
mess and smess were two different variables, and my goal wasn't to get "Total mass: " into smess, but to get "Total mass: " and smess into mess. Thanks for the help, though.

---

### Post by MadCow108 on 2009-06-05
I don't quite understand. sprintf is going to overwrite mess anyway so it makes no difference if you have Total mass: in smess or mess as you can always extract the cstring from the stringstream at any time.
cl_R total_mass = 2.2323;
smess << "Total mass: " << total_mass; // smess now holds: "Total mass: 2.2323"
char mess[smess.str().size()];
snprintf(mess,smess.str().size(),"%s",smess.str().c_str()); // mess now holds: "Total mass: 2.2323"

now mess holds ther same like smess (although its now a waste of memory as smess and mess both hold the same data).

---

### Post by Bulletbeast on 2009-06-05
cl_I total_mass=12900000; ...
Now total_mass goes into smess, because CLN can't work with C strings, and the contents of smess gets sprintf'd into mess, with the format, sprintf(mess, "Total mass: %s", smess);

---

### Post by MadCow108 on 2009-06-05
why not do the formating with a stream?

int i=0;
double d=0.3423;
const char * cstr = "cstring"
string str="string"
stream << "i can format ints "<<i<<" and doubles "<<d<<" and cstrings"<< cstr<<" and c++strings" << str << "and any other built in type (including the CLN thanks to overloading of <<"<< endl;

streams are the sprintf of c++

but I think I understood what you wanted to archive. As long as you take care of the boundaries of your char array it's ok.
(But watch out CLN ints can have unlimited size so buffer overflows are possible)

---

### Post by Bulletbeast on 2009-06-05
My total mass isn't unlimited, though. 1.29x10^12 at most.

However, I'm getting quite confused with CLN. It's quite strongly-typed, and I can't seem to figure out why some things aren't working... For example, this:

```

cl_I i_number;
cl_FF f_number;

cl_FF a;
cl_I b;

while (true)
{
  cin >> a >> b;
  f_number=expt(a,b);
  cout << f_number << endl;
}

```
A simple test program to output a to the bth until stopped, no? But it says:

no match for 'operator=' in 'f_number = cln::expt(const cln::cl_R&, const cln::cl_I&)(((const cln::cl_I&)((const cln::cl_I*)(&b))))'
candidates are...

Also, my masses are given in M.MMx10^N format. Once I calculate this, however, it should expand to an integer, something like 15000000 or 2692000000000, and how would I then convert it to cl_I? I'm not sure I'm getting the hang of this library...

---

### Post by MadCow108 on 2009-06-05
It seems expt is not defined for cl_FF
it is defined for cl_R so could use that (I expect that this even gives less rounding errors than using single floats).

or use cl_F and use the cl_float function:
f_number=cl_float(expt(a,b));
[http://www.ginac.de/CLN/cln_4.html#SEC40](http://www.ginac.de/CLN/cln_4.html#SEC40)

according to this using F is better than using FF anyway: [http://www.ginac.de/CLN/cln_3.html#SEC13](http://www.ginac.de/CLN/cln_3.html#SEC13)
> As a user of CLN, you can forget about the differences between the four floating-point types and just declare all your floating-point variables as being of type cl_F. [..] Also, many transcendental functions have been declared as returning a cl_F when the argument is a cl_F, but such declarations are missing for the types cl_SF, cl_FF, cl_DF, cl_LF

you can convert from Real or float to integer with for example round1. [http://www.ginac.de/CLN/cln_4.html#SEC26](http://www.ginac.de/CLN/cln_4.html#SEC26)

---

### Post by Bulletbeast on 2009-06-05
We're getting to something here. However, letting CLN calculate 600x10^9 with floor1(cl_float(cl_I(600))*expt(10.0,9)) yields something among the lines of 599999971328. I know about the inherent gotchas of floating point, but isn't there any way to be a bit more accurate here, at least up to the aforementioned limit of 1.29x10^12? Maybe enforcing cl_DF or even cl_LF in some way?

By the way, you've been a great help MadCow108. Thank you very much (:

---

### Post by MadCow108 on 2009-06-05
stay with the real numbers and integer types as long as possible. The Real type is exact for rational numbers (and complex with rational parts).
It should keep at least double precision when handling irrational numbers.

The Float type on the other hand has limited precision for any number.
(Its still better than the standard c float as it reduces errors in +,-,/,*,sqrt operations by converting the float to a real and returns the nearest float to that real number.)

So only convert to Floats in the last step when you have done all calculations and want to save the data.

eg this (yours without conversion to float):
cl_I result = floor1(cl_I(600)*expt(10.0,9));
or
cl_R result = cl_R(600.01)*exp(10.0,9);
give exact results.

apologies for when my answers aren't always consistent, I just learning the library myself (as it could be useful for future applications of mine)

---

