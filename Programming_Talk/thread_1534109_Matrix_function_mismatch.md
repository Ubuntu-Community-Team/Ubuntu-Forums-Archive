---
title: "Matrix function mismatch"
date: 2010-07-19
forum: Programming Talk
---

### Post by navaneethan on 2010-07-19
> #include<stdio.h>
#include<conio.h>
//void MatrixAdd(const Matrix *a, const Matrix *b, Matrix *c);
struct Matrix {
int Element[100][100];
int No_of_Rows;
int No_of_Cols;
};
typedef struct Matrix Matrix;
void main()
{
	int i,j;
	Matrix a,b,c;

	a.No_of_Rows=2;
	a.No_of_Cols=2;
	b.No_of_Rows=2;
	b.No_of_Cols=2;
	clrscr();

	printf("Enter the Matrix A:");
	for(i=0;i<=a.No_of_Rows;i++)
	{
		for(j=0;j<=a.No_of_Cols;j++)
		{
			scanf("%d",&a.Element[i][j]);
		}
	}
	printf("Enter the MAtrix B:");
	for(i=0;i<=b.No_of_Rows;i++)
	{
		for(j=0;j<=b.No_of_Cols;j++)
		{
			scanf("%d",&b.Element[i][j]);
		}
	}
	
	MatrixAdd(&a,&b,&c);
	getch();
}
void MatrixAdd(const Matrix *a, const Matrix *b, Matrix *c)
{
	int i,j;
	for(i=0;i<=a->No_of_Rows;i++)
	{
		for(j=0;j<=a->No_of_Cols;j++)
		{
			c->Element[i][j]=a->Element[i][j]+b->Element[i][j];
			printf("ANS IS\t%d\t",c->Element[i][j]);
		}
		printf("\n");
	}

}

Hi friends,Just in this program i have got input of two matrices a ,b using stricture,and i passed this to a function,i have done conceptually right but still it gets mess to execute May i know the reason behind this? Actually what is the problem?How to resolve?plz explain friends

---

### Post by Bachstelze on 2010-07-19
Rememver that if you do:

```
for(i=0; i <= n; i++)
```

You do n+1 iterations in the loop. What you want is

```
for(i=0; i < n; i++)
```

---

### Post by trent.josephsen on 2010-07-19
It's int main(void); conio.h has been deprecated for ages and is not available on Linux; and put code in [code] tags.

I'm beginning to wonder if you're trolling, if for no other reason than your stubborn insistence on using [quote] tags for code.

---

### Post by navaneethan on 2010-07-20
Here It is not that an issue to be resolved actually dude ;-)

---

### Post by navaneethan on 2010-07-20
ya fine ;-) I know do in linux machine friends but unfortunately i pulled to do in Borland one :-(

---

### Post by trent.josephsen on 2010-07-20
It's not a question of what platform you're on.  It's the fact that you're obviously using a book that describes an ancient and non-standard dialect of C.  Borland hasn't maintained a C compiler since 1990.  Their Turbo C++ line has had its ups and downs and now is defunct as well (despite still being available for download).  conio.h has been deprecated since before I could read and write -- no exaggeration.  void main() was made non-standard in 1989.  You're not doing yourself any favors by learning this archaic crap.

If you insist on pursuing the language you want to learn, despite the numerous excellent reasons to update your skills to something less than 20 years old, **AT LEAST use [code] tags when you post code.**

---

