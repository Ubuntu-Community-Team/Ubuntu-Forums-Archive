---
title: "deleting a ofstream"
date: 2009-07-04
forum: Programming Talk
---

### Post by monkeyking on 2009-07-04
Can anyone help me closing a ofstream referenced by ostream

Maybe its not even possible.
[PHP]
#include <iostream>
#include <fstream>
#include <string>

void print(std::ostream& os,std::string str){
  os << str << std::endl;
//how do i close the file if I'm not using cout
}


int main(int argc, char** argv){

  std::ofstream o;
  std::string fnams;
  if(argc>1 && argv[1]){
    fnams=argv[1];
    o.open(argv[1]);
  }

  std::ostream& out = fnams.empty()?std::cout:o; 
  print(out,"teaea");
  return 0;
}



[/PHP]

---

### Post by MadCow108 on 2009-07-04
edit:
this should do what you want:
```

try
{
 ofstream* file = dynamic_cast<ofstream*>(&os);
 if (file != NULL)
   file->close();
} catch (exception& e) {cout << "Exception: " << e.what();}

```
or
```

#include <typeinfo>
...
if (typeid(os) == typeid(ofstream))
{
  (ofstream&)os.close();
}

```
another way would be to just override the function for ofstreams

---
my first probably wrong answer:

you don't need to delete it as its created on stack
it deletes itself when it goes out of scope
you can define a finer scope with angle brackets { }

of course you should close the stream when finished with ostream.close()

---

### Post by monkeyking on 2009-07-04
Hmm,
thanks for you reply Madcow, but I can't get it to work.

This reassigning of the iostreams in c++ are quite counterintuitive compared to the stl generally,

[PHP]
#include <iostream>
#include <fstream>
#include <string>
#include <typeinfo>

void print(std::ostream& os,std::string str){
  os << str << std::endl;
  if(typeid(os)==typeid(std::ofstream))
    (std::ofstream&) os.close();
}


int main(int argc, char** argv){

  std::ofstream o;
  std::string fnams;
  if(argc>1 && argv[1]){
    fnams=argv[1];
    o.open(argv[1]);
  }

  std::ostream& out = fnams.empty()?std::cout:o; 
  print(out,"teaea");
  return 0;
}

[/PHP]


```

Compilation started at Sun Jul  5 03:00:21

g++ tst.cpp
tst.cpp: In function ‘void print(std::ostream&, std::string)’:
tst.cpp:9: error: ‘struct std::basic_ostream<char, std::char_traits<char> >’ has no member named ‘close’

Compilation exited abnormally with code 1 at Sun Jul  5 03:00:21




```

---

### Post by dwhitney67 on 2009-07-05
Why do you feel compelled to close the ostream object yourself?  Why not just let the program take care of that automatically when the object (whether it be an ofstream or ostream) falls out of scope and is destroyed?  The close() method should be used judiciously, and not necessarily all of the time -- contrary to what you see in text books or other tutorials.

Anyhow, aside from my simple suggestion above, if you examine the API carefully (read here for [details]("http://www.cplusplus.com/reference/iostream/")), you will notice that there is no close() method associated with cout, or for that matter, cerr/clog/cin.

P.S.  Another way to write your program:
```

#include <iostream>
#include <fstream>
#include <string>

void print(std::ostream& os, const std::string& str) {
  os << str << std::endl;
}


int main(int argc, char** argv) {

  std::ostream* o = (argc > 1 ? new std::ofstream(argv[1]) : &std::cout);

  print(*o,"teaea");

  if (o != &std::cout)
    delete o;
}

```

P.S.S.  [rant] Why is it when programmers put the opening curly bracket at the end of the line, as shown above, they feel compelled to insert a blank line afterwards?  Is it for readability?  Would it not be just as pleasing to the eye to insert the curly bracket on this empty line? [/rant]

---

### Post by MadCow108 on 2009-07-05
> **monkeyking said:**
> Hmm,
thanks for you reply Madcow, but I can't get it to work.


i forgot some brackets in my post:
```
((ofstream&)os).close();

```
should work

I'm actually confused about the destructers of the stream classes:
[http://www.cplusplus.com/reference/iostream/filebuf/~filebuf/](http://www.cplusplus.com/reference/iostream/filebuf/~filebuf/)
> Before being destructed, the member function close is automatically called.
this sounds nice. It seems we don't need to close the file it wil close when it goes out of scope
but:
[http://www.cplusplus.com/reference/iostream/ostream/~ostream/](http://www.cplusplus.com/reference/iostream/ostream/~ostream/)
> Note that it does not destroy nor performs any operations on the associated streambuf object.
does that now mean if you call the destructor of ostream it won't call the destructor of streambuf/filebuf?
sounds like a memory leak to me :/

---

### Post by dwhitney67 on 2009-07-05
> **MadCow108 said:**
> ...

this sounds nice. It seems we don't need to close the file it wil close when it goes out of scope
but:
[http://www.cplusplus.com/reference/iostream/ostream/~ostream/](http://www.cplusplus.com/reference/iostream/ostream/~ostream/)

does that now mean if you call the destructor of ostream it won't call the destructor of streambuf/filebuf?
sounds like a memory leak to me :/

streambuf is destroyed by the class object which subclasses ostream.  An example of one of these class objects is cout.

ostream only retains a handle to the streambuf, but does not take ownership of it, hence the reason it does not destroy it.

For (less than) specific details, see [here]("http://www.cplusplus.com/reference/iostream/streambuf/") and [here]("http://www.cplusplus.com/reference/iostream/ostream/ostream/").  Note that the constructor for ostream takes the handle to a streambuf.

---

### Post by monkeyking on 2009-07-05
Hi again,
I never got it to work.
I guess it's impossible then. :)

The syntatic problem for anyone reading is essentially,
that cout is of type ostream, and a filestream is of type ofstream.


I'll try to explain why I want to do this,

I'm calculating a dozen things, and according to which argument my program is supplied with, I want to be able to dump these data into files.

But instead of creating 12 different streams, I just want to assign my already defined stream to a new filehandle

In pseudocode

[PHP]
int main(){
ofstream os;

os.open();
write;
os.close;

os.open();
write;
os.close
etc.
//this should of course be done in different functions, with the cout/ofstream as argument.
}
[/PHP]

So I could do it the c-way by using printf/fprintf,
and the do a branch of a filename(if NULL printf).

I was thinking I could just use the c++ streams, but apparantly this is not so straightforward as I had hoped.

---

### Post by MadCow108 on 2009-07-06
```

#include <iostream>
#include <fstream>
using namespace std;

void write(ostream &os)
{
	os << "Test sentence"<<endl;
}

int main ()
{
  filebuf fb;
  fb.open ("test.txt",ios::out);
  ostream os(&fb);
  write(os);
  fb.close();

//asign new buffer to ostream
 filebuf fb2;
  fb2.open("test2.txt",ios::out);
  os.rdbuf(&fb2);
  write(os);
  fb2.close();
  
  write(cout);
  return 0;
}

```

ostream deletes itself when it goes out of scope

And you can distinguish between ostream and ofstream by dynamic_cast or typeid as I said above (although its not necessary in your problem)

---

### Post by monkeyking on 2009-07-07
Well, yet again, I ended up using a much more c-style approach.
I'm using a fprintf, but if no filename has been specified it will write to stdout.
Much more clean and understandable code. 
[PHP]
int print(const char* fname,const char*str){
  FILE *pFile;
  if(fname)
    pFile = fopen(fname,"w");
  else
    pFile= stdout;
  fprintf(pFile,"%s",str);
  fclose(pFile);
  return 0;
}

int main(int argc, char* argv[]){
  const char* fname;
  
  if(argc!=1 &&argv[1])
    fname=argv[1];

  print(fname,"hey\n");
  
  return 0;

}
[/PHP]

---

### Post by dwhitney67 on 2009-07-07
Do whatever pleases you, but I disagree with your approach.  One thing that is undesirable is that you open the file each time print() is called.  You should open the file just once.  You may also want to verify that you were able to open the file, and if not, default to stdout.

---

### Post by MadCow108 on 2009-07-08
```
int print(string fname, string str){
  filebuf fb;
  streambuf * buffer;
  if (!fname.empty())
  {
  	fb.open (fname.c_str(),ios::out);
  	buffer = &fb;
  }
  else
   buffer = cout.rdbuf();
   
  ostream os(buffer);
  os << str;
  return 0;
}
```

c++ version of yours. hows that less readable?
and as dwhitney said it's not very clever
open the file once and give the print function the stream and not open the stream in the print function
examples have been posted in this thread already

---

### Post by monkeyking on 2009-07-08
Sure, this looks great, much more simple than mine.

But I'm still puzzled by the complexity of sending the ostreams around the program.

---

### Post by dwhitney67 on 2009-07-08
Being puzzled in what way?

On most large projects, one developer usually makes the effort to develop a Logger class that can be initialized with a streambuf.

The Logger class will overload the operator<< so that users can output their data equivalently as when using cout.

It's best to implement the Logger class to be thread-safe, since cout (and cerr) by themselves are not.

Anyhow, if you ever wanted to develop something useful, the Logger class would be it!

P.S.  Many Logger's allow for one to seamlessly suppress the logging from any particular class by using some identifying attribute of the class (e.g. a name) and cross-referencing that class name with configuration data in a file, which indicates whether logging for that class ought to be displayed or suppressed.

---

