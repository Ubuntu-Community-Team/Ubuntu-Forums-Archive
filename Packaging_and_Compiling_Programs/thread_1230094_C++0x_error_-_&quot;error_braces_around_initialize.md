---
title: "C++0x error - &quot;error: braces around initializer for non-aggregate type&quot;"
date: 2009-08-03
forum: Packaging and Compiling Programs
---

### Post by trilobite on 2009-08-03
Hi all - 

 I'm trying to compile a program using g++ version 4.3.3, and using the "-std=c++0x" compiler option.  

 I'm trying to initialise a vector as follows- 
vector <string> myvec = {"foo", "bar", "baz"};  

Now, I've had a look around the web to check the new C++0x initialisation syntax, and (to me) this looks exactly like this example that I saw - 
vector<string> vs={ "ab", "cd", "ef"}; 

Yet, when I try to compile the code, I get this error - 
"error: braces around initializer for non-aggregate type" 

Very odd. I've used the syntax that I've seen, yet the compiler is complaining. So, does anyone know the reason (and the fix) for this?

Very many thanks in advance for your help! 
- trilobite

---

### Post by Sockerdrickan on 2009-08-03
use gcc-snapshot, 4.3.3 sucks
and you don't need the =

---

### Post by trilobite on 2009-08-03
> **Tux0r said:**
> use gcc-snapshot, 4.3.3 sucks
and you don't need the =

Ahh... thanks very much, Tux0r!  Yes, that's got rid of the error (and I agree - 4.3.3 does seem to be a bad release). I'll try the snapshot releases and see how they go. 
Thanks again - bye for now - 
- trilobite

---

