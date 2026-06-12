---
title: "Ansi c program with Geany in ubuntu 14.04 wierd problem"
date: 2014-10-14
forum: Programming Talk
---

### Post by pauls2 on 2014-10-14
Hi all! I am new to ansi c and a relative newb to Ubuntu. I used to write c code for DOS back before Windows happened but haven't done any programming since the mid 1980's.
So much for the introduction and on to the problem:
I have written, compiled, and built the following code without warnings (-wall is set) and without errors. the input() function is being used by the newfile() function and on the 16th iteration it by-passes the part that allows me to enter anything (as though it gets a "\n" when it gets there). I have commented out the code for the 15th, the 16th, and the 17th iteration and it just moves the failure around. I have looked hard to find the problem and can't find it.

I am hoping that someone else might see a mistake in the code. I have a pause in the code right now to hold for a few seconds between iterations so I can tell exactly when it happens. Can anyone help this old man?

```

// ExtBal6.c
// the <ESC> key exits the program until I get the ender func complete

// Preprossesor comands ***********************************************
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
// #include <math.h>  I will need this later but not for now
// #include <stdlib.h> I will need this later but not for now


// Prototypes *********************************************************
int mainmenu(void);
int ballistics (void); // dummy struct but the actual struct not done
int openfile(void); // dummy struct but the actual struct not done
int newrecord(void);
//int lprint(int); not done
int clearscreen(void); // complete ??
int input(char*, int); // entry routine for user input
//void ender(void; not done

// Global variables ***************************************************
int chois; //used to return values from functions
char lin[81]; // global to transfer input to struct

// structures defined *************************************************
struct gun
{
    char make[25];
    char model[25];
    char serial[15];
    float barrellength;
    float boretosite;
    float riflingtwist;
    int riflingdirection;
}gun;
struct kase
{
    char make[20];
    char type[25];
    char name[25];
    float trimlength;
    float overallength;
    float weight;
}kase;
struct bullet
{
    char make[25];
    float weight;
    char type[15];
    float coeff;
    char dragmodel[6];
    float dia;
    float length;
}bullet;
struct powder
{
    char make[20];
    char type[20];
    char lot[20];
    float chargeweight;
}powder;
struct primer
{
    char make[20];
    char type[15];
}primer;
struct wad
{
    char make[20];
    char type[15];
    float seatingpress;
}wad;
struct history
{
    char loaddate[12];
    int timesreloaded;
}history;
struct rangeresults
{
    float avrjvel;
    float stddev;
    float extreemspred;
    float groupsize;
    float siteinrang;
}rangeresults;
struct environ
{
    float altitud;
    float windvel;
    float windir;
    float humid;
    float baropres;
    float shotdirec;
    float latitude;
    float tempratr;
}environ;

    
// main begins ********************************************************
int main(void)
{
//    int ch;
    do
    { // do - while loop begins
        
        switch(mainmenu()) //put up main menu and return 
        { // switch begins
            case '1': 
            case 'B': 
            case 'b': 
            ballistics(); // ballistic struct
            break;
            case '2': 
            case 'O':  // O (as in Oscar)
            case 'o': // o (as in oscar)
            openfile();  // open existing record
            break;
            case '3': 
            case 'N': 
            case 'n': 
            newrecord();  // enter new record
            break;
            case '4': 
            case 'P': 
            case 'p': 
            //lprint();  // print current record
            break;
            case '5': 
            case 'F': 
            case 'f': 
            //lprint();  // print a range form (blank record form)
            break;
            case '6': 
            case 'Q': 
            case 'q': 
            chois = 27;
            //ender(); // prepare to end program (clean up and clear screen)
            // chois made to equal 27
            break;
            
            
        } // switch ends
        
    } // do - while loop ends
    while (chois != 27);  // while <ESC> is not used continue loop
            
return(0);
} 
// main ends **********************************************************

// Functions **********************************************************

// main menu begins ***************************************************

int mainmenu(void)
{
    int ch;
        clearscreen();
    // put up the menu
    printf("\n\n\n\n\t\t\t\t Main Menu \n\n");
    printf("\t\t\t 1. run Ballistics \n");
    printf("\t\t\t 2. Open existing record \n");
    printf("\t\t\t 3. enter New record \n");
    printf("\t\t\t 4. Print record \n");
    printf("\t\t\t 5. print range Form \n");
    printf("\t\t\t 6. Quit \n");
    printf("\n\t\t Enter your NUMBER or LETTER choice:  "); 
    
    chois = getchar(); // get the letter or number from user
    while ((ch = getchar()) != '\n' && EOF) // strip newline
    {
        continue;
    }
        
    return(chois); // return value to main in the global "chois"
}
// mainmenu ends ******************************************************

// ballistics begins **************************************************

int ballistics(void)
{
    int select; // selection from menu
    int ch;
    chois = 0; // reset the value of global chois to zero
    
    
    do
    {
    clearscreen();
    printf("\n\n\n\n\t\t\t Ballistics Menu \n\n"); // write menu
    printf("\t\t\t 1. use record data \n");
    printf("\t\t\t 2. enter fresh data \n");
    printf("\t\t\t 3. return to Main Menu \n");
    printf("\t\t\t 4. quit \n\n");
    printf("\t\t enter your NUMBER choice:  ");
    select = getchar(); // get number selection
    while((ch = getchar()) != '\n' && ch != EOF)
        {
      continue;
        }
    switch(select) // switch begins - use selection in switch
        {
            case '1':
            case '2': 
            case '3': // if value is 1, 2, or 3
            chois = 0; // assign global chois to zero
            break;
            case '4': // if the value is 4 
            chois = 27; // assign global chois to <ESC>
            break;
                        
        } // switch ends
        
    }
    while(select !=27 && select !='1' && select !='2' && select !='3' && select !='4');
    return(chois); // send chois back to main switch
}
// ballitics ends *****************************************************

// openfile begins ****************************************************

int openfile(void)
{
    int i = 0;
    int h;
    while(i < 100) // clear screen
    {
        printf("\n");
        i++;
    } // screen is cleared
    printf("this structure will open an existing saved file\n ");
    printf("if no file exists it will print \"no files found\" \n");
    for(i=0; i<=42767; i++) // time delay to read message
        for(h=0; h<=42767; h++)
    {}
    chois = 0;
    return(chois);
    
}
// openfile ends ******************************************************

// newrecord begins ***************************************************

int newrecord()
{
 char titl[80];
 int length;
 clearscreen();
 printf("\t\t\tEnter new record information\n\n");
 strcpy(titl, "bore to sight distance ");
 length = 10;
 input(titl, length);
 gun.boretosite = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 1 of 18 \n");
 strcpy(titl, "rifling twist: 1 in ? ");
 length = 6;
 input(titl, length);
 gun.riflingtwist =atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 2 of 18 \n");
 strcpy(titl, "direction of rifling - 0 for clockwise or 1 for counter-clockwise ");
 length = 3;
 input(titl, length);
 gun.riflingdirection = atoi(lin);
 lin[0] = '\0';
 printf("\ncompleted 3 of 18 \n");
 strcpy(titl, "bullet weight ");
 length = 6;
 input(titl, length);
 bullet.weight = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 4 of 18 \n");
 strcpy(titl, "ballistic coefficient ");
 length = 6;
 input(titl, length);
 bullet.coeff = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 5 of 18 \n");
 strcpy(titl, "Drag model ");
 length = 6;
 input(titl, length);
 strcpy(bullet.dragmodel, lin);
 lin[0] = '\0';
 printf("\ncompleted 6 of 18 \n");
 strcpy(titl, "bullet diameter ");
 length = 7;
 input(titl, length);
 bullet.dia = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 7 of 18 \n");
 strcpy(titl, "bullet length ");
 length = 7;
 input(titl, length);
 bullet.length = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 8 of 18 \n");
 strcpy(titl, "Average velocity ");
 length = 9;
 input(titl, length);
 rangeresults.avrjvel = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 9 of 18 \n");
 strcpy(titl, "sight-in range ");
 length = 10;
 input(titl, length);
 rangeresults. siteinrang = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 10 of 18 \n");
 strcpy(titl, "Altitude above sea level ");
 length = 9;
 input(titl, length);
 environ.altitud = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 11 of 18 \n");
 strcpy(titl, "Wind velocity ");
 length = 6;
 input(titl, length);
 environ.windvel = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 12 of 18 \n");
 strcpy(titl, "Wind from direction (N = 0, E = 90, S = 180, W = 270) ");
 length = 6;
 input(titl, length);
 environ.windir = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 13 of 18 \n");
 strcpy(titl, "Relative humidity in percent ");
 length = 5;
 input(titl,length);
 environ.humid = (atof(lin)/100);
 lin[0] = '\0';
 printf("\ncompleted 14 of 18 \n");
 strcpy(titl, "Barometric pressure ");
 length = 6;
 input(titl, length);
 environ.baropres = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 15 of 18 \n");
 strcpy(titl, "shooting direction (N = 0, E = 90, S = 180, W = 270) ");
 length = 6;
 input(titl, length);
 environ.shotdirec = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 16 of 18 \n");
 strcpy(titl,"Latitude, South latitudes are negative (-) ");
 length = 6;
 input(titl, length);
 environ.latitude = atof(lin);
 lin[0] = '\0';
 printf("\ncompleted 17 of 18 \n");
 strcpy(titl, "Temperature ");
 length = 6;
 input(titl, length);
 environ.tempratr = atof(lin);
 lin[0] = '\0';
 return 0;
}
// newrecord ends *****************************************************

// clearscreen begins *************************************************

int clearscreen()
{
    int i = 0;
    while(i < 100)
    {
        printf("\n");
        i++;
    } // screen is now cleared
    return(0);
}
// clearscreen ends ***************************************************

// input begins *******************************************************

int input(char *titl, int length)
{
    int i=0,x=0;
    char buf[length]; // set the length of input
    buf[0] = '\0'; // initialize buf to an empty string
    char *p; // pointer to position in buf
    lin[0] = '\0'; // erase any string in lin
    // place prompt
    printf ("Enter %sin less than %d characters ",titl, length);
  
    if (fgets(buf, length, stdin) != NULL) // get the input
    {
     // test for and remove newline 
     if ((p = strchr(buf, '\n')) != NULL)
        {
           *p = '\0';
        }
        printf ("\n\n%s is %s \n", titl, buf);
    }
    strcpy(lin, buf); // copy input to global 'lin'
    for(i=0;i<40000;i++)
    {
        for(x=0;x<40000;x++);
    }

    return 0;
}
// input ends *********************************************************



```

---

### Post by ofnuts on 2014-10-14
Nothing obvious. Did you add printf() statement to check if you enter the input() function or if the failure if before it?

Also, since the mid-80s, programming has a bit evolved and you can no use an interactive debugger (see 'gdb' in your repo, and 'ddd' which is a graphical font-end to it).

---

### Post by spjackson on 2014-10-14
I'm not sure whether this is your problem but maybe.
```

Enter bore to sight distance in less than 10 characters 123456789




bore to sight distance  is 123456789


completed 1 of 18
Enter rifling twist: 1 in ? in less than 6 characters


rifling twist: 1 in ?  is


completed 2 of 18



```
In this case, I don't get to type anything for item 2. The reason is that if the user enters precisely length-1 characters then hits return, then the '\n' is not consumed by fgets and is still waiting to be read on the next call to input.

---

### Post by pauls2 on 2014-10-14
It prints the prompt and I added a printf() after to print the the entered string. It prints out showing the string is empty.
It works for the 15 iterations before and the two that follow. I copied the code to an older machine and compiled it with no errors and no warnings (-Wall is set) the same thing happens on both computers but the older computer skips the 15th iteration.

I feel it must have something to do with the machine but I don't know how it could.

I don't see any place for a memory leak or buffer overflow but if that was the case would it go back to "normal" after the failed iteration?

---

### Post by ofnuts on 2014-10-14
spjackson may have the answer... you are prey to lingering LF characters. A possible fix is to reread if you get an empty line.

---

### Post by pauls2 on 2014-10-14
> **spjackson said:**
> I'm not sure whether this is your problem but maybe.
```

Enter bore to sight distance in less than 10 characters 123456789




bore to sight distance  is 123456789


completed 1 of 18
Enter rifling twist: 1 in ? in less than 6 characters


rifling twist: 1 in ?  is


completed 2 of 18



```
In this case, I don't get to type anything for item 2. The reason is that if the user enters precisely length-1 characters then hits return, then the '\n' is not consumed by fgets and is still waiting to be read on the next call to input.

SPJackson,
Thankyou, I missed your post originally because I must have been posting as you finished. In my initial tests of the function as a stand alone program it just truncated the input if it was too long. I will have to study the potential problem that you found. My inputs have all been well within the input lengths (I hadn't tried to break the code yet). 

ofnuts,
I wrapped the input in a while loop that checks for buf[0] == '\0' and the problem is gone. it doesn't seem very elegant but then I am not a professional. I would like to understand what happened but it is more important that it works.
here is what I changed:
```

int input(char *titl, int length)
{
    int i=0,x=0;
    char buf[length]; // set the length of input
    buf[0] = '\0'; // initialize buf to an empty string
    char *p; // pointer to position in buf
    lin[0] = '\0'; // erase any string in lin
    // place prompt
    printf ("Enter %sin less than %d characters ",titl, length);
  while ( buf[0] == '\0')
  {
    if (fgets(buf, length, stdin) != NULL) // get the input
    {
     // test for and remove newline 
     if ((p = strchr(buf, '\n')) != NULL)
        {
           *p = '\0';
        }
        printf ("\n\n%s is %s \n", titl, buf);
    }
  }
    strcpy(lin, buf); // copy input to global 'lin'
    for(i=0;i<40000;i++)
    {
        for(x=0;x<40000;x++);
    }

    return 0;

```

I will see what happens when I input different lengths of the string including maximum and more characters.

Thank you so much for the assist!

---

