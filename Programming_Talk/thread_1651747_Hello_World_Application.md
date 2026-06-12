---
title: "Hello World Application"
date: 2010-12-23
forum: Programming Talk
---

### Post by CatalystCorpse on 2010-12-23
Hello out there in ubuntu land, my name is catalystcorpse, I like long walks on the beach and candlelit dinners by the fire. WHAT!!, shutup you idiot and get on with it *cough*. I'm fairly new to this world of yours, as in brand spanking, but I think I have a deep desire to write code (nerd alert), I do have one small issue, or hurdle lets say that I need to cross. So here goes.

I am trying to write the hello world application but It doesn't work. I have tried various forms of the code in different application like eclipse, code::block, and Kdevelop 4, but I can't seem to get it. So I have a two part question, what code do I need to write, and which program do I write it in. I want a fairly basic program that won't write the code for me, that is easy to use.

Thanks in advance.
CatalystCorpse

---

### Post by papibe on 2010-12-23
Which version of Ubuntu are you using?
Which language are you using for your app?
Could you post the code (or a link to it)?

Regards.

BTW, Welcome!

---

### Post by Hur Dur on 2010-12-23
So, if I understand the question right, you're trying to compile a Hello World program in C++?

Save your code in whatever editor you are using (I use Geany) as filename.cpp

Then go to the terminal, cd to the file's directory, and type in

```
g++ -o executable filename.cpp
```

Then type in ./nameofexecutable to launch the application.

If you don't have gcc, try su'ing into root, and running: 
apt-get update
apt-get install build-essential

---

### Post by SteveDee on 2010-12-23
Check this post: [http://ubuntuforums.org/showthread.php?t=497579](http://ubuntuforums.org/showthread.php?t=497579)

---

### Post by ac7nj on 2010-12-23
> **CatalystCorpse said:**
> Hello out there in ubuntu land, my name is catalystcorpse, I like long walks on the beach and candlelit dinners by the fire. WHAT!!, shutup you idiot and get on with it *cough*. I'm fairly new to this world of yours, as in brand spanking, but I think I have a deep desire to write code (nerd alert), I do have one small issue, or hurdle lets say that I need to cross. So here goes.

I am trying to write the hello world application but It doesn't work. I have tried various forms of the code in different application like eclipse, code::block, and Kdevelop 4, but I can't seem to get it. So I have a two part question, what code do I need to write, and which program do I write it in. I want a fairly basic program that won't write the code for me, that is easy to use.

Thanks in advance.
CatalystCorpse

Answers are more than one
code::blocks has this as a demo program just cut and paste 

you could just use a text editor like gedit or note pad, word pad etc.

next *#include <iostream>* and *using namespace std* will make printing to screen easier 

you have to have a main function 
*int main() {* 
and a 
*return 0;*
*}* 

in between main and return *cout << "Hellow world!";*

Ok now you have the code it has to be compiled with a compiler like gcc code::blocks or other IDE can make this easier because you can just click on compile and run. 
the one thing we didn't solve is run where? you can do it in a terminal or most IDE's will use xterm if you make it a terminal application.

Randy

---

### Post by bodhi.zazen on 2010-12-23
*Thread moved to **Programming Talk**.*

---

### Post by dwhitney67 on 2010-12-23
Why didn't the OP post this thread on April 1?

---

### Post by worksofcraft on 2010-12-23
> **dwhitney67 said:**
> Why didn't the OP post this thread on April 1?

IDK but I recommend he/she uses bash as a language and tries something like this:
```

echo "Hello World!"

```

Mind you, knowing my luck there will be a bug in there somewhere :D

---

### Post by r-senior on 2010-12-23
> **worksofcraft said:**
> Mind you, knowing my luck there will be a bug in there somewhere :D
Yeah, you missed a comma, fiddled with case and added an exclamation point. The original and best writes, "hello, world". ;)

```

#include <stdio.h>

main()
{
        printf("hello, world\n");
}

```

(K&R, The C Programming Language, p6).

---

### Post by CatalystCorpse on 2010-12-24
WOW. Thanks heaps guys/girls. SteveDee, looks like I have some choices then, cheers. I have been using the exact code from r-senior. So looks like I can do it in notepad yeah? then save that as helloworld.c, open the terminal, go to the folder and type helloworld and it should work "theoretically". Zis I vill try. Thanks everyone

---

### Post by trent.josephsen on 2010-12-24
Not quite; you need to compile it first.  Your compiler is gcc.  This should do the trick:

```

$ gcc helloworld.c             # compile the program
$ ./a.out                      # run the program

```

For the record, this is C, not C++; either one you choose is fine.

---

### Post by worksofcraft on 2010-12-24
Well I think you need to move on from that 1970's hippy culture into the 21st century with an interactive GUI version. Here is one that lets the user turn the Hello message on or off with check box :shock:
[php]
#include "cs_glade.h" // generic glade gui interface module
#include <gtk/gtk.h> // gtk_init, gtk_main

using namespace cs;

// callbacks not name mangled so gtk module can find them
extern "C" {
	// call back for button state change
	bool on_checkbutton1_toggled(void *, cs_glade *pGlade) {
		const cs_gtkitem & rCheckButton = pGlade->widget("checkbutton1");
		if (integer(rCheckButton)) rCheckButton.set("Hello World");
		else rCheckButton.set("zzzz.....");
		return false; // also do standard button update
	}
} // end extern "C"

int main(int argc, char *argv[], char *envp[]) {
	gtk_init(&argc, &argv); // standard gtk command line options
	cs_glade sGlade; // get .glade file definition of user interface
	sGlade.show("window1"); // display the main app window
	gtk_main(); // process gui events
	return 0;
}
[/php]
Attached image shows both output displays and it is fully  amenable to internationalization and localization too :popcorn:

p.s. Oh, oops I see perhaps I should mention that you will need to link with the generic [cs_lib software library]("http://code.google.com/p/speaknumber/downloads/list") for that.

---

