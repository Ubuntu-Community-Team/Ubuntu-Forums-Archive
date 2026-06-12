---
title: "valgrind error: Invalid write of size 4"
date: 2012-06-22
forum: Programming Talk
---

### Post by spanlength1 on 2012-06-22
I am new to C and currently doing an assignment. I am getting lot of valgrind errors , please help me out.

//header file course.c
-----------------------------------------------------------------
```
#ifndef TKK_AS_C_COURSE_H
#define TKK_AS_C_COURSE_H

// This is a header file for the Course ADT, which is used to represent rows in
// a transcript of completed courses. One instance of the ADT stores the name of the course,
// and the grade received.
//
//
// Implement the struct in your .c file. The field used to store
// the name of the course must have type char * - you are not allowed to use
// a static array.

typedef struct Course_s Course;

// Creates a new course with name "courseName" and grade "grade". If courseName
// is NULL or if the grade is negative or zero (<= 0), the function returns NULL.
Course *courseConstruct(const char *courseName, int grade);

// Frees all memory allocated to the Course in the constructor functions Construct and Copy.
void courseDestruct(Course *);

// Returns the name of the course (shallow copy).
const char *courseGetName(Course const *);

// Returns the grade of the course
int courseGetGrade(Course const *);

// Creates a new course which is a deep copy of the course given in the parameter.
// The caller of the function must free the return value when it is not needed anymore.
Course *courseCopy(Course const *);

#endif
```

----------------------------------------------------
//source file course.c
----------------------------------------------------
```

#include <stdlib.h>
#include <string.h>
#include <assert.h>
#include "course.h"

// Implement the struct in your .c file. The field used to store
// the name of the course must have type char * - you are not allowed to use
// a static array.

typedef struct Course_s {
    char* coursename;
    int grade;
}Course_s;

// Creates a new course with name "courseName" and grade "grade". If courseName
// is NULL or if the grade is negative or zero (<= 0), the function returns NULL.
Course *courseConstruct(const char *courseName, int grade){

    if( courseName == NULL || grade <=0 )
        return NULL;
    else {
        Course *newCourse = malloc(sizeof(Course));
        size_t len = 1 + strlen(courseName);
        char *deepCopyString = malloc(len);
        newCourse->coursename = deepCopyString ? memcpy(deepCopyString, courseName, len) : NULL;
        newCourse->grade = grade;
        return newCourse;
    }
}

// Frees all memory allocated to the Course in the constructor functions Construct and Copy.
void courseDestruct(Course *course){
    assert(course);
    assert(course->coursename);
    free(course->coursename);
    free(course);
}

// Returns the name of the course (shallow copy).
const char *courseGetName(Course const *course){
    assert(course);
    return course->coursename;
}

// Returns the grade of the course
int courseGetGrade(Course const *course){
    assert(course);
    return course->grade;
}

// Creates a new course which is a deep copy of the course given in the parameter.
// The caller of the function must free the return value when it is not needed anymore.
Course *courseCopy(Course const *course){
    assert(course);
    Course *newCourse1 =  malloc(sizeof(Course));
    if(newCourse1){
    size_t len = 1 + strlen(course->coursename);
        char *deepCopyString = malloc(len);
    newCourse1->coursename = deepCopyString ? memcpy(deepCopyString, course->coursename, len) : NULL;
    newCourse1->grade = course->grade;
    return newCourse1;
    }
}


```
----------------------------------------------------
//header file transcript.h
----------------------------------------------------
```
#ifndef TKK_AS_C_TRANSCRIPT_H
#define TKK_AS_C_TRANSCRIPT_H

#include "course.h"

typedef struct Transcript_s Transcript;


// This function creates a new transcript for student (the name is given in "studentName")
// A Transcript contains the name of the owner of the transcript (whose transcript it is),
// and an array of completed courses (represented by the Course ADT).
//
// Define the struct in the .c file, but note: the array of completed courses must be
// dynamic - you are not allowed to use arrays of static size.
//
// Initially the student has no completed courses.
Transcript *tsConstruct(const char *studentName);

// This function frees all memory allocated by the abstract data type.
void tsDestruct(Transcript *);

// This function returns the name of the student (whose transcript this is)
// The string is not copied, the function just returns the pointer.
const char *tsGetName(Transcript const*);

// This function returns the average grade of the completed courses.
double tsAverageGrade(Transcript const *t);

// This function assigns a copy of the course array "courses" to the transcript.
// The old course array in the transcript and memory reserved by it are freed before
// assigning the new array.
//
// "courses" is a pointer to the first element of an array of Course pointers.
// The last element of the array is NULL. Elements of the array have been allocated using the
// Course ADT.
void tsSetCourseArray(Transcript *t, Course **courses);

// This function prints to the standard output all completed courses separated by newline.
// The format is:
// <Course name>:<Grade>
// For example:
// AS-0.1101 Basic Course in C Programming:4
void tsPrint(Transcript const *);

// Creates a deep copy of the transcript.
Transcript *tsCopy(Transcript const *);

#endif
```

----------------------------------------------------
//source file transcript.c
----------------------------------------------------


```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>
#include <assert.h>
#include <math.h>

#include "course.h"
#include "transcript.h"

typedef struct Transcript_s
{
    char* studentname;
    Course **course;
}Transcript_s;

// This function creates a new transcript for student (the name is given in "studentName")
// A Transcript contains the name of the owner of the transcript (whose transcript it is),
// and an array of completed courses (represented by the Course ADT).
//
// Define the struct in the .c file, but note: the array of completed courses must be
// dynamic - you are not allowed to use arrays of static size.
//
// Initially the student has no completed courses.
Transcript *tsConstruct(const char *studentName)
{
    assert(studentName);
    Transcript *newtranscript = malloc(sizeof(Transcript));
    size_t len = 1 + strlen(studentName);
    char *deepCopyString = malloc(len);
    newtranscript->studentname = deepCopyString ? memcpy(deepCopyString, studentName, len) : NULL;
    newtranscript->course = malloc(sizeof(Course*));
     newtranscript->course[0] = courseConstruct(NULL,0);
    return newtranscript;
}


// This function frees all memory allocated by the abstract data type.
void tsDestruct(Transcript *transcript)
{
    assert(transcript);
    free(transcript->studentname);
    for ( int i = 0; transcript->course[i] != NULL ; i++)
        courseDestruct(transcript->course[i]);
    free(transcript->course);
    free(transcript);

}
// This function returns the name of the student (whose transcript this is)
// The string is not copied, the function just returns the pointer.
const char *tsGetName(Transcript const* transcript)
{
    assert(transcript);
    return transcript->studentname;
}
// This function returns the average grade of the completed courses.
double tsAverageGrade(Transcript const *transcript)
{
    assert(transcript);
    int i = 0;
    int sum = 0;
    for (; transcript->course[i] != NULL ; i++ ){
        int grade = courseGetGrade(transcript->course[i]) ;
        sum = sum + grade;
    }
    double avg = (double)(sum/i);
    return avg;
}
// This function assigns a copy of the course array "courses" to the transcript.
// The old course array in the transcript and memory reserved by it are freed before
// assigning the new array.
//
// "courses" is a pointer to the first element of an array of Course pointers.
// The last element of the array is NULL. Elements of the array have been allocated using the
// Course ADT.
void tsSetCourseArray(Transcript *t, Course **courses)
{
    assert(t);
    for ( int i = 0; t->course[i] != NULL ; i++)
        courseDestruct(t->course[i]);
    free(t->course);
    int count= 0;
    int i = 0;
    do {
        count++;
        i++;
    } while (courses[i] != NULL);

    t->course = malloc(count * sizeof (Course*) + 1);
    if(t->course){
        for(int i = 0 ; i < count ; i++){
            t->course[i] = courseCopy(courses[i]);
        }
        t->course[count] = NULL;
    }
}

// This function prints to the standard output all completed courses separated by newline.
// The format is:
// <Course name>:<Grade>
// For example:
// AS-0.1101 Basic Course in C Programming:4
void tsPrint(Transcript const *transcript)
{
    assert(transcript);
    for (int i = 0 ; transcript->course[i] != NULL ; i++){
        printf("%s:%d\n",courseGetName(transcript->course[i]), courseGetGrade(transcript->course[i]));
    }
}

// Creates a deep copy of the transcript.
Transcript *tsCopy(Transcript const *transcript)
{
    Transcript *s = malloc(sizeof(Transcript));
    size_t len = 1 + strlen(transcript->studentname);
    char *deepCopyString = malloc(len);
    s->studentname = deepCopyString ? memcpy(deepCopyString, transcript->studentname, len) : NULL;
    int count= 0;
    int i = 0;
    do {
        count++;
        i++;
    } while (transcript->course[i] != NULL);
    s->course = malloc(count * sizeof (Course*) + 1);
    if(s->course){
        for(int i = 0 ; i < count ; i++){
            s->course[i] = courseCopy(transcript->course[i]);
        }
        s->course[count] = NULL;
    }
    return s;
}
```
----------------------------------------------------------
// test file tstest.c
---------------------------------------------------------

```
#include "transcript.h"
#include "course.h"

#include <stdio.h>
#include <stdlib.h>

int main() {
  // courses is an array of 3 course pointers.
  Course *courses[3];

  courses[0] = courseConstruct("AS-0.1101 Basic Course in C Programming", 5);
  courses[1] = courseConstruct("AS-0.1102 C/C++ Programming", 6);
  courses[2] = NULL;

  Transcript *t = tsConstruct("Antti");


  tsSetCourseArray(t, courses);
  // Antti has now 2 completed courses
     tsPrint(t);

  // Let's do it again. After this, Antti should still have 2 completed courses
  // because the set function erased the old courses.
  tsSetCourseArray(t, courses);

  // Should print both courses
  tsPrint(t);

  // Copy the transcript
  Transcript *t2 = tsCopy(t);
  tsPrint(t2);
  // ...and destroy it right away.
  tsDestruct(t2);

  // Free all memory

  tsDestruct(t);
  courseDestruct(courses[0]);
  courseDestruct(courses[1]);

  // We should have freed all allocated memory here.

}
```
--------------------------------------------------------------
valgrind errors:
-----------------------------------------------------------
==4175== Command: ./capplication_3
==4175== 
==4175== Invalid write of size 4
==4175==    at 0x804858F: tsConstruct (transcript.c:33)
==4175==    by 0x8048C2C: main (tstest.c:15)
==4175==  Address 0x419a144 is 0 bytes after a block of size 4 alloc'd
==4175==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4175==    by 0x8048530: tsConstruct (transcript.c:29)
==4175==    by 0x8048C2C: main (tstest.c:15)
==4175== 
==4175== Invalid read of size 4
==4175==    at 0x8048595: tsConstruct (transcript.c:34)
==4175==    by 0x8048C2C: main (tstest.c:15)
==4175==  Address 0x419a144 is 0 bytes after a block of size 4 alloc'd
==4175==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4175==    by 0x8048530: tsConstruct (transcript.c:29)
==4175==    by 0x8048C2C: main (tstest.c:15)
==4175== 
==4175== Invalid read of size 4
==4175==    at 0x804876A: tsSetCourseArray (transcript.c:80)
==4175==    by 0x8048C44: main (tstest.c:18)
==4175==  Address 0x419a144 is 0 bytes after a block of size 4 alloc'd
==4175==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4175==    by 0x8048530: tsConstruct (transcript.c:29)
==4175==    by 0x8048C2C: main (tstest.c:15)
==4175== 
==4175== Invalid read of size 4
==4175==    at 0x80488AC: tsPrint (transcript.c:107)
==4175==    by 0x8048C50: main (tstest.c:20)
==4175==  Address 0x419a144 is 0 bytes after a block of size 4 alloc'd
==4175==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4175==    by 0x8048530: tsConstruct (transcript.c:29)
==4175==    by 0x8048C2C: main (tstest.c:15)
==4175== 
==4175== Invalid read of size 4
==4175==    at 0x804861C: tsDestruct (transcript.c:44)
==4175==    by 0x8048CA4: main (tstest.c:37)
==4175==  Address 0x419a144 is 0 bytes after a block of size 4 alloc'd
==4175==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4175==    by 0x8048530: tsConstruct (transcript.c:29)
==4175==    by 0x8048C2C: main (tstest.c:15)
==4175==

---

### Post by Bachstelze on 2012-06-22
CODE tags, please...

---

### Post by Bachstelze on 2012-06-22
In transcript.c

```
 90     t->course = malloc(count * sizeof (Course*) + 1);
```

should be

```
 90     t->course = malloc((count+1) * sizeof (Course*));
```

and same thing on line 125.

---

### Post by spanlength1 on 2012-06-22
Do you think , is that the only error ?

---

### Post by Bachstelze on 2012-06-22
I don't know if it's the only error, but it's the one causing the valgrind messages.

---

### Post by spanlength1 on 2012-06-22
Thanks ..it solved the errors..

---

