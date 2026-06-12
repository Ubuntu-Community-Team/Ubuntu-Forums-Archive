---
title: "c++, cout and vectors of objects"
date: 2013-12-04
forum: Programming Talk
---

### Post by jerome1232 on 2013-12-04
So I'm thoroughly confused I'm trying to print elements of a vector of objects, and I get the comiler message of > error: no match for ‘operator<<’ in ‘std::operator<< <std::char_traits<char> >((* & std::cout.std::basic_ostream<_CharT, _Traits>::operator<< <char, std::char_traits<char> >((i + 1ul))), ((const char*)". ")) << ((GradeBook*)this)->GradeBook::theClass.std::vector<_Tp, _Alloc>::operator[]<Student, std::allocator<Student> >(i).Student::getName’|

The code:
```
    for ( size_t i = 0; i < theClass.size(); ++i ) {
        cout << i + 1 << ". " << theClass[i].getName << endl;
        }
```

theClass's definition
```
vector<Student> theClass;
```

The student header
```
 class Student
 {
	private:
		string studentName;
	public:
	    /* Constructs a Student object with student name studentName
		 * @param studentName student name
		 */
		Student( string );

		/* Set student name to name
		 * @param name student Name
		 */
		void setName( string studentName ) { this->studentName = studentName; }

		/* returns a studentName
		 * @return student name
		 */
		string getName() const { return studentName; }
};
```

---

### Post by spjackson on 2013-12-04
I *think* it is simply that you are missing the parentheses for calling the getName method. i.e. you want:
```

    cout << i + 1 << ". " << theClass[i].getName() << endl;

```

---

### Post by jerome1232 on 2013-12-04
oh gosh, it's always the simple things. That did eliminate the compiler error. Thanks.

::feeling sheepish::

---

