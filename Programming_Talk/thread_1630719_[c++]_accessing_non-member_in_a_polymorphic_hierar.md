---
title: "[c++] accessing non-member in a polymorphic hierarchy"
date: 2010-11-25
forum: Programming Talk
---

### Post by josephellengar on 2010-11-25
I asked this question in a rather obtuse/roundabout way in another thread, so I thought that I'd repost and try to ask the question more clearly here.

My problem function is this:
```

const Multinumber& Complex::operator+(const Multinumber & rhs) const
{
    return Complex(real + rhs.real, imag + rhs.imag);
}

```

The Complex class is an extension of Multinumber. Multinumber does not have the members imag and real, but Complex does. Whenever I try to compile this, I get a number of errors such as this one: 

```

/home/ross/flash/current/CS260/assignment6/Complex.cpp|27|error: 'const class Multinumber' has no member named 'real'|

```

Obviously I need to somehow tell the compiler to treat rhs as a Complex object, but i cannot change the function header to 

```

const Multinumber& Complex::operator+(const Complex & rhs) const

```

because the function is polymorphic and other classes in my hierarchy have the exact same header. Does anybody know how to fix this? Thank you.

---

### Post by worksofcraft on 2010-11-25
> **rossholley said:**
> I asked this question in a rather obtuse/roundabout way in another thread, so I thought that I'd repost and try to ask the question more clearly here.

My problem function is this:
```

const Multinumber& Complex::operator+(const Multinumber & rhs) const
{
    return Complex(real + rhs.real, imag + rhs.imag);
}

```

The Complex class is an extension of Multinumber. Multinumber does not have the members imag and real, but Complex does. Whenever I try to compile this, I get a number of errors such as this one: 

```

/home/ross/flash/current/CS260/assignment6/Complex.cpp|27|error: 'const class Multinumber' has no member named 'real'|

```

Obviously I need to somehow tell the compiler to treat rhs as a Complex object, but i cannot change the function header to 

```

const Multinumber& Complex::operator+(const Complex & rhs) const

```

because the function is polymorphic and other classes in my hierarchy have the exact same header. Does anybody know how to fix this? Thank you.

Yes, you need to cast your Multinumber rhs into a Complex and the safe way to do that is with dynamic_cast.

p.s. also if you return something by reference then you should not construct the thing where you return it. After returning it will have been destroyed leaving nothing there for the reference to refer to :shock:

---

### Post by nvteighen on 2010-11-25
I'm not sure on this, but wouldn't it be better to return a Complex& and take a Complex& as an argument? If someone wants to do the "pointer to base class", it's the caller's problem, not the callee... Really, I don't understand why you'd declare an operetor+ that returns and takes a Multinumber in the Complex class's namespace.

(I've read your other thread and I'm completely confused as to what your design is, although I think I understand what you want to do: an hyper-abstracted number class)

---

### Post by josephellengar on 2010-11-25
> **nvteighen said:**
> I'm not sure on this, but wouldn't it be better to return a Complex& and take a Complex& as an argument? If someone wants to do the "pointer to base class", it's the caller's problem, not the callee... Really, I don't understand why you'd declare an operetor+ that returns and takes a Multinumber in the Complex class's namespace.

(I've read your other thread and I'm completely confused as to what your design is, although I think I understand what you want to do: an hyper-abstracted number class)

I can't do that because then I couldn't make the call polymorphically. All three of my subclasses have the same functions but the functions would be different if the arguments were different, in which case I would have to write my data structure differently for each one.

---

### Post by worksofcraft on 2010-11-25
IDK... perhaps this will explain why you can't return the Complex by reference:

[php]
// g++ multinumber.cpp
#include <cstdio>

struct Multinumber {
	virtual Multinumber &operator+(const Multinumber & rhs) const = 0;
	virtual ~Multinumber() {}
	virtual void display() const = 0;
};

struct Complex: Multinumber {
	static Complex sResult;
	double real, imag;

	Complex & operator=(const Complex &rRhs) {
		printf("copying %p to %p\n", &rRhs, this);
		real = rRhs.real;
		imag = rRhs.imag;
		return *this;
	}
	Complex(double R, double I): real(R), imag(I) {
		printf("constructing "); display();
	}
	~Complex() {
		printf("destructing "); display();
	}
	Multinumber& operator+(const Multinumber & rhs) const {
		const Complex & rRhs = dynamic_cast<const Complex &> (rhs);
		// creates a temporary result then copies it to the statically allocated one
		sResult = Complex(real + rRhs.real, imag + rRhs.imag);
		// returns a reference to the statically allocated result
		// this is probably NOT what you want, but you can't return covariant type by value
		// because the compiler won't know how much memory to allocate for the result!
		return sResult;
	}
	void display() const {
		printf("Complex(%f, %f) @%p\n", real, imag, this);
	}
};

Complex Complex::sResult(0, 0);

int main(int argc, char *argv[], char *envp[]) {
	Complex A(1,2), B(3,4);
	Multinumber &C = A + B;
	C.display();
	return 0;
}
[/php]

p.s. if you had simply returned the temporary result by reference instead of the static copy then it would have
already been destroyed when you return to main!

---

