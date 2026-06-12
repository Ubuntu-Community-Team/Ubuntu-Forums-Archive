---
title: "C++ Adding/Output of long int"
date: 2007-02-21
forum: Programming Talk
---

### Post by qpwoeiruty on 2007-02-21
I've been trying to add an int+exponent to a long int by typecasting. No matter the combination, I can't seem to get the cout to work correctly. Usually, when the program is run, it outputs a value less than 10 instead of i*1e6+j*1e3+k.
As of now, I'm stuck...

The offending relevant code:
```

	int origin, m, i, j, k;
        long int step[50]={0};
	x=y=z=origin=m=0;
	
	srand(time(NULL));					//seed the RNG

        //i, j, k are defined from 0 to 1000 by for loops

	step[m] = (long int)(i)*(long int)(1000000);
	step[m] += (long int)(j)*1000;
	step[m] += (long int)(k);
        m++;

	for(int n=0; n<m; n++) {
		cout << step[n] << endl;
        }
}

```

---

### Post by thumper on 2007-02-21
If you show a little more about the initialisation of i, j, and k it might make a little more sense.

Also for constants you can specify
```

long somevalue = 1000000L;

```
Also when an int is used in conjunction with a long, the int gets 'promoted' to a long for the calculations.

I'm guessing it is a coding problem rather than a casting problem.  You don't need to cast like this.

---

### Post by qpwoeiruty on 2007-02-21
Thanks. This made it work.

```

long long int step[25] = {0}

step[m] = i*1000000ll + j*1000ll + k +1;

```
I think that was all I changed and it does work now.

Since you asked, this is i,j,k
```

for(int i=0; i<1000; i++) {
	for(int j=0; j<1000; j++) {
		for(int k=0; k<1000; k++) {
                      //stuff } //stuff } //stuff+the step[m] part }

```
Just simple increments doing things in the inner, middle, and outer loops...

---

### Post by thumper on 2007-02-22
I suppose I should point out that you are putting way more than 50 or 25 items into your step variable (which you should be using std::vector or std::deque for).

---

