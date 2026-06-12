---
title: "C++ Config Reading Problem"
date: 2010-01-16
forum: Programming Talk
---

### Post by dellwood on 2010-01-16
I'm working on script interpreter (just a small concept project).  Commands are written in like this: 

```

%printhw

	&1 hello&/1
	&1 world&/1

%/printhw
		


```

The format is:
1) *&* signifies a command
2) the number after the *&* signifies the function index (1, in this case, is the print function)
3) all the parameters come before the closing *&/* 

So, the first statement should print "hello" and the second  "world." 

Each script is stored in a script struct, which looks like this:

```


struct script {
	std::string name;
	unsigned int index[50];
	std::string parameters[50][3];
	unsigned int cmdCount;
};


```

1) *std::string name* is the name of the script, which is preceded by a % (the example scripts name is "printhw")
2) *unsigned int index[50]* stores the command index (in this case "1," to represent "print")
3) *std::string parameters[50][3]* stores the parameters for each command (currently supports up to four parameters per command -- "hello" and "world" are parameters in the example script) 
4) *unsigned int cmdCount* the number of commands in the script (50 currently supported).

So...

Everything seem to goes fine -- the "configRead.cpp" reads in basic global data (ex: debug_mode), and if it finds a script opening sends the command lines to be read, one at a time, to commandFind(), a function in the separate "scripting.cpp" file, which looks like this:

```


script commandFind(std::string command, script cScript) { 
	using namespace std;
	unsigned int i;

	if((i = command.find("1")) != string::npos) { 
	
		cScript.index[cScript.cmdCount] = atoi(command.substr(i,2).c_str());
		a = a-(i+2); // find length of string parameter
		
		cout << "[0][3] before = " << cScript.parameters[0][3] << endl;
		cScript.parameters[cScript.cmdCount][0] = command.substr(i+2,a);
		cout << "[0][3] after = " << cScript.parameters[0][3] << endl;
		
	}
	return cScript;
}


```

Which stores the corrct parameter in "cScipt.parameters[cScript.cmdCount][0]", but also stores the next line parameter in "cSciprt.parameters[cScript.cmdCount][3]", which is why I am here :).  As you can see above, I've narrowed the line between the two "cout" statements to be the problem, as I get the following output when I run the program:

```


Starting up...
        Reading in globals...done.
        Reading in startup script...[0][3] before =
[0][3] after =
[0][3] before =
[0][3] after = world
done.
done.


```

Meaning that when it goes onto the second function, where "world" is printed, it also stores "world" in the last variable in that command's array. It also stores "world" correct section of the array, but if I were to add a third line to the script after "world", that would also be stored in "world"'s last array element.  So something happens in this line :

*cScript.parameters[cScript.cmdCount][0] = command.substr(i+2,a)* that stores the next line variable in the last array element of the command before it.

Pheww...  ;)

So I've been trying to figure it out for about a week -- anyone else have any ideas :D?

All help is GREATLY appreciated.

---

### Post by dwhitney67 on 2010-01-17
Reply edited...


Your 'parameters' array is setup with dimensions as [50][3].  You stated that it can hold up to 4 parameters.  Look at this declaration:
```

std::string parameters[50][3];

```

From the statement above, you have declared 3 parameters.  Each is indexed using 0, 1, and 2.

Your app seems to think that there is a parameter available by using an index of 3.  That would be the forth parameter, which as discussed above, does not exist.  This is the cause of your app's woes.

Btw, why did you choose to declare this method such as:
```

script commandFind(std::string command, script cScript)

```
It is considered time-expensive to make copies of class objects.  Here you are copying the command object, copying the script object, and then returning a copy of the script object.  Whew!

Consider the following:
```

void commandFind(const std::string& command, script& cScript)

```

---

### Post by dellwood on 2010-01-17
Thanks so much! I think the first time I saw the 3 my brain for some reason dismissed it as being correct (maybe because array[3] is the fourth element?), and skipped over that every time I reviewed the code, so without the second set of eyes it would have probably taken another week.

And thanks for pointing out the object copying.  I think I may have had it there at some point, but have rewritten that function so many times they &'s just magically disappeared... ;).

---

