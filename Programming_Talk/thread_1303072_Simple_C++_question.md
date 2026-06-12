---
title: "Simple C++ question"
date: 2009-10-27
forum: Programming Talk
---

### Post by jualin on 2009-10-27
I am writing this program and one part of it is integer verification. I would like to know how can I check if the input value was an integer.
The programming language is C++.
Any ideas are welcome, thank you!

---

### Post by Bachstelze on 2009-10-27
Psudocode:

```
for char in string
    if !isdigit(char)
        return false
return true
```

---

### Post by jualin on 2009-10-27
Wouldn't that check if the number is "numeric". How can you check if the number is an "integer" and not a "double"?
Thank you

---

### Post by Bachstelze on 2009-10-27
> **jualin said:**
> Wouldn't that check if the number is "numeric". How can you check if the number is an "integer" and not a "double"?
Thank you

Because a double would contain a decimal separator, which is not a digit.

---

### Post by Frak on 2009-10-27
First thing that came to mind was to cast the value into another type, then compare the entered value against the casted value. If they're equal, it was an integer, if it wasn't, then it wasn't.

I go the long way for 99% of the stuff I do, because I'm always too lazy to check docs or anything of the sort.

---

### Post by nmccrina on 2009-10-27
Bachstelze method is what I would use.

Also, how did a forums staff member comment on this and not move it to Programming Talk??? lol

---

### Post by jualin on 2009-10-27
> **Bachstelze said:**
> Because a double would contain a decimal separator, which is not a digit.

Thank you very much!
You were right it works just great. 

> First thing that came to mind was to cast the value into another type, then compare the entered value against the casted value. If they're equal, it was an integer, if it wasn't, then it wasn't.

I go the long way for 99% of the stuff I do, because I'm always too lazy to check docs or anything of the sort.

That was the first thing I had in mind as well. But I wasn't able to make it work. Another thing I tried which worked was using the fmod built in function, but I needed to have a temporary double variable which made the code messier.

Thank you both for the quick help!

---

### Post by Hyporeal on 2009-10-27
You might consider something like this:

```
istringstream in(str);
int value;

in >> value;

if (in.fail()) {
    cout << "It wasn't an integer!" << endl;
} else {
    cout << "It was an integer!" << endl;
}
```

Isn't this the C++ way of doing things? It'll even work with negative numbers.

---

### Post by jualin on 2009-10-27
Thank you all for the suggestions.

---

