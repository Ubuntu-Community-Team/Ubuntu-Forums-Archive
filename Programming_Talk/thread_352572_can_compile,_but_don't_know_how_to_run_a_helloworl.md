---
title: "can compile, but don't know how to run a helloworld program. please help"
date: 2007-02-03
forum: Programming Talk
---

### Post by camerong on 2007-02-03
hey.
so i wrote a helloworld program just to start, and used g++ to compile it using:

> g++ helloworld.cpp -o helloworld

and in helloworld.cpp i had this:

> #include <iostream>

using namespace std;

int main()
{
	cout << "HEY, you, I'm alive! Oh, and Hello World!" << endl;
 	cin.get();

	return 0;
}


so then it flawlessly compiled, (no errors) but i cant run it! I double click on the program that it built and it just doesnt do anything. nothing opens, pops up, or anything!

i know this must be a very stupid question, but please help me. thanks in advance.

cameron

EDIT: and another quick question.. am i going to compile by command line and then run it manually every time i want to test something? in windows i can just hit F5 or whatnot and it compiles and runs.. is there any IDE's that will do that? I am using anjuta and just started programming on ubuntu

---

### Post by loko on 2007-02-03
i think you should try to start your program in the console.

try: ./helloworld

why do you think your program opens a window and prints its message?

---

### Post by camerong on 2007-02-03
worked!

see i knew it was a silly question. i'm just used to windows i guess, and i expected it to open a window for the program.

thanks.

oh and do u have any idea about how i can just get the compiling running procses all together just by hitting a button - like to any IDEs hve this feature?

thanks.

---

### Post by finer recliner on 2007-02-03
i assume you added that cin function so that the window would stay open until you hit another character (and then the window would automatically close). this is unneeded if you are executing from a terminal in linux -- the terminal will print your cout statement, and then will remain open and wait for another job for you to give it.

to compile and run in one line, try this in the terminal
```

g++ helloworld.cpp -o helloworld && ./helloworld

```
or
```

g++ helloworld.cpp -o helloworld;  ./helloworld

```

(both methods are untested, but i believe it will work)

---

### Post by Rui Pais on 2007-02-03
some IDES:
anjuta (gnome oriented)
kdevelop (kde oriented)
eclipse (more java oriented but can work for c)
[codeblocks]("http://www.codeblocks.org/nightly/CodeBlock_RSS.xml") (not in repos, but very good and simple to use)

---

