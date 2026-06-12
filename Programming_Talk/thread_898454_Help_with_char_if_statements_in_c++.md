---
title: "Help with char if statements in c++"
date: 2008-08-23
forum: Programming Talk
---

### Post by nerdpride on 2008-08-23
I am tying to write various programs and most of them involve something like what's in this test program
```
#include<iostream>
#include<ctime>
using namespace std;

int main ()
{
	char test;
	cin>>test;
	if (test='y')
	{
		cout<<"test = y\n";
	}
	return 0;
}
``` It seems fine to me, but no matter what character I enter it assumes the if statement is true.
Look at what happens:
```
pete@pete-laptop:~/Programming/test$ g++ testii.cpp -o testii
pete@pete-laptop:~/Programming/test$ ./testii
y
test = y
pete@pete-laptop:~/Programming/test$ ./testii
n
test = y
pete@pete-laptop:~/Programming/test$ 

```

---

### Post by WW on 2008-08-23
Use **==** to test for equality.  The single **=** is an assignment.

E.g.
```

    if (test == 'y')

```

---

### Post by nerdpride on 2008-08-23
Thanks a ton. That worked perfectly.

---

### Post by cmay on 2008-08-23
here is a c version. if you know that the test is always'y' then you can declare this way in c++ too i think. if i renember corretly:)
```
#include <stdio.h>
int main()
{
char test='y';
char c;
printf("enter something \n");
scanf("%c",&c);

if(c!=test){
printf("c is not eq 'y'\n");
printf("c was %c \n",c);
}
else printf("c = test 'y'\n");

return 0;
}

```

---

### Post by nerdpride on 2008-08-23
Here is the Quadratic Formula program i was stuck on.
```
# include<iostream>
# include<cstdio>
# include<cmath>
using namespace std;
//"Quad" by Pete Eigel

int main()
{
    //Declarations
	double a; 		 // input
	double b; 	        // input
	double c; 	       	// input
	double dis;	      	// discirmenant
	double ans1;	     	// answer 1
	double ans2;  	    	// answer 2
	double temp;      	 //temporary varible
	bool i;			// imaginary?
	char opt;     	//option menu
	int prec=3;	// precision
	char cont='y';	//continue?

	cout<<"\n\"Quad\" by Pete Eigel\nQuadratic Formula Calculator\n\n"<<endl;
		while (cont=='y')
		{

			cout<<"Ax^2+Bx+C\n\n";
			cout<<"A= ";
			cin>>a;
			cout<<"B= ";
			cin>>b;
			cout<<"C= ";
			cin>>c;

			temp=(b*b)-(4*a*c);
			if (temp<0)
			{
		               temp=temp*-1;
		               i=true;
		    	}
			dis=sqrt(temp);		//find disreminant
			if(i=true)
			{
				cout.precision(prec);
				cout<<"discriminant = "<<dis<<"i\n";

			}
			else
			{
				cout.precision(prec);
				cout<<"discriminant = "<<dis<<"\n";

			}
		    b=b*-1;
			ans1=(b+dis)/(2*a);
			ans2=(b-dis)/(2*a);
			if (i=true)
			{
		               cout.precision(prec);
		               cout<<ans1<<"i and "<<ans2<<"i"<<"\n"<<endl;
		    }
		    else
		    {
			    cout.precision(prec);
			    cout<<ans1<<" and "<<ans2<<"\n"<<endl;
		    }
    		cout<<"Continue? Y/N";
		cin>>cont;
	}	
	return 0;
}
```

---

### Post by WW on 2008-08-23
I think you have a couple bugs in there.  You don't initialize i to false, and you have some more single ='s in your if statements.

E.g.
```

...snip...

temp=(b*b)-(4*a*c);
i = false;    // <<<---
if (temp<0)
{
    temp=temp*-1;
    i=true;
}
dis=sqrt(temp);
if (i == true)   // <<<---

...snip...

```
and there is another incorrect "if (i=true)" further down in the code.

---

### Post by nerdpride on 2008-08-23
I'm not quite shure what you mean. The program works fine i just put it up for any one who wanted it.

---

### Post by WW on 2008-08-23
> **nerdpride said:**
> I'm not quite shure what you mean. The program works fine i just put it up for any one who wanted it.
Hey, thanks for sharing your code-that's a great idea.  I was just pointing out that, in fact, it doesn't work fine.  Because of the single = in "if (i=true)", it will always think the roots are imaginary.  Try your program with A=1, B=0, and C=-1. The roots should be 1 and -1, but your program prints 1i and -1i.

---

### Post by nvteighen on 2008-08-23
When compiling always use the -Wall flag to catch most of the errors WW is pointing you out.

For example:
```

g++ -o myapp myapp.cpp -Wall

```

---

### Post by DaymItzJack on 2008-08-23
> **nerdpride said:**
> I'm not quite shure what you mean. The program works fine i just put it up for any one who wanted it.

In C++ you can assign variables inside 'if' structures along with others, so when you do 'i=true', it sets i to true and always will return true, what you really want is 'i == true' which will compare i and true and check if it's the same.

---

### Post by NovaAesa on 2008-08-23
> **nvteighen said:**
> When compiling always use the -Wall flag to catch most of the errors WW is pointing you out.

For example:
```

g++ -o myapp myapp.cpp -Wall

```

What does the -Wall flag actually do? I've always used in blindly in my Makefile files because one of my friends said he heard it was a good idea. Just wondering :P

---

### Post by mujambee on 2008-08-23
> **NovaAesa said:**
> What does the -Wall flag actually do? I've always used in blindly in my Makefile files because one of my friends said he heard it was a good idea. Just wondering :P

It activates all compiler warning that are off by default.

---

### Post by cmay on 2008-08-23
@nerdpride
i dont know if this can be of any use to you at all.else just ignore me :)

but you could consider using a function like this that can be used again in other programs if you have a lot of small program similar to this program you posted. just write a function like this in a header file and you can reuse it.that way you dont have to write the same tests over and over again. you include them whit #include "my_header_file"
its just something i wrote for the fun of of it sometime ago.

```

// cmay:2006
#include<iostream>
using namespace std;
int inkey();
void program();

int main(){
do{
cout <<"continue[y][n]"<<endl;
}while(inkey() != 0);
program();
return 0;
}

void program(){
cout<<"hello world"<<endl;
cin.get();
}

int inkey(){
char in=0;
while((in=cin.get()) != 'y'){
if(in=='n'){
abort();
 }
}
return 0;
}
```

---

### Post by dribeas on 2008-08-23
> **mujambee said:**
> It activates all compiler warning that are off by default.

Not really all, but a bigger set of errors. There are more strict options: -pedantic, and then some warnings that must be manually requested -Wreturn-types...

   David

---

### Post by MarkieB on 2008-08-24
no longer participating in ubuntuforums.org

---

