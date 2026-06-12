---
title: "An interesting idea for a programming language"
date: 2009-04-06
forum: Programming Talk
---

### Post by beattyml1 on 2009-04-06
I don't know if anything like this exists but anyway here's the idea:

A language that does not execute sequentialy(think like VHDL, VERILOG, etc.) but unlike VHDL and other similar languages is actually for programming a computer, with syntax similar to C++ to make it easy for existing developers to learn, the use of this language would be for continuous data processing, one example would be audio processing.  
I have started figuring out what the syntax would have to look like and started coding in what I have to start figuring out what is needed and what is annoying etc.  

I think that this would greatly help out with sound related software development, and a compiler for linux for such a language might provide a nice draw to people looking to develop audio software.

I would just work on it my self but I do not believe that I am good enough/experienced enough programmer to take on a compiler, although I would love to do what I can, so I was wondering if any one could first off give me feed back on whether this is worth it, and second whether anyone would be interested in helping out.


What I have thus far is as follows
has three  different basic data types: 
variable, signal, and state 
-variables operate similar to C++ variables except they are buffer and designed for non-sequential use, they can be operated on, assigned, and compared,  they can not directly interact with stuff outside the program
-signals are also non sequential and must specify whether they are an input signal or an output, there is also a lets you output to an input using special techniques, they are not able to be operated, on assigned, etc, rather they are assign to a input/output on initialization/creation, directly interact with things outside the program
-states are have properties of both they cannot be assigned values except at initialization, but they be operated on (variable=state*variable), they are used mainly for control conditions from outside the program 

operating on these are:
-entities which take states and signals, as well as constant   variables, and can not return a value
-functions which take variables and properly initialized states, these may return a value

stuff inside of functions works almost exactly as it does in C++
you may define your own state, signal, and variable types like in C++ using similar syntax, templates should also work although they would probably not be as common as in C++

---

### Post by Firestom on 2009-04-06
The idea looks good, but you should explain with a sample program how it would work. From your post I understand it would look like:

```

include std

on(audio.ready)
{
  play(audio)
  display("Playing audio")
  emit audio.playing
}

on(audio.playing)
{
  if(atend(audio))
  emit audio.finished
}

on(audio.finished)
{
  display("Audio track finished")
}

on(button.play)
{
  emit audio.ready
}

...

```

A code based on signals that does not run linearly. I did not include states in this as I did not well understand how those are supposed to work. I think your idea is good, even though I don't think I could possibly write a compiler (I would first need to understand how Linux bytecode works, and this changes from a distribution to the other) but I could possibly write a parser that makes a more low-level code that could be compiled after.

---

### Post by kknd on 2009-04-06
You can already do that with GObject signal system, for example.

---

### Post by jpkotta on 2009-04-06
A few years ago I played with GNU Radio.  What they did was make a C++ back end made up of nodes (as in graph theory).  Nodes could be sources (generators), sinks (consumers), or filters (processors).  Then there was a Python front end that let you build a graph out of nodes and specify the (directed) edges between them.  Then you told a runtime to execute your graph.  It reminded me a lot of Simulink or LabVIEW, except it wasn't built with a GUI.

I've never looked in to it, but I think the Nyquist language works somewhat like this.  In any event, Nyquist is a language specifically for processing sound.

I would say that the idea of making the syntax C-like is fundamentally flawed.  It would be far better to make the syntax different from C whenever it is even remotely more intuitive to the data-flow nature of the language.  Syntax is not hard to learn, the concepts are.  I would think something more like shell with pipes.

---

### Post by Arndt on 2009-04-07
> **Firestom said:**
> 
 I think your idea is good, even though I don't think I could possibly write a compiler (I would first need to understand how Linux bytecode works, and this changes from a distribution to the other) but I could possibly write a parser that makes a more low-level code that could be compiled after.

There may be something I miss (happens all the time), but is there a particular concept "Linux bytecode"? As I understand it, the languages which compile to bytecode all have their very own execution environments and formats, like Java, Python, Prolog, Ruby, Perl (and which also typically enables them to run on different platforms without recompilation).

---

### Post by beattyml1 on 2009-04-07
I'm currently look into seeing whether I could achieve the results I want by creating a c++ library, let you guys know whether it pans out.

---

### Post by soltanis on 2009-04-07
You want a non-imperative programming language, it seems.

Might I suggest Common Lisp (really, all it takes to write your language is a few functions and macros and off you go to wonderland).

---

### Post by Firestom on 2009-04-07
> **Arndt said:**
> There may be something I miss (happens all the time), but is there a particular concept "Linux bytecode"? As I understand it, the languages which compile to bytecode all have their very own execution environments and formats, like Java, Python, Prolog, Ruby, Perl (and which also typically enables them to run on different platforms without recompilation).

What I mean by "Linux bytecode" is a standalone program compiled under Linux. This code won't work on Windows or other Linux ditrubtions than the one you compiled it in. Same thing for Windows.

Unless you think the language should be an interpreted language like Perl or Python, but a bad interpreter gives poor result.

---

### Post by jpkotta on 2009-04-07
> **Firestom said:**
> What I mean by "Linux bytecode" is a standalone program compiled under Linux. This code won't work on Windows or other Linux ditrubtions than the one you compiled it in. Same thing for Windows.

ELF is the native Linux binary format.  Any distro should be able to execute ELFs.  The incompatibilities usually come from different library versions.  Even different architectures like ARM use ELF, but obviously the machine code is different there.

> **Firestom said:**
> 
Unless you think the language should be an interpreted language like Perl or Python, but a bad interpreter gives poor result.
A bad compiler gives a poor result.

---

### Post by beattyml1 on 2009-04-08
here is a quick sample of the current syntax that I am using for a test of the library, note that the syntax is incomplete, in particular the syntax for the entity constructor does not yet have the ability to pass it a function to use to act on the signals, also the I would like to replace the try catch block that has the entity::execute() statements with a more seamless, multithreaded, less sequential syntax

as of right now the entity execute does nothing but pass but let the try block know that certain signals have changed
also as of right now the signal type contains no information, but does keep you from doing certain illegal operations 

```
#include "nsCpp.h"
#include <iostream>
using namespace std;
using namespace nsCpp;


int main()
{
	entity e1(1,1, 1);
	nsio::signal sin1;
	nsio::signal sout1;
	nsio::signal*  inputs1[1]={&sin1};
	nsio::signal*  outputs1[1]={&sout1};
	state*  states1[1];
	e1.map(inputs1, outputs1, states1);

	entity e2(1, 1, 1);
	nsio::signal sout2;
	nsio::signal*  inputs2[1]={&sout1};
	nsio::signal*  outputs2[1]={&sout2};
	state*  states2[1];
	e2.map(outputs1, outputs2, states2);


	while(true)
	{
		try
		{
			e1.execute(); 
		}
		catch(nsio::SIG_UPDATE)
		{
			cout<<"hello"<<endl;
			try
			{
				e2.execute();
			}
			catch(nsio::SIG_UPDATE)
			{
				cout<<"goodbye"<<endl;
			}
		}
	}
	return 0;
}
```

this is  a bit closer to what I want
```
#include "nsCpp.h"
#include <iostream>
using namespace std;
using namespace nsCpp;

void function1(nsio::signal* inputs[1], nsio::signal* outputs[1], state*  states[1]);
void function2(nsio::signal* inputs[1], nsio::signal* outputs[1], state*  states[1]);

int main()
{
	entity e1(function1, 1,1, 1);
	nsio::dbl_signal sin1(8);	//creates a signal of type double
					//with a buffer size of 8 samples
	nsio::dbl_signal sout1;
	nsio::signal*  inputs1[1]={&sin1};	//creates an array of signal
						//pointers of size 1,
	nsio::signal*  outputs1[1]={&sout1};
	state*  states1[1];
	e1.map(inputs1, outputs1, states1);	//maps the inputs and outputs
						//of the entity, to certain signals

	entity e2(function 2, 1, 1, 1);
	nsio::dbl_signal sout2;
	nsio::signal*  inputs2[1]={&sout1};
	nsio::signal*  outputs2[1]={&sout2};
	state*  states2[1];
	e2.map(outputs1, outputs2, states2);


	e1.run();//runs the entity
	e2.run();
	//some function would tell the entities to stop when a certain condition was met, 
	//could be done by setting some flag variable, or in an event based manner
	return 0;
}

void function1(nsio::signal* inputs[1], nsio::signal* outputs[1], state*  states[1])
{
	//do something
}
void function2(nsio::signal* inputs[1], nsio::signal* outputs[1], state*  states[1])
{
	//do something
}

```

---

### Post by beattyml1 on 2009-04-15
I have most of the basics for the library done, now I need to work on synchronizing its operation, so that entities execute in the proper order, as well as dummy proofing it

---

### Post by tom66 on 2009-04-15
It might be easier to make a converter into another language, such as C or Python, and in the case of C, put it through gcc to produce an executable.

---

