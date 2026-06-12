---
title: "compile is successful with geany,but how to run"
date: 2007-05-07
forum: Programming Talk
---

### Post by LaoLiulaoliu on 2007-05-07
Term.h
#include <iostream>
class Polynominal;
class Term
{
	public:
		Term(int c,int e);
		Term(int c,int e,Term *nxt);
		Term *InsertAfter(int c,int e);
	private:
		int coef;
		int exp;
		Term *link;
		friend std::ostream &  operator <<(std::ostream &, const Term &);
		friend class Polynominal;
};
######################################
Term.cpp
#include "Term.h"
Term::Term(int c,int e):coef(c),exp(e)
{
	link=0;
}
Term::Term(int c,int e,Term *nxt):coef(c),exp(e)
{
	link=nxt;
}
Term *Term::InsertAfter(int c, int e)
{
	link=new Term(c,e,link);
	return link;
}
std::ostream & operator <<(std::ostream &out,const Term & val)
{
	if(val.coef==0) return out;
	out<<val.coef;
	switch(val.exp)
	{
		case 0:break;
        case 1:out<<"X";break;
		default:out<<"X^"<<val.exp;break;
	}
	return out;
}


################################
Polynominal.h
#include "Term.h"

#include <iostream>

class Polynominal

{

	public:

		Polynominal();

		~Polynominal();

		void AddTerms(std::istream & in);

		void Output(std::ostream & out)const;

		void PolyAdd(Polynominal & r);

		void PolyMul(Polynominal & r);

	private:

		Term *theList;

		friend std::ostream & operator <<(std::ostream &,const Polynominal &);

		friend std::istream & operator >>(std::istream &,Polynominal &);

		friend Polynominal & operator +(Polynominal &,Polynominal &);

		friend Polynominal & operator *(Polynominal &,Polynominal &);

};


####################################
polynominal.cpp
#include "Polynominal.h"

Polynominal::Polynominal()

{

				theList=new Term(0,-1);

				theList->link=theList;

}

Polynominal::~Polynominal()

{

	Term *p=theList->link;

	while(p!=theList)

	{

		theList->link=p->link;

		delete p;

		p=theList->link;

	}

	delete theList;  

}



void Polynominal::AddTerms(std::istream & in)

{    Term *q=theList;

      int c,e;

for(;;)

	 { 

	 	std::cout<<"Input a term (coef, exp):\n"<<std::endl;

	 	std::cin>>c>>e;

		if (e<0) break;

		q=q->InsertAfter(c,e);

     }

}



void Polynominal::Output(std::ostream & out)const

{

   int first=1;

   Term *p=theList->link;

   std::cout<<"The polynomial is:\n"<<std::endl;

   for ( ; p!=theList; p=p->link)

   {  

   	if (!first && (p->coef>0)) out<<"+"; 

    first=0;

    out<<*p; 																	

   }

   std::cout<<"\n"<<std::endl;

}



void Polynominal::PolyAdd(Polynominal& r) 

{ 

	Term *q,*q1=theList,*p;  

	p=r.theList->link;           

    q=q1->link;   

    while (p->exp>=0)          

    {

    	while (p->exp<q->exp)        

        {  q1=q;  q=q->link; }

        if  (p->exp==q->exp)             

        {

        	q->coef=q->coef+p->coef;

            if(q->coef==0)

            {

            	q1->link=q->link;

            	delete q;

            	q=q1->link;

            } 

            else

            {

            	q1=q;  q=q->link;

            } 

		}

      else

      {

      	q1=q1->InsertAfter(p->coef,p->exp); 

       }

        p=p->link;

  }

}



void Polynominal::PolyMul(Polynominal& d)

{

	Term *p,*q,*e;

	Polynominal ta,tb;

	e=ta.theList;

	p=d.theList->link;

	q=theList->link;

	while(q->exp>=0)

	{

		for(int j=0;p->exp>=0;j++)

		{

			e=e->InsertAfter(q->coef*p->coef,q->exp+p->exp);

			p=p->link;

		}

		tb=tb+ta;

		e=ta.theList->link;

		while(e!=ta.theList)

		{

			ta.theList->link=e->link;

			delete e;

			e=ta.theList->link;

		}

		q=q->link;

		p=d.theList->link;

	}

	q=theList->link;

	while(q!=theList)

	{

		theList->link=q->link;

		delete q;

		q=theList->link;

	}

	Term *z=tb.theList->link;

	while(z!=theList)

	{

		q=q->InsertAfter(z->coef,z->exp);

		z=z->link;

	}

}



std::ostream & operator <<(std::ostream & out, const Polynominal &x) 

{ 

	 x.Output(out);

   return out;

}



std::istream & operator >>(std::istream & in, Polynominal &x)

{ 

	x.AddTerms(in);

   return in;

}



Polynominal & operator +(Polynominal &a, Polynominal &b) 

{  

	a.PolyAdd(b);

   return a;

}



Polynominal & operator *(Polynominal &a,Polynominal &b)

{

	a.PolyMul(b);

	return a;

}


##################################
main.cpp
#include "Polynominal.h"
int main()
{
	Polynominal p,q,t;
	std::cin>>p;	std::cout<<p;
	std::cin>>q;	std::cout<<q;
	q=q+p;	std::cout<<q;
	q=q*p;		std::cout<<q;
	return 0;
}


@@@@@@@@@@@@@@@
This is a program for polynominal addition.Sorry for so long.I just want to know why the multiply of polynominal can not run.Thanks very much.

---

### Post by rapolas on 2007-05-07
Press F5

---

### Post by LaoLiulaoliu on 2007-05-07
I press F8,then
Compilation finished successfully.
I press F5,nothing happened.
I use command line:
g++ Term.cpp Polynominal.cpp main.cpp -o main
Then ./main
Only the multiply of polynominal run a lot of time,then killed.That is to say,the last step of this program--multiply have some problem.

---

### Post by rapolas on 2007-05-07
It means that you have some errors in your program. Try to make, compile and run simple Hello World program at first:)

---

### Post by LaoLiulaoliu on 2007-05-07
Please help me.Thank you very much!!

---

### Post by Carlos Santiago on 2007-05-07
Write a text file with:
```

All:
    g++ Term.cpp Polynominal.cpp main.cpp -o main

```
And save it with the name Makefile

Then build all.

---

