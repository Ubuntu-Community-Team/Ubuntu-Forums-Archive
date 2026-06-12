---
title: "Doing something wrong, but what?"
date: 2005-08-17
forum: Programming Talk
---

### Post by Kimm on 2005-08-17
I'm writing a program that is ment to calculate salaries :-P
It loads information about how much money should be payed out during a sertain hour (day/night/weekend) from a file called "settings.pay" or any other file with the same data.

I have a problem with my settings.pay loading function. This is the code for it:

```

void fload() {
	FILE *setting;
	char yes_or_no;
	
	if(file_settings != 0) {
		printf("File allredy specified, use \"%s\" [Y/n]?", file_settings);
		scanf("%s", &yes_or_no);
		
		if(yes_or_no == 'Y' || yes_or_no == 'y') {
			goto load;
		}
	}
	
	printf("\nEnter filename: ");
	scanf("%s", file_settings);
		
	load:
	
	setting = fopen(file_settings, "r");
	
	if(!setting) {
		printf("The file \"%s\", does not exist!\n", file_settings);
		pause();
	}
	else {
		printf("File confirmed!\n");
		printf("Loading data, please wait...\n");
		
		/* fread(mode, 11, 1, setting); */
				
		fclose(setting);
	}
}

```

I'm sorry that it is not commented, I have never been good at that.
Anyway, to the problem. No mather what filename is enterd or given as an argument the program starts spinning complaining that the file "(null)" does not exist. I'm not sure what I am doing wrong. I am used to writing in C++ but I wanted to try C this time, so perhaps that is an issue?

Anyway, this function is not the one spinning. for some reason it spins the entire program, along with the menu's it seems to be inputing data by iselfe somehow  ](*,) 

This is how the menus work:

main():
```

int main(int argc, char *argv[]) {
	int mnu;
	
	if(argc != 1)
		file_settings = argv[1];
	else
		file_settings = 0;
	
	printf("MPSC v1.0\n\n");
	
	while(1) {	
		mnu = menu();
	
		if(mnu == 1)
			fload();
		else if(mnu == 2)
			finput();
		else if(mnu == 3)
			fabout();
		else if(mnu == 4)
			flicense();
		else if(mnu == 5) 
			return 0;
		else
			printf("\n%s: Invalid option!\n", mnu);
		
		mnu = 0;
	}
	
return 0;
}

```

menu():
```

int menu() {
	int t = 0;
	
	printf("---------------------------------------\n");
	
	printf("Menu:\n\n");
	
	printf("[1] Load settings file\n");
	printf("[2] Input work hours\n");
	printf("[3] About\n");
	printf("[4] Read License\n");
	printf("[5] Exit\n\n");
	printf("Please select: ");
	scanf("%i", &t);
	
return t;
}

```

I realy cant explain it, and I have been trying to figure it out for a while. Can anyone point me in the right direction.

And no. This is not homework!

---

### Post by jerome bettis on 2005-08-17
```
void fload() {	  
		if(yes_or_no == 'Y' || yes_or_no == 'y') {
			goto load;
		}
	load:
```

whoa hold on

NEVER type goto ever.   you want to use functions, not just jump around anywhere no matter what is happening.  

post the whole file and i'll take a look at it..  i started to but when i saw goto i had to stop.

---

### Post by Gus-O-Matic on 2005-08-18
Your trying to use the file_settings variable as both an int and a string.  Thus when you perform a scanf you get null.  As the above poster pointed out, this isn't very good C code, don't use goto.  I also suggest that C might not be the best language to  calculate salaries given your unfamiliarity and the ease with which mistakes can be made in C. 

Regards
Gus

---

### Post by Kimm on 2005-08-18
Well... here's the entire program:

```

/*	Copyright (C) 2005 Kim Lindgren

	This program is free software; you can redistribute it and/or
	modify it under the terms of the GNU General Public License
	as published by the Free Software Foundation

	This program is distributed in the hope that it will be useful,
	but WITHOUT ANY WARRANTY; without even the implied warranty of
	MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
	GNU General Public License for more details.

	You should have received a copy of the GNU General Public License
	along with this program; if not, write to the Free Software
	Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA. */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

void pause();
int menu();

int fload();
void rload();
void finput();
void fabout();
void flicense();

char *file_settings;
char *mode;
char *currency;

int main(int argc, char *argv[]) {
	int mnu;
	
	if(argc != 1)
		file_settings = argv[1];
	else
		file_settings = "<null>";
	
	printf("MPSC v1.0\n\n");
	
	while(1) {	
		mnu = menu();
	
		if(mnu == 1)
			fload();
		else if(mnu == 2)
			finput();
		else if(mnu == 3)
			fabout();
		else if(mnu == 4)
			flicense();
		else if(mnu == 5) 
			return 0;
		else
			printf("\n%s: Invalid option!\n", mnu);
		
		mnu = 0;
	}
			
return 0;
}

void pause() {
	getchar();
	while(getchar() == 0);
}

int menu() {
	int t = 0;
	
	printf("---------------------------------------\n");
	
	printf("Menu:\n\n");
	
	printf("[1] Load settings file\n");
	printf("[2] Input work hours\n");
	printf("[3] About\n");
	printf("[4] Read License\n");
	printf("[5] Exit\n\n");
	printf("Please select: ");
	scanf("%i", &t);
	
return t;
}

int fload() {
	char yes_or_no;
	
	if(strcmp(file_settings, "<null>") != 0) {
		printf("File allredy specified, use \"%s\" [Y/n]?", file_settings);
		scanf("%s", &yes_or_no);
		
		if(yes_or_no == 'Y' || yes_or_no == 'y') {
			rload();
			return 0;
		}
	}
	
	printf("\nEnter filename: ");
	scanf("%s", file_settings);
	
	rload();
	
return 0;
}

void rload() {
	FILE *setting;
	
	setting = fopen(file_settings, "r");
	
	if(!setting) {
		printf("The file \"%s\", does not exist!\n", file_settings);
		pause();
	}
	else {
		printf("File confirmed!\n");
		printf("Loading data, please wait...\n");
		
		/* fread(mode, 11, 1, setting); */
				
		fclose(setting);
	}
}

void finput() {
	time_t rawtime;
	struct tm *today;
		
	time(&rawtime);
	today = localtime(&rawtime);
	
	printf("%s", &today);
}

void flicense() {
	FILE *file;
	char *gpl;
	
	file = fopen("GPL.txt", "r");
	
	while(fread(gpl, 1, 4, file)) {
		printf("%s", gpl);
	}
	
	fclose(file);
	
	pause();
}

void fabout() {
	printf("\n");
	printf("\tMPSC version 1.0, Copyright (C) 2005 Kim Lindgren\n");
	printf("\tMPSC comes with ABSOLUTELY NO WARRANTY! without even\n");
	printf("\tthe implied warranty of MERCHANTABILITY or FITNESS FOR A\n");
	printf("\tPARTICULAR PURPOSE! This is free software, and you are welcome \n");
	printf("\tto redistribute it under the conditions of the GPL\n"); 
	printf("\n");
	printf("\tProgrammer:\tKim Lindgren\n");
	printf("\tVersion:\t1.0\n");
	printf("\tLicence:\tGPL\n\n");
	
	pause();
}

```

I made some changes to it, I'm sure you notice them.
Ofcourse it doesnt count anything yet as it cant load the file properly.

---

### Post by Gus-O-Matic on 2005-08-18
Ahhh, thats a lot better -> heres a quick fix for it

```

/*	Copyright (C) 2005 Kim Lindgren

	This program is free software; you can redistribute it and/or
	modify it under the terms of the GNU General Public License
	as published by the Free Software Foundation

	This program is distributed in the hope that it will be useful,
	but WITHOUT ANY WARRANTY; without even the implied warranty of
	MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
	GNU General Public License for more details.

	You should have received a copy of the GNU General Public License
	along with this program; if not, write to the Free Software
	Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA. */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

#define MAXLEN 20

void pause();
int menu();

int fload();
void rload();
void finput();
void fabout();
void flicense();

char file_settings[MAXLEN]; 
char *mode;
char *currency;

int main(int argc, char *argv[]) {
	int mnu;
	
	if(argc != 1)
	/* you can't use '=' to copy strings or '==' to compare them*/
		strcpy(file_settings, argv[1]);
	else
		strcpy(file_settings, "<null>");
	
	printf("MPSC v1.0\n\n");
	
	while(1) {	
		mnu = menu();
	
		if(mnu == 1)
			fload();
		else if(mnu == 2)
			finput();
		else if(mnu == 3)
			fabout();
		else if(mnu == 4)
			flicense();
		else if(mnu == 5) 
			return 0;
		else
		{	printf("\n%s: Invalid option!\n", mnu);
			break; /* don't want any infinite loops */
		}
		mnu = 0;
	}
			
return 0;
}

void pause() {
	getchar();
	while(getchar() == 0);
}

int menu() {
	int t = 0;
	
	printf("---------------------------------------\n");
	
	printf("Menu:\n\n");
	
	printf("[1] Load settings file\n");
	printf("[2] Input work hours\n");
	printf("[3] About\n");
	printf("[4] Read License\n");
	printf("[5] Exit\n\n");
	printf("Please select: ");
	scanf("%i", &t);
	
return t;
}

int fload() {
	char yes_or_no;
	
	
	if(strcmp(file_settings, "<null>") != 0) {
		printf("File allredy specified, use \"%s\" [Y/n]?", file_settings);
		scanf("%s", &yes_or_no);
		
		if(yes_or_no == 'Y' || yes_or_no == 'y') {
			rload();
			return 0;
		}
	}
	
	
	printf("\nEnter filename: ");
	scanf("%s", file_settings);
	
	rload();
	
return 0;
}

void rload() {
	FILE *setting;
	
	setting = fopen(file_settings, "r");
	
	if(!setting) {
		printf("The file \"%s\", does not exist!\n", file_settings);
		pause();
	}
	else {
		printf("File confirmed!\n");
		printf("Loading data, please wait...\n");
		
		/* fread(mode, 11, 1, setting); */
				
		fclose(setting);
	}
}

void finput() {
	time_t rawtime;
	struct tm *today;
		
	time(&rawtime);
	today = localtime(&rawtime);
	
	printf("%s", &today);
}

void flicense() {
	FILE *file;
	char *gpl;
	
	file = fopen("GPL.txt", "r");
	
	while(fread(gpl, 1, 4, file)) {
		printf("%s", gpl);
	}
	
	fclose(file);
	
	pause();
}

void fabout() {
	printf("\n");
	printf("\tMPSC version 1.0, Copyright (C) 2005 Kim Lindgren\n");
	printf("\tMPSC comes with ABSOLUTELY NO WARRANTY! without even\n");
	printf("\tthe implied warranty of MERCHANTABILITY or FITNESS FOR A\n");
	printf("\tPARTICULAR PURPOSE! This is free software, and you are welcome \n");
	printf("\tto redistribute it under the conditions of the GPL\n"); 
	printf("\n");
	printf("\tProgrammer:\tKim Lindgren\n");
	printf("\tVersion:\t1.0\n");
	printf("\tLicence:\tGPL\n\n");
	
	pause();
}

```

---

### Post by Kimm on 2005-08-18
Thank you! that works so much better! ^^

---

### Post by LordHunter317 on 2005-08-18
Tons of issues in that code, but I don't have time to really go over them all, so I'll be brief:[list][*]scanf() is evil, don't use it.[*]A "%s" isn't a char, it's a string (char *).  So don't mix the two.[*]User-input strings of a fixed length are bad, unless you limit the input they can provide.  So don't do that.[/list]You need to go google for and read the C FAQ.

---

