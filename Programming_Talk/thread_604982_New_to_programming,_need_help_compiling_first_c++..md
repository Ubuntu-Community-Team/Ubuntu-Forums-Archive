---
title: "New to programming, need help compiling first c++..."
date: 2007-11-06
forum: Programming Talk
---

### Post by bf2loser on 2007-11-06
So I put this into Scite Text Editor

> 
#include <iostream>
using namespace std;
int main()
{
	int x, y;
	for(x=1;x<=10;x++)
		cout<<count<<endl;
	cin>>y;
	return 0;
}


Looks fine to me, and we used this code im my programming class and it worked fine. The problem is, we did this on windows xp using microsoft visual studio or whatever, and I cant figure out how to run this on ubuntu. I used this
gcc 1st.cpp -o first_c++_Program
and it seems to have compiled it but my problem is I cant find the binary and I dont know how to run it. Can anyone help out a nooby here? and by the way, this is the first thing ive ever written in any language other than web scripting and BASIC...

---

### Post by LaRoza on 2007-11-06
What do you mean "can't find"? If you type:

```

./programName

```

It should work.

If you don't specify -o, it will be named "a.out"

---

### Post by aks44 on 2007-11-06
0. did you install the "build-essential" package? (**sudo apt-get install build-essential**)

1. if you ain't got no output, it worked :) (which is true for **all** *nix commands I know of, however sometimes you get some output *even though* it worked)

2. for C++ use **g++** rather than gcc:
```
$ g++ -o test_output main.cpp more.cpp even_more.cpp
```

3. once compiled, run it using:
```
$ ./test_output
```
The **./** part is *very* important (not to say mandatory)


Don't hesitate to ask if you still have trouble...

---

### Post by bf2loser on 2007-11-06
oh okay, I guess it was because I was using gcc instead of g++, because it just worked, thanks guys!

---

