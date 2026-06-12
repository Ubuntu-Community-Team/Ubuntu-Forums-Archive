---
title: "C++ cout Hex values"
date: 2009-02-25
forum: Programming Talk
---

### Post by patryk77 on 2009-02-25
Hey,

I am writing a parser for binary data files, and would like to print the Hex values of each char.

I have a pointer, and I assign what it points to to an int. 

```
int hexVal = *ptrStart;

cout.flags(ios::hex);

cout << hexVal << endl;
```

I tried it with two values, and while I expect A1 and 80, it prints ffffffa1 and ffffff80. 

Could anyone tell me why it does that? And how to make it assign and print the correct values?

Thanks

Edit: I guess it must be during the conversion to int that it happens, right?

---

### Post by monkeyking on 2009-02-25
I am in no way an expert but I think you are expecting the hexval of the first byte (8bits),
but  cout gives you all 4 bytes (32 bits)(1 int).
you should use chars if you are really only interested in 1 byte.
Futhermore, you should consider using unsigned values, if you are planning to do bit stuff. otherwise your number are in 2-complements

good luck

---

### Post by patryk77 on 2009-02-25
Thanks for the reply. I am looking for a single byte value, but I am not sure how to get it.

I actually just tried a short int now, which gives me FFA1. Close but no cigar.

Edit: Meh, no big deal. Will compare with 0xFFA1 for now.

I would still like some input if anyone knows the right way to achieve this, but I need to have it done quick for now.

---

### Post by eye208 on 2009-02-25
> **patryk77 said:**
> I would still like some input if anyone knows the right way to achieve this, but I need to have it done quick for now.
```
cout << (hexVal & 0xFF) << endl;
```

---

### Post by the_unforgiven on 2009-02-25
You use [setf()]("http://www.cplusplus.com/reference/iostream/ios_base/setf.html") to set flags and not flags().

---

### Post by movieman on 2009-02-25
> **monkeyking said:**
> you should use chars if you are really only interested in 1 byte.

If you use chars you're likely to get a result you didn't expect :).

Unsigned int and/or (int & 0xff) is the way to go.

---

### Post by patryk77 on 2009-02-25
> **the_unforgiven said:**
> You use [setf()]("http://www.cplusplus.com/reference/iostream/ios_base/setf.html") to set flags and not flags().

[http://www.cplusplus.com/reference/iostream/ios_base/flags.html](http://www.cplusplus.com/reference/iostream/ios_base/flags.html)

flags() works too. Is there a reason for the preference?

[COLOR="Blue"]Edit 2: Should have read the page first. flags() unsets the other ones. where as setf() just changes specific ones[/COLOR]


> **movieman said:**
> If you use chars you're likely to get a result you didn't expect :).

Unsigned int and/or (int & 0xff) is the way to go.

Yeah hehe, tried the char method... Printed out garbage.

I'm using unsigned shorts now. Should be good too, right? [COLOR="Blue"]Edit: they give me the results I expect, even if 0xFFA1 instead of just 0xA1, but I can live with that.[/COLOR]


Thanks for the replies :)

---

### Post by monkeyking on 2009-02-25
> **movieman said:**
> If you use chars you're likely to get a result you didn't expect :).

Unsigned int and/or (int & 0xff) is the way to go.

If you only need 1byte, then unsigned char is the only choice.
Why should it give strange results?

---

### Post by soltanis on 2009-02-25
> **patryk77 said:**
> 
```
int hexVal = *ptrStart;

cout.flags(ios::hex);

cout << hexVal << endl;
```


Yes. You are using an integer to store the value of a character. Since an integer seems to be 4 bytes on your system, the extra 3 bytes are being printed. Use an unsigned char instead.

---

### Post by patryk77 on 2009-02-25
Unsigned char also prints garbage.

Will stick to unsigned short, I guess.

---

### Post by the_unforgiven on 2009-02-25
This following code seems to be working for me:
```

#include <iostream>

int main()
{
	int hexVal = 0xa1;
	std::cout.setf(std::ios::hex, std::ios::basefield);
	std::cout.setf(std::ios::showbase);
	std::cout <<  hexVal << std::endl;
	return 0;
}

```
Note that I'm using a plain int and it still prints '0xa1' for me.

---

### Post by eye208 on 2009-02-25
> **the_unforgiven said:**
> Note that I'm using a plain int and it still prints '0xa1' for me.
Chars are signed by default. If you convert char 0xA1 to signed int, the result is not 0x000000A1 (161) but 0xFFFFFFA1 (-95).

---

### Post by geirha on 2009-02-25
> **patryk77 said:**
> 
```
int hexVal = *ptrStart;

cout.flags(ios::hex);

cout << hexVal << endl;
```


If you give cout an unsigned char, it will print it as a char. But if you give it an int, it will print it as a number.
```

unsigned char hexVal = *ptrStart;
cout << showbase << hex << (int)hexVal << endl;

```

---

### Post by patryk77 on 2009-02-25
> **geirha said:**
> If you give cout an unsigned char, it will print it as a char. But if you give it an int, it will print it as a number.
```

unsigned char hexVal = *ptrStart;
cout << showbase << hex << (int)hexVal << endl;

```

Awesome! Thanks :)

This works, and comparing it to 0xA1 works :)

---

