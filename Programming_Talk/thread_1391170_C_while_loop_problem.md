---
title: "C while loop problem"
date: 2010-01-26
forum: Programming Talk
---

### Post by Woody1987 on 2010-01-26
Im writing a small console application. when the program starts the user is presented with a menu and the user inputs a number which corresponds to the action they want to take. There is a while loop running which checks for a certain value, in this case the value is 4 which will exit the program. If a value other than 4 is entered it continues. If an incorrect value is entered, it should clear the screen and show the menu again and await input, but instead of waiting for input, it keeps looping. The scanf function works on the first loop, but on subsequent loops it seems to fail. How do i fix this? 

```
int option = 0;

int main(int argc, char *argv[])
{
    while(option != 4)
    {
        mainMenu();
    }

    return 0;
}

void mainMenu()
{
    system("clear");

    printf("Welcome\n");
    printf("1. Register\n");
    printf("2. Unregister\n");
    printf("3. Query\n");
    printf("4. Exit\n");
    printf("\nOption: ");
    scanf("%d", &option);

    if(option == 1)
        registerObject();
    if(option == 2)
        unRegisterObject();
    if(option == 3)
        query();
    if(option > 4 || isdigit(option) != 0) //check for incorrect options
        printf("Enter a valid Option, 1 - 4");
}
```

---

### Post by Woody1987 on 2010-01-26
Fixed it, added:

```
int ch;
while((ch = getchar()) != '\n' && ch != EOF);
```

at the end of the menu function

---

### Post by dwhitney67 on 2010-01-26
Start by removing the global variable.  Their use is not recommended for countless reasons.

The main issue you are having is that you are not clearing the input stream should the scanf() fail to find a valid integer.

Here's a different rendition of your app:
```

#include <stdio.h>
#include <stdlib.h>

int mainMenu(void);

int main(int argc, char *argv[])
{
   while(mainMenu() != 4);

   return 0;
}

int mainMenu(void)
{
   int option = -1;

   system("clear");

   printf("Welcome\n");
   printf("1. Register\n");
   printf("2. Unregister\n");
   printf("3. Query\n");
   printf("4. Exit\n");
   printf("\nOption: ");
   scanf("%d", &option);

   switch (option)
   {
      case 1:
         registerObject();
         break;
      case 2:
         unregisterObject();
         break;
      case 3:
         query();
         break;
      case 4:
         printf("All done!\n");
         break;
      default:
         // no point printing message; system("clear") will erase it.
         //printf("Enter a valid Option, 1 - 4");

         // this will flush the input stream
         while (getchar() != '\n');
         break;
   }

   return option;
}

```

---

### Post by Woody1987 on 2010-01-26
Thankyou, i changed it to what you suggested and it worked perfectly.

---

