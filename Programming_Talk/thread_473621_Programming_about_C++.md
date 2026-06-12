---
title: "Programming about C++"
date: 2007-06-14
forum: Programming Talk
---

### Post by Lina_inpas on 2007-06-14
Hello!
I met a problem in C++ programming. 
It says:'[B]no 'Matrix Matrix::toep(Matrix&)' member function declared in      
            class 'Matrix[/B]' after I compile it.
But I have already declare it in the class' Matrix' (Matrix.h) like below:
     class Matrix;
     class cplxMatrix;
     class Matrix  
{      public:
		int rowNum;  // number of rows
		......
	public:
		Matrix(); // Constructor
		......
		**Matrix toep(Matrix& A);**
}
and the problem occured when I defined this function 'Matrix toep(Matrix& A) in another file(Matrix.cc)


I don't know what's wrong with it!.

---

### Post by WW on 2007-06-14
In Matrix.cc, the function should be declared as:
```

Matrix Matrix::toep(Matrix& A)

```

---

### Post by Lina_inpas on 2007-06-14
Thanks, But I did use '**Matrix Matrix::toep(Matrix& A)**' in the file' Matrix.cc'.

---

### Post by WW on 2007-06-14
For some reason, the signature of the definition of toep does not match the declaration in the header file.  Could you post the complete header file?

---

### Post by Soybean on 2007-06-14
It's probably something simple...
1) Did you ```
#include "Matrix.h"
``` in Matrix.cc and in whichever file you're calling the function from?
2) Check spelling carefully. I know it's a 4-letter function and this seems obvious, but a typo is the easiest way to get that error. Check for typos in the return type and parameter, too. And check all 3 places -- the declaration, the definition, and the place you're calling it from (where the error is probably being reported).
3) Check the line(s) immediately above the declaration of the function. Unclosed quotation marks or parentheses, or missing semicolons, often result in confusing error messages pointing a line or two after the actual problem.
4) If you're still having trouble, consider copy-pasting the actual code in here, rather than retyping it. If it is a typo, it's hard for us to tell from "well, the code looks kind of like this: ..." ;)

---

### Post by Lina_inpas on 2007-06-14
Thanks to all !!!
I have fixed it. I recopied the original words and it worked. So I guess there was something wrong with the typos.
:D

---

### Post by PandaGoat on 2007-06-14
The missing A is because the compiler makes the code more efficient and leaving that off goes towards that goal.

---

