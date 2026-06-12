---
title: "Urgent!!!!"
date: 2012-12-17
forum: Programming Talk
---

### Post by Divakar on 2012-12-17
please help me with this program.. we are trying to create a program to generate timetable..
the following segment of the program is showing me an error:
General Protection Exception Processor Fault

here is the code segment...

```
#include<iostream.h>
#include<fstream.h>
#include<stdlib.h>
#include<stdio.h>
#include<string.h>
#include<math.h>
#include<ctype.h>
#include<iomanip.h>
#include<process.h>
#include<time.h>

    class linkobj
		 {	public:
		char name[25];
		int cls,sec;
	 };
class Subject
	{public:
	char sname[10];
	void stores()
		{cout<<"Enter name of subject : ";
			gets(sname);
		}
	  class teacher
	  {public:
	  int nocls;
		char tname[25];

		class pref
			{public:
				int cls;
				int sec;
			}preff[5];
		class day
			{public:
			char dname[10];

			class period
				{public:
				int clssoft;
				int section;
				}p[8];
			}d[6];
		}t[7];
		void write();
		void show();
  }*s=new Subject[3];


class Class
{public:
	int cname;

		class section

	  { public:
		char secname[10];



		class day
			{public:
			char dname[10];


			class period
				{public:
				char nameoftheteachertakingclass[25];
				///when outputting setw

				}p[8];
			}d[6];
		}sec[4];
		void write1();
		void storedataofstudent();

	} cls[5];    int i,j,k;
/*void Class:: storedataofstudent()
	  { for(i=0;i<5;++i)
			{cls[i].cname=(i+1);
			  {for(j=0;j<4;++j)
				 { if(j==0)
					strcpy(cls[i].sec[j].secname,"a");
					else if(j==1)
					strcpy(cls[i].sec[j].secname,"b");
					else if(j==2)
					strcpy(cls[i].sec[j].secname,"c");
					else if(j==3)
					strcpy(cls[i].sec[j].secname,"d");
					for(k=0;k<6;++k)
						{
						if(k==0)
						strcpy(cls[i].sec[j].d[k].dname,"MONDAY");
						else if(k==1)
						strcpy(cls[i].sec[j].d[k].dname,"TUEDAY");
						else if(k==2)
						strcpy(cls[i].sec[j].d[k].dname,"WEDNESDAY");
						else if(k==3)
						strcpy(cls[i].sec[j].d[k].dname,"THURSDAY");
						else if(k==4)
						strcpy(cls[i].sec[j].d[k].dname,"FRIDAY");
						else if(k==5)
						strcpy(cls[i].sec[j].d[k].dname,"SATURDAY");
						}
					 }
			  }
			}
	  } */
	  struct teacher
	  {int randnum,ab;
	  int seedval,clss,secc,k,l,sub,tecr,f;
	  }s1;
		struct k
		{

			  struct l{


				 char c[5][25];
		  }b[4];
		}a[5];


void selectteacher()
{
	//time_t t;
	//s1.seedval=time(&t);
 srand(time(NULL));

	//char x[5][4][5][25];
	 //
	for(s1.clss=0;s1.clss<5;s1.clss++)
	{
	  for(s1.secc=0;s1.secc<4;s1.secc++)
	  {
		int f=0;											//this name and select one from this using random and assign the values to the major classes of teacher and student.
		while(f!=5)//////////////////// exit from the loop
		{
		for(s1.sub=0;s1.sub<3;++s1.sub)
		  {  for(s1.tecr=0;s1.tecr<1;s1.tecr++)///to search the whole teacher's class and select the teachers who have selected this class and this section.
				{for(s1.k=0;s1.k<5;s1.k++)//the preferred class she needs there are 5 of them
					if((s[s1.sub].t[s1.tecr].preff[s1.k].cls==s1.clss)&&(s[s1.sub].t[s1.tecr].preff[s1.k].sec==s1.secc))

						{ //this teacher will have only once select this class if she actually wants it
							{
							 strcpy(a[s1.clss].b[s1.secc].c[f],s[s1.sub].t[s1.tecr].tname); /////////////////////////////			TERROR!

								f++;
								if(f==5)
								break;
							}
						}

				}
		  }
		}
	 }
  }
for(s1.clss=0;s1.clss<5;s1.clss++)
	{
	  for(s1.secc=0;s1.secc<4;s1.secc++)
		 {
			for(s1.k=0;s1.k<6;s1.k++)//day
				  {for(s1.l=0;s1.l<8;s1.l++)  //period
					  {
					  s1.ab=(rand()%5)+0;// The random is generated between 0 to 5 and is used to dereference into the pointer's index
											// and five such teachers' names are stored into the teacher's name of the class teacher.
						///condition so that not more than 2 continuous random nos are the same.


					 strcpy( cls[s1.clss].sec[s1.secc].d[s1.k].p[s1.l].nameoftheteachertakingclass,a[s1.clss].b[s1.secc].c[s1.ab]);////////////////////////////
					  //s[clss].t[secc].d[k].p[l].cls=clss;
					  //s[clss].t[secc].d[k].p[l].sec=secc;
					  }
				  }
		 }

}  }
void main()
{ selectteacher();

}
```

---

### Post by Cheesemill on 2012-12-17
Sounds like homework to me :)

---

### Post by oldos2er on 2012-12-17
Moved to Programming Talk.

---

### Post by trent.josephsen on 2012-12-17
Let's see, obvious homework problem posted in the wrong forum, under an appeal to urgency, exhibiting a vague error message most likely from an archaic IDE, terrible formatting, mixed C with C++, <iostream.h>, gets(), and voided main... yeah, not going to get any good answers. At least not until OP fixes the code to something marginally readable.

---

### Post by QIII on 2012-12-17
I think I remember that assignment...

---

### Post by zombifier25 on 2012-12-18
> **trent.josephsen said:**
> Let's see, obvious homework problem posted in the wrong forum, under an appeal to urgency, exhibiting a vague error message most likely from an archaic IDE, terrible formatting, mixed C with C++, <iostream.h>, gets(), and voided main... yeah, not going to get any good answers. At least not until OP fixes the code to something marginally readable.

Agreed. Who is your programming teacher?

---

