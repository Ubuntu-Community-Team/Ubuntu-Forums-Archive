---
title: "C - structures"
date: 2008-03-02
forum: Programming Talk
---

### Post by S15_88 on 2008-03-02
hi i'm making a "database" program for school that holds employee records in a structure containing their phone number name and address nad writes it to a binary file and can read it back in and add to it.

i'm having a great deal of trouble understanding how to go about doing this, we don't have good notes from lectures and i've read alot online about structures but am still not understanding a few things.

my question is can you pass a structure by reference/value?
example:
```

typedef struct  
{
    int a;
} number;

void change(*num) 
/* whats the prototype for num? struct *num? number *num?*/ 
{
    num.a = 10
    printf("%d\n", num.a);
}

int main(void)
{
    number num;
    num.a = 5;
    printf("%d", num.a);
    newRecord(&num);
}

```

Also I don't undersdtand why in the given structure for the assignment why the name and address char's are pointers?

whats this about printing the strings apart from the structure??

i'm so lost!

here is what i have so far, if someone could please take a look and tell me if they understand this and possibly help explain what needs to be done.

i am not asking for code as this is for a school, but i would really appreciate if someone could shed some light on this program!

i've included what needs to be done in comments, i figured splitting the tasks into functions would be the easiest way to go about this.

Thanks in advance, ALain

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <strings.h>

typedef struct  
{
    int	phoneNumber;
    char *name;
    char *address;
    short addressLength, nameLength;

} employeeRecord;

void newRecord()
{
    FILE * records;
    records = fopen("/home/alain/Documents/school/cis/2500/assignments/a-3/records", "w");
/*    
    if(records does not exist create it)
    {
    }
*/
    printf("Enter the name: ");
    /*fgets(?, some length, stdin);*/
    printf("Enter the address: ");
    /*fgets(?, some length, stdin);*/
    printf("Enter telephone number: ");
    /*scanf("%d\n", ?);  ignore the fact that an int cant hold a phonenumber with an area code, prof just wants a number in there*/ 

    fwrite(pointer, size, number, filePointer);
/*    
    if(fwrite is successful)
    {
        printf("The Information Has Been Stored\n");
    }
    else
    {
        printf("Error Occured\n");
    }
*/    
    fclose(records);
   
/*When the data has been entered it should be stored in a structure and written to disk. After the data has been saved to the file, print a message telling the user that the information has been stored.*/
}
void nameRetrieve()
{
    FILE * records;
    records = fopen("/home/alain/Documents/school/cis/2500/assignments/a-3/records", "w"); 
    
    printf("Enter a name: ");    
    /*fgets(?, some length, stdin);*/
    
   
/*
    while(records != EOF)
    {
        Search for structure containing entered name
    }
*/

/*After the user enters the name you should search the file starting with the first structure. Read each record in order and compare the name string in the file with the name which the user entered. If you find a record in the file with the name that the user entered then print the contents of the structure to the screen. Use the following headings and place the information after the headings.*/

/*If found
    printf("Name: ");
    printf("Address: ");
    printf("Telephone number: ");
*/

/*Not found
    printf("Record Not Found\n");
*/

}
void numberRetrieve()
{
    FILE * records;
    records = fopen("/home/alain/Documents/school/cis/2500/assignments/a-3/records", "w");

    printf("Enter a record number: ");
    /*scanf("%d\n", ?);*/

/*
    while(records != EOF)
    {
        Search for structure containing entered name
        fseek()  adressLength and nameLength
    }
*/


/*Use the number to locate the record in the file. The first structure in the file is record zero.  When retrieving records by number, move past the strings by using the string lengths from the structure and the fseek() function.*/

/*If found
    printf("Name: ");
    printf("Address: ");
    printf("Telephone number: ");
*/

/*Not found
    printf("Record Not Found\n");
*/
}
int main()
{
    int choice;

    printf("1. Enter a new record.\n");
    printf("2. Retrieve a record by name.\n");
    printf("3. Retrieve a record by number.\n");
    printf("4. Exit\n");
    printf("Enter a number from 1-4: ");
    scanf("%d", &choice);

    if(choice == 1)
    {
        newRecord();        
    }
    else if(choice == 2)
    {
        nameRetrieve();
    }   
    else if(choice == 3)
    {
        numberRetrieve();
    }
    else if(choice == 4)
    {
        return 0;
    }
    
    return 0;
}


```


Thanks again, ALain

---

### Post by LaRoza on 2008-03-02
I would suggest taking better notes during the lecture...

For the question on how to pass a structure, you should pass a pointer to the structure.

Thread closed because it is a homework question.

If you have specific questions on C, and your reading and classes need clarification, you can ask, but don't post assignments like this.

---

