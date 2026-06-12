---
title: "Can check my sqlite problem?"
date: 2013-04-17
forum: Programming Talk
---

### Post by Newbie89 on 2013-04-17
Source code:

#include <stdio.h> 
#include <sqlite3.h>
#include <stdlib.h>
static char *createsql = "CREATE TABLE Employee(" "ID INTEGER PRIMARY KEY," "Name VARCHAR(10)," "BadgeID VARCHAR(10));";
static char *insertsql = "INSERT INTO Employee VALUES(NULL, 'Danny', '12345');"; 
static char *querysql = "SELECT * FROM Employee;";
int main(void) 
{     
    
    int i,j;
    int rows, cols; 
    sqlite3 *db; 
    char *errMsg = NULL; 
    char **result; 
/* Open database file */ 
if (sqlite3_open("my_example.db3", &db)) 
    { 
        return 0; 
    }
/* Build Table */ 
sqlite3_exec(db, createsql, 0, 0, &errMsg);
/* Add a new record */ 
sqlite3_exec(db, insertsql, 0, 0, &errMsg);
/* Get all records in database */ 
sqlite3_get_table(db,querysql,&result, &rows, &cols, &errMsg);

/* List all the data */ 
for (i=0;i<rows;i++) 
{ 
    for (j=0;j<cols;j++) 
    { 
        printf("%s\t", result[i*cols+j]); 
    }

printf("\n"); 
}
/* Free table */ 
sqlite3_free_table(result); 
/* Close database */ 
sqlite3_close(db); 
}

My output:
1st time:
hong@ubuntu:~/test$ gcc -o qqq qqq.c -lsqlite3
hong@ubuntu:~/test$ ./qqq
ID    Name    BadgeID    
hong@ubuntu:~/test$ 

2nd time:
hong@ubuntu:~/test$ ./qqq
ID    Name    BadgeID    
1    Danny    12345    
hong@ubuntu:~/test$ 

How to solve the 2nd time output show on the 1st time?Suppose the output should show after ./qqq at the 1st time.

---

### Post by schragge on 2013-04-17
Shouldn't this
```

if (sqlite3_open("my_example.db3", &db)) 
    { 
        return 0; 
    }

```
better be
```
if (SQLITE_OK != sqlite3_open("my_example.db3", &db)) return 1;
```:?:

[highlight]Update[/highlight]
I see that ```
#define SQLITE_OK 0
``` so your code should work nevertheless.
Well, it seems that *sql3_get_table* returns in the fourth parameter the actual number of data rows not counting the header row. You should do it like
```
for (i=0;i<(rows+1)*cols;i++)
    printf("%s%s", result[i], (i+1)%cols?"\t":"\n");
```
Also note that each time you invoke your program it inserts a new row into the table.

---

### Post by Newbie89 on 2013-04-17
schragge,thanks for kind help.:p

---

### Post by Newbie89 on 2013-04-17
Let say I wanna give the user to key in the input to insert the data as above...

Such like this,

printf("Enter the number of data to be inserted\n");
    scanf("%d",&x);
    
    for(number=x;number>0;number--) 
    {    
     printf("Enter the name for insert\n");
    scanf("%s",name);
     printf("Enter the badge ID for insert\n");
    scanf("%d",&badge_id);
    }
sprintf(insertsql, "insert into Employee(Name,BadgeID) values ('%s', %d);",name,badge_id);

I got miss anything?Please guide me thanks...

---

### Post by schragge on 2013-04-18
[LIST]
[*]*sprintf* obviously should be inside the loop body as well as *sqlite3_exec* call that actually inserts the row 
[*]you should either allocate enough space for *insertsql* to hold the full command (i.e. template+name+badge_id) or use [asprintf(3)](http://manpages.ubuntu.com/manpages/quantal/en/man3/asprintf.3.html) 
[*]BadgeID was VARCHAR(10) when you were creating the table, now you treat it as an integer 
[*]*scanf("%s", [COLOR=red]&[/COLOR]name);* 
[/LIST]

---

### Post by trent.josephsen on 2013-04-18
> **schragge said:**
> scanf("%s", [COLOR=red]&[/COLOR]name);

Nope. scanf populates the array, not a pointer to it.

---

### Post by Newbie89 on 2013-04-18
> **schragge said:**
> 
[LIST]
[*]*sprintf* obviously should be inside the loop body as well as *sqlite3_exec* call that actually inserts the row 
[*]you should either allocate enough space for *insertsql* to hold the full command (i.e. template+name+badge_id) or use [asprintf(3)]("http://manpages.ubuntu.com/manpages/quantal/en/man3/asprintf.3.html") 
[*]BadgeID was VARCHAR(10) when you were creating the table, now you treat it as an integer 
[*]*scanf("%s", [COLOR=red]&[/COLOR]name);* 
[/LIST]


Thanks for the hints...
Now I have the problem...as shown below

#include <stdio.h> 
#include <sqlite3.h>
#include <stdlib.h>

static char *createsql = "CREATE TABLE Employee(" "ID INTEGER PRIMARY KEY," "Name VARCHAR(10)," "BadgeID VARCHAR(10));";
static char *insertsql; 
static char *querysql = "SELECT * FROM Employee;";
int main(void) 
{     
    
    int i,j;
    int rows, cols; 
    sqlite3 *db; 
    char *errMsg = NULL; 
    char **result; 
    char sql_lite[900]=" ";
    char name[50];
    int number,x,badge_id;

    if (sqlite3_open("test.db3", &db)) 
        { 
            return 1;
        }
    printf("Enter the number of data to be inserted\n");
    scanf("%d",&x);
    
    for(number=x;number>0;number--)   
    {    
     printf("Enter the name for insert\n");
    scanf("%s",name);
     printf("Enter the badge ID for insert\n");
    scanf("%d",&badge_id);
    sprintf(sql_lite, "insert into Employee(Name,BadgeID) values ('%s', %d);",name,badge_id);
    
    }

sqlite3_exec(db, createsql, 0, 0, &errMsg);
 
sqlite3_exec(db, insertsql, 0, 0, &errMsg);
sqlite3_exec(db, sql_lite, 0, 0, &errMsg);
 
sqlite3_get_table(db,querysql,&result, &rows, &cols, &errMsg);

 
for (i=0;i<(rows+1)*cols;i++)
    printf("%s%s", result[i], (i+1)%cols?"\t":"\n");

sqlite3_free_table(result); 
 
sqlite3_close(db); 
}
    
I can insert the data,but when i key in 2 to insert,it list out only the last insert data...below is my output:

hong@ubuntu:~/test$ gcc -o aaa aaa.c -lsqlite3
hong@ubuntu:~/test$ ./aaa
Enter the number of data to be inserted
2
Enter the name for insert
tsh
Enter the badge ID for insert
111
Enter the name for insert
tck
Enter the badge ID for insert
222
ID    Name    BadgeID
1    tck    222

can check my code?thanks...

---

### Post by schragge on 2013-04-18
```

[COLOR=red]sqlite3_exec(db, createsql, 0, 0, &errMsg);[/COLOR]
for (number=x;number>0;number--)   
    {    
     printf("Enter the name for insert\n");
     scanf("%s",name);
     printf("Enter the badge ID for insert\n");
     scanf("%d",&badge_id);
     sprintf(sql_lite, "insert into Employee(Name,BadgeID) values ('%s', %d);",name,badge_id);
     [COLOR=red]sqlite3_exec(db, sql_lite, 0, 0, &errMsg);[/COLOR]
    }

```

---

### Post by schragge on 2013-04-18
> **trent.josephsen said:**
> Nope. scanf populates the array, not a pointer to it.Yep, you are right, sorry.

---

### Post by Newbie89 on 2013-04-18
> **schragge said:**
> ```

[COLOR=red]sqlite3_exec(db, createsql, 0, 0, &errMsg);[/COLOR]
for (number=x;number>0;number--)   
    {    
     printf("Enter the name for insert\n");
     scanf("%s",name);
     printf("Enter the badge ID for insert\n");
     scanf("%d",&badge_id);
     sprintf(sql_lite, "insert into Employee(Name,BadgeID) values ('%s', %d);",name,badge_id);
     [COLOR=red]sqlite3_exec(db, sql_lite, 0, 0, &errMsg);[/COLOR]
    }

```

Thanks for ur correction...It's work:p

---

