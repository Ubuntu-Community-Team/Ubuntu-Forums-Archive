---
title: "C program works in windows, not in ubuntu"
date: 2010-04-26
forum: Programming Talk
---

### Post by MichaelWyckmans on 2010-04-26
i am beginning with C programming. the next program does compile and runs as expected in windows, but in ubuntu it gives the following result:

pointer1.c:13: warning: format ‘%X’ expects type ‘unsigned int’, but argument 2 has type ‘char *’

does anyone can help me by clarifying what goes wrong here? thanks.

-------------------------------------------------------------------

#include <stdio.h>

main()
{

char a[]="test pointer";
char* ap = a;

int i = 0;

while (*ap)
        {
         printf("address: %c, %c\n", ap, *ap);
         ap++;
        }

for ( ap=a, i=0 ; i<20 ; i++)
        {
         *(ap + i) = '\0';
        }
}

---

### Post by phrostbyte on 2010-04-26
Pointers are %p

printf("address: %p, %c\n", ap, *ap);

---

### Post by gmargo on 2010-04-26
"ap" is a pointer, but a "%c" in the printf specification expects a "char".

Use "%p" to print the value of a pointer.
```

printf("address: %p, %c\n", ap, *ap);

```

---

### Post by phrostbyte on 2010-04-26
I fixed all your warnings. It should work now.

```

#include <stdio.h>

// main() = int main()
int main()
{
	char a[]="test pointer";
	char* ap = a;
	
	int i = 0;
	
	while (*ap) {
                // %c = %p
		printf("address: %p, %c\n", ap, *ap);
		ap++;
	}
		
	for ( ap=a, i=0 ; i<20 ; i++) {
		*(ap + i) = '\0';
	}
	
        // main should return an int
	return 0;
}

```

---

### Post by MichaelWyckmans on 2010-04-26
ok thank you very much!

i got this example from the VTC video tutorials. how comes it does work with %X in windows?

---

### Post by phrostbyte on 2010-04-26
> **MichaelWyckmans said:**
> ok thank you very much!

i got this example from the VTC video tutorials. how comes it does work with %X in windows?

It should work with %X too, it will just format the pointer differently.

---

### Post by Compyx on 2010-04-26
> **phrostbyte said:**
> It should work with %X too, it will just format the pointer differently.

There's a little more to it. It might happen to work, but it's not correct.

Take a machine on which pointers have a different size than int (my 64-bit machine has 64-bit pointers and 32-bit int).

%x/%X expects an unsigned integer and since printf() and friends are variadic functions they cannot check the type of the arguments they get passed, so printf will pop an unsigned int from the stack (32-bits), while the argument on the stack is actually a pointer (64-bits). The next format specifier will then pop it's argument from the stack, but instead of getting the argument it should get it'll get the left-over 32-bits (and perhaps more, depends on the specifier) of the pointer.

In other words, it is important to provide the right arguments to functions like printf. That's why the compiler warns you. Providing the wrong specifiers and/or arguments to printf and friends usually manifests itself in mysterious failures/segfaults someplace further in your code, since the stack is screwed. This usually seems to happen when you show your code to a client or your boss ;)

---

### Post by MadCow108 on 2010-04-26
it will only work with %X when a pointer has the same size as an integer
e.g. on 64 bit systems this is not the case

also above was only a warning, this does not mean the program does not work but just that the compiler thinks the code will not do what you want it to do in all cases
mostly the compiler is correct, so always fix your warnings

---

### Post by phrostbyte on 2010-04-26
> **Compyx said:**
> There's a little more to it. It might happen to work, but it's not correct.

Take a machine on which pointers have a different size than int (my 64-bit machine has 64-bit pointers and 32-bit int).

%x/%X expects an unsigned integer and since printf() and friends are variadic functions they cannot check the type of the arguments they get passed, so printf will pop an unsigned int from the stack (32-bits), while the argument on the stack is actually a pointer (64-bits). The next format specifier will then pop it's argument from the stack, but instead of getting the argument it should get it'll get the left-over 32-bits (and perhaps more, depends on the specifier) of the pointer.

In other words, it is important to provide the right arguments to functions like printf. That's why the compiler warns you. Providing the wrong specifiers and/or arguments to printf and friends usually manifests itself in mysterious failures/segfaults someplace further in your code, since the stack is screwed. This usually seems to happen when you show your code to a client or your boss ;)

Strangely enough, MSVC doesn't seem to be throwing a single compliant (even though it seems to segfault, even on 32-bit Windows??). I guess GCC "warns" a little better or something.

---

### Post by Compyx on 2010-04-26
GCC can be very picky, if you tell it to do so. I have never used MSVC, but from what I've heard from co-workers and friends, it seems to be a pretty decent compiler. Perhaps you need to tell it to warn about unsafe constructs with various switches, just like GCC. (By default GCC is very liberal in what it accepts, but using at least '-Wall -Wextra -pedantic' will produce useful warnings.)

---

### Post by phrostbyte on 2010-04-26
GCC will warn about this behaviour without any special switches, at least as it is configured in Ubuntu.

---

### Post by Compyx on 2010-04-26
So it does. I'm not sure this always used to be the case. But thumbs up for GCC.

You can disable these warnings by using '-ffreestanding' or '-fno-builtin', but these switches are meant (as their name implies) for freestanding environments: embedded stuff and and standalone programs where the standard C library isn't fully or not at all present.

In those freestanding environments the standard even allows for the abomination that is 'void main()' since there might not be anything to return to from main(). :-?

---

### Post by MadCow108 on 2010-04-26
disabling warnings should be done over the -W switches not -f switches which turn functionalities on and off
By using -f switches the missing warnings are only side effects of the missing functionality.
especially using -ffreestanding is a bad idea. -fnobuiltin should als not be used when not needed (it disables the warning because the typesafe printf is implemented over builtins)

this warning can be disabled with -Wno-format

to find the flag use -fdiagnostics-show-options which will then display the flag for the warning
adding a no- in front mostly disables it.

---

### Post by Compyx on 2010-04-27
I agree turning off warnings or disabling functionality is generally a bad idea. I was just curious how I could disable the format warnings, I tried 'Wnoformat', but must have missed 'Wno-format' in the GCC man page somehow.

Personally I don't touch the -f switches when working on my code, I do use a lot of -W switches though, these usually take up 4 or 5 lines in a terminal. I'm a little paranoid when it comes to writing portable and robust code, and a touch of paranoia is a good thing for programmers, in my opinion :)

---

