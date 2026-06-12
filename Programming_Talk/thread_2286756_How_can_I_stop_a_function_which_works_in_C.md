---
title: "How can I stop a function which works in C?"
date: 2015-07-14
forum: Programming Talk
---

### Post by NoWeDoR on 2015-07-14
I'm writing a simply phone book program. I have completed two function but I have a small problem. 
In second function as you see there is if-else idiom at the end of the lines.
If anyone from s->name, s->surname or s->number is empty, I want to warn user like "[COLOR=#333333]"There is no record like this" and exit from it. 
However for this, return; command doesn't work and program continues jumping in else structure and show me unmeaning things on the screen. How can I solve this?


[/COLOR]```
#include <stdio.h>
#include <stdlib.h>      // "stdlib" library contains of exit() function
#include <malloc.h>     // "malloc" library contains of malloc() function
#include <Windows.h>   // "Windows" library contains of Sleep() function which waits the system as you want
#include <io.h>       // "io" library contains of filelength() function


struct personKnowledge
{
	char name[32];
	char surname[32];
	char number[32];
};


FILE *ptrFILE, *ptrFILE1;
long int recordLength, totalRecordLength, location;
int number, totalRecordNumber;
static int counter = 0;


void newRecord();
void display();
void deletE();
void add();
void update();


int main()
{
	int choice;
	do
	{
		printf("\n\t\t --- Phone Book ProgRam ---");
		printf("\n\n\t\t 1) New record");   // The options are being presented to user
		printf("\n\n\t\t 2) Display person knowledge");
		printf("\n\n\t\t 3) Delete someone");
		printf("\n\n\t\t 4) Add person to list");
		printf("\n\n\t\t 5) Update person knowledge");
		printf("\n\n\t\t 6) Exit");
		printf("\n\n\nEnter your choice: ");
		scanf("%d", &choice);
		switch (choice)
		{
		case 1:
		{
			newRecord();
			break;
		}
		case 2:
		{
			display();
			break;
		}
		case 3:
		{
			break;
		}
		case 4:
		{
			break;
		}
		case 5:
		{
			break;
		}
		case 6:
		{
			printf("\nWorking has been completed.\n");
			return 0;
		}
		default:
		{
			printf("\nWrong entry! The program has been terminated.\n");
			break;
		}
		}
	} while (choice >= 1 && choice <= 6);
	return 0;
}


void newRecord()
{
	if (counter > 0)
	{
		printf("You have already entered '1' and opened a file. To add a person please enter '4'\n");
		return;
	}
	else
	{
		if ((ptrFILE = fopen("Phone Book.dat", "wb")) == NULL)
		{
			printf("The file couldn't open\n");
			exit(0);
		}
		system("cls");   // Screen is being cleaned
		struct personKnowledge *p;   // p means person
		p = (struct personKnowledge *)malloc(sizeof(struct personKnowledge));   // Memory is being allocated
		fflush(stdin);
		recordLength = sizeof(*p);   // size of p
		printf("\n\Express person name: ");   // User is entering the person's knowledge and they are being saved in file
		gets(p->name);
		printf("Express %s's surname: ", p->name);
		gets(p->surname);
		printf("Express %s's number: ", p->name);
		gets(p->number);
		fwrite(&(*p), recordLength, 1, ptrFILE);
		printf("\nPlease wait, information is saving to file..\n");
		Sleep(750);
		printf("*-* Saving operation has been completed succesfully. *-*\n");
		free(p);
	}
	fclose(ptrFILE);
	counter++;
}


void display()
{
	if ((ptrFILE = fopen("Phone Book.dat", "rb")) == NULL)
	{
		printf("The file couldn't open\n");
		exit(0);
	}
	system("cls");   // Screen is being cleaned
	struct personKnowledge *s;   // s means searching
	s = (struct personKnowledge *)malloc(sizeof(struct personKnowledge));
	fflush(stdin);
	recordLength = sizeof(*s);
	totalRecordLength = filelength(fileno(ptrFILE));
	totalRecordNumber = totalRecordLength / recordLength;
	printf("\n\nExpress person record number which you search: ");
	scanf("%d", &number);
	location = (number - 1)*(recordLength);
	fseek(ptrFILE, location, SEEK_SET);
	fread(&(*s), recordLength, 1, ptrFILE);
	printf("\n*-* Person knowledge which you search *-*\n");
	Sleep(750);
	if (s->name == NULL || s->surname == NULL || s->number == NULL)
	{
		printf("There is no record like this.\n");
		return;
	}
	else
	{
		printf("Name: %s\n", s->name);
		printf("Surname: %s\n", s->surname);
		printf("Number: %s\n", s->number);
	}
	free(s);
	fclose(ptrFILE);
}

```


And except this

if (s->name == NULL || s->surname == NULL || s->number == NULL)
	{
		printf("There is no record like this.\n");
		return;
	}

I have tried to write 

[COLOR=#000000][FONT=Verdana]if (strcmp(s->name,NULL)==0) [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]{ [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]printf("There is no record like this.\n"); [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]return; [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]} 

[/FONT][/COLOR]But again there is no result.

---

### Post by ofnuts on 2015-07-17
The attributes name, surname, and number of your struct aren't pointers since the arrays are allocated in the struct.  Your test isn't valid to indicate that the user doesn't exist. 

Plenty of strange things in your code: fread([SIZE=5]***&(*s)***[/SIZE], recordLength, 1, ptrFILE); really?

---

