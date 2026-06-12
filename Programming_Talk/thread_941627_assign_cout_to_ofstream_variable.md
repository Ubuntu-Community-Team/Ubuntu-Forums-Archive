---
title: "assign cout to ofstream variable"
date: 2008-10-08
forum: Programming Talk
---

### Post by monkeyking on 2008-10-08
I have a huge class with many cout statements,
but sometimes I want to write it to a file.

So I was thinking about, since cout works the same way as ofstream.
Of having a general "ofstream os". 
So at class instantiation, I want to be able to choose which stream.
like

[PHP]
ostream os;
if(writeToScreen)
  os = cout;
else
  os.open("myfile");
[/PHP]
This is the idea, but this of cause doesnt' work.
I found this example, that uses ref's to a ofstream.
[http://stdcxx.apache.org/doc/stdlibug/34-2.html](http://stdcxx.apache.org/doc/stdlibug/34-2.html) (bottem)
[PHP]
int main(int argc, char *argv[])
{
  std::ostream& fr;
  if (argc > 1)
    fr = *(new std::ofstream(argv[1]));
  else
    fr = std::cout;

  fr << "Hello world!" << std::endl;

  if (&fr!=&std::cout) 
    delete(&fr);
}
[/PHP]
This won't even compile.

Does anyone hav an idea?
or should I just do a if statement each time I want to write?

thanks in advance.

/thorfinn

---

### Post by Zugzwang on 2008-10-08
Next time, please also copy&paste the errors you are getting.

This version works well here:

[PHP]
#include <iostream>
#include <fstream>

int main(int argc, char *argv[])
{
  std::ostream& fr = (argc > 1)?*(new std::ofstream(argv[1])):std::cout;

  fr << "Hello world!" << std::endl;

  if (&fr!=&std::cout) 
    delete(&fr);
}
[/PHP]

---

### Post by bfhicks on 2008-10-08
Define a macro at the top to do what you want. This is an example of using an ifstream instead of cin. You can do the same for ofstream and cout.

```
[color=#BC7A00]#include <iostream>
#include <fstream>
#include <string>
[/color]
[color=#008000]**using**[/color] [color=#008000]**namespace**[/color] std;

[color=#408080][i]//ifstream fin("cube.txt");
//#define cin fin
[/i][/color]
[color=#B00040]int[/color] main()
{
	string line;
	[color=#008000]**while**[/color] (getline(cin,line))
	{
		cout [color=#666666]<<[/color] line [color=#666666]<<[/color] endl;
	}
	
	[color=#008000]**return**[/color] [color=#666666]1[/color];
}

```

Simply uncomment the #define's at the beginning. This simple example will echo back what you type. If you uncomment out, it'll print out the lines in the file.

---

### Post by Zugzwang on 2008-10-08
> **bfhicks said:**
> Define a macro at the top to do what you want. This is an example of using an ifstream instead of cin. You can do the same for ofstream and cout.

[...]

Simply uncomment the #define's at the beginning. This simple example will echo back what you type. If you uncomment out, it'll print out the lines in the file.

Well, the OP wanted to select his/her output "device" at runtime, your solution fixes that at compile time.

---

### Post by monkeyking on 2008-10-08
Thanks zugzwang,
Now I can initalize it,
but I'me having trouble doing it from a class initializer.

This code:
[PHP]
class cls{
  std::ofstream& os;
public:
  cls(string str);
  int test();
};

cls::cls(string str) : os((str.compare(""))?std::cout:*(new std::ofstream(str.c_str())))// <- error is here
{
}

int cls::test(){
  os << "test in yes\n";
  return 0;
}
[/PHP]

Generates the following error:
[PHP]
error: invalid initialization of reference of type ‘std::ofstream&’ from expression of type ‘std::ostream’
[/PHP]

This problem is awkward.

thanks in advance.

---

### Post by dribeas on 2008-10-08
> **monkeyking said:**
> 
[PHP]
class cls{
  std::ofstream& os;
public:
  cls(string str);
  int test();
};

cls::cls(string str) : os((str.compare(""))?std::cout:*(new std::ofstream(str.c_str())))// <- error is here
{
}
[/PHP]


Types do not match. Change os to std:: ostream&. The reason is that std:: ofstream derives from std:: ostream, so that you can have a std:: ostream& referring to an std:: ofstream. But the opposite is not true.

```

std::ofstream f( "file.txt" );
std::ofstream &fr( f );         // ok exact type
std::ostream &or1( std::cout ); // ok exact type
std::ostream &or2( f );         // ok std::ostream is a base of std::ofstream
std::ofstream &fr2( std::cout ); // !error, std::ofstream is not a base of std::ostream

```

Also note that you are creating an std:: ofstream object that may never be destroyed. This might be fine with you (if you only use one cls object whose lifetime extends the whole application lifetime), but keep that in mind if you go creating and destroying cls objects around, as you are acquiring resources you do not free.

---

### Post by monkeyking on 2008-10-08
Hi thanks, it works now.
For the sake of completeness,
heres is my full code that works, also with a destructor.

Nasty syntax in the constructor though.

[PHP]#include <iostream>
#include <fstream>
#include <string>

using namespace std;

class cls{
  std::ostream& os;
public:
  cls(string str);
  ~cls() {if (&os!=&std::cout)     delete(&os);}
  int test();
};

cls::cls(string str) : os((!str.compare(""))?std::cout:*(new std::ofstream(str.c_str())))
{
}

int cls::test(){
  os << "printing in stream writer function";
  return 0;
}

int main(int argc, char *argv[]){
  cls kls("");
  kls.test();
}
[/PHP]
If cls is being called with "", then outstream will be screen, otherwise it will be written into the filename given.

---

### Post by dribeas on 2008-10-08
Depending on your system/application, you can just forget about handling it internally and greatly simplify your code:

```

class cls
{
public:
   cls( std::ostream & o ) : os( o ) {};
   void test();
private:
   std::ostream & os;
};

int main()
{
   cls c1( std::cout ); // functionally equivalent to c1("") in your code

   std::ofstream file( "file.txt" );
   cls c2( file ); // functionally equivalent to c1("file.txt")
}

```

But you must be careful that the lifetime of *file* last at least as long as that of *c2* which in some cases will be feasible while in some others it won't be.

---

