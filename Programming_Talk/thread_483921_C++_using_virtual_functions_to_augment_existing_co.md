---
title: "C++: using virtual functions to augment existing code"
date: 2007-06-25
forum: Programming Talk
---

### Post by WebDrake on 2007-06-25
One more in the C/C++ "How do I ... ?" query list. :)

According to the C++ FAQ, [http://www.parashift.com/c++-faq-lite/virtual-functions.html#faq-20.1](http://www.parashift.com/c++-faq-lite/virtual-functions.html#faq-20.1), when defining virtual functions,
> The derived class can either fully replace ("override") the base class member function, or the derived class can partially replace ("augment") the base class member function. The latter is accomplished by having the derived class member function call the base class member function, if desired.

I've been unable to find any examples of the latter procedure------using a virtual function to augment the one in the base class.  Could someone give an example?

Many thanks again.

---

### Post by hod139 on 2007-06-25
Here is an example.
```

#include <iostream>

class BaseClass{
protected: 
  void printFunction(){
    std::cout << "Hello";
  } 
};

class DerivedClass : public BaseClass{
public:
  void printFunction(){
    BaseClass::printFunction(); // call the Base class function
    std::cout << " World" << std::endl; // Augment it
  }
};

int main(void){
  DerivedClass dc;
  dc.printFunction();
 
  return 0;
}

```

---

### Post by WebDrake on 2007-06-25
> **hod139 said:**
> Here is an example.
```

#include <iostream>

class BaseClass{
protected: 
  void printFunction(){
    std::cout << "Hello";
  } 
};

class DerivedClass : public BaseClass{
public:
  void printFunction(){
    BaseClass::printFunction(); // call the Base class function
    std::cout << " World" << std::endl; // Augment it
  }
};

int main(void){
  DerivedClass dc;
  dc.printFunction();
 
  return 0;
}

```
D'oh!

Thanks very much. :)

---

### Post by the_unforgiven on 2007-06-25
Here's another example:
```
#include <iostream>

class person
{
	private:
		std::string m_name;
		int m_age;
	public:
		person(const std::string& name, int age) 
			: m_name(name), m_age(age)
		{
		}

		void print_details()
		{
			std::cout << "Name: " << m_name << std::endl;
			std::cout << "Age: " << m_age << std::endl;
		}
};

class employee : public person
{
	private:
		std::string m_dept;
		int m_sal;
	public:
		employee(const std::string& name, int age,
			const std::string& dept, int sal) 
		: person(name, age), m_dept(dept), m_sal(sal)
		{
		}

		void print_details()
		{
			person::print_details();
			std::cout << "Dept: " << m_dept << std::endl;
			std::cout << "Salary: " << m_sal << std::endl;
		}
};

class student : public person
{
	private:
		std::string m_class;

	public:
		student(const std::string& name, int age, 
			const std::string& standard)
		: person(name, age), m_class(standard) {}

		void print_details()
		{
			person::print_details();
			std::cout << "Standard: " << m_class << std::endl;
		}
};

int main()
{
	person jack("Jack", 20);
	employee tom("Tom", 30, "Engg.", 3000);
	student tim("Tim", 16, "Tenth");

	jack.print_details();
	tom.print_details();
	tim.print_details();

	return 0;
}
```

---

