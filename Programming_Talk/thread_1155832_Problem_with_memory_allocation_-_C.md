---
title: "Problem with memory allocation - C"
date: 2009-05-11
forum: Programming Talk
---

### Post by stfu05 on 2009-05-11
Hey guys!
I wrote the next code:
 
```

[SIZE=2][SIZE=2][/SIZE]
void DynamicFileAddCourse(char courseCode[], char courseName[], char departmentNumber[], char fileName[])
{
 FILE* file;
 char* record; // a string to save record in the file
 
 // calculating the total length of the record, to know how much memory to allocate
 int length = strlen(courseCode) + GetCorrectLengthOfString(courseName) + strlen(departmentNumber);
 
 record = (char*)malloc(length + 1); // allocating memory for the record string
 
// if allocation failed
 if(record == NULL)
 {
        PrintError("Memory allocation failed");
 }
 
 // concatenating the 3 given strings into the record string
 strcpy(record, courseCode);
 strcat(record, courseName);
 strcat(record, departmentNumber);
 record[length] = '\0';
 
 // opening the file for appending (writing)
 file = fopen(fileName, "a+");
 
 // checking if opening was successful
 if(file == NULL)
 {
       PrintError("Opening file failed");
 }
 
 // writing the new record to the file
 fprintf(file, "\n%s", &record);  
 
 free(record); // free the memory we allocated for the record string
 
// closing the file
 fclose(file);
}
 
int GetCorrectLengthOfString(char* str)
{
 int i = 0;
 int length = 0;
 if(str != NULL)
 { 
    while(str[i] != '\0')
    {
        if((str[i] >= 65 && str[i] <= 90) || (str[i] >= 97 && str[i] <= 122))
       {
            length++;
        }
        i++;
    }
 }
 
 return length;
}
 
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] PrintError([/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]char[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]* msg)
{
    fprintf(stderr, [/SIZE][SIZE=2][COLOR=#a31515][SIZE=2][COLOR=#a31515]"Error: %s\n"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2], msg);[/SIZE]
[SIZE=2] 
[/SIZE][SIZE=2][COLOR=#008000][SIZE=2][COLOR=#008000]    // exiting from the program with error
[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]    exit(1);
}
[/SIZE][/SIZE] 

```
 
And my program crashes in the memory allocation for the record string...
Can it be a problem with the computer? that he doesn't have enough memory or something?
Because I think the code is ok..
 
thnx in advance!!

---

### Post by Sockerdrickan on 2009-05-11
If you could post the complete code, I could fix it.

---

### Post by stfu05 on 2009-05-11
> **Tux0r said:**
> If you could post the complete code, I could fix it.
 
added the full code...
the courseName string i get from the user dynamically meaning i don't know what length it will be... therefore the special the function to calculate the length, because strlen() doesn't return the right length...

---

### Post by PmDematagoda on 2009-05-11
Try using an strcpy first instead of an strcat to fill the record array, I think your issue may be trying to use an array that hasn't been initialised, and hence has garbage in it, so when you try to concatenate strings onto it, you run out of space because the garbage takes some space as well.

Edit:- And please consider formatting your code using indents before posting it, it is not that fun trying to read code that is not indented properly.:)

---

### Post by stfu05 on 2009-05-11
> **PmDematagoda said:**
> Try using an strcpy first instead of an strcat to fill the record array, I think your issue may be trying to use an array that hasn't been initialised, and hence has garbage in it, so when you try to concatenate strings onto it, you run out of space because the garbage takes some space as well.
 
Edit:- And please consider formatting your code using indents before posting it, it is not that fun trying to read code that is not indented properly.:)
 
I've changed the first strcat to strcpy and the result was:
 
Any more ideas? :)

---

### Post by PmDematagoda on 2009-05-11
I'm sorry, looks like I was wrong, it does seem that the array does get initialised when it is malloced.

But the code to count the number of characters seems to be a bit wrong, try this:-
[PHP]int GetCorrectLengthOfString(char* str)
{
 int length = 0;
 if(str != NULL)
 { 
    while(str[length] != '\0')
            length++;
 }
 
 return length;
}[/PHP]

---

### Post by stfu05 on 2009-05-11
> **PmDematagoda said:**
> I'm sorry, looks like I was wrong, it does seem that the array does get initialised when it is malloced.
 
But the code to count the number of characters seems to be a bit wrong, try this:-
[php]int GetCorrectLengthOfString(char* str)
{
 int length = 0;
 if(str != NULL)
 { 
    while(str[length] != '\0')
            length++;
 }
 
 return length;
}[/php]
 
doesn't worked...
I still get the error - [SIZE=2][COLOR=#a31515]
[SIZE=2][COLOR=#a31515]Memory allocation failed[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#a31515]and the program terminates - exit(1);[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#a31515]what to do? :([/COLOR][/SIZE]
 
maybe the problem is with the function that gets the dynamic string from the user?
 
[COLOR=black][php]
 
char* GetDynamicCourseNameFromUser()
{
    int size = 6;
    int position = 0;
    char* str = (char*)malloc(size); // allocating memory first time for the string
 
    // if allocation failed
    if(str == NULL)
   {
        PrintError("Memory allocation failed");
   }
   printf("Enter name of the course to add: ");
   // a process in which I get the course name the user gave and save it in the char* variable
   while(fgets((str + position), size, stdin) != NULL)
   {
       if(strchr(str, '\n'))
       {
            break;
        }
        else
        {
            position += size - 1;
            str = (char*)realloc(str, position + size);
        }
   }
   return str;
}
 

[/php][/COLOR]
[/COLOR][/SIZE]

---

### Post by stfu05 on 2009-05-11
someone got a clue? :confused:

---

### Post by Zugzwang on 2009-05-11
Use a debugger - Set a breakpoint to the line where you print the error and run the program. As soon as you reach that point, examine the local variables of the functions and on the call stack and see what you can find.

---

### Post by stfu05 on 2009-05-11
> **Zugzwang said:**
> Use a debugger - Set a breakpoint to the line where you print the error and run the program. As soon as you reach that point, examine the local variables of the functions and on the call stack and see what you can find.
 
did that... 
i think i have a memory leek somewhere... that's why I get the "heep corrupted" message...

---

### Post by eye208 on 2009-05-11
I think the problem is that you get a "Memory allocation failed" message without knowing where it came from. Change this function...
```
void PrintError(char* msg)
{
    fprintf(stderr, "Error: %s\n", msg);
 
    // exiting from the program with error
    exit(1);
}
```
... into this...
```
void PrintError(char* msg, int line, char* file)
{
    fprintf(stderr, "Error: %s in line %d of file %s\n", msg, line, file);
 
    // exiting from the program with error
    exit(1);
}
```
... and then call it like this:
```
PrintError("Memory allocation failed", __LINE__, __FILE__);
```
__LINE__ is a predefined macro that returns the current line number during compilation. __FILE__ returns the name of the current source file. Now you don't need a debugger to see where the errors occur.

---

### Post by Zugzwang on 2009-05-11
> **stfu05 said:**
> did that... 
i think i have a memory leek somewhere... that's why I get the "heep corrupted" message...

No! Memory leaks do not "corrupt" the heap (or the stack, as shown in your screenshot). Please follow eye208's advice.

---

### Post by Ackowa on 2009-05-11
> **stfu05 said:**
> Hey guys!
I wrote the next code:
 
```

[SIZE=2][SIZE=2][/SIZE]
void DynamicFileAddCourse(char courseCode[], char courseName[], char departmentNumber[], char fileName[])
{
 FILE* file;
 char* record; // a string to save record in the file
 
 // calculating the total length of the record, to know how much memory to allocate
 int length = strlen(courseCode) + GetCorrectLengthOfString(courseName) + strlen(departmentNumber);
 
 record = (char*)malloc(length + 1); // allocating memory for the record string
 
// if allocation failed
 if(record == NULL)
 {
        PrintError("Memory allocation failed");
 }
 
 // concatenating the 3 given strings into the record string
 strcpy(record, courseCode);
 strcat(record, courseName);
 strcat(record, departmentNumber);
 record[length] = '\0';
 
 // opening the file for appending (writing)
 file = fopen(fileName, "a+");
 
 // checking if opening was successful
 if(file == NULL)
 {
       PrintError("Opening file failed");
 }
 
 // writing the new record to the file
 fprintf(file, "\n%s", &record);  
 
 free(record); // free the memory we allocated for the record string
 
// closing the file
 fclose(file);
}
 
int GetCorrectLengthOfString(char* str)
{
 int i = 0;
 int length = 0;
 if(str != NULL)
 { 
    while(str[i] != '\0')
    {
        if((str[i] >= 65 && str[i] <= 90) || (str[i] >= 97 && str[i] <= 122))
       {
            length++;
        }
        i++;
    }
 }
 
 return length;
}
 
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] PrintError([/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]char[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]* msg)
{
    fprintf(stderr, [/SIZE][SIZE=2][COLOR=#a31515][SIZE=2][COLOR=#a31515]"Error: %s\n"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2], msg);[/SIZE]
[SIZE=2] 
[/SIZE][SIZE=2][COLOR=#008000][SIZE=2][COLOR=#008000]    // exiting from the program with error
[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]    exit(1);
}
[/SIZE][/SIZE] 

```
 
And my program crashes in the memory allocation for the record string...
Can it be a problem with the computer? that he doesn't have enough memory or something?
Because I think the code is ok..
 
thnx in advance!!


Are you sure that the problem is in that code and not somewhere else or has problem with the input that you get.

Cause when I run it with:

int
main(void)
{
        printf("Start\n");
        DynamicFileAddCourse("a", "b", "c", "d");
        printf("Start2\n");
        return 0;
}

it works for me without any problems (I tried it on a solaris machine using gcc but that shouldn't matter)
(added "return;" before fopen line since I didn't want to open a file)

---

### Post by lloyd_b on 2009-05-11
> **stfu05 said:**
> Hey guys!
I wrote the next code:
 
```

[SIZE=2][SIZE=2][/SIZE]
void DynamicFileAddCourse(char courseCode[], char courseName[], char departmentNumber[], char fileName[])
{
 FILE* file;
 char* record; // a string to save record in the file
 
 // calculating the total length of the record, to know how much memory to allocate
 int length = strlen(courseCode) + GetCorrectLengthOfString(courseName) + strlen(departmentNumber);
 
 record = (char*)malloc(length + 1); // allocating memory for the record string
 
// if allocation failed
 if(record == NULL)
 {
        PrintError("Memory allocation failed");
 }
 
 // concatenating the 3 given strings into the record string
 strcpy(record, courseCode);
 strcat(record, courseName);
 strcat(record, departmentNumber);
 record[length] = '\0';
 
 // opening the file for appending (writing)
 file = fopen(fileName, "a+");
 
 // checking if opening was successful
 if(file == NULL)
 {
       PrintError("Opening file failed");
 }
 
 // writing the new record to the file
 fprintf(file, "\n%s", &record);  
 
 free(record); // free the memory we allocated for the record string
 
// closing the file
 fclose(file);
}
 
int GetCorrectLengthOfString(char* str)
{
 int i = 0;
 int length = 0;
 if(str != NULL)
 { 
    while(str[i] != '\0')
    {
        if((str[i] >= 65 && str[i] <= 90) || (str[i] >= 97 && str[i] <= 122))
       {
            length++;
        }
        i++;
    }
 }
 
 return length;
}
 
[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] PrintError([/SIZE][SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]char[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]* msg)
{
    fprintf(stderr, [/SIZE][SIZE=2][COLOR=#a31515][SIZE=2][COLOR=#a31515]"Error: %s\n"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2], msg);[/SIZE]
[SIZE=2] 
[/SIZE][SIZE=2][COLOR=#008000][SIZE=2][COLOR=#008000]    // exiting from the program with error
[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]    exit(1);
}
[/SIZE][/SIZE] 

```
 
And my program crashes in the memory allocation for the record string...
Can it be a problem with the computer? that he doesn't have enough memory or something?
Because I think the code is ok..
 
thnx in advance!!

Add some debugging printf()'s to the code:```
 FILE* file;
 char* record; // a string to save record in the file
 
 // calculating the total length of the record, to know how much memory to allocate
 int length = strlen(courseCode) + GetCorrectLengthOfString(courseName) + strlen(departmentNumber);
 
 record = (char*)malloc(length + 1); // allocating memory for the record string
 
// if allocation failed
 if(record == NULL)
 {
        PrintError("Memory allocation failed");
        printf("length: %d, courseCode: %d, courseName: %d, departmentNumber: %d\n", length, strlen(courseCode), GetCorrectLengthOfString(courseName), strlen(departmentNumber);
 }
```
The only reason for that malloc() to fail is if you're giving it a strange number (very large number, negative number, etc).  Seeing exactly what value it's using, and what the components used to calculate the value are, should tell you where things are going wrong.

Lloyd B.

---

### Post by Ackowa on 2009-05-12
> **lloyd_b said:**
> Add some debugging printf()'s to the code:```
 FILE* file;
 char* record; // a string to save record in the file
 
 // calculating the total length of the record, to know how much memory to allocate
 int length = strlen(courseCode) + GetCorrectLengthOfString(courseName) + strlen(departmentNumber);
 
 record = (char*)malloc(length + 1); // allocating memory for the record string
 
// if allocation failed
 if(record == NULL)
 {
        PrintError("Memory allocation failed");
        printf("length: %d, courseCode: %d, courseName: %d, departmentNumber: %d\n", length, strlen(courseCode), GetCorrectLengthOfString(courseName), strlen(departmentNumber);
 }
```
The only reason for that malloc() to fail is if you're giving it a strange number (very large number, negative number, etc).  Seeing exactly what value it's using, and what the components used to calculate the value are, should tell you where things are going wrong.

Lloyd B.

Problem with you change is that your printf will never be called snice PrintError does exit(1);
So if you want any printout added you have to add it before PrintError

---

### Post by lloyd_b on 2009-05-12
> **Ackowa said:**
> Problem with you change is that your printf will never be called snice PrintError does exit(1);
So if you want any printout added you have to add it before PrintError

Lol - that's what I get for not reading ALL of the code :)

Lloyd B.

---

