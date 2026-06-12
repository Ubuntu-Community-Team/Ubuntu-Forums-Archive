---
title: "Why I Got This Compilation Error?"
date: 2010-03-30
forum: Programming Talk
---

### Post by huangyingw on 2010-03-30
Hello,
    I got compilation error:```
Error	1	error C2248: 'std::basic_ios<_Elem,_Traits>::basic_ios' : cannot access private member declared in class 'std::basic_ios<_Elem,_Traits>'	c:\program files\microsoft visual studio 9.0\vc\include\fstream	803	List

```
    at this file:```
#include <fstream>
using namespace std;

class List
{
	public:
		List MergeCreateNew();
	private:
		ofstream fout; 	
};

List List::MergeCreateNew()
{
	List result;
	return result;
}
```
      I know if I return a reference in MergeCreateNew, I would not get this error. But, I don't think this a good idea.
      Could someone point to me a better solution to this error?

---

### Post by Zugzwang on 2010-03-30
I think that "ofstream" objects are non-copyable. However, returning a "List" object would require copying its contents. As you did not define assignment operators and copy-constructors, it is automatically generated. Finally, automatic generation fails because the automatically generated copy-constructor would copy the "ofstream" object which is non-copyable.

Note that whenever you have problems like this, it is a good idea to compile with "g++" and copy&paste the resulting error messages into this forum. The Visual C++ error messages are unknown to most of us here, so you are likely to get better answers this way.

---

### Post by MadCow108 on 2010-03-30
yes streams are not copyable, it would also make little sense to do so.

solution:
save a reference to the stream instead of the stream itself

---

### Post by huangyingw on 2010-03-31
> **Zugzwang said:**
> I think that "ofstream" objects are non-copyable. However, returning a "List" object would require copying its contents. As you did not define assignment operators and copy-constructors, it is automatically generated. Finally, automatic generation fails because the automatically generated copy-constructor would copy the "ofstream" object which is non-copyable.

Note that whenever you have problems like this, it is a good idea to compile with "g++" and copy&paste the resulting error messages into this forum. The Visual C++ error messages are unknown to most of us here, so you are likely to get better answers this way.
Yes, thanks. You point out the root. For c, c++ programming, I will try in Linux from now on.

---

### Post by huangyingw on 2010-03-31
> **MadCow108 said:**
> yes streams are not copyable, it would also make little sense to do so.

solution:
save a reference to the stream instead of the stream itself
Thanks. Sometimes, I am very hesitated at using reference. The problem of reference to a release memory area, is quite headaching..

---

### Post by Zugzwang on 2010-03-31
> **huangyingw said:**
> Thanks. Sometimes, I am very hesitated at using reference. The problem of reference to a release memory area, is quite headaching..

There are the so-called smart pointers which release you from the duty to do so yourself. You might want to have a look: [http://ootips.org/yonat/4dev/smart-pointers.html](http://ootips.org/yonat/4dev/smart-pointers.html)

---

### Post by huangyingw on 2010-04-01
> **Zugzwang said:**
> There are the so-called smart pointers which release you from the duty to do so yourself. You might want to have a look: [http://ootips.org/yonat/4dev/smart-pointers.html](http://ootips.org/yonat/4dev/smart-pointers.html)
Thanks, I am reading.

---

