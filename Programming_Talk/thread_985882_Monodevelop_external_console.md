---
title: "Monodevelop? external console"
date: 2008-11-18
forum: Programming Talk
---

### Post by pagaNs on 2008-11-18
I'm not so big noob
PROBLEM:
Cant force Monodevelop to run my simple prog in external console.
Tried Project->Options->Configuration->Debug->Custom Commands
    I selected from drop down menu [execute]
    Browsed to the executable, path from (project)bin folder
    Workind dir -> tried every combination
    Clicked on [Run on external console] & [pause console output]
I HAVE installed gmcs to be able to compile progs from within MD - newest version of CLR

the message I get is: cannot execute binnary file
now, now, I know that this is easily produced if 'we' don't use 'mono f.exe' on the command line, I know its different on win but:
can anyone help solve this

I have no problem executing solution/project and watching it's results in the output pane, the problem comes (Console applications) when my prog have need to read from user input. That commands are skipped, more precisely, values that should be assigned to variables ARE assigned and they are all 0 [zero]. I don't want, IF I DON'T HAVE TO, to go to terminal every time I want to execute program that reads user input, and this is essential to me, since I'm in process of learning (A lot of short programs, a lot of experimenting(quick?).

I thank you very much in advance, if you have even an idea for solution, I ask you kindly to post it.
P.S. Didn't find any answer on google, this forum or monodevelop docs

---

### Post by directhex on 2008-11-18
Sorry, your post is a little hard to read, but...

You want to be able to assign values to args[] when you execute your project. Is that right?

---

### Post by directhex on 2008-11-18
If so, then that's easily done. Right click on the project in the Solutions pane, go to Options, Configurations, active, Output, and set your chosen parameters.

e.g.:
Parameters set to: flim flam flom
```
using System;

namespace directhex
{
	class MainClass
	{
		public static void Main(string[] args)
		{
			if( args.Length > 0 )
				Console.WriteLine( args[0] );
		}
	}
}
```

Prints on the output pane:
flim

---

### Post by pagaNs on 2008-11-18
Thanks,
I was just confused about how some IDE features work, was looking at the wrong features all night...
I had 3 problems, while you helped me solve one, you gave me answer where to look to solve other 2.
Thanks

---

### Post by directhex on 2008-11-18
"install binfmt-support" ought to answer another of your questions (I think it's a question)

---

### Post by true_friend on 2008-11-20
externel console is there, but it has a bug, it doen't save, so at next opening you wont get output in external console. The bug was filed, and developers said it is solved in svn, now see when new version comes and when it is added to Ubuntu and when this problem will disappear.

---

### Post by directhex on 2008-11-20
> **true_friend said:**
> externel console is there, but it has a bug, it doen't save, so at next opening you wont get output in external console. The bug was filed, and developers said it is solved in svn, now see when new version comes and when it is added to Ubuntu and when this problem will disappear.

IF. Some developers are trying to block it, apparently. Take a peek at the ubuntu-motu mailing list.

---

### Post by true_friend on 2008-11-22
The bug was filed at official site, to monodevelop website and on the same list i.e. monodevelop mailing list I was infromed about it.

---

