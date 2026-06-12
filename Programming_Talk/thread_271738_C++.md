---
title: "C++"
date: 2006-10-05
forum: Programming Talk
---

### Post by Lster on 2006-10-05
Hi... I saw a reply by thumper about sstream. I modified the code, but I get an error. What's wrong with my program.

...

Thanks,

Lster

---

### Post by Ayman on 2006-10-05
Hi,

std::istringstream is an input steam, you can read from it, but not write. If I understand what you are trying to achieve, I believe you need to use ostringstream:
```
#include <iostream>
#include <sstream>

int main(){
  int number = 55;

  std::ostringstream sout;
  sout << number;
  std::string val = sout.str();

  std::cout << val;

  return 0;
}


```

Hope this helps.

---

### Post by jespdj on 2006-10-05
So you want to convert a number to a string using a string stream. You have to use ostringstream, not istringstream, to do that.
```

#include <iostream>
#include <sstream>

int main(){
	int number = 55;
	
	std::ostringstream sout;
	sout << number;
	std::string val = sout.str();
	
	std::cout << val;
	
	return 0;
}
```

---

### Post by jespdj on 2006-10-05
Wow, Ayman beat me... ;)

---

### Post by Lster on 2006-10-05
Thanks guys... I am nooby with C/ C++...

Can I convert doubles like that too? And how can I convert back?

---

### Post by amo-ej1 on 2006-10-05
Exactly the same way, I have expanded jespdj's code. So first the integer gets put on the ostringstrea and it gets read as a string and written, then the ostringstream gets cleared, the double gets pushed on it and we read it from there.

To do the conversion back we create an input stringstream (istringstream), put the string on it, and read it to a number.

The code:

```

#include <iostream>
#include <sstream>

int main(){

	// Read the int
	int number = 55;
	std::ostringstream sout;
	sout << number ;
	std::string val = sout.str();	
	std::cout << val << std::endl;
	
	// Read the double
	double doubleNumber = 0.25;	
        sout.str("");          // Clear it
        sout << doubleNumber;  // Push the double
	val = sout.str();      // Read it back
	std::cout << val << std::endl;

	// Convert the double hidden in the string
	std::string  stringNumber= "0.5555666";
        double d;
        std::istringstream sin(stringNumber);
        sin >> d;
	std::cout << d << std::endl;

	return 0;
}


```

You might want to give [http://pegasus.rutgers.edu/~elflord/cpp/stdlib/stringstream.html](http://pegasus.rutgers.edu/~elflord/cpp/stdlib/stringstream.html) a look

---

### Post by thumper on 2006-10-05
I can't believe I got that the wrong way around.

That's what happens when you take a full time python job :(

---

