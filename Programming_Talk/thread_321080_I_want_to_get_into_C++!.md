---
title: "I want to get into C++!"
date: 2006-12-18
forum: Programming Talk
---

### Post by Ben Sprinkle on 2006-12-18
I am quitting Java and wish to start C++ making gui'sand stuff.

I installed gcc-4.1 and g++-3.4, is this all I need? Or do I need some other crap?
What's the use of gtkmm when you have gtk?
Help?

---

### Post by raul_ on 2006-12-18
I have to tell you that Java protects the programmer, whereas C++ don't..it's like, with Java you can do all the crap you want, if u sneeze, the compiler gives a warning, in C++ it will just let you go :) Plus, u can do gui's with java (i think, i personally never tried) 

I think u just need a good tutorial to get started, and then you're off

---

### Post by Ben Sprinkle on 2006-12-18
> **raul_ said:**
> I have to tell you that Java protects the programmer, whereas C++ don't..it's like, with Java you can do all the crap you want, if u sneeze, the compiler gives a warning, in C++ it will just let you go :) Plus, u can do gui's with java (i think, i personally never tried) 

I think u just need a good tutorial to get started, and then you're off

So what crap do I need installed to make C++ GUI's and Terminal apps?

---

### Post by raul_ on 2006-12-18
see if this helps

[http://www.yolinux.com/TUTORIALS/LinuxTutorialC++.html]("http://www.yolinux.com/TUTORIALS/LinuxTutorialC++.html")

---

### Post by Keffin on 2006-12-18
> **Goat Spirit said:**
> I am quitting Java and wish to start C++ making gui'sand stuff.

I installed gcc-4.1 and g++-3.4, is this all I need? Or do I need some other crap?
What's the use of gtkmm when you have gtk?
Help?

I'd install build-essential, it gives you access to make, which you'll want for all but the most trivial projects, and other stuff you may or may not want.

Assuming you already know a bit of C++, then google for either Qt tutorials (KDE) or Gtk tutorials (Gnome). gtkmm, to the best of my understanding, is a C++ wrapper around the Gtk (written in C) library. It just makes it look more natural to a C++ programmer.

---

### Post by Ben Sprinkle on 2006-12-18
> **Keffin said:**
> I'd install build-essential, it gives you access to make, which you'll want for all but the most trivial projects, and other stuff you may or may not want.

Assuming you already know a bit of C++, then google for either Qt tutorials (KDE) or Gtk tutorials (Gnome). gtkmm, to the best of my understanding, is a C++ wrapper around the Gtk (written in C) library. It just makes it look more natural to a C++ programmer.

What does a wrapper mean?
Does that mean it makes gtk make more like good looking? Or just is a change in syntax?

---

### Post by Keffin on 2006-12-18
> **Goat Spirit said:**
> What does a wrapper mean?
Does that mean it makes gtk make more like good looking? Or just is a change in syntax?

It's a code wrapper, the only difference is in the API (Application Programming Interface). So the syntax will be different - more object-oriented I suppose than the native C version - but it will be using the exact same library to do all the real work.

---

### Post by VDM on 2006-12-18
2 GREAT Free books, completely legal!

[http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html](http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html)

Enjoy.

---

### Post by raul_ on 2006-12-18
OH MY GOD!!! Can't u find the latest "Thinkin in Java" by the same author? :mrgreen:

---

### Post by Ben Sprinkle on 2006-12-18
> **VDM said:**
> 2 GREAT Free books, completely legal!

[http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html](http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html)

Enjoy.

Thanks, hey guys want to see my first 2 apps?
```

#include <iostream>

using namespace std;

int main() {
	cout << "Howdy!\n";
}

```
```

#include <iostream>

using namespace std;

int main() {
	int i;	//Make an int
	cout << "Enter a number for i:\n";
	cin >> i;	//i = user input
	cin.ignore();	//Ignore the enter key pressed
	cout << "i now equals: " << i;
	cin.get();	//Wait for enter pressed to see output
}

```
:)

---

### Post by VDM on 2006-12-18
> **raul_ said:**
> OH MY GOD!!! Can't u find the latest "Thinkin in Java" by the same author? :mrgreen:

Yeah, but i recon i doesn't need those to learn c++ :mrgreen:

---

### Post by pmasiar on 2006-12-18
BTW author of "thinking in java", bruce Eckel, now prefers python. He even charges less (smaller hourly rate) for work in python. Just FYI - and also because python was not mentioned in this thread :-P

---

### Post by sailingboarder on 2006-12-19
i don't see how thinking in Java or bruce eckel using python have anything to do with the OP's topic, C++

---

### Post by pmasiar on 2006-12-19
Question:
> **sailingboarder said:**
> i don't see how thinking in Java or bruce eckel using python have anything to do with the OP's topic, C++

Answer:
> **raul_ said:**
> OH MY GOD!!! Can't u find the latest "Thinkin in Java" by the same author? :mrgreen:

:twisted: 

Also: python was not mentioned and promoted enough :-)

---

