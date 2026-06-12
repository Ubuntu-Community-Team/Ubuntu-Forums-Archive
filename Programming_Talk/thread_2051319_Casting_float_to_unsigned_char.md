---
title: "Casting float to unsigned char"
date: 2012-09-01
forum: Programming Talk
---

### Post by eldudorinio on 2012-09-01
Hi,

I am unsuccessfully trying to pass a **float** value to an **unsigned char** variable in a C++ program. I have written a small C++ program to test it, but it seems that I am doing something wrong.

The unsigned char has a range from 0 to 255. So in my example I am using a float within those margins.

The other way around works just fine (unsigned char --> float).

Here is the code:
    ```
unsigned char c = 255;
    float f = 128;


    float i = (float) c;
    unsigned char b;
    
    b = static_cast<unsigned char> (f*255);
    
    cout << "Casting from unsigned char to float (255) result: "<< i << endl;
    cout << "Casting from float to unsigned char (128) result: "<< b << endl;
```
_Note:_ I am only including <iostream>

Instead of "b = static_cast<unsigned char> (f*255)" I have also used:
[LIST=1]
[*]b = (unsigned char) f;
[*]b = (unsigned char) (f*255);
[*]b = static_cast<unsigned char> (f);
[/LIST]

All of the above give me the same output:
```
$ g++ test.cc
$ ./a.out 
Casting from unsigned char to float (255) result: 255
Casting from float to unsigned char (128) result: &#65533;
```

As you can see when casting from float to unsigned char I get this unknown character.

Any ideas?

Thanks

---

### Post by MadCow108 on 2012-09-01
the cout << operator is overloaded for a bunch of input types.
If the input are char's it prints them in ascii encoding
255 is a nonprintable ascii so you get some weird output
see the extended ascii table: [http://www.asciitable.com/](http://www.asciitable.com/)

cast it to an integer before using it in cout to get the numerical output.
e.g.
```
cout << "Casting from float to unsigned char (128) result: "<< (int)b << endl;
```

---

### Post by StephenF on 2012-09-01
You are not using a float within the margins. 
128.0 * 255 = 32640.0

Also, cout prints char variables as characters. If you need the value simply cast it to an int.

---

### Post by eldudorinio on 2012-09-01
> **StephenF said:**
> You are not using a float within the margins. 
128.0 * 255 = 32640.0

Also, cout prints char variables as characters. If you need the value simply cast it to an int.

Hi Stephen. You are right about not being within the margins. I originally tried the number without multiplying with 255, but got no result. Multiplying with 255 is something that I read when casting a float between 0 and 1 to unsigned char. I just gave it a try.

Thanks to the both of you, StephenF and MadCow108, for your replies. Casting the unsigned char to an integer before using it in cout works great for my case.

---

### Post by StephenF on 2012-09-02
Gleaned from your code this amused me.

128 * 255 = 128 * 256 - 128

Multiples of 256 cancel modulo 256 (modular arithmetic 101!)

= 0 - 128 = (0 + 256) - 128 = 128

---

