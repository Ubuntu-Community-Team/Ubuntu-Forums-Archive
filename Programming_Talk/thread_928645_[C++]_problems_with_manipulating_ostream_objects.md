---
title: "[C++] problems with manipulating ostream objects"
date: 2008-09-24
forum: Programming Talk
---

### Post by NovaAesa on 2008-09-24
Hi, I have to do some manipulation of ostream objects, but I'm somewhat stuck.

Say I have the following code:
```

#include <ostream>
#include <iostream>
using namespace std;

class foo {
    
    public:
    foo(int num) {
        this->num = num;
    }
    
    private:
    int num;
    
    friend ostream& operator<<(ostream& out, foo& f) {
        out << f.num << (f.num+1) << endl;
        out << (f.num+2) << (f.num+3) << endl;
        return out;
    }
};

int main() {
    foo a(1);
    foo b(5);
    cout << a << b;
    return 0;
}
```
It will print out:
```

12
34
56
78
```
This is exactly what I would expect from that code (so no problem there), but it's not really what I want to do. What I really want to do is print out the following:
```

1256
3478
```
So rather that printing each foo object after each other, I need to do some sort of 'splicing' to get them side by side. Does anyone know the best way of doing this? Even a point in the right direction would be nice, i.e. which class I should look at to use. I've been trying to work this out for a few hours now, and it's getting a bit frustrating... Well, I haven't been working on this exact code, this is just the extraction of my problem into an easy example.

Thank you to anyone who can help. :)

---

### Post by mike_g on 2008-09-24
Would this do what you want?
```
    friend ostream& operator<<(ostream& out, foo& f) {
        out << f.num << (f.num+1) << (f.num+4) << (f.num+5) << endl;
        return out;
    }
```
Edit: oh, no that would not work for 'b' but perhaps you could create a variable negative offset based on the f.num?

---

### Post by NovaAesa on 2008-09-24
Thanks for the reply mike_g. That's not really what I want though. Say I have two objects that are going to both print out multiline text (in a rectangle, so length is the same for each line). Now instead of printing the two rectanges of text on top of each other, I want to print them side by side.

E.g. I have an object that will print:
&*&*&*
*&*&*&
&*&*&*

and an object that will print:
#$#$#$
$#$#$#
#$#$#$
$#$#$#

I want to somehow write a function that can use their << operators to print out:
&*&*&*#$#$#$
*&*&*&$#$#$#
&*&*&*#$#$#$
*&*&*&$#$#$#

Thanks, sorry about not being clearer about it before.

---

### Post by kjohansen on 2008-09-24
i dont think this is going to be possible just by overriding the << operator. the << operator of each class would have to know which object to print, but the << is only going to take one argument.  And what would happen if you did

```

foo a(1);
foo b(2);
foo c(4);
cout<<a<<b<<c;

or 

foo a(1);
foo c(4);
cout<<a<<"foo"<<c;


```

There is too much variability here.


if you are set on overriding the << I think you are going to have to create a wrapper class that holds two objects, or a list of objects.

---

### Post by davidcaiazzo on 2008-09-25
Hmmm the only way I can seem to get this to work is by doing this:
```

#include <iostream>
#include <vector>
using namespace std;

class foo {
    
    public:
    foo(int num) {
        this->num = num;
    }
    int getnum(){
    	return num;
	}
    
    private:
    int num;
    
    friend ostream& operator<<(ostream& out, vector<foo>& f) {
    	for(size_t i=0;i<f.size();i++){
    		out << f[i].getnum()<< f[i].getnum()+1;
		}
		out<<endl;
    	for(size_t i=0;i<f.size();i++){
    		out << f[i].getnum()+2 << f[i].getnum()+3;
		}
		return out;
	}
};

int main() {
    foo a(1);
    foo b(5);
    vector<foo>c;
    c.push_back(a);
    c.push_back(b);
    cout<<c;
    		
}

```

This is by no means a perfect way to do this at all...but it seems to be what you are looking for.

---

### Post by NovaAesa on 2008-09-25
Thanks for the help guys. I asked some of my friends at uni (who are a few years ahead of me) and they said to just have a method that will return a string and then make a splicing algorithm that will put it all together.

Thank you for the replies!
I will post up my algorithm later (once I have written it) for anyone else that has this particular problem.

---

