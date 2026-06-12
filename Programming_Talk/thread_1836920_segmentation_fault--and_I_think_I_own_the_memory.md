---
title: "segmentation fault--and I think I own the memory"
date: 2011-08-31
forum: Programming Talk
---

### Post by audit on 2011-08-31
```
static int cb_create_container(void* ptr_4th_arg, int num_col, char** col_text, char** col_name)
{
    int num_rec;
    sscanf(col_text[0], "%d", &num_rec);
    printf("%d\n",num_rec);
    if(!*(struct Out_put**)ptr_4th_arg)
    {
        struct Out_put** pp_out = (struct Out_put**)ptr_4th_arg;
        *pp_out = (struct Out_put*) calloc(num_rec + 1,sizeof(struct Out_put));
        strcpy(pp_out[num_rec]->field_name, "test"); /*Right here I get a seg fault and I cannot see why I don’t own this piece of memory???*/
    }
    return 0;
}
```

It seems to me I am doing every thing right but I obviously am not.

---

### Post by pjd99 on 2011-08-31
Not an expert by any means, been a few years since I did any c/c++, but here goes:

strycpy isn't overrunning the length of the destination is it? Pretty sure it doesn't check if has enough length in the destination. Maybe check the length of field_name in the struct before writing? 

Do you have to dereference pp_out in the strcpy line? Like I said its been ages, but when I used to get seg faults with pointers and I didn't know what was going on, I'd just start whacking in *'s (or deleting them) and then try again.

---

### Post by schauerlich on 2011-08-31
You never make sure ptr_4th_arg is not null before dereferencing it. Also: how big is field_name?

---

### Post by audit on 2011-08-31
this is the struct:
```
struct Out_put
{
    char field_name[25];
    char field_value[25];
};
```

edit: decided it was easier to show the whole file than just part.
```
#include<stdio.h>
#include<stdlib.h>
#include<assert.h>
#include<string.h>
#include <sqlite3.h>
#include "create_and_pop.h"

static int callback(void* ptr_4th_arg, int num_col, char** col_text, char** col_name)
{
    int i =0;
    struct Out_put** pp_out = (struct Out_put**)ptr_4th_arg;
    for(i = 0; i < num_col; i++)
    {
        strcpy(pp_out[i]->field_name, col_name[i]);
        strcpy(pp_out[i]->field_value, col_text[i]);
    }

    return 0;
}

static int cb_create_container(void* ptr_4th_arg, int num_col, char** col_text, char** col_name)
{
    int num_rec;
    sscanf(col_text[0], "%d", &num_rec);
    printf("%d\n",num_rec);
    if(!*(struct Out_put**)ptr_4th_arg)
    {
        struct Out_put** pp_out = (struct Out_put**)ptr_4th_arg;
        *pp_out = (struct Out_put*) calloc(num_rec + 1,sizeof(struct Out_put));
        strcpy(pp_out[num_rec]->field_name, "test"); 
    }
    return 0;
}

void summary(const char* db_name)
{   
    char* error_msg = 0;
    char create_summary_string[]
        = "select pay_grp, sum(gross) as \"total\" from payroll_foot group by pay_grp;"; 
    int rc = 0;
    sqlite3* db = 0;
    struct Out_put* out_structure = 0;
    sqlite3_open(db_name, &db);
    rc = sqlite3_exec(db, "select count(*) as \"data_size\" from  payroll_foot;", 
            cb_create_container, &out_structure, &error_msg);
    if( rc!=SQLITE_OK )
    {
        fprintf(stderr, "SQL error: %s\n", error_msg);
        sqlite3_free(error_msg);
    }

    rc = sqlite3_exec(db, create_summary_string, callback, &out_structure, &error_msg);
    if( rc!=SQLITE_OK )
    {
        fprintf(stderr, "SQL error: %s\n", error_msg);
        sqlite3_free(error_msg);
    }

    printf("%s\n", out_structure[0].field_name);
  
    sqlite3_close(db);
}
```

---

### Post by Senesence on 2011-08-31
As schauerlich said, you're not checking for NULL before dereference, so that's something you should do.

Also, your function takes 4 arguments, but uses only 2 .... any reason for that?

It's hard to figure out everything that could be wrong, but I would take a real close look at num_rec. What is the value of that variable before it's used in pp_out[num_rec]?

If you're calling pp_out[0], that seems fine, but I'm not so sure about pp_out[1], or anything higher.

You ran this through gdb already, right?

---

### Post by audit on 2011-09-01
> As schauerlich said, you're not checking for NULL before dereference, so that's something you should do.

done but not the problem.

> Also, your function takes 4 arguments, but uses only 2 .... any reason for that?

sqlite designed the interface so my callback must conform to it unless I want to write my own

> It's hard to figure out everything that could be wrong, but I would take a real close look at num_rec. What is the value of that variable before it's used in pp_out[num_rec]?

the value for this test is 200--I have tested it with a printf in the function and it is being set at 200.

> If you're calling pp_out[0], that seems fine, but I'm not so sure about pp_out[1], or anything higher.

your right pp_out[0] can be set- I have tested that but everything else is a seg fault.

> You ran this through gdb already, right?

yes, but I am a real novice with gdb and all I can tell is that it will not let me do anything to pp_out[200].

Thanks for reading.

---

### Post by Bachstelze on 2011-09-01
> **audit said:**
> 
yes, but I am a real novice with gdb and all I can tell is that it will not let me do anything to pp_out[200].

Run it in valgrind. We can't test anything without a main.

---

### Post by audit on 2011-09-01
> If you allocate memory for 200 items, it will be pp_out[0] to pp_out[199]. pp_out[200] is out of bounds. Run it in valgrind and it will tell you.

I wish that was the problem, but all values other than pp_out[0] result in seg fault--and I am actually allocating 200 + 1. I'll sit down to today and run it in valgrind. Thanks

---

### Post by dwhitney67 on 2011-09-01
When receiving data from the "unknown", _never_ use strcpy().  Use strncpy() so that you can limit how much data is copied to the destination.  Otherwise you could inadvertently receive a long source string that will overrun your destination buffer, and subsequently cause your application to crash.

[Content edited... my analysis was incorrect.]

Consider the following, untested code:
```

typedef struct
{
   char field_name[25];
   char field_value[25];
} DB_Result;
...
static int callback(void* result, int num_col, char** col_text, char** col_name)
{
   int i = 0;
   DB_Result** db_result = (DB_Result**) result;

   for(i = 0; i < num_col; i++)
   {
      strncpy((*db_result)[i].field_name, col_name[i], sizeof((*db_result)[i].field_name));
      strncpy((*db_result)[i].field_value, col_text[i], sizeof((*db_result)[i].field_value));
   }

   return 0;
}

static int cb_create_container(void* result, int num_col, char** col_text, char** col_name)
{
   DB_Result** db_result = (DB_Result**) result;
   int num_rec;
   int status = -1;

   if (db_result && col_text && *col_text)
   {
      if (sscanf(col_text[0], "%d", &num_rec) == 1 && num_rec > 0)
      {
         *db_result = calloc(num_rec, sizeof(DB_Result));

         if (*db_result)
         {
            status = 0;
         }
      }
   }
   
   return status;
}

```

---

### Post by audit on 2011-09-01
@dwhitney67

Thank you--you are very smart. I will not have time till later tonight to figure out what I was doing wrong; but your suggestions were obviously correct. 

Again thank you.

---

### Post by audit on 2011-09-01
I just finished trying to see what the main problem was with my code and why it was addressing memory that I did not own (it is my understanding that trying to address memory that you do not own is what a segmentation fault is).

There were other potential problems but as far as I can tell this was the problem, I was trying to write to a member with this line:

```

strcpy(pp_out[num_rec]->field_name, "test");
```

and it should probably have been written like this:
```

strncpy((*pp_out)[num_rec].field_name, "test", sizeof((*pp_out)[0].field_name));
```

so my question is why is this ```
(*pp_out)[num_rec].field_name
```
different from this: ```
pp_out[num_rec]->field_name
```

If you can explain the difference I would appreciate it?

Thanks for all the help.

---

### Post by Longinus00 on 2011-09-01
It's another level of indirection. Look at your declaration of pp_out. If that is still confusing then review how arrays are treated in C.

---

### Post by dwhitney67 on 2011-09-01
> **audit said:**
> 
If you can explain the difference I would appreciate it?


Maybe a picture and some verbose code may help:
```

              pp_out
         +-------------+
addr A   |    addr B --|---+
         +-------------+   |
                           |
...                        |
                           |
  +------------------------+
  |
  V      +-------------+
addr B   |  record 0   |
         +-------------+
         +-------------+
addr C   |  record 1   |
         +-------------+
         +-------------+
addr D   |  record 2   |
         +-------------+
              ...
         +-------------+
addr Z   | record N-1  |
         +-------------+


By dereferencing the pointer (pp_out) at Addr A, you would yield the Addr B;
that's what *(pp_out) does.

Next, by adding an offset to Addr B, you can obtain the correct record.
Offset 0 is the first record; offset 1 is the second, etc.

Perhaps the following code would clear this up...
----------------------------------------------------------

struct Out_put** pp_out = (struct Out_put**) ptr_4th_arg;  /* reinterpret Addr A */

struct Out_put*  recs_begin = *pp_out;   /* dereference pp_out to get start address, Addr B, of records */

struct Out_put*  first_rec  = recs_begin[0];  /* or first_rec = recs_begin; */ 
struct Out_put*  second_rec = recs_begin[1];
struct Out_out*  third_rec  = recs_begin[2];
...
struct Out_put*  nth_rec    = recs_begin[N-1];

```

---

