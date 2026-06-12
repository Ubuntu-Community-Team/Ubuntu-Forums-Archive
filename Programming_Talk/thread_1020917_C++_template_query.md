---
title: "C++ template query"
date: 2008-12-24
forum: Programming Talk
---

### Post by WebDrake on 2008-12-24
Hello everyone,

I'm writing some C++ code with two sets of classes.  The first class (and its subclasses) are for performing data analysis.  The second class is for generating that data and feeding it to the data analysis class.

Conceptually, the problem is like this: the data analysis classes all have a common interface, but different internal algorithms.  They are all of the form, roughly,
```

template<class T1, class T2> analysisClass {
    /* ... */
}

```

Depending on the use case, the data generation classes may want to use one or the other of these analysis classes.  The question is how to achieve this.

My desire is to have a template of roughly the form,
```

template<class ANALYSISCLASS> dataClass {
    ANALYSISCLASS<int,int> a;
    /* ... */
}

```
... but this is illegal: if I declare, for example ```
dataclass<analysisClass>
``` then I'm not passing it a type.

I could of course rewrite the code above as,
```

template<class ANALYSISCLASS> dataClass {
    ANALYSISCLASS a;
    /* ... */
}

``` and then use ```
dataclass< analysisClass<int,int> >
``` but I want the types T1, T2 to be hardwired inside dataClass.

Can anyone advise on how to achieve what I'm trying to do?

By analogy, consider the following (correct, compilable) code which I put together to experiment with the concept I was trying to achieve.  In this case it puts a 'wrapper' class around a container of some kind, either a vector or a list:
```

#include <iostream>
#include <list>
#include <vector>

using namespace std;

template<class CONTAINER> class myContainer {
private:
	CONTAINER x;
public:
	void push_back(double z)
	{
		x.push_back(z);
	}
	void print()
	{
		for(typename CONTAINER::iterator it=x.begin();
		    it!=x.end();++it) {
			cout << (*it) << " ";
		}
		cout << endl;
	}
};

int main()
{
	myContainer< vector<double> > v;
	myContainer< list<double> > l;

	for(int i=0;i<10;++i) {
		v.push_back(((double) i)/2);
		l.push_back(-i);
	}
	v.print();
	l.print();
	return 0;
}

```
Here you can see the declarations of the form e.g. ```
mycontainer< vector<double> >
``` when what I would really like is to be able simply to specify the class of container (vector or list) and let the myContainer class take care of the datatype (in this case, double).

Is there a way to achieve what I want or am I going about this completely the wrong way?

Thanks & best wishes,

    -- Joe

---

