---
title: "[C++] Problems in passing arguments ( argv[] )."
date: 2009-07-31
forum: Programming Talk
---

### Post by credobyte on 2009-07-31
What I'm missing here ? :-?

```
    if (argv[1] == "demo") {
        cout << argv[1] << " is equal to demo. \n";
    } else {
        cout << argv[1] << " is NOT equal to demo. \n";
    }

``````
dainis@ubuntu:~/Programming$ sudo ./main demo
demo is NOT equal to demo. 
```

---

### Post by Sockerdrickan on 2009-07-31
You are comparing the memory addresses of the variables... use strcmp

if(strcmp(argv[1],"demo")==0) //equal

and why the HECK do you run it with **sudo**? :-O

---

### Post by credobyte on 2009-07-31
> **Tux0r said:**
> You are comparing the memory addresses of the variables... use strcmp

if(strcmp(argv[1],"demo")==0) //equal

and why the HECK do you run it with **sudo**? :-O

Thank you! sudo is simply because of the fact that I need to access some files/locations that are not available for "humans" ( app is set to exit(0) if not being executed with root privileges ) :p

---

### Post by dwhitney67 on 2009-07-31
@ the OP

Consider using getopt() or getopt_long().  Refer to the man-page for either for complete examples.

---

### Post by Habbit on 2009-07-31
If you are using C++, then by all means use the std::string class instead of strcmp and the likes. You could write if(argv[1] == string("demo")) and it would work fine, as the left hand argument would be promoted to a string instance and compared according to the string equality operator, which performs a semantic comparison instead of an address comparison.

---

### Post by Sockerdrickan on 2009-07-31
Hope is already lost from the beginning, better stick with consistency or shout at wg21 for an int main(size_t argc, std::string argv[])

---

