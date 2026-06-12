---
title: "c++ convert int32_t to float"
date: 2014-09-28
forum: Programming Talk
---

### Post by jhay2 on 2014-09-28
hi can someone help me with this ? ;D

i have a sample code or a test code 

int main(){
int32_t x=0x4153b68d \\ 13.23207;


 float value= (float) x;


cout <<value<< endl;
return 0;
}

i am expecting 13.23207 but it gives me wrong value= 1.09601e+09 


can you teach me the right way to get the correct float value from int32_t thank you

---

### Post by jhay2 on 2014-09-28
oops sorry :) i accidentally solve my problem using union

---

### Post by ofnuts on 2014-09-29
What I don't understand is how/why the floating point value is stored in an int32. Why isn't that variable a float in the first place?

---

### Post by dataformsaction on 2014-09-29
Although what you're doing is a bit odd, it's quite convenient that (at least on my architecture)
a float fits into 4 bytes, which is why you could do the cast.

a double though needs 8 bytes.

I guess you might want to do something like this if you'd persisted the data to file and were reading it back maybe?

---

### Post by ofnuts on 2014-09-30
Even when saving to file there are functions to read directly to a float?

---

### Post by dataformsaction on 2014-09-30
> **ofnuts said:**
> Even when saving to file there are functions to read directly to a float?

Oh yes of course, it's easy enough to read from a file directly into a float (potentially adjusting for endianness of course).

I was just speculating.

---

