---
title: "Weird Problem with this code"
date: 2008-07-30
forum: Programming Talk
---

### Post by dynamethod on 2008-07-30
Hey there, ill start off by saying im quite fresh with C, but im trying

I'm having a problem with some code here:

```

/* Program:	Course Project - CD Inventory
 * Version: 	1.0
 * Author: 	Joe
 * 
 * This program is used to track its inventory of CD's
 * 
 * Version 1.0
 * 	- Only Reads input from user, and displays input
 * 	- Only Reads in Title/Artist/Number of Tracks/(Album or Single)/Price
 * 	- Does not save user input once program has finished
 * 	- Only stores infomation about ONE CD
 */

#include <stdio.h>
#include <string.h> 	// string library to access string functions

int main(void)
{
    char Title[101];	// Store track Title, extra 1 for NULL char
    char Artist[101];	// Store Artist Name, extra 1 for NULL char
    short nTracks;	// Store No. of Tracks				
    short Album; 	// Store Album/Singles as int
    char type;		// For figuring out Albulm or single
    float Price;	// Store price as double to store cents as well
	
	
    printf("\n******** CD Inventory v 1.0 ********\n");
	
    /* The title */
    
    printf("Please enter the Title of the CD: ");
    scanf("%s", Title);

    /* The artist */

    printf("Please enter the Artist: ");
    scanf("%s", Artist);

    /* The tracks */
	
    printf("Please enter the Number of tracks on the CD: ");
    scanf("%d", &nTracks);
	
    /* The Price */
	
    printf("Please enter the Price of the CD: $ ");
    scanf("%f", &Price);
	
    /* Album or Single */
	
    printf("Album or Single? Type a for album or s for single: ");
    scanf("%c", &type);
    Album = type == 'a';
	
    /* Output of CD details */

    printf("\n========== CD Details =========\n"); 
    printf("Title: %s\n", Title);
    printf("Artist: %s\n", Artist);
    printf("Tracks: %d\n", nTracks);
    printf("Price: $%.2f\n", Price);
    
    if(Album)
        printf("Album\n");
    else
        printf("Single\n");
		
    getchar();
    
    return 0;
}

```

Problem being that after the program asks for the price of the CD, it skips the code:

```

/* Album or Single */
	
printf("Album or Single? Type a for albulm or s for single: ");
scanf("%c", &type);
Album = type == 'a';

```

And i have no idea why, it's driving me crazy, help MUCH appreciated!

EDIT fixed up the source paste, easier to read now

---

### Post by rehin on 2008-07-30
Can you show the output of the program when you run it and give it all the answers?

---

### Post by dynamethod on 2008-07-30
Sure here we are:

```
******** CD Inventory v 1.0 ********
Please enter the Title of the CD: title
Please enter the Artist: artist
Please enter the Number of tracks on the CD: 25
Please enter the Price of the CD: $ 19.95
Album or Single? Type a for album or s for single: 
========== CD Details =========
Title: title
Artist: artist
Tracks: 25
Price: $19.95
Single

```

---

### Post by era86 on 2008-07-30
Try this: use the function gets().  Research this.  Sometimes scanf() can cause alot of problems especially if you do it multiple times with different data types.  I have run into alot of issues using scanf() with strings.  Using gets(), it may be safer.

Let me know how it goes.  PM me if you need more in depth advice.

---

### Post by era86 on 2008-07-30
> **dynamethod said:**
> Sure here we are:

```
******** CD Inventory v 1.0 ********
Please enter the Title of the CD: title
Please enter the Artist: artist
Please enter the Number of tracks on the CD: 25
Please enter the Price of the CD: $ 19.95
Album or Single? Type a for album or s for single: 
========== CD Details =========
Title: title
Artist: artist
Tracks: 25
Price: $19.95
Single

```

I think it is counting your '\n' at the end of the 19.95.  Since the price is taken in as a float, scanf() doesn't read in the newline character '\n'.  Instead, it is being passed to the next scanf() as a character.

Someone correct me if I am wrong here.  I could be missing it...

Goodluck

---

### Post by rehin on 2008-07-30
> **dynamethod said:**
> sure here we are:

```
******** cd inventory v 1.0 ********
please enter the title of the cd: Title
please enter the artist: Artist
please enter the number of tracks on the cd: 25
please enter the price of the cd: $ 19.95
album or single? Type a for album or s for single: 
========== cd details =========
title: Title
artist: Artist
tracks: 25
price: $19.95
single

```


t

---

### Post by dynamethod on 2008-07-30
> **era86 said:**
> Try this: use the function gets().  Research this.  Sometimes scanf() can cause alot of problems especially if you do it multiple times with different data types.  I have run into alot of issues using scanf() with strings.  Using gets(), it may be safer.

Let me know how it goes.  PM me if you need more in depth advice.

Ok thanks for the advice, its just that what i havent learned anything about gets() so far, so it out of the scope of my study materials, the material im studying from so far only implements scanf as yet, ive noticed another with scanf too like this:


```
scanf("%[^\n]", var_whatever);

printf("enter more stuff: ");
fflush(stdin);

scanf("%[^\n]", var_stuff);


```

scanf should be able to read in input as well as white spaces, but this does not work with Linux OS's, does with windows for me though

---

### Post by rehin on 2008-07-30
The problem is that scanf("%c",&type) takes "\n" of the previous input and assigns it to type. For getting rid of this you can put Album or Single question at the top. If you first ask it it can not take any "\n" as its char input.

---

### Post by david_lynch on 2008-07-30
> **dynamethod said:**
> 
scanf should be able to read in input as well as white spaces, but this does not work with Linux OS's, does with windows for me though
IMHO this has nothing to do with windows or linux, it has to do with the compiler. It sounds like gcc is a little more strict than microsoft visual c or whatever you were using on windows.

I also agree with the those who suggest using gets() - scanf is arcane.

---

### Post by dynamethod on 2008-07-30
> **rehin said:**
> The problem is that scanf("%c",&type) takes "\n" of the previous input and assigns it to type. For getting rid of this you can put Album or Single question at the top. If you first ask it it can not take any "\n" as its char input.

Aha! Ok I never thought of it like that, however because all of the printf questions require an input as well as the carriage return, I was wanting to use the scanf("%[^\n]", var_whatever) technique, but this doesnt work on ubuntu, I've just tested it like that on windows and it works, so anyone know the linux equivilant of scanf("%[\n]", var) ?

---

### Post by dynamethod on 2008-07-30
> **david_lynch said:**
> IMHO this has nothing to do with windows or linux, it has to do with the compiler. It sounds like gcc is a little more strict than microsoft visual c or whatever you were using on windows.

I also agree with the those who suggest using gets() - scanf is arcane.

Ok, how do i configure gcc to allow me to use scanf("%[\n]", var) ?

---

### Post by dynamethod on 2008-07-30
Solved

I just placed getchar() before the scanf("%c", &type);

---

### Post by dynamethod on 2008-08-02
Acutally, there must be a better solution, I've got into the chapter about fgets, fputs, puts, gets etc.

But ive tried to implement fgets in place of scanf like this:

```

fgets(type, 1, stdin);

```

But its not working for me (I take it it's because char only stores one character and i have to press enter to confirm input(\n) which fgets doesnt like, but i tried fgets(type, 2, stdin) and still no joy) 

I can use fgets() with a string array, but not with single char's, and the man pages are quiet confusing for me to interpret as i havent learned about pointers yet and i *think* they use pointers as part of the explanations in the man page and other reference material, could someone please help me out here.

All these scanfs are killing me because i have to put in these stupid gethchar()'s everywhere so that the program doesnt skip questions


Heres the updated code:

```

/* Program:	Course Project - CD Inventory
 * Version: 	2.0
 * Author: 	Joe
 * 
 * This program is used to track its inventory of CD's
 * 
 * Version 2.0
 *
 * 	- Only Reads input from user, and displays input
 * 	- Only Reads in Title/Artist/Number of Tracks/(Album or Single)/Price
 * 	- Does not save user input once program has finished
 * 	- Stores up to 100 CD's of infomation
 */

#include <stdio.h>
#include <string.h>

int main(void)
{
    char    title[100][61];  
    char    artist[100][61];	
    int     tracks[100];
    char    type;
    int     album[100];
    float   price[100];
    int     count = 0;          // How many CDs are being tracked
    int     i;                  // loop counter
   
    
    
   
   /*********************************
    *          PROGRAM BEGINS       *
    *********************************/
    
    
    puts("******** CD Inventory v 1.0 ********");
    puts("You can store a maximum of 100 CD's");
    
    for(;;)
    {
        getchar(); // i have to have these stupid getchars everywhere
                   // to catch that f**** scanf stream
        
        fputs("Do you want to store CD's? (y/n): ", stdout);
       
        scanf("%c", &type);
        if(toupper(type)!='Y')
            break;
        
        
        puts(""); // Just to tidy up the output
        
        /*      title           */
        
       
        printf("Please enter the details of CD %d...\n", count+1);
        getchar();
        fputs("Title?: ", stdout);
        
       
        fgets(title[count], sizeof(title[count]), stdin);
        title[count][strlen(title[count])-1] = '\0';
        
        /*      artist          */
      
        fputs("Artist?: ", stdout);
        
        fgets(artist[count], sizeof(artist[count]), stdin);
        artist[count][strlen(artist[count])-1] = '\0';
        /*      tracks          */
       
        fputs("Number of tracks?: ", stdout);
        scanf("%d", &tracks[count]);
        getchar();
        /*      Album/Single    */
                
        for(;;)
        {
          
            fputs("Album or single? (a for album s for single): ", stdout);
            
            scanf("%c", &type);
            type = toupper(type);
            if(type=='A' || type=='S')
                break;
            puts("Error - only 'a/A' or 's/S' are allowed");
        }
        album[count] = type == 'A';
        
        
        /*      Price           */
       
        
        printf("Retail Price? (eg 19.95)? ");
        getchar();
        scanf("%f", &price[count]);
        
        count = count+1;
        
        
        /*       check if we have filled up the array       */
        
        if(count == 100)
        {
            puts("You have reached the limits of this program");
            break;
        }
    }
    
    for(i = 0; i<count;i++)
    {
        printf("\nThe details of CD %d are\n", i+1);
        puts("========================");
        printf("Title: %s\n", title[i]);
        printf("Artist: %s\n", artist[i]);
        printf("Tracks: %d\n", tracks[i]);
        if(album[i])
            puts("Album");
        else
            puts("Single");
        printf("Price: %.2f\n", price[i]);
        puts("========================");
        
        if(i<count-1)       // if there are more CDs to see 
        {
            puts("\nPress ENTER to see the next set of details: ");
            getchar();
        }
        
    }
}


```

---

### Post by dwhitney67 on 2008-08-02
When reading in a string (a character array), always used fgets().  _Never_ use scanf(), fscanf(), or gets(); all of these are unsafe and could lead an operator to enter a string longer than is expected and corrupt the data on the stack, thus potentially leading to a program crash or corrupted data.

So:
[PHP]char buf[101] = {0};
printf( "Enter a string: " );
fgets( buf, sizeof(buf), stdin );[/PHP]
With respect to reading a float, you can read it in as a string, then convert if to a float using strtof().

An alternative, which is perhaps more attactive:
[PHP]float price;
printf( "Enter a float: " );
scanf( "%f%*c", &price );

// And for single characters (like the album type)
char type;
printf( "Enter type (s for single, a for album): " );
scanf( "%c%*c", &type );[/PHP]

---

### Post by dynamethod on 2008-08-02
> **dwhitney67 said:**
> When reading in a string (a character array), always used fgets().  _Never_ use scanf(), fscanf(), or gets(); all of these are unsafe and could lead an operator to enter a string longer than is expected and corrupt the data on the stack, thus potentially leading to a program crash or corrupted data.

So:
[PHP]char buf[101] = {0};
printf( "Enter a string: " );
fgets( buf, sizeof(buf), stdin );[/PHP]
With respect to reading a float, you can read it in as a string, then convert if to a float using strtof().

An alternative, which is perhaps more attactive:
[PHP]float price;
printf( "Enter a float: " );
scanf( "%f%*c", &price );

// And for single characters (like the album type)
char type;
printf( "Enter type (s for single, a for album): " );
scanf( "%c%*c", &type );[/PHP]

Why ```
scanf( "%c%*c", &type );
``` ?

---

### Post by dwhitney67 on 2008-08-03
> **dynamethod said:**
> Why ```
scanf( "%c%*c", &type );
``` ?
Um, so that you don't have to perform the getchar().  The first %c is used to capture the character you want (e.g. the CD type), the %*c is needed to capture, yet ignore, the carriage return (i.e. the 'enter').

---

