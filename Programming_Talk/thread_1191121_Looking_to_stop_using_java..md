---
title: "Looking to stop using java."
date: 2009-06-18
forum: Programming Talk
---

### Post by jfitzpat on 2009-06-18
I have a project that I have been working on. I used Java b/c I was most comfortable with it. Unfortunatly, when I sent my program around, not all machines could replicate the same output that mine did. Probably due to the version of java, every machine is different, I dont know. 

What language should I switch to?

I need:
-to make a standalone executable(not more asking people to install a JRE).
-I am used to using notepad, so hopefully something with a simple IDE.
-I think I am going to work on this project solely on linux.
-hopefully nothing too difficult to learn.
-to open a plain-text file with about 3000 records of this:

```
 50  62  59  44  46  42  59  58  89  30 
 55  57  62  62  91  20  5  0  3  8  1 
 1995  22  11  100000  0  2013  3  22  22 
 0  0  0  0 
 0  0  0  0 
 0  0  0  0  0  1 
 9  1  0  0  0  5 
 0  0  0  0  55550451  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0 
 0  0  0  55550423  0  0  0  0  0  57660091 
 0  0  0  0  2  187  9  6 
 0  0  0  0  0 
-
Bohumil Vostrak

drafted
030094150095075112075083100150100114100
1.16 (24.3.2002)
1.16 (24.3.2002)
 0  0  22  55  67 
```


thanks for any suggestions.

---

### Post by TheBuzzSaw on 2009-06-18
I recommend C++. It has many great long-term benefits.

---

### Post by sloggerkhan on 2009-06-18
c++ or python.

---

### Post by s.fox on 2009-06-18
I think python as well.

---

### Post by credobyte on 2009-06-18
C++ ( if you want to get some kind of privacy ) or Python.

---

### Post by froggyswamp on 2009-06-18
> 
... not all machines could replicate the same output that mine did. Probably due to the version of java...

I'm pretty sure it's not about Java but rather about your code. I've heard a few such suggestions before and every time it was programmer's fault. If you created your app in Java and it "works" it doesn't yet mean you've written it correctly, there's still lots to pay attention to when doing cross-platform stuff. Since I don't got your source code can't comment further.

Interpreted lang:
Get rid of Java and its issues, choose another interpreted language (say Python) but you still have to make sure it's installed on that OS/computer and consider the installed runtime version and so on - problem not solved.

Native lang:
I'd suggest C++. I'm not even going to start enumerating the issues arising in C++ compared to Java. I'm myself transitioning from Java to C++ (Gtkmm) and boy is it difficult. The g++ compiler is nowhere as fast and friendly as the Java one, this alone is worth a lot, but there's a long list of other stuff, like built-in utf8 support and other issues I consider ridiculous. The C++0x standard is supposed to "fix" them in the future.

---

### Post by HotCupOfJava on 2009-06-18
There are certain coding issues you have to consider even with a "write once, run anywhere" language like Java. Properly coded, it WILL give you the same output even on different platforms.

---

### Post by doas777 on 2009-06-18
"write once, run everywhere" quickly turns into "write once, debug everywhere". as HotCupOfJava mentioned it can be achieved, but it becomes a burden regression testing for multiple platforms, in a long running development and maintenance cycle.

---

### Post by Can+~ on 2009-06-18
Hmm, moving from Java to C++ could be painful (drop garbage collector, start wondering with pointers, manual memory allocation) if you are trying to accomplish a one time task.

However, I am wondering, what's up with that file, is there a reason why it's been set up that way? Why not a binary file with random access? or sqlite?

---

### Post by jfitzpat on 2009-06-19
> **Can+~ said:**
> 
However, I am wondering, what's up with that file, is there a reason why it's been set up that way? Why not a binary file with random access? or sqlite?

it is a file of players for a freeware hockey manager that was written almost 10 years ago. I have been making a tool to do lots of tedious jobs that people do as well as a lot of stuff people want to do, but are outside of the limitations of the game(like longer drafts, or fantasy drafts, salary rollbacks).

In java, I had a huge sting array that was working really well, but I noticed that 1 tool worked on most machines, but not all and the final method that prints the new players file would print extra blank lines on various other machines(that part i can fix).

I initially thought it would be cool to make one class that had a bunch of methods that people could call on and make their own tools, but no one that plays the game knows java. I have added enough to the project and used some lazy coding styles, so I want to start a new version.

I dont really like the idea of asking someone to download 100mb worth of stuff to use a 10kb program. Python looks pretty cool, but c++ is probably what I should do. All I really know how to do is make loops and arrays and compare stuff. But I do have a fat deitel book on c++ that I have avoided opening.

Thanks for the input.:)

---

### Post by stefanadelbert on 2009-06-19
Transitioning over to C++ will mean a fair amount of uphill and I wouldn't recommend it unless there is a really good reason for it (like you'll use it for work). Writing your functionality into a C++ DLL (or source code that could be compiled on any platform) would make some sense, but others would still need to compile the code on their platform and then write their own app that makes use of your code.

Maybe consider writing an application that lives on the net and get around platform compatability that way. Take a look into creating a simple PHP based CMS and custom PHP classes behind the scenes that do the calculations. Text files could be uploaded from the client to the server and results sent back to the client with few worries. Bonus would be that you could start an online community at the same time.

If you want to consider this, check out Joomla, SilverStripe, WordPress which are all open-source, PHP based CMS's. There are others too, of course.

Good luck
Stef

---

### Post by jespdj on 2009-06-19
> **jfitzpat said:**
> I have a project that I have been working on. I used Java b/c I was most comfortable with it. Unfortunatly, when I sent my program around, not all machines could replicate the same output that mine did. Probably due to the version of java, every machine is different, I dont know. 

What language should I switch to?
This sounds really strange. Because your program doesn't work correctly, you want to switch to a different programming language? :confused:

It is more than likely that there is simply a bug in your program, rather than that it is the fault of Java.

---

### Post by Mirge on 2009-06-19
> **jfitzpat said:**
> I dont really like the idea of asking someone to download 100mb worth of stuff to use a 10kb program. Python looks pretty cool, but c++ is probably what I should do. All I really know how to do is make loops and arrays and compare stuff. But I do have a fat deitel book on c++ that I have avoided opening.

Thanks for the input.:)

This is another reason why he is trying out a different language.

---

### Post by shadylookin on 2009-06-19
well if you only care about linux most distros have a python interpreter. 

You could pick up c/c++ but they're harder than java. Plus you have to compile for every architecture you want to run it on.

---

### Post by doas777 on 2009-06-19
> **jespdj said:**
> This sounds really strange. Because your program doesn't work correctly, you want to switch to a different programming language? :confused:

It is more than likely that there is simply a bug in your program, rather than that it is the fault of Java.

a fair statement but if your problem is stakeholders saying that the software cannot depend on a separately installed interpreter (JRE in this case) then there is no choice but a binary compiled langague.

---

### Post by jfitzpat on 2009-06-19
I am trying out c++ now. so far, I really like how it handles input and output.

But I do have a question.

lines 94 to 101 are being sent to the array as their own element.(ie: arr[i][94] == line 94). But I want to be able to print all the elements in a row to a text file with each row having its own line.

the problem is that when I use getline(file, arr[][]), the line keeps its formatting. How do I stop that?

Also, if there is a blank line, how do I allow getline() to get a blank line and let an element of an array be a blank line?

---

### Post by slavik on 2009-06-19
processing text ... in C++ ... there is a better language out there for text processing. :P

---

### Post by jfitzpat on 2009-06-19
> **slavik said:**
> processing text ... in C++ ... there is a better language out there for text processing. :P

is it java?:p

---

### Post by slavik on 2009-06-19
No.

---

### Post by jfitzpat on 2009-06-19
> **slavik said:**
> No.

ok... b/c that would be some good irony.

---

### Post by JordyD on 2009-06-19
> **slavik said:**
> processing text ... in C++ ... there is a better language out there for text processing. :P

Perl? Awk?

---

### Post by Can+~ on 2009-06-19
> **slavik said:**
> No.

Guessing... I'll go with "perl"

but I still think that python would be the softest transition from Java.

---

### Post by fr4nko on 2009-06-20
I think for your task python or perl will be perfect. Otherwise you can use ocaml, it is a really great programming language and it can produce stand-alone executables.

Francesco

---

### Post by jfitzpat on 2009-06-20
> **jfitzpat said:**
> I am trying out c++ now. so far, I really like how it handles input and output.

the problem is that when I use getline(file, arr[][]), the line keeps its formatting. How do I stop that?


I was having a problem of c++ formatting a line when I used getline(), But, when I compile this on the DevC++ compiler on my laptop(windows), I dont get this problem at all. As for writing it wrong, I am sure the java stuff I wrote is pretty jacked up, but this c++ stuff so far seems as simple as I can do it:

```
// EHM Tool in C++

#include <iostream>
#include <fstream>
#include <string>

using namespace std;

int numPlayers;
string players[3060][106];

void loadPlayers(){
	ifstream PlayersFile;
	PlayersFile.open ("players.ehm");
	PlayersFile >> numPlayers;

	for(int i=0;i<numPlayers;i++){
		for(int j=0;j<106;j++){
			if((j>94) && (j<101)){
				getline(PlayersFile, players[i][j]);
			}
			else{
				PlayersFile >> players[i][j];	
			}
		}
		players[i][94] = players[i][94] + players[i][95];
	}
	PlayersFile.close();
}

void printNewPlayers(){
	ofstream NewPlayersFile;
	NewPlayersFile.open ("NEWplayers.ehm");

	for(int i=0;i<numPlayers;i++){
		for(int j=0;j<106;j++){
			if(j==95){
				
			}
			else{
				NewPlayersFile << players[i][j] + " ";
			}
		}
		NewPlayersFile << "\n";
	}	
	NewPlayersFile.close();	
} 

int main (){
	loadPlayers();
	printNewPlayers();
	return 0;
}
```

---

### Post by jfitzpat on 2009-06-20
> **fr4nko said:**
> I think for your task python or perl will be perfect. Otherwise you can use ocaml, it is a really great programming language and it can produce stand-alone executables.

Francesco

Thanks, I will check that out too. My girlfriends parents run a book selling thing on amazon and I have noticed some pearl books lying around.:D

---

