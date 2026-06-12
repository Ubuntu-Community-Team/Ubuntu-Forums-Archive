---
title: "C++ forward declaration"
date: 2008-05-09
forum: Programming Talk
---

### Post by Timdejager on 2008-05-09
Hi,

Im learning C++ by going through the tutorials at learncpp.com. I have a Java background so some things are quite confusing. One aspect which i don't really get is forward declaration of structs and classes. 

[PHP]#include <iostream>

class something;
int main(int argc, char** argv)
{
	using namespace std;
	something *some = new something();
	some->set(3);
	
	cout << "Hello World!";
	return 0;
}

class something{
	private:
		int i;
	public:
	void set(int a){i = a;}
}; [/PHP]

Why am i unable to compile this code? Is it impossible to forward declare classes this way?

Thanks,
Tim

---

### Post by Npl on 2008-05-09
> **Timdejager said:**
> Why am i unable to compile this code? Is it impossible to forward declare classes this way?Yep... you can forward declare classes as you did, but you cant use its methods (including Constructors) or use sizeof on them - which means its only helping if you need references or pointers to the class (I can only think of other class-delacations where you`d need this).

Everything else needs full declaration of members and methods - which is why you typically put those declarations in a header and include them where you need the class.

---

### Post by smartbei on 2008-05-09
There are two problems. The first is that you cannot 'new' an object that the compiler does not know the size of. When the compiler processes the line where you are trying to create a new instance of the class something, it does not know the size of an instance of this class, and so cannot allocate space accordingly. Also, new calls a classes constructor, which the compiler does not know about at that line.

Similarly, when you call the set() method of the something class, at that line the compiler does not yet know that this method exists, and so cannot pair it to the correct virtual table entry.

---

### Post by Timdejager on 2008-05-10
Ok this makes it somewhat clearer. So it is possible to use this kind of forward declaration for a Foo *f; reference to the object. But for more extensive use the class prototype must be more fully declared?:)

---

