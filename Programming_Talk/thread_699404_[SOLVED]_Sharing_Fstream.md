---
title: "[SOLVED] Sharing Fstream"
date: 2008-02-17
forum: Programming Talk
---

### Post by Zeotronic on 2008-02-17
I've been writing code that stores very related (in fact interdependant) information in different files, the only reason I have it do this is because I wanted the code in different segments that could be accessed by other code... but it just occured to me that I could probably have this code share fstream (actually ifstream and ofstream, not interchangibly mind you) in a fashon similar to this:
```
void slave(fstream file)
{

}

void master(string filename)
{
   fstream file(filename);
   if (file.good())
   {
      //Use file, then...
      slave(file);//Let slave use file.
   }
}
```
While I personally suspect this would work, I thought I should make sure, and should check if it would also pass along the current position of the pointer which is used to access information from within the file.

---

### Post by LaRoza on 2008-02-17
Wouldn't it make sense to make a class for this?

---

### Post by EXCiD3 on 2008-02-17
Correct me if im wrong but this would work, however you will need to pass the fstream by reference I think. ```

void slave(fstream& file)
```You will also need to pass a parameter for the position if you are needing it to begin in a certain location.

EDIT: I agree a class would make it much easier for you too.

---

### Post by Zeotronic on 2008-02-17
> Wouldn't it make sense to make a class for this?
You may be right... but I wouldn't know as I have never worked with classes before.
> Correct me if im wrong but this would work, however you will need to pass the fstream by reference I think.
Your probably right.

---

### Post by LaRoza on 2008-02-17
> **Zeotronic said:**
> You may be right... but I wouldn't know as I have never worked with classes before.


It is C++ isn't it?

---

### Post by Zeotronic on 2008-02-17
> It is C++ isn't it?
Yes. Does my failure to use classes make my code interchangeable with C?

---

### Post by LaRoza on 2008-02-17
> **Zeotronic said:**
> Yes. Does my failure to use classes make my code interchangeable with C?

fstream is C++ only, and there are other things as well. You can use references like was suggested in C either.

---

