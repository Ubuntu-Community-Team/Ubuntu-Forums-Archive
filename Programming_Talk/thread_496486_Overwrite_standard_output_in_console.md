---
title: "Overwrite standard output in console"
date: 2007-07-09
forum: Programming Talk
---

### Post by Arlanthir on 2007-07-09
I'm really hoping I can clear this doubt with your help..

Have you seen fsck running? Of course you have..
What I'm trying to do here is like that progress bar and percentage.. 
It prints in the _same position_ as the print before! How can I do that?

For proof of concept let's just assume I want to make a program in C that prints 'Hello world' and then prints World _instead_ of world. Anyone that can show me how? 

Thank you very very much!

---

### Post by lisati on 2007-07-09
The exact details of how to do this will depend on which programming language you are using. The underlying idea is that instead of emitting a "carriage return" with a "line feed", you just putt out a "carriage return".

---

### Post by Arlanthir on 2007-07-09
I'm sorry, I forgot to add I want to do this in C!
Will edit ;) Thank you!

---

### Post by meatpan on 2007-07-09
It sounds like you could use the ncurses library.  Ncurses is a text CLI programming library written in C.  Here is a tutorial:  [http://www.writeka.com/ed/ncurses_library.html](http://www.writeka.com/ed/ncurses_library.html)

The main ncurses page:  [http://www.gnu.org/software/ncurses/](http://www.gnu.org/software/ncurses/)

Check it out and see if it helps.

---

### Post by Wybiral on 2007-07-09
I also vote nCurses... It's easy and will do exactly what you want (and more).

---

### Post by Arlanthir on 2007-07-09
So, I can't do that without an external lib? Thank you all for the tip ;)

---

### Post by Thomas Jensen on 2007-07-09
Here's what I think you're looking for:
```

#include <iostream>

int main(int argc, char** argv)
{
	std::cout << "Hello world\b\b\b\b\bWorld" << std::endl;

	return EXIT_SUCCESS;
}

```
When you run this example all you will see is the text "Hello World". This is because \b works like a backspace, deleting the previous character. Another way to achieve the same effect is this:
```

#include <iostream>

int main(int argc, char** argv)
{
	std::cout << "Hello world\rHello World" << std::endl;

	return EXIT_SUCCESS;
}

```
The \r is called a "carriage return"; basically it tells the terminal to move the cursor to the beginning of the current line -- thus what I'm doing here is simply overriding "Hello world" with "Hello World".

Here's an example of how to use this:
[HTML]
#include <iostream>

int main(int argc, char** argv)
{
	unsigned long int Counter = 0;

	while (true)
	{
		std::cout << "\r" << Counter;
		Counter += 1;
	}

	return EXIT_SUCCESS;
}
[/HTML]
This will print an increasing  number on the same line over and over. Press Ctrl+C to stop it.

Have fun :)

---

### Post by Mr. C. on 2007-07-09
> **Arlanthir said:**
> So, I can't do that without an external lib? Thank you all for the tip ;)

You can, but the code won't be portable, and it will probably be very inefficient and more taxing on the system than necessary.

Curses is designed to minimize the amount of output going to the terminal device (a device which is relatively slow), and to be very portable.  Your code will work for essentially all terminal types, not just the one you've hardcoded.

Uses one of the curses variants as others have suggested.

MrC

---

### Post by Arlanthir on 2007-07-10
Oh, that's great :D
The examples are in C++, but I guess the \r and \b work in C too, right?

Thank you for both the examples and the lib, it's just what I was searching for!

---

### Post by Thomas Jensen on 2007-07-10
Oops... Didn't even notice I were using C++

But yes I believe \r and \b also work in C.

Oh and while we're at it I should also tell you that \f clears the screen.

---

