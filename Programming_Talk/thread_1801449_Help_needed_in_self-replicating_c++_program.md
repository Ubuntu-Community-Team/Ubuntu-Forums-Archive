---
title: "Help needed in self-replicating c++ program"
date: 2011-07-10
forum: Programming Talk
---

### Post by abybaddi on 2011-07-10
```

[COLOR="RoyalBlue"]#include<iostream.h>[/COLOR]
[COLOR="Navy"]**int**[/COLOR] main() {
	[COLOR="Navy"]**char**[/COLOR] *p={[COLOR="Orange"]"#include<iostream.h>",
		"int main() {",
		"char *p={",
		"};",
		"for(int i=0;i<3;i++)",
		"cout << *(p+i) << endl;",
		"for(i=0;i<10;i++)",
		"cout << char(34) << *(p+i) << char(44) << char(34) << endl;",
		"for(i=3;i<10;i++)",
		"cout << *(p+i) << endl;",
		"}",[/COLOR]
	};
	[COLOR="Navy"]**for**[/COLOR]([COLOR="Navy"]**int**[/COLOR] i=[COLOR="Lime"]0[/COLOR];i<[COLOR="Lime"]3[/COLOR];i++)
	cout << *(p+i) << endl;
	[COLOR="Navy"]**for**[/COLOR](i=[COLOR="Lime"]0[/COLOR];i<[COLOR="Lime"]10[/COLOR];i++)
	cout << [COLOR="Navy"]**char**[/COLOR]([COLOR="Lime"]34[/COLOR]) << *(p+i) << [COLOR="Navy"]**char**[/COLOR]([COLOR="Lime"]44[/COLOR]) << [COLOR="Navy"]**char**[/COLOR]([COLOR="Lime"]34[/COLOR]) << endl;
	[COLOR="Navy"]**for**[/COLOR](i=[COLOR="Lime"]3[/COLOR];i<[COLOR="Lime"]10[/COLOR];i++)
	cout << *(p+i) << endl;
	[COLOR="Navy"]**return**[/COLOR] [COLOR="Lime"]0[/COLOR];
}

```

I was working on this for a while but cannot figure out the errors. Any enlightenment is appreciated. Thanks in advance!

```
In function 'int main()':
Line 14: error: scalar object 'p' requires one element in initializer
compilation terminated due to -Wfatal-errors.
```

---

### Post by nvteighen on 2011-07-10
p should be an array of strings...
```

const char *p[] = {"Hello, hello, hello",
                   "Is there anybody in there?",
                   "Just nod if you can hear me",
                   "Is there anybody home?"};

```

It has to be const because those strings are constants.

But be aware that C++ has lots of data structures that can help you to do this in a much easier fashion. I suggest you to look at std::string and std::vector to avoid just compiling C code with a C++ compiler.

Also, a good program wouldn't need to hardcode the sizes that way... Actually, you can do this without repeating the code itself again in that array.

---

### Post by abybaddi on 2011-07-11
> **nvteighen said:**
> p should be an array of strings...
```

const char *p[] = {"Hello, hello, hello",
                   "Is there anybody in there?",
                   "Just nod if you can hear me",
                   "Is there anybody home?"};

```

It has to be const because those strings are constants.

But be aware that C++ has lots of data structures that can help you to do this in a much easier fashion. I suggest you to look at std::string and std::vector to avoid just compiling C code with a C++ compiler.

Also, a good program wouldn't need to hardcode the sizes that way... Actually, you can do this without repeating the code itself again in that array.

THANKS A LOT!!!!:biggrin:

I also saw your Solution to Programming exercise 2: the gtk+ program. It was really awesome!!

---

