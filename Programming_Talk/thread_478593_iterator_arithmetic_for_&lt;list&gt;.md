---
title: "iterator arithmetic for &lt;list&gt;"
date: 2007-06-19
forum: Programming Talk
---

### Post by spamalot on 2007-06-19
hello everyone!

i have a feeling std::list does not support distance between two iterators. is it or not?

i would have thought the member difference_type would have something to do with it (e.g. [http://www.informatik.uni-freiburg.de/~danlee/fun/STL-doc/STL/List.html](http://www.informatik.uni-freiburg.de/~danlee/fun/STL-doc/STL/List.html)). does it?

i am using g++ within eclipse

e.g.

std::list<ClassA> aList; 
// put some elements in a List
typedef std::list<ClassA> Iter;
Iter i=aList.begin();
// while(some condition){++i;};
 if(aList.end()==++i){...}; //works OK

-------------------------------
however if i replace the last line by
by if(myList.end()==(i+1)){...}; (or some variant of it ) i get:

error: no match for `operator+' (or some variant)

---

### Post by spamalot on 2007-06-19
erratum:

not 

by if(myList.end()==(i+1)){...}; (or some variant of it ) i get: 

but 

not by if(aList.end()==(i+1)){...}; (or some variant of it ) i get:

---

### Post by spamalot on 2007-06-19
after a bit of experimentation it appears the answer to the first question is no: iterator difference is supported:

typedef list<ClassA>::difference_type Difference
Difference diff=distance(aList.end(),i)
if(diff==1){...}

i would have thought there'd be a less cumbersome way...

---

### Post by aks44 on 2007-06-19
std::list iterators are not random, only bidirectional.

what exactly are you trying to achieve? there definitely IS an easier way to do it, we just need to know what you're trying to do...

---

### Post by spamalot on 2007-06-20
hi, thanks!

yes, i'm aware it's bi-directional and i'm not attempting list[i].

i would like to return the number of increments to take a list iterator, say i, from its current position to end().

thanks again!

---

### Post by aks44 on 2007-06-20
> **spamalot said:**
> yes, i'm aware it's bi-directional and i'm not attempting list[i].
operator+() / operator-() are only defined for random iterators, that's why I mentionned it in the first place. They are equivalent to subscript indexing.

> **spamalot said:**
> i would like to return the number of increments to take a list iterator, say i, from its current position to end().
*Why* do you want to do that? Without you being a bit more specific, it will be hard to help you. I believe your problem lies more in the chosen approach / algorithm than in a specific line of code. A few (complete) lines of code may help, even pseudo-code or non compilable C++.

Sure there is a way to rewrite your algorithm so you get rid of that ugly / non efficient distance().

Cheers

---

### Post by spamalot on 2007-06-20
good point, thanks.

in the end i'm asking mostly out of curiosity because it turns out the the first solution i proposed, which tests directly whether  .end() is reached is cleaner (see un-commented below).

however, here's the complete code. you might see things within it that can be improved. 

the member function below updates an approximation (envelope) to a function f formed by joining the segments {(x_i,f_i=f(x_i)):i=1,...,n} with {x_1,...,x_n} ordered. l_abscissa and right are x_1 and (x_n,f_n), respectively.  the update varies on whether the new point (x,f(x)) is x<x_1, x>x_n or in the middle.

thanks again for you interest!

void Log_density_lower_envelope::update(Log_density_point& log_density_point){
	typedef std::list<Log_density_join_segment>::iterator Iter;

	double x=log_density_point.abscissa();
	if(x<l_abscissa){			
			Log_density_join_segment tmp(log_density_point,envelope.begin()->left());
			envelope.push_front(tmp);
			l_abscissa=x;
		}else
		{
			if(x>right.abscissa()){
				Log_density_join_segment tmp(right,log_density_point);
				envelope.push_back(tmp);
				right=log_density_point;
			} else {
					Iter i=envelope.begin(); 
					while(!(i->is_in_interval(x))){++i;};				
					i->update_ub(log_density_point); 
					if(envelope.end()==++i){//instead of //envelope.end()-1==i 
							Log_density_join_segment tmp(log_density_point,right);			
							envelope.push_back(tmp);
						} else {
							Log_density_join_segment tmp(log_density_point,i->left());
							envelope.insert(i,tmp);							
					};
				};
		};
};

---

### Post by spamalot on 2007-06-20
ps: i'm still puzzled as to why distance(i1,i2) works and not i2-i1.

---

### Post by spamalot on 2007-06-20
ps2: i mean obviously the implementation has to be different, but how?

---

### Post by aks44 on 2007-06-20
> **spamalot]ps: i'm still puzzled as to why distance(i1,i2) works and not i2-i1.
ps2: i mean obviously the implementation has to be different, but how?[/QUOTE]

Here is one possible (yet very inefficient) implementation of **distance()** (warning, pseudo code ahead, for the sake of explaining the concept) :

```
Difference distance(Iterator i1, Iterator i2)
{
  Difference result = 0 said:**
> ()**.
I hope you get the basic idea...


[QUOTE=spamalot;2882231]```
Iter i=envelope.begin(); 
while(!(i->is_in_interval(x))){++i;};				
i->update_ub(log_density_point); 
if(envelope.end()==++i){//instead of //envelope.end()-1==i 
	Log_density_join_segment tmp(log_density_point,right);			
	envelope.push_back(tmp);
} else {
	Log_density_join_segment tmp(log_density_point,i->left());
	envelope.insert(i,tmp);							
};
```

I see one problem with this code... whenever you enter the **else** block, your iterator has already been incremented. So **(envelope.end()==++i)** is not a direct replacement for **(distance(i,envelope.end())==1)** or the supposed **(i+1==envelope.end())**, as **distance()** is not supposed to change the iterators that are passed as arguments (and neither is **operator+()**).

I can't guess much about your underlying data structure (Log_density_point / Log_density_join_segment), but what strikes me is that you should be able to store only a list of points, and have your other functions operate on pairs of points.
It would allow you to avoid maintaining the segments.

At work we use this scheme in a data analysis application, and it has proven way more reliable & performant than the segments option in our case. YMMV though.

Hope this helps a bit.

---

### Post by spamalot on 2007-06-20
thanks again aks44,

think i follow what you are saying.

keeping a list of K-1 segments vs K points: the slope of each segment is stored rather than computed each time is it needed but since you tell me that does not offset the overhead associated with i'll probably try both ways.

whenever you enter else etc: seemed to work but will think more about it.

cheers.

---

### Post by spamalot on 2007-06-25
aks44, you we're so right about "I can't guess much about your underlying data structure (Log_density_point / Log_density_join_segment), but what strikes me is that you should be able to store only a list of points, and have your other functions operate on pairs of points.
It would allow you to avoid maintaining the segments." thanks again!

---

### Post by aks44 on 2007-06-25
You're welcome.

Another tip : *IF* you really need performance on that matter, you can still cache segment slopes in a separate vector. However, there is absolutely no need to do that unless your profiler tells you to ;)

---

