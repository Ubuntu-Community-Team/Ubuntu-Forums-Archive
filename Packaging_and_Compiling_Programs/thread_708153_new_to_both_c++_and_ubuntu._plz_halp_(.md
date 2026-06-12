---
title: "new to both c++ and ubuntu. plz halp :("
date: 2008-02-26
forum: Packaging and Compiling Programs
---

### Post by vegtard on 2008-02-26
hi. yesterday i installed ubuntu, so im still learning. and today, i made my first c++ program, the infamous hello world. after hours of googling and forum browsing ive decided to make my own thread, cus i cant find what im looking for. 

in the terminal, after i do the SU thing to become root, it says /home/"myname"#. i assume this means that when i do the g++ world.ccp -o world command, it checks for the file in the /home/"myname" folder, so i moved my .ccp file there. i got no idea how i change what folder it checks in. (if you care to elaborate on that as well id be thrilled)

anyways, when i do the command, i get this error message: 

/usr/bin/ld:World.ccp: file format not regognized; treating as linker script
/usr/bin/ld:World.ccp:1: syntax error (does that mean my coding is wrong?)
collect2: ld returned 1 exit status

any idea whats going on? ive done what i should do in the terminal to get the g++ command working, so im stuck on this one. new OS + new programming language = confused me :(

---

### Post by pedro_orange on 2008-02-26
> in the terminal, after i do the SU thing to become root, it says /home/"myname"#. i assume this means that when i do the g++ world.ccp -o world command, it checks for the file in the /home/"myname" folder, so i moved my .ccp file there. i got no idea how i change what folder it checks in. (if you care to elaborate on that as well id be thrilled)

To change to a directory you do (like you would in Windows pretty much)

```

cd /Dekstop/Documents

```


> /usr/bin/ld:World.ccp: file format not regognized; treating as linker script
/usr/bin/ld:World.ccp:1: syntax error (does that mean my coding is wrong?)
collect2: ld returned 1 exit status

Do you have build-essential installed?

```

sudo apt-get install build-essential

```

What is your command to compile/link?

---

### Post by vegtard on 2008-02-26
> **pedro_orange said:**
> What is your command to compile/link?

hi, and thank you for answering. :) i installed the essential build like you said. (reason i hadnt done it earlier is that i didnt have the cd with me to work). 

i re-entered the command just in case, its confirmed that my build-essential is the latest version. 

the command i'm using to compile is "g++ <filename.ccp> -o <name>". from what ive read, that should do it, but im getting the same error message as before i installed the build-essential. any idea why?

---

### Post by amingv on 2008-02-26
```
/usr/bin/ld:World.ccp: file format not regognized; treating as linker script
```

Ok... would you mind posting the contents of World.cpp? It would make it so much easier to see a syntax error (which doesn't seem the case here, but anyway).

---

### Post by amingv on 2008-02-26
Also, just noticed, why do you need to become root to do this?

---

### Post by WW on 2008-02-26
Rename your file to World**.cpp**. The compiler does not like the .ccp extension.

I have the same question as amingv: Why are you compiling as root?  This is not necessary.  In fact, it is a very bad idea.

---

### Post by vegtard on 2008-02-27
my world.ccp looks like this:

```
// funky comment thing

#include <<ionstream
using namespace std;
int main()
{
	cout << "Hello World!";
	return 0;
}
```

im not entirely sure why im compiling as root. it simply seems easier, cause when i did the root thing i got the /home/"myname"# thing which means i knew where to put my script. 

ive tried altering the file to .ccp and compiling as non-root, im getting this error:

World.cpp:3:10: error: #include expects "FILENAME" or <FILENAME>
World.cpp: In function 'int main()':
World.cpp:7: error: 'cout' was not declared in this scope

so theres something wrong with my script. i got no idea what tho, because my script is an exact copy of the tutorial. with the exeption of the comment thing.

EDIT:

amateurism strikes again. i took another look at the tutorial, turns out i messed up the brackets around the ionstream. i fixed my program and i compiled it. yay :D

theres still 1 question for you guys tho. how do i run what i just compiled? i just wanna make sure i know how to run it before i move on with the tutorial. thanks alot for the help so far :D

---

### Post by amingv on 2008-02-27
> **vegtard said:**
> my world.ccp looks like this:

```
// funky comment thing

#include <<ionstream
using namespace std;
int main()
{
	cout << "Hello World!";
	return 0;
}
```

im not entirely sure why im compiling as root. it simply seems easier, cause when i did the root thing i got the /home/"myname"# thing which means i knew where to put my script. 

ive tried altering the file to .ccp and compiling as non-root, im getting this error:

World.cpp:3:10: error: #include expects "FILENAME" or <FILENAME>
World.cpp: In function 'int main()':
World.cpp:7: error: 'cout' was not declared in this scope

so theres something wrong with my script. i got no idea what tho, because my script is an exact copy of the tutorial. with the exeption of the comment thing.

EDIT:

amateurism strikes again. i took another look at the tutorial, turns out i messed up the brackets around the ionstream. i fixed my program and i compiled it. yay :D

theres still 1 question for you guys tho. how do i run what i just compiled? i just wanna make sure i know how to run it before i move on with the tutorial. thanks alot for the help so far :D

Well, looks like you solved your problem then, all you need to do to run it is type
```
./World #or whatever name you gave your program
```

A few pointers:
1. I missed it in my previous post, but take notice of the file extension, as WW said, it must be .cpp; not .ccp.
2. Always be careful when writing code, do not rush yourself and take notice of what you type.
3. DON'T EVER get used to running as root in linux; it is not advisable at all. There is no need and trust me, it doesn't make it easier to compile. The reason why you see /home/yourname with root it's because that's not the home folder for the root user. When you're on your regular account your home directory will apear as ~. I'll elaborate: in linux/unix (and other OSs); this is what some signs mean:

~ = The current user's home directory. Writing ~ in the console is the same as writing /home/yourusername.
. = Current directory. See the example I gave you to run your program? It says "execute the file World, located in the directory I'm in right now".
.. = Parent directory; the directory to which the current directory belongs. For example, if you're in /home/yourusername, the parent directory would be /home.

<edit>
I also suggest you read the sticky in the programming talk. There's many resources that no doubt will help you.
</edit>

---

### Post by ad_267 on 2008-02-27
Yeah, and it should be <iostream>, not <ionstream>. But I guess you know that if it's working now.

---

