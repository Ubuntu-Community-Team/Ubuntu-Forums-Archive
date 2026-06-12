---
title: "typedef typename vector&lt;S&gt;::const_iterator const_iterator;"
date: 2007-07-14
forum: Programming Talk
---

### Post by spamalot on 2007-07-14
hi all,

could someone please help with this code?

using std::vector;
template<typename S> class E{
	public:
		E(const vector<S>& vec_):vec(vec_){}
		typedef typename vector<S>::const_iterator const_iterator;
		const_iterator begin()const{return vec.begin();};
		const_iterator end()const{return vec.end();};
		private:
			vector<S> vec;		
};

vector<double> vec(3,1.1);
E<double> e(vec);
e.const_iterator i;// Multiple markers at this line 
	                        //-error: expected `;' before ‘i’
	                        //-error: invalid use of ‘E<double>::const_iterator’

---

### Post by spamalot on 2007-07-14
...easy. sorry:

E<double>::const_iterator i;

---

### Post by Jessehk on 2007-07-14
I didn't know what the problem was, but I correctly guessed that the typedef is instantiated for the class, not the instance (or something like that). Therefore, The following will not work:

```

e.const_iterator

```

but this will

```

E<double>::const_iterator

```

EDIT: Opps, I missed your second post. My bad. :)

---

### Post by spamalot on 2007-07-15
thanks anyhow.

---

