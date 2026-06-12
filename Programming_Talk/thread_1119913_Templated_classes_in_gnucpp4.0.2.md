---
title: "Templated classes in gnucpp4.0.2"
date: 2009-04-08
forum: Programming Talk
---

### Post by CMGmadison on 2009-04-08
I just registered for these forums because there seem to be a number of knowledgeable and helpful c++ people here, and I'm fighting a c++ problem that is beyond my knowledge.  I'm a fairly novice coder, and I've been tasked with debugging a code written by my phd advisor a few years ago.  He swears it used to compile, but it no longer does.  It's a pretty large program, so I'll just include the part that I'm having problems with right now, and I think it has to do with the way the class is templated.  As in, it used to be okay to do it this way, but it no longer is with gnucpp4.0.2.

```
template<class T>                       // line 215
void matrix<T>::erase(const int id)     // line 216
{                                       // line 217
  std::vector<std::vector<T> >::iterator p=mat.begin()+id;  // line 218
  mat.erase(p);                         // line 219
}                                       // line220

template<class T>                       // line 222
void matrix<T>::erase_col(const int id) // line 223
{                                       // line 224
  for (int i=0;i<mat.size();i++){       // line 225
          std::vector<T>::iterator p=mat[i].begin()+id; // line 226
    if (id<mat[i].size()) mat[i].erase(p); // line 227
  }                                     // line 228
}
```

The error messages are:

```
matrix.h: In member function `void matrix<T>::erase(int)':
matrix.h:218: error: expected `;' before "p"
matrix.h:219: error: `p' was not declared in this scope
matrix.h: In member function `void matrix<T>::erase_col(int)':
matrix.h:226: error: expected `;' before "p"
matrix.h:227: error: `p' was not declared in this scope
make: *** [convasp.o] Error 1

```

Any thoughts or suggestions would be hugely appreciated.  Thanks!

---

### Post by dwhitney67 on 2009-04-08
Fix the appropriate lines as shown below:
```

typename std::vector<std::vector<T> >::iterator p=mat.begin()+id;  // line 218

...

typename std::vector<T>::iterator p=mat[i].begin()+id; // line 226

```

I wish I could offer an explanation as to why this is needed, but I cannot.  I just know it is.

---

### Post by CMGmadison on 2009-04-08
> **dwhitney67 said:**
> Fix the appropriate lines as shown below:
```

typename std::vector<std::vector<T> >::iterator p=mat.begin()+id;  // line 218

...

typename std::vector<T>::iterator p=mat[i].begin()+id; // line 226

```

I wish I could offer an explanation as to why this is needed, but I cannot.  I just know it is.

That solved the problem!  Thank you!

---

### Post by Habbit on 2009-04-08
> **dwhitney67 said:**
> Fix the appropriate lines as shown below:
```

typename std::vector<std::vector<T> >::iterator p=mat.begin()+id;  // line 218

...

typename std::vector<T>::iterator p=mat[i].begin()+id; // line 226

```

I wish I could offer an explanation as to why this is needed, but I cannot.  I just know it is.

Can anyone offer such explanation? I'm quite curious, and particularly I'd like to know whether it's required due to a limitation of the current C++ standard (like "no non-PODs in unions"), or of G++ (like "no more than 10-tuples").

---

