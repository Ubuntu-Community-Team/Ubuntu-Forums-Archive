---
title: "multiple calls to the same method (java)"
date: 2009-01-08
forum: Programming Talk
---

### Post by apartmentDweller on 2009-01-08
I am completely new to java, and can't for the life of me figure out what's going on. Here's my code:

```

public static void main (String [] args){
		System.out.println("This class evalutes functions of n variables");
		double [] tuple= {.3,3};
		double [] tuple2= {.5,3};
		Func f=new Func("x.2*x.1*(1-x.1)",2);
		if (f.isFormatCorrect()==1){
			System.out.println("the first answer is " + f.eval(tuple));
			System.out.println("the sencond answer is: "+ f.eval(tuple2));
		}
	}
```	

so I declare an Func (the class to which the main method belongs) object and call the method eval. The first time every works great. But on the second call the program seems to evaluate the method with the parameters of the first call (.3,30 instead of (.5,3), and then freezes shortly thereafter, part way through the method. The  only class variables pertain the to the string,"x.2*x.1*(1-x.1), yet it would seem that somehow the variables in the method eval are still left over from the first call. Here's the output from running the program.

```
This class evalutes functions of n variables
the method eval has been called
1-0.3  XXXXX
1-0.3   adsfasd   numBegin : 0  numEnd: 0   substring   1
-0.3   adsfasd   numBegin : 1  numEnd: 3   substring   0.3
0.7 x
0.3 x
0.0 x
0.0 x
0.0 x
0.0 x
0.0 x
0.0 x
0.0 x
0.0 x
3.0*0.3*;0>  XXXXX
3.0*0.3*;0>   adsfasd   numBegin : 0  numEnd: 2   substring   3.0
*0.3*;0>   adsfasd   numBegin : 1  numEnd: 3   substring   0.3
*0.7   adsfasd   numBegin : 1  numEnd: 3   substring   0.7
0.6299999999999999 x
0.7 x
0.7 x
0.0 x
0.0 x
0.0 x
0.0 x
0.0 x
0.0 x
0.0 x
the first answer is 0.6299999999999999
the method eval has been called
3.0*0.3*;0>  XXXXX
3.0*0.3*;0>   adsfasd   numBegin : 0  numEnd: 2   substring   3.0
*0.3*;0>   adsfasd   numBegin : 1  numEnd: 3   substring   0.3
```

freezes after this point

WTF is going on?

---

### Post by luca.cappelletta on 2009-01-08
I don't see what is the problem, but I suggest to totally re-build your project because it is NOT a Java project, but a C one written in Java syntax.

---

### Post by apartmentDweller on 2009-01-08
You're right I want to write this in C, but this class will eventually need to be used in another program involving graphics, which to me Java seems like the easiest to start with. (Although at the moment I am download OpenGl so I dont have to mess with java)


As for the problem, why is it that when the method eval is called for the  second time i get:

```
the method eval has been called
3.0*0.3*;0>  XXXXX
3.0*0.3*;0>   adsfasd   numBegin : 0  numEnd: 2   substring   3.0
*0.3*;0>   adsfasd   numBegin : 1  numEnd: 3   substring   0.3
```

and then it freezes.

it should begin something like: 
```
the method eval has been called
3.0*0.5*;0>  XXXXX
3.0*0.5*;0>   adsfasd   numBegin : 0  numEnd: 2   substring   3.0
*0.5;0>   adsfasd   numBegin : 1  numEnd: 3   substring   0.5
```

and keep going, but it doesn't....

---

### Post by SupaSonic on 2009-01-09
There's a bug in your code somewhere, I'd think in the eval() method, but there's no code here to look at really. I'd suggest commenting out the whole content of the eval() method, and then adding something like 

```
public String eval(double[] param) {

System.out.println(param[0]);
System.out.println(param[1]);

//commented out code
//...
//...
//...

}
```

of course replace param with whatever your argument name is. Then you'll see what values are being passed to the methods. 

Or you could just use debug in eclipse and see exactly where (and, most probably, why) your application fails.

---

