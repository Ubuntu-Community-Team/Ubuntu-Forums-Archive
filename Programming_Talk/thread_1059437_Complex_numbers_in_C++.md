---
title: "Complex numbers in C++"
date: 2009-02-03
forum: Programming Talk
---

### Post by benjorino on 2009-02-03
I'm having a ridiculous amount of trouble trying to work with complex numbers in C++... I can't even successfully declare the damn things.
I've tried including <complex> and <complex.h>, because from what I can gather there are subtle differences between the two, but with no luck.

I've spent hours (no joke) trying to work out how to do this, and I rightly feel very stupid at the moment.

Could somebody please just write out the code to declare a complex number for me and save me a lot of trouble?


(Please?)

Thanks,
Ben

---

### Post by kjohansen on 2009-02-03
The <complex> is templated, complex.h is not.  Here is my use of <complex>.  This compiles with g++.

```

#include<complex>
#include<iostream>
using namespace std;

int main(void)
{
	complex <double> c1;
	c1=complex<double>(1,1);
	cout<<c1<<endl;
}

```

---

### Post by kjohansen on 2009-02-03
I cannot get the complex.h to work at all.  There are lots of examples out there but none of them compile for me.  Not that it matters since the <complex> works, but this was bothering me...

---

### Post by monkeyking on 2009-02-03
this works for me
[PHP]
#include <iostream>
#include <complex>
using namespace std;
int main(){
  complex<float> numone (3,5);
  complex<float> numtwo (7,11);
  complex<float> res1 = numone+numtwo;
  complex<float> res2 = numone*numtwo;

  cout<<res1<<endl;
  cout<<res2<<endl;
  return 0;
}



[/PHP]

---

### Post by benjorino on 2009-02-04
Thank you to you both, although only monkeyking's method works for me.
In retrospect, for the fairly simple purposes for which I need this functionality, I could have just written my own code!
I failed at finding a simple, working library for matrix manipulation, so I just ended up writing my own code to multiply small matrices, and it's proved much less of a headache.
Thanks :)

---

