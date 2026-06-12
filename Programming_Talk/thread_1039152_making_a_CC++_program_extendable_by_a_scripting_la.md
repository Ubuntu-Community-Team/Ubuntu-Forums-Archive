---
title: "making a C/C++ program extendable by a scripting language"
date: 2009-01-14
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-01-14
how do you do it?  my reason that i need it is i am making a program that will use its own small scripting language, but since i know how hard that will be to make so i want to make it able to run python, perl, and ruby sripts that you code

will

[PHP]
system("perl foo.pl");
[/PHP]

wor well or is there a better way?

---

### Post by stevescripts on 2009-01-14
jimi_hendrix - easy enough to embed tcl, python, etc in a c program,
(also easy to embed Tk).  A c/c++ program to use more than one scripting language at a time would probably prove ... challenging ... to say the least.

Steve 
(who would be glad to help if you decide to use tcl...)

---

### Post by Reiger on 2009-01-14
A system() call will make the script run as a sub-program of its own, it will therefore not be possible for the scripting language to interact with objects/data *inside* the scope of your main program -- which is presumably what you'd expect in an embedded scripting language: the ability to call upon the 'host' functions.

Of course there would exist ways around that by means of File I/O...

---

### Post by johnl on 2009-01-14
LUA is an excellent choice for providing extensibility to your C/C++ application, used by plenty of commercial applications or games.  Python or Perl may work great as well, but I have no experience there :)

If you visit [this page](http://gamedevgeek.com/tutorials/) and scroll down to LUA tutorials, it will go over how expose C/C++ functions to LUA, as well as call LUA functions from your C/C++ code.  I'm pretty sure this is the tutorial that I followed when I was messing around with this, and it worked pretty well.

---

### Post by jimi_hendrix on 2009-01-14
ok well the program is a hand coded irc bot...but heres the functionality i want:

command -> bot gets command -> bot locks up command in a file made by owner -> bot will either use a simple scripting language in the file to find out how to reply (and i mean really simple) or executes a perl/python/ruby/tcl script on how to reply (these are for more advanced logics) -> bot gets value to output -> outputs value

---

### Post by stevescripts on 2009-01-14
Eggdrop redux?  

[http://www.eggheads.org/support/egghtml/1.6.19/tcl-commands.html](http://www.eggheads.org/support/egghtml/1.6.19/tcl-commands.html)

Steve

---

### Post by dempl_dempl on 2009-01-14
try Boost/Python

[http://www.boost.org/doc/libs/1_37_0/libs/python/doc/index.html](http://www.boost.org/doc/libs/1_37_0/libs/python/doc/index.html)

---

### Post by johnl on 2009-01-14
> **dempl_dempl said:**
> try Boost/Python

[http://www.boost.org/doc/libs/1_37_0/libs/python/doc/index.html](http://www.boost.org/doc/libs/1_37_0/libs/python/doc/index.html)

This is another good suggestion.

---

### Post by jimi_hendrix on 2009-01-14
i only looked at the hello world tutorial...will that work vice versa (as in i take in python in the C++ program and interperate it?)

---

### Post by jmartrican on 2009-01-15
Are you looking to run C/++ code in an interpreted language application, or to run interpreted language code in a C/++ application?

---

### Post by jpkotta on 2009-01-15
If it's *really* simple, you could just write a simple command parser.  Something like
```

while (get_next_line(file, string)) {
    if (!strcmp("command1", string)) {
        do_command1();
    }
    else if (!strcmp("command2", string)) {
        do_command2();
    }
    else {
        syntax_error();
    }
}
```

Obviously, you will have to be more careful than that.  There is also flex/bison, but they're kind of complicated and other options are probably better.

[http://en.wikipedia.org/wiki/Greenspun's_Tenth_Rule](http://en.wikipedia.org/wiki/Greenspun's_Tenth_Rule)

---

### Post by cb951303 on 2009-01-15
+1 for lua

---

### Post by jimi_hendrix on 2009-01-15
> **jmartrican said:**
> Are you looking to run C/++ code in an interpreted language application, or to run interpreted language code in a C/++ application?
the latter

---

### Post by jimi_hendrix on 2009-01-15
> **cb951303 said:**
> +1 for lua

forgot about lua...and it is made to run on top of other language isnt it?

---

### Post by cb951303 on 2009-01-15
yes, and the official library is for C/C++. There are a lot of tutorials around web to show how to integrate lua with your code.

---

### Post by stevescripts on 2009-01-15
> **jimi_hendrix said:**
> the latter

OK, so we are talking about embedding the scripting language, vs
extending the scripting language with its c/c++ interface.

So - a *very* simple C program - it will run a tcl script, and allow
all of tcl and tk's funcionality from the command line at the same time.
(This is basically a custom wish, FWIW.  I will hack out a better example
that shows using your C variables/commands as time and energy allow... 
I am *OLD* and SLOW, and have to pay attention to paywork ;) )
```


#include <tcl.h>
#include <tk.h>
 
int AppInit(Tcl_Interp *interp);

int main(int argc, char *argv[]) {
        Tk_Main(argc, argv, AppInit);
        return 0;
}

int AppInit(Tcl_Interp *interp) {
    if (Tcl_Init(interp) != TCL_OK) {
		return TCL_ERROR;
		}

	if (Tk_Init(interp) != TCL_OK) {
		return TCL_ERROR;
		}

	if (Tcl_EvalFile(interp, "hw.tcl") != TCL_OK) {
		return TCL_ERROR;
		}

	return TCL_OK;
}

```

The simple tcl script this program calls:  (shebang unnecessary when calling the script this way)
```

pack [button .b -text "Hello World!" -command {exit}]

```

You gotta love one-liners like this ;)

To build this from the command line (you will need the tcl/tk dev stuff,
or, as in my case, I am building this against a custom build/install of
tcl/tk8.5)
```

steveo@delldesktop:~$ gcc working.c -o mywish -I:/usr/local/include -L:/usr/local/lib -ltcl8.5 -ltk8.5 -lm

```

The astute observer will quickly conclude that it would be quite easy
to modify this little hack to take the name of *any* tcl script as an argument and run that script ;)

Several years back, it was common for me to embed tcl and tk in a C or C++ program (quite useful for debugging classes with a quick GUI ;) ).
However, in recent years due to the development of tclkit, critcl, and starpacks, coupled with the increased performance of todays computers, I tend towards the "single-file executable" delivery model.

Hope this helps some folks, and I am sure some others will at least find it interesting.

Steve

---

### Post by stevescripts on 2009-01-15
Finding just a bit of time and energy - we move along a bit.

The folloiwng code embeds a tcl interpreter in a c program, prints the c variable from C, links the c variable to a tcl variable, and prints it again:

```

#include <tcl.h>

int main(int argc, char *argv[]) {
        
        char *the_C_String = "Welcome from Tcl inside C!";
		printf("This is the C string from C: %s\n", the_C_String);

		Tcl_Interp *interp;
		Tcl_FindExecutable(argv[0]);
		interp = Tcl_CreateInterp();

		if (Tcl_Init(interp) != TCL_OK) {
			printf("Tcl_Init error! %s\n");
			return TCL_ERROR;
		}

		char *script = "puts $the_tcl_String";
		Tcl_SetVar(interp, "the_tcl_String", the_C_String, 0);
		Tcl_Eval(interp, script);

        return 0;
}

```

When I find a bit more time, will show how to make a tcl command from a C function.

Hope somebody finds this interesting.

Steve

---

### Post by jimi_hendrix on 2009-01-15
looks simple

---

### Post by stevescripts on 2009-01-16
> **jimi_hendrix said:**
> looks simple

It is ... Did you build and run it?

Steve

---

### Post by crazyfuturamanoob on 2009-01-16
You can use Python interpreter directly from C/C++, easy as eating a pie.

[http://docs.python.org/c-api/intro.html#embedding-python](http://docs.python.org/c-api/intro.html#embedding-python)

---

### Post by jimi_hendrix on 2009-01-16
> **stevescripts said:**
> It is ... Did you build and run it?

Steve

havnt had time...long weekend so i can this weekend

---

### Post by slavik on 2009-01-16
One of the design goal of Lua is to be embedded in compiled code. WoW uses Lua for mods. :)

---

### Post by jimi_hendrix on 2009-01-16
i know

---

### Post by stevescripts on 2009-01-24
> **crazyfuturamanoob said:**
> You can use Python interpreter directly from C/C++, easy as eating a pie.

[http://docs.python.org/c-api/intro.html#embedding-python](http://docs.python.org/c-api/intro.html#embedding-python)

hmm... I was hoping that someone with more python savvy than I would post a simple example...

Since nobody did, I took the time to do a little searching and hacking and came up with a couple of simple examples.

First - a python interpreter from a C program:
```

#include <python2.5/Python.h>

int main (int argc, char* argv[])
{
	Py_Initialize();
	Py_Main(argc, argv);
	Py_Finalize();

	return 0; 
}

```

Second, running a little python code from a C program:
```

#include <Python.h>

const char* cmd1 = "import exceptions";

const char* cmd2 = "print 2 + 2;";

int main()
{
	Py_Initialize();
	PyEval_InitThreads();
	PyRun_SimpleString(cmd1);
	Py_EndInterpreter(PyThreadState_Get());
	Py_NewInterpreter();
	PyRun_SimpleString(cmd2);
	Py_Finalize();

	return 0;
}

```

The command line to build it (you may need to flavor this a bit to suit your own setup):
```

gcc pyinterp.c -o pyinterp -I/usr/local/include/python2.5 -L/usr/local/lib/python2.5/config -lpthread -ldl -lutil -lm -lpython2.5

```

Hope somebody finds this a bit useful and time-saving perhaps.

Steve

---

### Post by jimi_hendrix on 2009-01-24
thanks steve

---

### Post by stevescripts on 2009-01-24
My pleasure ;)

For me, an enjoyable distraction.

BTW, there are some nice examples in the python docs...

Steve

---

