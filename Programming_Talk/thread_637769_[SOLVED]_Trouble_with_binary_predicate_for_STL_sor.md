---
title: "[SOLVED] Trouble with binary predicate for STL sort in C++"
date: 2007-12-11
forum: Programming Talk
---

### Post by m_kylli on 2007-12-11
I'm trying to create a program that will sort roman numerals stored in a vector by providing a binary predicate, but the compiler complains that the function gets to few arguments.

```

bool test(const string& a, const string& b)
{
   return roman_to_int(a) < roman_to_int(b);
}

```

```

sort (romanlist.begin(), romanlist.end(), test());

```

Can anyone help me out with this problem?

---

### Post by iharrold on 2007-12-11
(return val) roman_to_int(std::string &)  is not part of the STL.

I have no idea what it returns,  so I just put return val.

I think you are confusing some python code with C++

---

### Post by m_kylli on 2007-12-11
No, roman_to_int is my own function. That one returns the number that the roman numeral represents and works correctly. It's the customized sorting that doesn't work.

---

### Post by Tuna-Fish on 2007-12-11
> **m_kylli said:**
> 

Can anyone help me out with this problem?


```

sort (romanlist.begin(), romanlist.end(), test());

```

look at that call twice. What do you think happens in it?

if you put () after a function, you call it. here you are first calling test with no arguments, then passing it's value to sort.

Try with:

```

sort (romanlist.begin(), romanlist.end(), test);

```

---

### Post by m_kylli on 2007-12-11
Well this is embarrassing. It worked. I didn't even think to try that.

---

