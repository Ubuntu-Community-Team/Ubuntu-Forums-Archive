---
title: "gcc error; can't pin down the problem"
date: 2008-03-01
forum: Programming Talk
---

### Post by rye_ on 2008-03-01
Hi all, 

I'm sure I'll kick myself, but can someone please help me with the error I get for the following code;
[http://projecteuler.net/index.php?section=problems&id=9]("http://projecteuler.net/index.php?section=problems&id=9")

The code is short enough, and the gcc outputs several and unclear, such that I'm not going to bother posting them.

```

#include <stdio.h>
#include <math.h>
#include <stdbool.h>

#define LIMIT 300
#define PI 3.14
#define theta = 30, //therefore sin(30) = .5, cos(30) = 1/sqrt(2)

int main(int argc, char * argv[]){
	
	int x_dim;
	for (x_dim = 1; x_dim < LIMIT; x_dim++){	
		double y_dim = x_dim*tan(theta*PI/180);
		double hyp = x_dim/cos(theta*PI/180);
		double test = x_dim*y_dim*hyp;
		if (test == 1000){
			printf("answer is %lf\n", test);
			break;
		}
	}
		
	return 0;
	
}

```

---

### Post by mike_g on 2008-03-01
Shouldent this:
```
#define theta = 30, //therefore sin(30) = .5, cos(30) = 1/sqrt(2)
```
Be:
```
#define theta 30 //therefore sin(30) = .5, cos(30) = 1/sqrt(2)
```

Edit: also you dont want be be testing floating point values for equlity.

Edit2: here: 
```
double test = x_dim*y_dim*hyp;
```
Accoring to whats in the link you posted dosent test want to be:
```
double test = x_dim+y_dim+hyp;
```

---

### Post by hanniph on 2008-03-01
```
#include <stdio.h>
#include <math.h>
#include <stdbool.h>

#define LIMIT 300
#define PI 3.14
//#define theta = 30 //therefore sin(30) = .5, cos(30) = 1/sqrt(2)

int main(int argc, char * argv[]){
**int const theta = 30; **
	
	int x_dim;
	for (x_dim = 1; x_dim < LIMIT; x_dim++){	
		double y_dim = x_dim*tan(theta*PI/180);
		double hyp = x_dim/cos(theta*PI/180);
		double test = x_dim*y_dim*hyp;
		if (test == 1000){
			printf("answer is %lf\n", test);
			break;
		}
	}
		
	return 0;
	
}
```

Well, it works if you change define statement.

---

### Post by rye_ on 2008-03-01
whoops.  thanks guys.
I think sometimes you get too close to the code and can't see obvious mistakes.

Thanks,

again

---

### Post by DoktorSeven on 2008-03-01
In addition to the above, be sure you compile with **-lm** to specify linking in the math functions.

---

### Post by rye_ on 2008-03-01
```

#include <stdio.h>
#include <math.h>
#include <stdbool.h>

#define LIMIT 400
#define PI 3.14
#define theta 30 //therefore sin(30) = .5, cos(30) = 1/sqrt(2)

int main(int argc, char * argv[]){
	
	int x_dim;
	for (x_dim = 1; x_dim < LIMIT; x_dim++){	
		int y_dim = (int) x_dim*tan(theta*PI/180);
		int hyp = (int) x_dim/cos(theta*PI/180);
		int test = (int) (x_dim+y_dim+hyp);
		//printf("%d\n", test);
		if (test == 1000){
			printf("answer is %lf\n", x_dim*y_dim*hyp);
			break;
		}
	}
		
	return 0;
	
}

```

interesting that it does not locate the answer I'm looking for.
the website doesn't accept the answer 0, for a = 0, b = 500, c = 500
I'll check it symbolically on paper (could be a rounding error I suppose)

---

### Post by mike_g on 2008-03-01
Well I had a poke around with it and got something working.  Its not completely accurate, and quite slow. I commented the changes I made. hope that helps :)
```
#include <stdio.h>
#include <math.h>
#include <stdbool.h>

#define LIMIT 500  [COLOR="DarkRed"]//Limit needed to be higher ( finds at around 366)[/COLOR]
#define PI 3.14159265
#define THETA 30.0 
#define DEG_TO_RAD 0.0174532925 [COLOR="DarkRed"]// saves a little extra calculation[/COLOR]

int main(int argc, char * argv[])
{	
	double x_dim;[COLOR="DarkRed"] // x_dim needs to be double [/COLOR]
	for (x_dim = 1; x_dim < LIMIT; x_dim+=0.0001)[COLOR="DarkRed"] //Increment needs to be very small to produce a result[/COLOR]
        {	
		double y_dim = x_dim*tan(THETA*DEG_TO_RAD);
		double hyp = x_dim/cos(THETA*DEG_TO_RAD);
		double test = x_dim+y_dim+hyp;[COLOR="DarkRed"] // here stuff is added together[/COLOR]
		if(test > 999.9999 && test < 1000.0001)[COLOR="DarkRed"]// Check within range becasue of floating point innacuracy[/COLOR]
                {
			printf("answer has been found\n");
                        printf("X = %lf\n", x_dim);
                        printf("Y = %lf\n", y_dim);
                        printf("H = %lf\n", hyp);
                        printf("Test result = %lf\n", test);
			break;
		}
	}
	getchar();	
	return 0;	
}
```

---

