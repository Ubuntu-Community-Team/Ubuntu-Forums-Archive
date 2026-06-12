---
title: "c++ array largest size?"
date: 2008-02-27
forum: Programming Talk
---

### Post by nbo10 on 2008-02-27
Hey, I have a program with some arrays

when I add this line to my program

complex<double> Field[1000][1000][50];

The program complies but when I execute the program comes back  with

Segmentation fault (core dumped) 

but with

complex<double> Field[64][64][50];

everything runs just fine. I'm not doing anything to the arrays just declaring them.

How can I increase the size of the arrays I can use. I'm using g++ compiler.

Thanks

---

### Post by darsu on 2008-02-27
If I catch myself thinking I need an array that huge when I'm programming, I'll think very hard of a more optimized way to store whatever I'm going to store.

What are you trying to do?

---

### Post by nbo10 on 2008-02-27
I'm doing a physics calculation on a grid. and the third dimension is sorta like a time value.

---

### Post by hod139 on 2008-02-27
This question seems to keep coming up: 
[http://ubuntuforums.org/showthread.php?t=680535](http://ubuntuforums.org/showthread.php?t=680535)
The problem is that you are allocating on the (limited) stack.

---

### Post by arkangel on 2008-02-27
if coming from PDE  ,  use a sparse format

A complex is  2 long  double,   simply it does not fit in memory 

anyway try  with 
ulimit -s unlimited 

but try to store it in a more efficient way

---

### Post by nbo10 on 2008-02-27
I used the ulimit -s unlimited  command and got everything working. 

I don't know how to store it more efficiently.

---

### Post by arkangel on 2008-02-27
what are you doing ?  can you explain in more detail  ?

---

### Post by nbo10 on 2008-02-27
This is the meat of my program 
```

for(h = -3;h<=3;h++){
	for(k=-3;k<=3;k++){
		m++;
	//	cout << m << endl;
		for(int xi=0;xi<gridsize;xi++){
			for(int yi=0;yi<gridsize;yi++){
				complex<double> num(0, q* (h*(xi*dx - (150*a) ) + k*(yi*dy - (150*a))));
				complex<double> frontx(0,q*h);
				complex<double> fronty(0,q*k);
				Field[xi][yi][0] = Field[xi][yi][0] +  FormFactorAveTotal[h+3][k+3] * exp(num);
				derBx[xi][yi] = derBx[xi][yi] + constant*FormFactorAveTotal[h+3][k+3] * frontx * exp(num);
				derBy[xi][yi] = derBy[xi][yi] + constant*FormFactorAveTotal[h+3][k+3] * fronty * exp(num);
			//	Field[xi][yi][m-1] = FormFactorAveTotal[h+3][k+3] *   exp(num);
			//	cout << exp(num) << endl;
				//cout << yi*dy - (ysize)*a/2 <<endl;
				//postion[xi][yi] = xsize
	//			cout << h <<" " << k << endl; 
			}
		}
	}
}

```

---

### Post by arkangel on 2008-02-27
and that means ? :S

If the last dimension is time ,  do  you need a complex time ?

maybe you can have  a 2D array for whatever you need and 3D array of floats to store the time 

I see a grid size something? ...   so if your grid is regular you need  only to store the diagonals  or even something smaller 

 try to  think about ?

---

### Post by nbo10 on 2008-02-27
Just calculating the diagonal would be meaningless. 

I'm calculating the magnetic field over a region of space. 

I said the third Dimension was sorta like time, it keeps track of changes as h and k change.

---

### Post by arkangel on 2008-02-27
I didn't mean the diagonal   i mean several diagonals 

well   I can think  in the following 

you need all previous times ?  or only 1 or 2 or none  ,  then you can flush in files  and  use a  3D array with a small 3rd dimension ....

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-28
it has nothing to do with time
he has a bunch of points in 2d space that all have a value that needs to be stored with them

Am i correct? is this what your doing.

---

### Post by arkangel on 2008-02-29
exactly !  but  does he need to store all of them  during run time ?  does he need 50 values for each point ?

---

