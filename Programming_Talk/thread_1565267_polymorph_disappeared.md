---
title: "polymorph disappeared?"
date: 2010-08-31
forum: Programming Talk
---

### Post by worksofcraft on 2010-08-31
OK I know my C++ is a bit rusty, but I'm totally baffled by this:

```

#include <stdio.h>

typedef const char *charptr;

// base class with default virtual operators
struct obj {
	virtual obj *operator[] (charptr) { return NULL; }
	virtual operator const charptr() const { return "instance of obj"; }
};

// derived class overrides const char* cast to identify itself differently
struct string_obj: obj {
	const charptr S;
	string_obj(charptr pName): S(pName) {}
	operator const charptr() { return S; }
};

// derived class overrides indexing by string to return a string_obj
struct index_obj: obj {
	obj *operator[] (charptr pName) {
		string_obj *S = new string_obj(pName);
		printf("S=%s\n", (charptr) *S);
		return S;
	}
};

int main() {
	index_obj IndexObj;
	obj *pStringObj = IndexObj["instance of string_obj"];
	printf("but *pStringObj=%s\n", (charptr) *pStringObj);
	delete pStringObj;
}

```

*pStringObj polymorphism should allow me to print the string_obj charptr result but it doesn't :shock: It prints:
```

$> g++ a.cc
$> ./a.out
S=instance of string_obj
but *pStringObj=instance of obj

```

Now why on earth is that?

---

### Post by GeneralZod on 2010-08-31
```

// derived class overrides const char* cast to identify itself differently
struct string_obj: obj {
        const charptr S;
        string_obj(charptr pName): S(pName) {}
        operator const charptr() const { return S; }
};

```  

Spot the difference ;)

---

### Post by worksofcraft on 2010-08-31
> **GeneralZod said:**
> ```

// derived class overrides const char* cast to identify itself differently
struct string_obj: obj {
        const charptr S;
        string_obj(charptr pName): S(pName) {}
        operator const charptr() const { return S; }
};

```  

Spot the difference ;)

Yes, thank you ever so much :)

... but now I'm puzzled why that should be necessary, in particular because my real application index_obj derives from template map and then I don't think it's going to let me use a an operator charptr() const there :(

---

### Post by GeneralZod on 2010-08-31
> **worksofcraft said:**
> 
... but now I'm puzzled why that should be necessary, in particular because my real application index_obj derives from template map and then I don't think it's going to let me use a an operator charptr() const there :(

charptr() in the base class was marked as const; in the derived class it was not: signatures differ (I believe - I should probably check with the standard), so the method in the derived class did not *override* that in the base class.

---

