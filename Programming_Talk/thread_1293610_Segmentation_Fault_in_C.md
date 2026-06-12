---
title: "Segmentation Fault in C"
date: 2009-10-17
forum: Programming Talk
---

### Post by ajmburgos09 on 2009-10-17
This C program is supposed to be a perpetual calendar. But whenever I enter this input:
1
1
12

The program gives a seg fault. I checked for errors, but I didn't see any double-free errors or freeing a null pointer errors.

Can somebody help me?

Thanks!

```


#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
/*Subprogram name: useagain
  Description: Gets the user input to determine if the user wants to use the subprogram again. The subprogram will return 1 if the user wants to 
  use the subprogram again. Otherwise, the subprogram would return 0.*/
char* namemonth [12]= {"January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"};
char useagain()
{
    char input[100], yorn;
    while (1)
    {
        printf("Do you want to use this subprogram again (y/n)?\n");
        do
        {
            fgets(input, 100, stdin);
        }while (input[0] == '\n');
        sscanf(input, "%c", &yorn);
        if (strlen(input) != 2) printf("Warning: Wrong Input.\n");
        else if (yorn == 'y' || yorn == 'Y') return 1;
        else if (yorn == 'n' || yorn == 'N') return 0;
        else printf("Warning: Wrong Input.\n");
    }
}
/*Subprogram name: isleapyear
  Description: Returns 1 if the year is a leap year. Returns 1 otherwise.*/
char isleapyear(int year)
{
    if (year > 1582)
    {
        if (year % 400 == 0) return 1;
        else if (year % 100 == 0) return 0;
        else if (year % 4 == 0) return 1;
        else return 0;
    }
    else
    {
        if (year % 4 == 0) return 1;
        else return 0;
    }
}

/*Subprogram name: convToFile
  Description: Returns a string that contains the filename of the note for the particular date. Returns a null pointer otherwise.*/
char* convToFile(int month, int day, int year)
{
    char monthdays [12] = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
    char* fname = (char*) malloc(40*sizeof(char));
    if (day < 1) return 0;
    else if ((month != 10 || year != 1582) && ((month != 2 && day <= monthdays[month-1]) || (month == 2 && ((day <= 29 && isleapyear(year)) || (day <= 28 && !isleapyear(year))))))
    {
        sprintf(fname, "%c%d%d%d.calendar", 'C', month, day, year);
        return fname;
    }
    else if (month == 10 && year == 1582)
    {
        if (day > 4 && day < 15)
        {
            return 0;
        }
        else
        {
            sprintf(fname, "%c%d%d%d.calendar", 'C', month, day, year);
            return fname;
        }
    }
    else
    {
        return 0;
    }
}
/*Subprogram name: readfile
  Description: Handles the case when the user wants to read a note for a particular date.*/
void readfile(char* filename, int month, int day, int year)
{
    FILE* note;
    char input [1000];
    note = fopen(filename, "r");
    if (note == NULL) printf("Note for %s %d, %d does not exist.\n", namemonth[month-1], day, year);
    else
    {
        printf("Your entry for %s %d, %d:\n", namemonth[month-1], day, year);
        do
        {
            fgets(input, 900, note);
            printf("%s", input);
        }
        while (!feof(note));
        fclose(note);
    }
    free(filename);
}
/*Subprogram name: writefile
  Description: Handles the case when the user wants to write a note for a particular date.*/
void writefile(char* filename, int month, int day, int year, int choice)
{
    FILE* note;
    char input[1000];
    char cont = 1;
    if (choice == 1) note = fopen(filename, "w");
    else
    {
        note = fopen(filename, "r");
        if (note == NULL)
        {
            printf("Note for %s %d, %d does not exist.\n", namemonth[month-1], day, year);
            cont = 0;
        }
        else
        {
            fclose(note);
            note = fopen(filename, "a");
        }
    }
    int i = 0;
    if (cont)
    {
        if (note == NULL) printf("Cannot write note. It is because of some error I don't know yet.\n");
        else
        {
            printf("Write to note now. Leave a blank line then press Enter to stop writing note.\n");
            do
            {
                fgets(input, 900, stdin);
                if (input[0] == '\n') i++;
                else i = 0;
                fprintf(note, "%s", input);
            }
            while (i != 1);
            fclose(note);
        }
    }
    free(filename);
}
/*Subprogram name: deletefile
  Description: Handles the case when the user wants to delete a note for a particular date.*/
void deletefile(char* filename, int month, int day, int year)
{
    if (filename == 0) printf("The date %s %d, %d does not exist.\n", namemonth[month-1], day, year);
    else if (remove(filename) == 0) printf("Note successfully deleted.\n");
    else printf("Note for date %s %d, %d does not exist.\n", namemonth[month-1], day, year);
    free(filename);
}
/*Subprogram name: exists
  Description: Returns 1 if the note exists. Return 0 otherwise.*/
char exists(int month, int day, int year)
{
    FILE* note;
    char* filename = convToFile(month, day, year);
    note = fopen(filename, "r");
    if (note == NULL) return 0;
    else
    {
        fclose(note);
        return 1;
    }
}
/*Subprogram name: getmonth
  Description: Determines if the input of the user for the month is between 1 and 12 inclusive.
  If it is, it will return the user input.
  If it isn't, it will warn the user and loop again to query the user.*/
int getmonth()
{
    int i, month = 0;
    char input[100];
    while (month > 12 || month < 1)
    {
        printf("Enter month (format: x or xx): ");
        do
        {
            fgets(input, 100, stdin);
        } while (input[0] == '\n');
        if (sscanf(input, "%d", &month))
        {
            for (i = 0; i < strlen(input)-1; i++)
            {
                if (!isdigit(input[i]))
                {
                    month = -1;
                    break;
                }
            }
            if (month == -1)
            {
                printf("Enter numbers only.\n");
            }
            else if (month < 1 || month > 12)
            {
                printf("Month must be between 1 and 12.\n");
            }
        }
        else
        {
            printf("Enter numbers only.\n");
        }
    }
    return month;
}


/*Subprogram name: getyear
  Description: Determines if the input of the user for the year is between 1 and 9999 inclusive.
  If it is, it will return the user input.
  If it isn't, it will warn the user and loop again to query the user.*/
int getyear()
{
    int i, year = 0;
    char input[100];
    while (year > 9999 || year < 1)
    {
        printf("Enter year (format: x or xx or xxx or xxxx): ");
        do
        {
            fgets(input, 100, stdin);
        } while (input[0] == '\n');
        if (sscanf(input, "%d", &year))
        {
            for (i = 0; i < strlen(input)-1; i++)
            {
                if (!isdigit(input[i]))
                {
                    year = -1;
                    break;
                }
            }
            if (year == -1)
            {
                printf("Enter numbers only.\n");
            }
            else if (year < 1 || year > 9999)
            {
                printf("Year must be between 1 and 9999.\n");
            }
        }
        else
        {
            printf("Enter numbers only.\n");
        }
    }
    return year;
}
/*Subprogram name: compday1AD
  Description: This returns what day is January 1, 1.*/
int compday1AD(void)
{
    int year = 2009;
    char day = 4;
    year--;
    while (year > 0)
    {
        if (year == 1582) day += 2;
        else if (isleapyear(year) == 1) day += 5; // Line 27
        else day += 6;
        day %= 7;
        year--;
    }
    return day;
}
/*Subprogram name: compdayoffset
  Description: This returns which day the first day resides given the month and year.*/
int compdayoffset(int month, int year)
{
    char normalyear [12] = {0, 3, 3, 6, 1, 4, 6, 2, 5, 0, 3, 5};
    char leapyear [12] = {0, 3, 4, 0, 2, 5, 0, 3, 6, 1, 4, 6};
    char day = compday1AD(); // Line 127
    int ctr;
    if (month == 10 && year == 1582) return -1;
    for (ctr = 1; ctr < year; ctr++)
    {
        if (ctr == 1582) day += 5;
        else if (isleapyear(ctr) == 1) day += 2; // Line 27
        else day += 1;
        day %= 7;
    }
    if (isleapyear(year) == 1) // Line 27
    {
        day += leapyear[month-1];
    }
    else 
    {
        day += normalyear[month-1];
    }
    day %= 7;
    return day;
}
/*Subprogram name: compmatrixmonth
  Description: Generates a matrix that helps in displaying the calendar.*/
int compmatrixmonth(char calendar[6][7], int day, int month, int year)
{
    int i, j;
    int addnum = 1, ctr = 1;
    char monthdays [12] = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
    if (day == -1) return 0;
    for (i = 0; i < 6; i++) for (j = 0; j < 7; j++) calendar[i][j] = 0;
    for (i = 0; i < 6; i++)
    {
        for (j = 0; j < 7; j++)
        {
            if (addnum == 1 && day != 0)
            {
                if (j == day-1) addnum = 0;
            }
            else
            {
                if (month == 10 && year == 1582)
                {
                    if (ctr == 5) ctr = 15;
                }
                if (month == 2 && isleapyear(year) == 1)
                {
                    if (ctr <= 29) calendar[i][j] = ctr;
                }
                else
                {
                    if (ctr <= monthdays[month-1]) calendar[i][j] = ctr;
                }
                ctr++;
            }
        }
    }
    return 0;
}
/*Subprogram name: printcalendar
  Description: Returns the string representation of the calendar.*/
char* printcalendar (char calendar[6][7], int month, int year)
{
    char* buffer = (char*)malloc(50);
    char* str = (char*)malloc(2000);
    int lentitle = strlen(namemonth[month-1]) + 1;
    int temp = year;
    int i, j;
    while (temp != 0)
    {
        temp /= 10;
        lentitle++;
    }
    for (i = 0; i < (30-lentitle)/2; i++)
    {
        strcat(buffer, " ");
    }
    sprintf(str, "%s%s %d\n", buffer, namemonth[month-1], year);
    strcat(str, "-----------------------------\n");
    strcat(str, "|Sun|Mon|Tue|Wed|Thu|Fri|Sat|\n");
    strcat(str, "-----------------------------\n");
    /*if (month == 10 && year == 1582)
    {
        strcat(str, "|   |  1|  2|  3|  4| 15| 16|\n");
        strcat(str, "-----------------------------\n");
        strcat(str, "| 17| 18| 19| 20| 21| 22| 23|\n");
        strcat(str, "-----------------------------\n");
        strcat(str, "| 24| 25| 26| 27| 28| 29| 30|\n");
        strcat(str, "-----------------------------\n");
        strcat(str, "| 31|   |   |   |   |   |   |\n");
        strcat(str, "-----------------------------\n");
    }*/
    if (month == 10 && year == 1582) compmatrixmonth(calendar, 1, 10, 1582);
    if (month == 11 && year == 1582) compmatrixmonth(calendar, 1, 11, 1582); // Line 63
    if (month == 12 && year == 1582) compmatrixmonth(calendar, 4, 12, 1582); // Line 63
    for (i = 0; i < 6; i++)
    {
        for (j = 0; j < 7; j++)
        {
            if (calendar[i][j] != 0) break;
        }
        if (j == 7) break;
        strcat(str, "|");
        for (j = 0; j < 7; j++)
        {
            if (calendar[i][j] == 0) 
            {
                sprintf(buffer, "   ");
            }
            else
            {
                if (exists(month, calendar[i][j], year))
                {
                    if (calendar[i][j] < 10) 
                    {
                        sprintf(buffer, " *%d", calendar[i][j]);
                    }
                    else sprintf(buffer, "*%d", calendar[i][j]);
                }
                else
                {
                    if (calendar[i][j] < 10) 
                    {
                        sprintf(buffer, "  %d", calendar[i][j]);
                    }
                    else sprintf(buffer, " %d", calendar[i][j]);
                }
            }
            strcat(str, buffer);
            strcat(str, "|");
        }
        strcat(str, "\n-----------------------------\n");
        free(buffer);
    }
    return str;
}

int main (void)
{
    char tobreak = 0;
    char case1;
    char* str;
    int input2;
    int month, year, day, dayoffset;
    char calendar [6][7], input[100];
    char filename[40];
    char* fname;
    FILE *tofile;
    printf("Introduction\n\n");
    printf("Source: http://www.wiskit.com/calendar.html\n\n");
    printf("\tPrior to 1582, every year divisible by 4 was a leap year. Since a year\ncontains only 365.242199 days");
    printf("(slightly less than 365.25 days), an error of ten\ndays accumulated over the centuries. To compensate for this error, ");
    printf("Pope Gregory XIII (after whom the Gregorian Calendar is named) decreed that the ten days\nbetween October 5, 1582 and October 14, 1582 ");
    printf("would be eliminated from the\ncalendar.\n\n\tThis made October 1582 the shortest month, with only 21 days. After\n1582, ");
    printf("years divisible by 100 are not leap years unless they are also divisible\nby 400. Thus, 1900 is not a leap year, but 2000 is.\n\n");
    while (1)
    {
        case1 = 1;
        printf("Enter 0 if you want to exit this program.\n");
        printf("Enter 1 if you want to query for the calendar given month and year.\n");
        printf("Enter 2 if you want to create a file containing the calendar for a given year.\n");
        printf("Enter 3 if you want to read a note.\n");
        printf("Enter 4 if you want to add a note or overwrite an existing note.\n");
        printf("Enter 5 if you want to add to an existing note.\n");
        printf("Enter 6 if you want to delete a note.\n");
        printf("Enter 7 if you want to remove all notes.\n");
        do
        {
            fgets(input, 100, stdin);
        }
        while (input[0] == '\n');
        if (sscanf(input, "%d", &input2))
        {
            if (strlen(input) != 2) printf("Warning: Wrong Input.\n");
            else
            {
                switch (input2)
                {
                    case 0: 
                        tobreak = 1;
                        printf("The program will now exit.\n");
                        break;
                    case 1:
                        while (case1)
                        {
                            month = getmonth(); // Line 47
                            year = getyear(); // Line 88
                            str = (char*)malloc(500);
                            dayoffset = compdayoffset(month, year); // Line 144
                            compmatrixmonth(calendar, dayoffset, month, year); // Line 171
                            str = printcalendar(calendar, month, year); // Line 204
                            printf("An * beside a date means there is a note in that date.\n");
                            printf("%s", str);
                            // After this saka nagkakamali. Seg fault daw.
                            free(str);
                            case1 = useagain(); // Line 8
                        }
                        break;
                    case 2:
                        while (case1)
                        {
                            printf("Enter filename (up to 30 characters only including extension):\n");
                            do
                            {
                                fgets(filename, 40, stdin);
                            }
                            while (filename[0] == '\n');
                            filename[strlen(filename)-1] = 0;
                            year = getyear(); // Line 88
                            tofile = fopen(filename, "w");
                            fprintf(tofile, "An * beside a date means there is a note in that date.\n");
                            for (month = 1; month <= 12; month++)
                            {
                                str = (char*)malloc(500);
                                dayoffset = compdayoffset(month, year); // Line 144
                                compmatrixmonth(calendar, dayoffset, month, year); // Line 171
                                str = printcalendar(calendar, month, year); // Line 204
                                fprintf(tofile, "%s\n", str);
                                fprintf(tofile, "\n");
                                // After this saka nagkakamali. Seg fault daw.
                                free(str);
                            }
                            fclose(tofile);
                            case1 = useagain(); // Line 8
                        }
                        break;
                    case 3:
                        while (case1)
                        {
                            month = getmonth();
                            year = getyear();
                            do
                            {
                                printf("Enter day: ");
                                fgets(input, 90, stdin);
                            }
                            while (input[0] == '\n');
                            sscanf(input, "%d", &day);
                            fname = convToFile(month, day, year);
                            if (fname == 0) printf("The date you entered does not exist.\n");
                            else
                            {
                                readfile(fname, month, day, year);
                            }
                            case1 = useagain();
                        }
                        break;
                    case 4:
                        while (case1)
                        {
                            month = getmonth();
                            year = getyear();
                            do
                            {
                                printf("Enter day: ");
                                fgets(input, 90, stdin);
                            }
                            while (input[0] == '\n');
                            sscanf(input, "%d", &day);
                            fname = convToFile(month, day, year);
                            if (fname == 0) printf("The date you entered does not exist.\n");
                            else
                            {
                                writefile(fname, month, day, year, 1);
                            }
                            case1 = useagain();
                        }
                        break;
                    case 5:
                        while (case1)
                        {
                            month = getmonth();
                            year = getyear();
                            do
                            {
                                printf("Enter day: ");
                                fgets(input, 90, stdin);
                            }
                            while (input[0] == '\n');
                            sscanf(input, "%d", &day);
                            fname = convToFile(month, day, year);
                            if (fname == 0) printf("The date you entered does not exist.\n");
                            else
                            {
                                writefile(fname, month, day, year, 2);
                            }
                            case1 = useagain();
                        }
                        break;
                    case 6:
                        while (case1)
                        {
                            month = getmonth();
                            year = getyear();
                            do
                            {
                                printf("Enter day: ");
                                fgets(input, 90, stdin);
                            }
                            while (input[0] == '\n');
                            sscanf(input, "%d", &day);
                            fname = convToFile(month, day, year);
                            if (fname == 0) printf("The date you entered does not exist.\n");
                            else
                            {
                                deletefile(fname, month, day, year);
                            }
                            case1 = useagain();
                        }
                        break;
                    case 7:
                        printf("Please wait...\n");
                        system("del *.calendar");
                        system("rm *.calendar");
                        printf("Deleted all notes.\n");
                        break;
                    default:
                        printf("Warning: Wrong Input.\n");
                        break;
                }
            }
            if (tobreak == 1) break;
        }
        else
        {
            printf("Warning: Wrong Input.\n");
        }
    }
    return 0;
}

```

---

### Post by dwhitney67 on 2009-10-17
> **ajmburgos09 said:**
> This C program is supposed to be a perpetual calendar. But whenever I enter this input:
1
1
12

The program gives a seg fault. I checked for errors, but I didn't see any double-free errors or freeing a null pointer errors.

Can somebody help me?

Thanks!

Can you please edit your post to include your code directly, versus adding an attachment?  Remember to use the [code ] <your code> [/CODE] tags.

---

### Post by kripkenstein on 2009-10-17
Well, first off, there are some memory leaks, like
```

str = (char*)malloc(500);
dayoffset = compdayoffset(month, year); // Line 144
compmatrixmonth(calendar, dayoffset, month, year); // Line 171
str = printcalendar(calendar, month, year); // Line 204

```
The first line is not needed - those 500 bytes will be lost as a memory leak, since the last line makes str point to another memory area.

But those don't cause the segfault. The cause seems to be due to
```

char* buffer = (char*)malloc(50);

```
Change the 50 to, say, 5000, and it will work ok. So probably at some point more than 50 characters are written to the area buffer points to.

---

### Post by dwhitney67 on 2009-10-17
Two issues I came across...

1)  You are unnecessarily allocating space for 'str' before you call printcalendar().  See line 453.

2)  For whatever reason, you are trampling over the boundaries of 'buffer' in printcalendar().  Apparently its size is not sufficient for your needs.

Since 'buffer' is a local variable, just declare it on the stack, versus allocating memory for it on the heap.

I was able to get your program to work by declaring 'buffer' as such:
```

char buffer[100] = {0};   // the 100 was arbitrarily chosen, but it beats 50!

```

---

### Post by ajmburgos09 on 2009-10-17
Thanks guys! I was finally able to make the program work because of all your suggestion.
But I have a question. Why does the line:

```

char buffer [100]= {0};

```

work, and why did the line

```

char* buffer = (char*) malloc(50);

```

not work?

Thanks again!

---

### Post by dwhitney67 on 2009-10-17
100 is a greater number than 50.  With 'buffer' of 50 bytes allocated on the heap, you corrupted the 'str' buffer when you overran the allocated space for 'buffer'.

For all I know, 100 is not enough either.  You will need to determine what is the appropriate size for the buffer.

The space of 100 worked for me because I declared 'buffer' on the stack, and this area is distinct from the heap (where 'str' is allocated).

P.S.  Here's another potential problem in your code:
```

    for (i = 0; i < (30-lentitle)/2; i++)
    {
        strcat(buffer, " ");
    }

```
At this point, 'buffer' has not been initialized.  Thus it could contain crap, and possibly a null-termination character 1000 bytes from it beginning point.

You probably should have used strcpy(), not strcat().  Or you could consider using memset() to zero-out the buffer, or just calloc() when allocating.  So many choices for you to consider.

When I declared 'buffer' on the stack, I also initialized it to all nulls, hence why the strcat() worked in my test case.

---

### Post by ajmburgos09 on 2009-10-17
At first, I didn't mind the possible size of buffer because when I printed out the size of buffer using strlen, it always prints out 3 as its size. Why is it like that?

Thanks again, really!

:grin:

---

### Post by dwhitney67 on 2009-10-17
strlen() prints the number of characters in a buffer up to, but not including, the null-termination character.

When you walk away from this exercise, hopefully you will have learned that it is always important to initialize your variables.  You failed to do that with 'buffer'.

The other thing you should avoid are the unsafe methods strcat(), strcpy(), sprintf(), etc.  Use their augmented equivalents, such as strncat(), strncpy(), and snprintf(), when dealing with fixed-length buffers.

---

### Post by ajmburgos09 on 2009-10-17
Okay. I'll take note of that next time.

Thanks!

---

