---
title: "[SOLVED] Program to Program communication (Python &amp;lt;-&amp;gt; C++) - How?"
date: 2007-08-12
forum: Programming Talk
---

### Post by Senesence on 2007-08-12
I found some documentation about "interprocess communication", the python "subprocess" module, pipes, sockets, and even some stuff talking about shared memory. However, out of all those, I couldn't find one straightforward example that actually implements any single one of those methods.

Maybe there is some magic google functionality that I am not yet aware of, but I honestly couldn't find a thing.

So if someone could make an example for me, using the following setting, I would really appreciate it:

The C++ program:

```

#include <iostream>
using namespace std;

int main(int argc, char* args[])
{
	int python_message, quit;
	python_message = 0;
	quit = 0;
	
	while (quit != 1)
	{
		cin >> python_message;
		
		switch (python_message)
		{
			case 0:
				quit = 1;
				break;
			case 1:
				cout << "First Hello" << endl;
				break;
			case 2:
				cout << "Second Hello" << endl;
				break;
			case 3:
				cout << "Third Hello" << endl;
				break;
			default:
				cout << "Idle" << endl;
		}
	}
	
	return 0;
}

```

The python program with which I want to control the C++ program:

```

state = "run"
coutlist = []

while state != "quit":
	python_message = raw_input("Message to C++: ")
	if python_message != "quit":
		# Send python message to C++ program -- but how exactly?
		print "Sent " + python_message
		# And then I want to get what the C++ program "spits out" in return (it's cout) -- how?
		print "cout from C++ program"
		coutlist.append("cout from C++ program")
	else:
		state = "quit"

```

O, and I should mention that I need the C++ program to keep running - that is to say I can't just send arguments to it and then take the return value. It should be able to communicate while running. It should only terminate when the python control program terminates.

It would be nice if I could get one example for each method (subprocess, pipes, shared memory...), but I'll settle for one. Also, please feel free to comment on what you consider to be the best method (if you can speak from experience).

Tia.

---

### Post by Note360 on 2007-08-12
hmmmm.... I am thinking about writing the python messages to a file... That might just work its almost crazy.

---

### Post by foxylad on 2007-08-12
I don't think you can use shared memory unless both processes are written in c and one was forked by the other.

Pipes are the easiest method, but only work when you run both processes at the same time, so you can "connect" one processes stdout to another's stdin. It looks like you need a two-way pipe, so check python's popen2 and popen3 functions.

Sockets are the best method, because you can leave one process running as a daemon and have temporary client processes connect to it whenever you want. Databases usually use this method, with a daemon listening to a socket for queries, and clients sending queries to the socket. You need to know quite a lot about daemons to do this successfully - google for "unix socket" and the listen function.

---

### Post by Wybiral on 2007-08-12
Do they need to run parallel to each other? If not, you could make a Python module in C++ and execute it's functions from Python.

I suppose you could do the same thing even if they need to be parallel using threads in the module, although I've never done this myself.

But if you can get away with just executing the C++ code via function calls, you can whip up a module pretty easily.

---

### Post by pmasiar on 2007-08-12
[http://docs.python.org/lib/ipc.html](http://docs.python.org/lib/ipc.html) might be a start?

---

### Post by slavik on 2007-08-12
2 words: named pipes
or 1 word: d-bus

:)

Also, in C, it is possible to open another program but redirect the new program's stdin and stdout to your own pipes (dup2 and popen).

---

### Post by the_unforgiven on 2007-08-13
> **pmasiar said:**
> [http://docs.python.org/lib/ipc.html](http://docs.python.org/lib/ipc.html) might be a start?
Yeah, the easiest one being UNIX domain sockets - if the processes are on the same host.
;)

---

### Post by Senesence on 2007-08-13
If you read my original post, you'll notice that I explicitly ask for an example.

I appreciate your opinions on what the best methods are, but without an example implementation I don't really have much use for them. (*I searched through google, and I did find API docs, but no example code.*)

So if anyone is knowledgeable enough to write an example I asked for, please do me that favor.

---

### Post by Wybiral on 2007-08-13
You can't find any examples for unix pipes?

I've personally posted a couple on these forums: [http://ubuntuforums.org/showthread.php?t=497906](http://ubuntuforums.org/showthread.php?t=497906)


Or, after a couple of google searches...

[http://tldp.org/LDP/lpg/node11.html](http://tldp.org/LDP/lpg/node11.html)
[http://www.gnu.org/software/libc/manual/html_node/Creating-a-Pipe.html](http://www.gnu.org/software/libc/manual/html_node/Creating-a-Pipe.html)
[http://www.opengroup.org/onlinepubs/009695399/functions/pipe.html](http://www.opengroup.org/onlinepubs/009695399/functions/pipe.html)
[http://www.gmonline.demon.co.uk/cscene/CS4/CS4-06.html](http://www.gmonline.demon.co.uk/cscene/CS4/CS4-06.html)
[http://docsrv.caldera.com:8457/cgi-bin/info2html?(libc.info.gz)Creating%2520a%2520Pipe](http://docsrv.caldera.com:8457/cgi-bin/info2html?(libc.info.gz)Creating%2520a%2520Pipe)
[http://www.ecst.csuchico.edu/~beej/guide/ipc/pipes.html](http://www.ecst.csuchico.edu/~beej/guide/ipc/pipes.html)
[http://www.math.tau.ac.il/~danha/courses/software1/chapter12.txt](http://www.math.tau.ac.il/~danha/courses/software1/chapter12.txt)
[http://www.cs.uregina.ca/Links/class-info/330/Pipe/pipes.html](http://www.cs.uregina.ca/Links/class-info/330/Pipe/pipes.html)
[http://www.cs.uml.edu/~fredm/courses/91.308/files/pipes.html](http://www.cs.uml.edu/~fredm/courses/91.308/files/pipes.html)

I didn't read them all, but I'm willing to bet at least one of them has an example :)

Google is a tool every developer should learn to use.

I suggest you explain exactly what you need them for... The example you gave looks like a simple module would work... If it's more complex, it would help to know it what way.

---

### Post by Senesence on 2007-08-13
[quote=Wybiral]You can't find any examples for unix pipes?[/quote]

Those are nice, but they're not Python examples. I need to be able to run the C++ program (the one I posted initially) from my Python program, and additionally have the ability to provide that C++ program with stdin and retrieve the resulting stdout *As long as the C++ program is active (note the while loop in the C++ program,)* - all from Python.

I guess asking for any example, for any method was somewhat unrealistic on my part - so if anyone could just show me how to use the Python subprocess module to do the (seemingly) simple communication I already described, that would be great.

[quote=Wybiral]I suggest you explain exactly what you need them for... The example you gave looks like a simple module would work... If it's more complex, it would help to know it what way.[/quote]

I'm just doing this to see if it can be done - that is, to see if I can control a  C++ binary from python <- that's really the essence of what I want to do here.

---

### Post by foxylad on 2007-08-13
You really want to look at popen() in hte python docs. This lets your python program launch another program (c, python, you name it...) and use stdin and stdout to control it. It really is pretty simple, have a play and you'll get it in no time.

The problem with asking for sample code, particularly just "to see if it can be done" is you are asking other people to do your exploring for you, and some of us could be charging $100/hour instead. You will learn way more and better if you do it yourself, too.

---

### Post by Wybiral on 2007-08-13
> **Senesence said:**
> I'm just doing this to see if it can be done - that is, to see if I can control a  C++ binary from python <- that's really the essence of what I want to do here.

Does it HAVE to be through std in/out?

If not... Then yes, you can (without hassling with pipes or anything, though they aren't hard... And while the examples I posted were C it isn't going to be different for python).

If you go the non-pipe route, the easiest is a module. You can have python execute any C++ code you want, and YES, you can start a new thread in the module to execute concurrently. You can also execute python code and share data back and forth.

---

### Post by slavik on 2007-08-13
I think you should really look into dbus.

---

### Post by Senesence on 2007-08-13
[QUOTE=foxylad]You really want to look at popen() in hte python docs. This lets your python program launch another program (c, python, you name it...) and use stdin and stdout to control it. It really is pretty simple, have a play and you'll get it in no time.[/quote]

Just to be clear, we are talking about this set of docs, right?: [http://docs.python.org/lib/module-popen2.html](http://docs.python.org/lib/module-popen2.html)

If so, I already looked over those. Given, I had to kind of guess on it's usage - since there was no example code - but I did try to implement it, and got nowhere:

```

import popen2
coutlist = []

state = "run"

#"Test.bin" is the C++ program I initially posted.
child_out, child_in = popen2.popen2("Test.bin")

while state != "quit":
	python_message = raw_input("Message to C++: ")
	if python_message != "quit":
		
		child_in.write(python_message)
		stdout = child_out.read()
		
		print "Got ", stdout
                coutlist.append(stdout)
	
	else:
		state = "quit"

```

This results in nothing more than a freeze, and I am forced to CTRL-C out.

I know I'm missing something, that's why I asked for example code.

[quote=foxylad]The problem with asking for sample code, particularly just "to see if it can be done" is you are asking other people to do your exploring for you.[/QUOTE]

No.

I did not ask anyone to do any "exploring" on my part. I simply asked that someone who already knew (and therefore didn't have to "explore") provide me with an example, on top of the (in my opinion) very convenient template I already supplied.

I know how this may look, but please understand: My questions are the result of my legitimate confusion - not my laziness.

[quote=Wybiral]If you go the non-pipe route, the easiest is a module. You can have python execute any C++ code you want, and YES, you can start a new thread in the module to execute concurrently. You can also execute python code and share data back and forth.[/quote]

How exactly? I only know how to write and implement python modules: [http://www.ibiblio.org/g2swap/byteofpython/read/making-modules.html](http://www.ibiblio.org/g2swap/byteofpython/read/making-modules.html)

Can you give me/point me to an example of a python module written in C++?

Tia.

[quote=slavik] I think you should really look into dbus.[/quote]

Thanks slavik. I'm still looking into that, but I would much rather use something that already comes with python. (afaik, dbus doesn't)

---

### Post by pmasiar on 2007-08-13
> **Senesence said:**
>  I would much rather use something that already comes with python. (afaik, dbus doesn't)

[http://www.google.com/search?q=python+dbus](http://www.google.com/search?q=python+dbus) gives:
[http://dbus.freedesktop.org/doc/dbus-python/doc/tutorial.html](http://dbus.freedesktop.org/doc/dbus-python/doc/tutorial.html)
[http://packages.ubuntu.com/gutsy/python/python-dbus](http://packages.ubuntu.com/gutsy/python/python-dbus)

Python is "batteries included" :-D

---

### Post by Senesence on 2007-08-13
**pmasiar**:

Ahh, so it does come with python. If it's simpler than popen2 (which I still can't get working), it should do great - I hope that is.

Thanks.

---

### Post by Wybiral on 2007-08-14
> **Senesence said:**
> How exactly? I only know how to write and implement python modules: [http://www.ibiblio.org/g2swap/byteofpython/read/making-modules.html](http://www.ibiblio.org/g2swap/byteofpython/read/making-modules.html)

Can you give me/point me to an example of a python module written in C++?


It's pretty easy, you just need the python development package installed.


Save this as test.c, compile with the command at the top
```

// gcc -shared -s -o test.so test.c `python-config --cflags --libs` -Wall

#include <Python.h> 
#include <stdio.h>

PyObject *c_send_command(PyObject *self, PyObject *args)
{ 
    int command;
    PyArg_ParseTuple(args, "i", &command);
    switch(command)
    {
        case 0: printf("Hello\n"); break;
        case 1: printf("And\n"); break;
        case 2: printf("Goodbye\n"); break;
    }
    Py_INCREF(Py_None); 
    return Py_None; 
} 

static PyMethodDef test_mod_funcs[] = {
   {"send_command", c_send_command, METH_VARARGS, ""},
   {NULL, NULL, 0, NULL}
};

PyMODINIT_FUNC inittest(void)
{
    Py_InitModule("test", test_mod_funcs);
}

```

It should generate a ".so" which can be used as:

```

import test

for i in range(3):
    test.send_command(i)

```

And _IF_ you need concurrency, then you can spawn a thread when the module is initialized, but it doesn't sound like you need to. It sounds like you just want a way to communicate with C++ from python. In which case this will do.

---

### Post by trwww on 2007-08-14
> **Senesence said:**
> If you read my original post, you'll notice that I explicitly ask for an example.

I appreciate your opinions on what the best methods are, but without an example implementation I don't really have much use for them. (*I searched through google, and I did find API docs, but no example code.*)

So if anyone is knowledgeable enough to write an example I asked for, please do me that favor.

This STILL isnt exactly what you wanted, but it is a straightforward example. It is the example you requested in perl instead of python. Please feel free to ignore, I just like to demonstrate how much easier it can be to do stuff in perl than in other languages sometimes. Though for this example I'm sure it would be pretty easy to port to python.

I compiled your C++ program, and then I wrote the following perl code:

```
$ cat rw.pl
use warnings;
use strict;
use FileHandle;
use IPC::Open2;

my $cmd = '/home/trwww/misc/ipc/switcher';

my $pid = open2(*READER, *WRITER, $cmd);

foreach my $input ( 1, 2, 3, 4, 3, 2, 1 ) {
  print "writing: $input...";
  *WRITER->print( "$input\n" );
  my $output = <READER>;
  print " got: $output";
}
```

When I run it, I get the following output:

```
$ perl rw.pl
writing: 1... got: First Hello
writing: 2... got: Second Hello
writing: 3... got: Third Hello
writing: 4... got: Idle
writing: 3... got: Third Hello
writing: 2... got: Second Hello
writing: 1... got: First Hello
```

Regards,

trwww

---

### Post by Senesence on 2007-08-14
Thanks Wybiral. It's good to know that I have that option, although I would still like to see a piping example.

I mean foxylad makes it sound so unbelievably easy, yet I can't seem to implement it right.

**trwww**

No need to taunt me. :cry:

---

### Post by Senesence on 2008-09-27
**nice007** stumbled upon this thread, and asked me if I figured it out. Since I did, some time ago, I thought it would be a good idea to actually provide a working example, and mark the thread as solved.

So here it goes:

Given the C++ program named **slave**, compiled from the following source code:

[PHP]
#include <iostream>
#include <string>
using namespace std;

int main(int argc, char* args[]){

	string python_message = "";
	bool quit = false;

	while (!quit){
		cin >> python_message;

		if (python_message == "quit"){
			quit = true;
		}else if (python_message == "first"){
			cout << "First Hello!" << endl;
		}else if (python_message == "second"){
			cout << "Second Hello!" << endl;
		}else if (python_message == "third"){
			cout << "Third Hello!" << endl;
		}else {
			cout << "Huh?" << endl;
		}
	}	
	return 0;
}
[/PHP]

The Python program, named **master.py** that can be used to communicate with the above program, can be written like this:

[PHP]
import subprocess

proc = subprocess.Popen("/full/path/to/slave", 
                        stdin=subprocess.PIPE, 
                        stdout=subprocess.PIPE)

state = "run"
while state == "run":
	input = raw_input("Message to CPP>> ")

	if input == "quit":
		state = "terminate" # any string other than "run" will do
	
	proc.stdin.write(input + "\n")
	print proc.stdout.readline().rstrip("\n")
[/PHP]

When testing this arrangement, you should get the following results:

```

$python master.py
Message to CPP>> first
First Hello!
Message to CPP>> second
Second Hello!
Message to CPP>> third
Third Hello!
Message to CPP>> blah
Huh?
Message to CPP>> quit

$

```

I hope that was helpful.

---

### Post by nice007 on 2008-10-06
Senesence:
   Thanks for your kindness to ask my questions.Auctuall,I'm try to find a better solution to communicate with two software developed by different languages such as c++ and python,they are used frequently.
   I have read your example code,and it seems you use the stdin and stdout and standard pipe to aacomplish the communication.Glad it works.
   But what I want is a common solution such as shard memory or named pipe(in Linux should called FIFO).In that case ,one process should create or open some media  or port and another one can access the resource with this media.In that way,only the process who know the protocal can have the access to communicate,not a stdin or stdout.I know socket could do it,but hope there are some simpler solutions.
    Anyway,thanks for your help very much,I know it may be a bother,but I'll appreciate if you can help me using other other method such as shard memeory or names pipe.

---

### Post by tspan on 2008-10-06
> **nice007 said:**
> Senesence:

    Anyway,thanks for your help very much,I know it may be a bother,but I'll appreciate if you can help me using other other method such as shard memeory or names pipe.

Here is (not so) simple C++ code for server program using named pipes for full-duplex communication with one client process. It creates (and removes) two FIFO files (one for reading and one for writing). It then goes into loop in which it reads from input pipe and writes that input back to output pipe until it reads "Terminate". 

duplex_fifo.h
```

#ifndef DUPLEX_FIFO_H_
#define DUPLEX_FIFO_H_

#include <string>

class duplex_fifo
{
public:
  duplex_fifo(const std::string& _fifo_in, const std::string& _fifo_out);
  ~duplex_fifo();
  void run();

private:
  void remove();
  void create();
  void init();
  std::string read_fifo(std::string& str);
  void write_fifo(const std::string& str);
  void perform_action();

  bool ok;
  bool cr_in;
  bool cr_out;
  std::string fifo_in;
  std::string fifo_out;
};

#endif /* DUPLEX_FIFO_H_ */

```

duplex_fifo.cpp

```

#include <iostream>
#include <fstream>
#include <cerrno>
#include <sys/stat.h>

#include "duplex_fifo.h"

using namespace std;

duplex_fifo::duplex_fifo(const string& _fifo_in, const string& _fifo_out)
{
  fifo_in = _fifo_in;
  fifo_out = _fifo_out;
}

duplex_fifo::~duplex_fifo()
{
  remove();
}

// remove fifos from file system
void duplex_fifo::remove()
{
  int err;
  ok = true;

  if(cr_in)
    {
      // remove fifo_in file if it exists
      err = ::remove(fifo_in.c_str());
      if(err == -1 && errno != ENOENT)
        {
          cerr << "Error removing fifo_in: " << strerror(errno) << "\n";
          ok = false;
        }
    }
  if(cr_out)
    {
      // remove fifo_out file if it exists
      err = ::remove(fifo_out.c_str());
      if(err == -1 && errno != ENOENT)
        {
          cerr << "Error removing fifo_out: " << strerror(errno) << "\n";
          ok = false;
        }
    }
}

// create fifo_in and fifo_out
void duplex_fifo::create()
{
  int err;
  cr_in = cr_out = true;

  // create fifo_in
  err = mkfifo(fifo_in.c_str(), S_IRUSR | S_IWUSR | S_IRGRP | S_IWGRP);
  if(err == -1)
    {
      cerr << "Could not create FIFO: " << strerror(errno) << "\n";
      cr_in = false;
    }

  // create fifo_out
  err = mkfifo(fifo_out.c_str(), S_IRUSR | S_IWUSR | S_IRGRP | S_IWGRP);
  if(err == -1)
    {
      cerr << "Could not create FIFO: " << strerror(errno) << "\n";
      cr_out = false;
    }

  ok = cr_in && cr_out;
}

// initialize fifo files
void duplex_fifo::init()
{
  cr_in = cr_out = true;
  ok = true;

  remove();
  if(!ok)
    return;

  create();
}

// reads string from fifo_in
string duplex_fifo::read_fifo(string& str)
{
  ifstream ifs(fifo_in.c_str()); // ifstream for reading

  // test ifs
  if(!ifs.good()) {
    cerr << "Cannot read from input stream.\n";
    ok = false;
    return str;
  }

  // read data
  ifs >> str;

  return str;
}

// writes string to fifo_out
void duplex_fifo::write_fifo(const string& str)
{
  ok = true;

  ofstream ofs(fifo_out.c_str()); // ofstream for writing

  // test ofs
  if(!ofs.good())
  {
    cerr << "Cannot write to output stream.\n";
    ok = false;
    return;
  }

  // write data
  ofs << str;
}

// reads from fifo_in, writes to fifo_out
void duplex_fifo::perform_action()
{
  string str;

  // read string from fifo_in
  read_fifo(str);
   if(!ok)
     return;

   // terminate server
   if(str.compare("Terminate") == 0)
     {
       cerr << "Terminating ...\n";
       ok = false;
     }
   else
     // write string to fifo_out
     write_fifo(str);

   if(!ok)
     return;
}

// read data from fifo_in in a loop
void duplex_fifo::run()
{
  init();
  if(!ok)
    return;

  while(true)
    {
      perform_action();
      if(!ok)
        break;
    }
}

```

And main.cpp to run it:

```

#include "duplex_fifo.h"

#define FIFO_IN "/tmp/test_fifo_in"
#define FIFO_OUT "/tmp/test_fifo_out"

int main(int argc, char *argv[])
{
  duplex_fifo df(FIFO_IN, FIFO_OUT);
  df.run();
  return 0;
}

```

Use this to compile (couldn't bother to write Makefile):

```

g++ -c duplex_fifo.cpp
g++ -c main.cpp
g++ -o fifo_test duplex_fifo.o main.o

```

Basically you create FIFOs with mkfifo and then read/write using fstreams like they are regular files.

Code is a bit long and has too many functions but I hope that will make it easier for you to modify it for your own needs (you will probably only need to change perform_action() function). Sorry for messy syntax and short names, I was in a hurry :(

Your client process (in python or whatever) should only need to open fifo_in file for writing, write, than open fifo_out for reading, read and so on.

You can test it from Terminal like this. First start server process in one Terminal window. Then in another one type:

```

$echo "Action1" > /tmp/test_fifo_in
$cat /tmp/test_fifo_out
Action1
$echo "Action2" > /tmp/test_fifo_in
$cat /tmp/test_fifo_out
Action2
$echo "Terminate" > /tmp/test_fifo_in

```

(Note: Action1 and Action2 will not be followed by newline, I just wrote it that way for clarity)

Server will respond in its Terminal window with:

```

Terminating...

```

That's it. It probably has bugs and could have been done better so all improvements are welcome.

Hope it helped.

---

### Post by nice007 on 2008-10-06
> Your client process (in python or whatever) should only need to open fifo_in file for writing, write, than open fifo_out for reading, read and so on.
Thanks,tspan:
   It did gread help.Actually,what I want to know is what you said in the Quote field.You mean,if I created a named pipe or fifo with C/C++ or other languages in one process A,I can communicate with process A just open the file and using read&write function.
   I think it solved my problems ,thansk again.

---

### Post by tspan on 2008-10-07
> **nice007 said:**
> You mean,if I created a named pipe or fifo with C/C++ or other languages in one process A,I can communicate with process A just open the file and using read&write function.


That's right.

You should pay attention to few things though. Use two FIFOs - one for input and another for output (like in my example), otherwise it can get messy. Another important issue is that C++ streams provide only blocking I/O (reading from FIFO will block until something writes to it).

This example was made for a simple case given by original poster where only one client process sends data to one server process and reads server's response. If you need more client processes to communicate with server you will have to take a different approach (like sockets).

Best regards.

---

