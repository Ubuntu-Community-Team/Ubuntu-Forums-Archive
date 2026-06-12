---
title: "An issue with deleting function"
date: 2015-07-23
forum: Programming Talk
---

### Post by NoWeDoR on 2015-07-23
I have written a phone book program. However, I'm encountering an issue with deleting function. For instance, when I compile the codes which are below and follow the way like this;

I open a file and add someone to list by entering 1 using first function and after that I enter 5 to delete this person from list. As it was expected it's deleting first record correctly.

From now on, I add another person to list by entering 4 and again to delete this last person I enter 5 and notify to delete "1". It shows me a warning on the screen like "The record has been cleared". However, when I look location which is file's recorded place and by using second function I see the last record is still staying.

Why while at the first time it's deleting, at second not?


```
#include <stdlib.h>      // "stdlib" library contains of exit() function
#include <malloc.h>     // "malloc" library contains of malloc() function
#include <Windows.h>   // "Windows" library contains of Sleep() function which waits the system as you want
#include <io.h>       // "io" library contains of filelength() function
#include <string.h>  // "string" library contains of strlen() function
#include <stdio.h>  // "stdio" library contains of other functions which hasn't been mentioned


struct personKnowledge   // Structe and it's elements are being defined
{
	char name[32];
	char surname[32];
	char number[32];
};


FILE *ptrFILE, *ptrFILE1;   // Variables are being defined
long int recordLength, totalRecordLength, location;
int choice, number, totalRecordNumber, i;
static int counter = 0;


int menu();   // Functions are being defined
void newRecord();
void display();
void update();
void add();
void deletE();


int main()   // Program is being initialiezed 
{
	menu();
	return 0;
}


int menu()   // Options are being presented to user 
{
	do
	{
		printf("\n\t\t --- Phone Book Program ---");
		printf("\n\n\t\t 1) Open file and record someone");
		printf("\n\n\t\t 2) Display person knowledge");
		printf("\n\n\t\t 3) Update person knowledge");
		printf("\n\n\t\t 4) Add person to list");
		printf("\n\n\t\t 5) Delete someone");
		printf("\n\n\t\t 6) Exit");
		printf("\n\n\nEnter your choice: ");
		choice = 0;
		scanf("%d", &choice);
		fflush(stdin);
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
			update();
			break;
		}
		case 4:
		{
			add();
			break;
		}
		case 5:
		{
			deletE();
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
}


void newRecord()   // This function opens a file and records one person in file
{
	if (counter > 0)
	{
		system("cls");   // Screen is being cleaned
		Sleep(350);     // Sleep functions waits user for a while
		printf("\nYou have already entered '1' and opened a file. To add a person please enter '4'\n");
		return;
	}
	else
	{
		if ((ptrFILE = fopen("Phone Book.dat", "wb")) == NULL)   // wb is binary writing mode
		{
			printf("The file couldn't open\n");
			exit(EXIT_SUCCESS);
		}
		system("cls");
		Sleep(350);
		struct personKnowledge *p;   // p = (Person)
		p = (struct personKnowledge *)malloc(sizeof(struct personKnowledge));   // Memory is being allocated
		fflush(stdin);   // Cache memory is being cleaned
		recordLength = sizeof(*p);
		printf("\n\Express person name: ");   // User is entering the person's knowledge and they are being saved in file
		fgets(p->name, sizeof(p->name), stdin);
		size_t wordLength = strlen(p->name);  // "size_t is unsigned integer type"
		if (wordLength > 0 && p->name[wordLength - 1] == '\n')   // This if idiom has been used for sentence seperation
		{
			p->name[--wordLength] = '\0';
		}
		printf("Express %s's surname: ", p->name);
		fgets(p->surname, sizeof(p->surname), stdin);
		printf("Express %s's number: ", p->name);
		fgets(p->number, sizeof(p->number), stdin);
		fwrite(&(*p), recordLength, 1, ptrFILE);   // Knowledge which has been got from user is being saved in file processionally
		printf("\nPlease wait, information is saving to file..\n");
		Sleep(750);
		printf("*-* Saving operation has been completed succesfully. *-*\n");
		free(p);   // Allocated part of memory is being released
	}
	fclose(ptrFILE);   // File is being closed
	counter++;
}


void display()   // If there is person knowledge which is searched in file, this function reads it and prints on the screen
{
	if ((ptrFILE = fopen("Phone Book.dat", "rb")) == NULL)   // rb is binary reading mode
	{
		printf("The file couldn't open\n");
		exit(EXIT_SUCCESS);
	}
	system("cls");
	Sleep(350);
	struct personKnowledge *s;   // s = (Searching)
	s = (struct personKnowledge *)malloc(sizeof(struct personKnowledge));
	recordLength = sizeof(*s);   // Necessary location calculations are being done and person's knowledge is being displayed
	totalRecordLength = filelength(fileno(ptrFILE));   // The equalities explains what the purpose is from 137th line to 145th line 
	totalRecordNumber = totalRecordLength / recordLength;
	printf("\n\nExpress person record number which you search: ");
	number = -791673918435;
	scanf("%d", &number);
	fflush(stdin);
	printf("\n*-* Person knowledge which you search *-*\n");
	Sleep(750);
	location = (number - 1)*(recordLength);
	fseek(ptrFILE, location, SEEK_SET);   // The cursor locates place which is searched with fseek() function
	if (fread(&(*s), recordLength, 1, ptrFILE) != 0 && number > 0)  // If there is knowledge in that location and numbeer is greater than 0
	{
		printf("Name: %s\n", s->name);
		printf("Surname: %s", s->surname);
		printf("Number: %s\n", s->number);
	}
	else
	{
		printf("There is no record like this.\n");
		return;
	}
	free(s);
	fclose(ptrFILE);
}


// In this function, the code line explanations are same as previous ones
void update()   // This function updates only one person knowledge from his/her name to phone number that gets from user again
{
	if ((ptrFILE = fopen("Phone Book.dat", "rb+")) == NULL)   // rb+ is both reading and writing mode
	{
		printf("The file couldn't open\n");
		exit(EXIT_SUCCESS);
	}
	system("cls");
	Sleep(350);
	struct personKnowledge *d;   // d = (Deleting)
	d = (struct personKnowledge *)malloc(sizeof(struct personKnowledge));
	recordLength = sizeof(*d);
	totalRecordLength = filelength(fileno(ptrFILE));
	totalRecordNumber = totalRecordLength / recordLength;
	if (totalRecordNumber == 0)
	{
		printf("\nThere is no any record to update.\n");
		return;
	}
	printf("\nEnter the person record number which you update: ");
	scanf("%d", &number);
	fflush(stdin);
	location = (number - 1)*(recordLength);
	fseek(ptrFILE, location, SEEK_SET);
	if (fread(&(*d), recordLength, 1, ptrFILE) == 0 || number <= 0)
	{
		Sleep(350);
		printf("There is no record like this.\n");
		return;
	}
	else
	{
		fseek(ptrFILE, location, SEEK_SET);
		printf("\n\Express new person name: ");
		fgets(d->name, sizeof(d->name), stdin);
		size_t wordLength = strlen(d->name);
		if (wordLength > 0 && d->name[wordLength - 1] == '\n')
		{
			d->name[--wordLength] = '\0';
		}
		printf("Express %s's surname: ", d->name);
		fgets(d->surname, sizeof(d->surname), stdin);
		printf("Express %s's number: ", d->name);
		fgets(d->number, sizeof(d->number), stdin);
		fwrite(&(*d), recordLength, 1, ptrFILE);
		printf("\nPlease wait, information is saving to file..\n");
		Sleep(750);
		printf("*-* Updating operation has been completed succesfully. *-*\n");
	}
	free(d);
	fclose(ptrFILE);
}


// In this function, the code line explanations are same as previous ones
void add()   // This functions records person in file as much as user wants
{
	if ((ptrFILE = fopen("Phone Book.dat", "ab")) == NULL)
	{
		printf("The file couldn't open\n");
		exit(EXIT_SUCCESS);
	}
	system("cls");
	Sleep(350);
	struct personKnowledge *a;   // a = (Adding)
	a = (struct personKnowledge *)malloc(sizeof(struct personKnowledge));
	fflush(stdin);
	recordLength = sizeof(*a);
	printf("\n\Express person name: ");
	fgets(a->name, sizeof(a->name), stdin);
	size_t wordLength = strlen(a->name);
	if (wordLength > 0 && a->name[wordLength - 1] == '\n')
	{
		a->name[--wordLength] = '\0';
	}
	printf("Express %s's surname: ", a->name);
	fgets(a->surname, sizeof(a->surname), stdin);
	printf("Express %s's number: ", a->name);
	fgets(a->number, sizeof(a->number), stdin);
	fwrite(&(*a), recordLength, 1, ptrFILE);
	printf("\nPlease wait, information is adding to file..\n");
	Sleep(750);
	printf("*-* Adding operation has been completed succesfully. *-*\n");
	free(a);
	fclose(ptrFILE);
}


void deletE()   // ??
{
	if ((ptrFILE = fopen("Phone Book.dat", "rb")) == NULL)
	{
		printf("The file couldn't open\n");
		exit(EXIT_SUCCESS);
	}
	if ((ptrFILE1 = fopen("Phone Book1.dat", "wb")) == NULL)
	{
		printf("The file couldn't open\n");
		exit(EXIT_SUCCESS);
	}
	system("cls");
	Sleep(350);
	struct personKnowledge *del;   // del = (Deleting)
	del = (struct personKnowledge *)malloc(sizeof(struct personKnowledge));
	fflush(stdin);
	recordLength = sizeof(*del);
	totalRecordLength = filelength(fileno(ptrFILE));
	totalRecordNumber = totalRecordLength / recordLength;
	printf("\nExpress person number which you want to delete: ");
	scanf("%d", &number);
	fflush(stdin);
	if (fread(&(*del), recordLength, 1, ptrFILE) == 0 || number <= 0)
	{
		Sleep(350);
		printf("There is no record like this.\n");
		return;
	}
	for (i = 1; i <= totalRecordNumber; i++)
	{
		if (i == number)
		{
			Sleep(350);
			printf("The record has been cleared.\n");
			continue;
		}
		else
		{
			fwrite(&(*del), recordLength, 1, ptrFILE1);
		}
	}
	fclose(ptrFILE);
	fclose(ptrFILE1);
	remove("Phone Book.dat");
	rename("Phone Book1.dat", "Phone Book.dat");
	free(del);
}

```

---

### Post by spjackson on 2015-07-23
In your deletE function, you have a single fread before the start of your for loop. Hence, every fwrite within the loop will be writing repeats of the first record. Perhaps that is why you are getting the behaviour your are seeing.

---

