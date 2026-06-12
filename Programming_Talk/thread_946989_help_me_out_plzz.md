---
title: "help me out plzz"
date: 2008-10-13
forum: Programming Talk
---

### Post by azroule on 2008-10-13
hello there,
im facing a problem rite now.. currently doing my asmen on grading system using c language..
iv done 90 % of it.. but duno how to sort the data in descending order..

here is some quoted c code done by me..any idea to sort the data?
```

////////////////////////////////

#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<ctype.h>


FILE *Records;


#define SIZE 500

void main();
void menu();
void new_record();

void view();

void bye();
char info[SIZE];
char fname[500];
int n = 0;
int m = 0;




struct detail
{
	char name [500][500];
	int mark[500][500];
	char gred[500];


} detail;


//main function
//function is used to create text file with the name of the file specified by the user
//the main function also will call menu function to start the program

void main()
{
	

	  
	 	 
		                      
		printf("\n\n\t Key In Your Prefer Filename (eg: Physic.txt):");
		scanf("%s", &fname);
		printf("\t Your Filename is %s\n\n", fname);
		menu();


}

//menu function is used as a guide for the user to interact with the software
//contain three menus which are "key in student detail", "view student detail", and exit menu


void menu()
{
	int num;
	
		 printf("\n\n\t\t              >>> MAIN MENU <<<\n\n");
		 printf("\t\t      ************************************\n");
		 printf("\t\t      *            SELECT MENU           *\n");
		 printf("\t\t      ************************************\n");
	     printf("\t\t      *    1 .  KEY IN STUDENT DATA      *\n");
	     printf("\t\t      *    2 .  VIEW STUDENT DATA        *\n");
		 printf("\t\t      *    3 .  EXIT                     *\n");
	     printf("\t\t      ************************************\n");
	 	      
		 
         printf("\n\n");		

		
		 num=0;
		
		 printf("\n\t\t* ENTER YOUR CHOICE:");
		 scanf("%d",&num);

	
	//used as a selection menu
		
	switch (num)
	{	
	
			case 1:new_record();break;	//calling new record function to create or key in student detail including mark and name

			case 2:view();break;		//calling view function to view student detail being entered with the grade given
			
	    	case 3:bye();break;			//calling bye function to terminate the program
		    
			default:
				
				printf("\n\n");
				printf("\t   @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@\n");
				printf("\t   *****************************************************\n\n");
				printf("\t\t* Please Only Choose Between number 1-3\n");   
				printf("\n\n");
				system("pause");
				break;
				menu();
	}
}


//new record function is used to enter or stored student data into the system
//user only need to keyin student name an mark, the grade will be given automatically

void new_record()
{
	
		char a;
		char greds;
		char signmin = '-';
		char signplus = '+';
	

			//opening a file to be used as an input/output file
			//name will be specify by the user

			Records = fopen(fname, "a+");

			

			printf("\n\n\n\t\t\t     >>> STUDENT DATA <<<\n\n");
			printf("\t\t  @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@\n");
			printf("\t\t\t PLEASE KEY IN STUDENT DETAIL\n");
			printf("\t\t  *********************************************\n");
		    
			fflush(stdin);

			//entering student name
			printf("\n\t\t* Student Name:");
			scanf("%s",detail.name[n]);
			
		

			
			
			
			fflush(stdin);

			//entering student mark
			printf("\t\t* Student Mark:");
			scanf("%d",detail.mark[n]);
		
			printf("%s\n", detail.name[n]);
			printf("%d", *detail.mark[n]);
		
			
			//to determine grade obtained by the student 
			//based on the mark entered by the user

			if (*detail.mark[n] < 0 )
					printf("\n\t\t>>Please enter mark between 0-100 only\n");

			else if (*detail.mark[n] < 30)
			{
				greds = 'E';
				*detail.gred = greds;
				fprintf(Records,"%s\t\t\t %d\t %s\n",detail.name[n],*detail.mark[n], detail.gred);
				
			}
			else if (*detail.mark[n] <= 35)
			{
				greds = 'D';
				*detail.gred = greds;
				fprintf(Records,"%s\t\t\t %d\t %s\n",detail.name[n],*detail.mark[n], detail.gred);
			}
			else if (*detail.mark[n] <= 40)
			{
				greds = 'D';
				*detail.gred = greds;
				fprintf(Records,"%s\t\t\t %d\t %s%c\n",detail.name[n],*detail.mark[n], detail.gred, signplus);
			}
			else if (*detail.mark[n] <= 45)
			{
				greds = 'C';
				*detail.gred = greds;
				fprintf(Records,"%s\t\t\t %d\t %s%c\n",detail.name[n],*detail.mark[n], detail.gred, signmin);
			}
			else if (*detail.mark[n] <= 50)
			{
				greds = 'C';
				*detail.gred = greds;
				fprintf(Records,"%s\t\t\t %d\t %s\n",detail.name[n],*detail.mark[n], detail.gred);
			}
			else if (*detail.mark[n] <= 55)
			{
				greds = 'C';
				*detail.gred = greds;
				fprintf(Records,"%s\t\t\t %d\t %s%c\n",detail.name[n],*detail.mark[n], detail.gred, signplus);
			}
			else if (*detail.mark[n] <= 60)
			{
				greds = 'B';
				*detail.gred = greds;
				fprintf(Records,"%s\t\t\t %d\t %s%c\n",detail.name[n],*detail.mark[n], detail.gred, signmin);
			}
			else if (*detail.mark[n] <= 65)
			{
				greds = 'B';
				*detail.gred = greds;
				fprintf(Records,"%s\t\t\t %d\t %s\n",detail.name[n],*detail.mark[n], detail.gred);
			}
			else if (*detail.mark[n] <= 70)
			{
				greds = 'B';
				*detail.gred = greds;
				fprintf(Records,"%s\t\t\t %d\t %s%c\n",detail.name[n],*detail.mark[n], detail.gred, signplus);
			}
			else if (*detail.mark[n] <= 75)
			{
				greds = 'A';
				*detail.gred = greds;
				fprintf(Records,"%s\t\t\t %d\t %s%c\n",detail.name[n],*detail.mark[n], detail.gred, signmin);
			}
			else  if (*detail.mark[n] <= 100 )
			{
				greds = 'A';
				*detail.gred = greds;
				fprintf(Records,"%s\t\t\t %d\t %s\n",detail.name[n],*detail.mark[n], detail.gred);
			}
			else 
				printf("\n\t\t>>Please enter mark between 0-100 only\n");
			
				n++;

			//closing the input/output file

			fclose(Records);
			fflush(stdin);
		    printf("\n\n\t* Press Y to continues & N to main_menu:");
			scanf("%c",&a);
			fflush(stdin);
			



		//if user type y or Y then a new record will be entered
		//if user type n or N then the control of this software will be passed back to menu function

		if (a=='y'||a=='Y')
		
			{
				new_record();
			}	
			

	
	
		else if(a=='n'||a=='N')
		
			{
				menu();	
			
			}


			
}




void view()
{
		
		char b;

	


		Records = fopen(fname,"r");
		printf("\n\t\tLIST OF STUDENT'S MARKS WITH GRADE\n\n");
		printf("\t\t**************************************\n\n");
		printf("\t\tNAME\t\t\t MARK\t GRADE\n");
		printf("\t\t**************************************\n\n");
		while(!feof(Records))
		{
		

			fgets(info,SIZE,Records);
			printf("\t\t%s\n",info);
		
		}
		
		
			
			fclose(Records);
			printf("\t\t");
		    
		    printf("\n\n");
			printf("\t   @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@\n");
			printf("\t   *****************************************************\n\n");
			scanf("%c",&b);
      		printf("\n\n\t* Press Y to main menu & N to exit:");
			scanf("%c",&b);
			fflush(stdin);
			
		if (b=='y'||b=='Y')
		
			{
				menu();	
			}	
			

	
	
		else if(b=='n'||b=='N')
		
			{
				bye();
			}

		

		



}








//bye function is used to terminate the software and displaying the program author of this software
//

void bye()
	{
			printf("\n\t\t    THANK YOU FOR USING THIS SOFTWARE \n\n\n");
			printf("\n\t\t* software created by:");
			printf("\n\t\t 1-group member 1");
			printf("\n\t\t 2-group member 2");
			printf("\n\t\t 3-group member 3\n\n\n\n\n");
			

return;
	}
```

---

### Post by overdrank on 2008-10-13
Moved to Programming Talk

---

### Post by slavik on 2008-10-13
first and foremost: you're not using '[code]' tags

next:
5 global variables which don't have to be global
poor code documentation
main returns void?!?!
fflush(stdin) has undefined behavior and is pretty much useless, since there is no real meaning behind flushing an input stream ...
the way you use the switch in main(), it is completely useless.

your program will eventually blow the stack because of the flow after a user makes a selection.

And a question: Is this for an intro C class? or are you learning on your own?

---

### Post by Sinkingships7 on 2008-10-13
I'd love to read it, but I simply refuse to without [code] tags. Please fix.

---

### Post by azroule on 2008-10-14
> **slavik said:**
> first and foremost: you're not using '[code]' tags

next:
5 global variables which don't have to be global
poor code documentation
main returns void?!?!
fflush(stdin) has undefined behavior and is pretty much useless, since there is no real meaning behind flushing an input stream ...
the way you use the switch in main(), it is completely useless.

your program will eventually blow the stack because of the flow after a user makes a selection.

And a question: Is this for an intro C class? or are you learning on your own?

yeah i do learn on my own..
im not from computer field. learning c as a minor subject..
i got this code from other forum which is initially used to stored phone no. so i chnge most of the code to suit mine..

refering to so much text book which are not "talking" or gving response make me much more confuse...
so dat y i ask in this forum..
i spend 50%of my time this few week just to get this code..anyway sorry if this code look "idiot" to an expert like u..

---

### Post by azroule on 2008-10-14
> **Sinkingships7 said:**
> I'd love to read it, but I simply refuse to without [code] tags. Please fix.

i think the admin oredi put it in the[code] tag..
sori for the incovenience..

---

### Post by dwhitney67 on 2008-10-14
I voted "poor" because it is indeed written poorly.

You have unnecessarily declared global variables, you have improperly declared the main() function (when it is not required!), and you have unintentionally employed recursion when based on your skills, tells me that you have no idea what you are doing.

Any erroneous input that does not match the menu choices will terminate the program.  It seems you attempted to call menu() again (btw, this is recursion), however right before it is a break statement; so in effect menu() won't be called.  But you do call menu() at the end of new_record()... this will lead to disaster.

I suggest that if you are indeed interested in C programming, that you procure a book on the subject that will guide you into learning about program structure, for/while loops, and other areas.

P.S.  Never use scanf() to read a string (e.g. a student name).  Use fgets() instead.

P.S.S.  Here's the first tutorial I found after googling for one:  [http://www.iu.hio.no/~mark/CTutorial/CTutorial.html](http://www.iu.hio.no/~mark/CTutorial/CTutorial.html)

---

### Post by nvteighen on 2008-10-14
Oh dear...

Normally, I'd recommend you to go for Python, but as this is for college/school/whatever and you must code in C, please look at the GNU C Programming Tutorial: [http://crasseux.com/books/ctutorial/](http://crasseux.com/books/ctutorial/) (dwhitney67 gave you the link to an older version... I like this newer one better).

---

