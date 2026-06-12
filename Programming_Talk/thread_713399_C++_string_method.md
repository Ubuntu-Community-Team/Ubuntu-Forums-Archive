---
title: "C++ string method"
date: 2008-03-02
forum: Programming Talk
---

### Post by tashe on 2008-03-02
I have this class with a method:

class Record {
	private:
		string name;
		int	won,lost;
	public:
            string showName() {
			return this->name;
		}

I want the method to return the name after being called, but instead it doesn't return anything when I call it.
Anyone?

---

### Post by LaRoza on 2008-03-02
That code doesn't show the variable "name" having a value, is there a setter function? Or is it set in the constructor?

Is the notation -> needed with C++ strings? You didn't declare a pointer.

---

### Post by tashe on 2008-03-02
The answer to my stupid question is simple. 
I inserted:
Record a;
a.showName();
The correct thing was to do the following: 
cout<<a.showName();
and it all sorted itself out
thanks for the effort anyway ;)

---

