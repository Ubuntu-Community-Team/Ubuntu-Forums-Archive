---
title: "Need help on C program"
date: 2009-11-26
forum: Programming Talk
---

### Post by tauman5263 on 2009-11-26
Okay, I'm having a little difficulty wrapping my head around structs.
 
Here's my code so far:
> 
#include<stdio.h>
#include<string.h>
 
typedef struct {
char make[15];
char model[15];
int odometer;
int date_manuf[5];
int date_purchase[5];
int gas_capacity;
int gas_level;
} auto_t;
 
void get_info(auto_t *car);
void print_info(auto_t car);
 
int main(void)
{ 
auto_t cars;
get_info(&cars);
print_info(cars);
return 0;
}
 
void get_info(auto_t *car)
{
int i;
printf("Enter the car's make: ");
gets(car->make);
printf("%s", car->make);
printf("Enter the car's model: ");
gets(car->model);
printf("Enter the current odometer reading: ");
scanf("%d", &car->odometer);
printf("Enter the Date of Manufacture (in MM DD YY format).\n");
printf("For example, May 5, 2009 would be entered as 05 05 09: ");
for (i=0;i<3;i++)
scanf("%d", car->date_manuf[i]);
printf("Enter the Date of Purchase (use same format as date of manufacture: ");
for (i=0;i<3;i++)
scanf("%d", car->date_purchase[i]);
printf("Enter the fuel tank capacity: ");
scanf("%d", &car->gas_capacity);
printf("Enter the current fuel level: ");
scanf("%d", &car->gas_level);
return;
}
 
void print_info(auto_t cars)
{
printf("GOT HERE");
printf("%s\n", cars.make[15]);
printf("%s\n", cars.model[15]);
printf("%d\n", cars.odometer);
printf("%d %d %d\n", cars.date_manuf[0], cars.date_manuf[1], cars.date_manuf[2]);
printf("%d %d %d\n", cars.date_purchase[0], cars.date_purchase[1], cars.date_purchase[2]);
printf("%d\n", cars.gas_capacity);
printf("%d\n", cars.gas_level);
return;
}

 
I'm having trouble with passing the struct by reference. When I run the program, I get an error saying something like: Segmentation fault (core dumped).
 
By the way, I compiled it with gcc in cygwin.

---

### Post by lisati on 2009-11-26
Try losing the "[15]" in the first couple of lines function print_info (I've highlighted the changed lines in red):
```


#include<stdio.h>
#include<string.h>

typedef struct {
char make[15];
char model[15];
int odometer;
int date_manuf[5];
int date_purchase[5];
int gas_capacity;
int gas_level;
} auto_t;

void get_info(auto_t *car);
void print_info(auto_t car);

int main(void)
{
auto_t cars;
get_info(&cars);
print_info(cars);
return 0;
}

void get_info(auto_t *car)
{
int i;
printf("Enter the car's make: ");
gets(car->make);
printf("%s", car->make);
printf("Enter the car's model: ");
gets(car->model);
printf("Enter the current odometer reading: ");
scanf("%d", &car->odometer);
printf("Enter the Date of Manufacture (in MM DD YY format).\n");
printf("For example, May 5, 2009 would be entered as 05 05 09: ");
for (i=0;i<3;i++)
scanf("%d", car->date_manuf[i]);
printf("Enter the Date of Purchase (use same format as date of manufacture: ");
for (i=0;i<3;i++)
scanf("%d", car->date_purchase[i]);
printf("Enter the fuel tank capacity: ");
scanf("%d", &car->gas_capacity);
printf("Enter the current fuel level: ");
scanf("%d", &car->gas_level);
return;
}

void print_info(auto_t cars)
{
printf("GOT HERE");
[B][COLOR="Red"]printf("%s\n", cars.make);
printf("%s\n", cars.model);[/COLOR][/B]
printf("%d\n", cars.odometer);
printf("%d %d %d\n", cars.date_manuf[0], cars.date_manuf[1], cars.date_manuf[2]);
printf("%d %d %d\n", cars.date_purchase[0], cars.date_purchase[1], cars.date_purchase[2]);
printf("%d\n", cars.gas_capacity);
printf("%d\n", cars.gas_level);
return;
} 

```

Edit: possible explanation. In your struct definition, you have defined make and model as 15 bytes long. Doing something like referring to make[15] in this situation will take you past the end of the storage allocated to make, since the count starts at 0.

---

### Post by tauman5263 on 2009-11-26
Nope, I'm not even getting that far before I run into the error. The error shows up at the first for loop.

---

### Post by lisati on 2009-11-26
> **tauman5263 said:**
> Nope, I'm not even getting that far before I run into the error. The error shows up at the first for loop.

/me scratches head. I got an error this time, it worked before! 
Anyone else got any suggestions? (I'm currently checking things out in Vista)

---

### Post by lisati on 2009-11-26
Got it! A missing "&" on a couple of lines!
Suggested Changes highlighted in red:
```


#include<stdio.h>
#include<string.h>

typedef struct {
char make[15];
char model[15];
int odometer;
int date_manuf[5];
int date_purchase[5];
int gas_capacity;
int gas_level;
} auto_t;

void get_info(auto_t *car);
void print_info(auto_t car);

int main(void)
{
auto_t cars;
get_info(&cars);
print_info(cars);
return 0;
}

void get_info(auto_t *car)
{
int i;
printf("Enter the car's make: ");
gets(car->make);
printf("%s", car->make);
printf("Enter the car's model: ");
gets(car->model);
printf("Enter the current odometer reading: ");
scanf("%d", &car->odometer);
printf("Enter the Date of Manufacture (in MM DD YY format).\n");
printf("For example, May 5, 2009 would be entered as 05 05 09: ");
for (i=0;i<3;i++)
[COLOR="Red"]scanf("%d", &car->date_manuf[i]);[/COLOR]
printf("Enter the Date of Purchase (use same format as date of manufacture: ");
for (i=0;i<3;i++)
[COLOR="Red"]scanf("%d", &car->date_purchase[i]);[/COLOR]
printf("Enter the fuel tank capacity: ");
scanf("%d", &car->gas_capacity);
printf("Enter the current fuel level: ");
scanf("%d", &car->gas_level);
return;
}

void print_info(auto_t cars)
{
printf("GOT HERE");
printf("%s\n", cars.make);
printf("%s\n", cars.model);
printf("%d\n", cars.odometer);
printf("%d %d %d\n", cars.date_manuf[0], cars.date_manuf[1], cars.date_manuf[2]);
printf("%d %d %d\n", cars.date_purchase[0], cars.date_purchase[1], cars.date_purchase[2]);
printf("%d\n", cars.gas_capacity);
printf("%d\n", cars.gas_level);
return;
}
```

Edit: Apologies for not spotting it sooner, I haven't done much C/C++ programming.

---

### Post by LKjell on 2009-11-26
Some nice program code you have. Very hard to read and use of dangerous function like gets!

---

### Post by lisati on 2009-11-26
> **LKjell said:**
> Some nice program code you have. Very hard to read and use of dangerous function like gets!

:) I might have done it differently too.

---

### Post by LKjell on 2009-11-26
This is not the best but more readable. To compile this use -std=gnu99 or -std=c99 . Another thing is preference. I like to write struct before every struct. Makes it easy to see what they are.

```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define BUF 15
struct auto_t
{
	char make[BUF];
	char model[BUF];
	int odometer;
	int date_manuf[5];
	int date_purchase[5];
	int gas_capacity;
	int gas_level;
};

void get_info(struct auto_t *car);
void print_info(struct auto_t *car);

int main()
{
	struct auto_t *cars = malloc(sizeof(struct auto_t));
	
	get_info(cars);
	print_info(cars);
	
	free(cars);

/*	The above and under is mutual exclusive	*/

/*	struct auto_t cars;*/
/*	*/
/*	get_info(&cars);*/
/*	print_info(&cars);*/
	
	return EXIT_SUCCESS;
}

void get_info(struct auto_t *car)
{
	/*gets is dangerous and is deprecated and should not be used at all!!!*/
	printf("Enter the car's make: ");
	fgets(car->make, BUF, stdin);
	
	printf("Enter the car's model: ");
	fgets(car->model, BUF, stdin);
	
	printf("Enter the current odometer reading: ");
	scanf("%d", &car->odometer);
	
	printf("Enter the Date of Manufacture (in MM DD YY format).\n");
	printf("For example, May 5, 2009 would be entered as 05 05 09: ");
	
	for (int i=0; i<3; i++)
		scanf("%d", &car->date_manuf[i]);
	
	printf("Enter the Date of Purchase (use same format as date of manufacture: ");
	
	for (int i=0; i<3; i++)
		scanf("%d", &car->date_purchase[i]);
		
	printf("Enter the fuel tank capacity: ");
	scanf("%d", &car->gas_capacity);
	
	printf("Enter the current fuel level: ");
	scanf("%d", &car->gas_level);
}

void print_info(struct auto_t *cars)
{
	printf("GOT HERE\n");
	printf("%s", cars->make);
	printf("%s", cars->model);
	printf("%d\n", cars->odometer);
	printf("%.2d %.2d %.2d\n", cars->date_manuf[0], cars->date_manuf[1], cars->date_manuf[2]);
	printf("%.2d %.2d %.2d\n", cars->date_purchase[0], cars->date_purchase[1], cars->date_purchase[2]);
	printf("%d\n", cars->gas_capacity);
	printf("%d\n", cars->gas_level);
}
```

---

### Post by tauman5263 on 2009-11-26
Thank you for your help. It was easier to read, but when I posted it, it got rid of all my spacing. I also haven't documented it.
 
Also, I'm doing this for a class, and my textbook went over defining structs with typedef. It also uses gets, and my professor is aware that it is dangerous. 
 
I do have one question though. Can someone explain why I need to add the "&" in the couple of lines that I missed them in? I thought they weren't needed because it was an array. 
 
Again, thanks for the help. It's very much appreciated.

---

### Post by Nohtanhoj on 2009-11-26
You need the & operator because functions like "gets" and "scanf" take in pointers to their inputs. For example, if I wanted to read an integer from standard input and print it into the screen, the code would look something like this.

int tmp;
printf("Input an integer: ");
scanf("%d", &tmp);
printf("%d", tmp);

I don't know if your prof has talked about C doing "passed by value" yet... When you call a function in C, any arguments have copies of their values made for use in the function. If you want a function to change any variable that is not local, you need to pass in the **address of** that variable. This is what the & operator does - signifies an address. Since scanf and gets are functions just like any that you define, they need the address of variables to change outside of their scope...

Make sense?

---

### Post by tauman5263 on 2009-11-26
Okay, I remember now. Yeah, we went over all of that stuff. I guess I was just having a bit of a brain fart.

Thanks for the help!

---

### Post by weresheep on 2009-11-26
Hi,

I got your code working and made some changes and added some notes to what I think are important points.

Compiles with...
```
gcc -Wall -ansi -pedantic car.c
```

Hope it helps.
-weresheep

```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>

#define BUF_LEN 15
/* Note - Length of date arrays was 5. Couldn't see a reason so changed. */
#define DATE_LEN 3

typedef struct {
  char make[BUF_LEN];
  char model[BUF_LEN];

  /* Note - long might be better type here. Int only guaranteed
  to hold -32768 to 32767 (i.e. 16 bits). unsigned type modifier also useful
  if there is no reason to have negative numbers. */
  int odometer;
  int date_manuf[DATE_LEN];
  int date_purchase[DATE_LEN];
  int gas_capacity;
  int gas_level;
} auto_t;

/* Make internal functions static so they can't be seen or used outside
this file. */
static void get_info(auto_t *car);
static void print_info(const auto_t *car);
static void strip_newline(char *s);

int main(void) {
  auto_t cars;

  get_info(&cars);
  print_info(&cars);

  return 0;
}

static void get_info(auto_t *car) {
  int rtn;

  printf("Enter the car's make: ");

  /* Note - Never use 'gets'. Always a good idea to check if user input was
  successful. */
  if (fgets(car->make, BUF_LEN, stdin) == NULL) {
    fprintf(stderr, "Failed to read car make\n");
    exit(EXIT_FAILURE);
  }

  /* Note - Make sure we don't have a '\n' in the input to save later
  printing extra blank lines. */
  strip_newline(car->make);

  /* Note - May also be a good idea here to check 'strlen(car->make)' to see
  if user just pressed return and entered a blank line. */

  /* This was annoying me during testing :p */
  /*puts(car->make);*/

  printf("Enter the car's model: ");

  /* Note - Again, check inputs. */
  if (fgets(car->model, BUF_LEN, stdin) == NULL) {
    fprintf(stderr, "Failed to read car model\n");
    exit(EXIT_FAILURE);
  }

  strip_newline(car->model);

  printf("Enter the current odometer reading: ");

  /* Note - scanf returns the number of matched items. Check user entered a
  valid number. i.e. if user entered 'alksdjkasdj' scanf would return 0. */
  if (scanf("%d", &car->odometer) != 1) {
    fprintf(stderr, "Failed to read car odometer\n");
    exit(EXIT_FAILURE);
  }

  printf("Enter the Date of Manufacture (in MM DD YY format).\n");
  printf("For example, May 5, 2009 would be entered as 05 05 09: ");

  /* Note - The problem with using scanf on stdin directly is what if user
  enters more data that expected? If user enters '1 2 3 4 5 6' then the below
  scanf will read '1 2 3' then return. However the next scanf wont wait for
  the user to enter any more text as '4 5 6' is still in the input buffer
  so it will be read that instead and the program will jump to the next scanf
  (fuel tank capacity).

  It would be better to use fgets to read the whole input line from the user
  in one go and then use sscanf on saved string. That way each time you ask
  the user a question, you read a complete line from them and throw away
  any extra, unwanted values. */
  
  /* Note - You could change the below scanf to accept MM/DD/YY by using
  '%d/%d/%d' */
  rtn = scanf("%d %d %d",
    &car->date_manuf[0], &car->date_manuf[1], &car->date_manuf[2]);

  if (rtn != 3) {
    fprintf(stderr, "Failed to read car manufacturing date\n");
    exit(EXIT_FAILURE);
  }

  /* Line was too long for my terminal :p */
  printf("Enter the Date of Purchase " \
    "(use same format as date of manufacture): ");

  /* Note - Make use of scanf's ability to match a known format against an
  input string to get the three numbers in one go.*/
  rtn = scanf("%d %d %d",
    &car->date_purchase[0], &car->date_purchase[1], &car->date_purchase[2]);

  if (rtn != 3) {
    fprintf(stderr, "Failed to read car purchase date\n");
    exit(EXIT_FAILURE);
  }

  printf("Enter the fuel tank capacity: ");

  if (scanf("%d", &car->gas_capacity) != 1) {
    fprintf(stderr, "Failed to read car gas capacity\n");
    exit(EXIT_FAILURE);
  }

  printf("Enter the current fuel level: ");

  if (scanf("%d", &car->gas_level) != 1) {
    fprintf(stderr, "Failed to read car gas level\n");
    exit(EXIT_FAILURE);
  }
}

static void print_info(const auto_t *cars) {
  /* This was annoying me during testing :p */
  /*printf("GOT HERE");*/

  /* Note - This function shouldn't be changing any of the 'cars' elements
  so lets get the compiler to do that checking for us by making the input
  parameter a const. */

  /* Note - puts automatically adds a '\n' after the input string. */
  puts(cars->make);
  puts(cars->model);
  printf("%d\n", cars->odometer);

  /* Note - Change the below format to '%.2d %.2d %.2d' to always print
  2 charaters. e.g. if date is '1 2 5' print '01 02 05'. */
  printf("%d %d %d\n",
    cars->date_manuf[0], cars->date_manuf[1], cars->date_manuf[2]);

  printf("%d %d %d\n",
    cars->date_purchase[0], cars->date_purchase[1], cars->date_purchase[2]);

  printf("%d\n", cars->gas_capacity);
  printf("%d\n", cars->gas_level);
}

static void strip_newline(char *s) {
  size_t len = strlen(s);
  char *last_char = len == 0 ? NULL : (s + (len - 1));

  if (last_char && *last_char == '\n') {
    *last_char = '\0';
  }
}


```

---

### Post by Nohtanhoj on 2009-11-26
Don't worry about it... If you need anything clarified, feel free to PM me. I've only been learning to program because of my engineering major - I took my first C class a year ago - and have since moved on to Python... When the profs stop caring about what language you use and only care whether your program works, you go Python. =D

Like I said, hit me up if you've got questions. I've got a decent understanding of C.

---

### Post by nvteighen on 2009-11-27
> **Nohtanhoj said:**
> Don't worry about it... If you need anything clarified, feel free to PM me. I've only been learning to program because of my engineering major - I took my first C class a year ago - and have since moved on to Python... When the profs stop caring about what language you use and only care whether your program works, you go Python. =D

Like I said, hit me up if you've got questions. I've got a decent understanding of C.

Er... let me remind you that PMs shouldn't be used for support questions. AFAIK, it isn't a Forum Guidelines violation and you won't be banned for that, but better not to do that: If you post questions and answers in a thread, you make it possible to others to benefit and learn too.

---

