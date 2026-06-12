---
title: "Using sqlite and C programming to insert data"
date: 2013-04-03
forum: Programming Talk
---

### Post by Newbie89 on 2013-04-03
Can help me see the problem?Below is my code

Create.sql

create table student (No integer primary key autoincrement, Date1 varchar(20), Time varchar(10),Name varchar(10),
Id_no integer);

insert into student (Date1 , Time, Name, Id_no) values
('10/10/2012', '9.35am', 'Kean Heng', '091021434');


insert.c

```

# include <stdio.h>
# include <sqlite3.h>
# include <stdlib.h>

int main(void)
{
sqlite3 *conn;
sqlite3_stmt *res;
int     error = 0;
int     rec_count = 0;
const char     *errMSG;
const char     *tail;
char sql_lite[900]=" ";

char name[50];
int date=0,month=0,year=0,matrix_number=0,number,x;
float time =0;
error = sqlite3_open("hong.sl3", &conn);
if (error)
{
printf("Can not open database");

}


printf("Enter the number of data to be inserted\n");
scanf("%d",&x);

for(number=x;number>0;number--) 
{ 
printf("Enter the name of the student for insert\n");
scanf("%s",name);
printf("Enter the date, month, year of the student\n");
scanf("%d%d%d",&date,&month,&year);
printf("Enter the time \n");
scanf("%f",&time);
printf("Enter the matrix number of the student for insert\n");
scanf("%d",&matrix_number);
}

sprintf(sql_lite, "insert into student values ('%d/%d/%d','%.2fam','%s',%d);",date,month,year,time,name,matrix_number);
error = sqlite3_exec(conn, sql_lite, 0, 0, 0);
error = sqlite3_prepare_v2(conn, "select * from student order by No",1000, &res, &tail);


if (error != SQLITE_OK)
{
printf("We did not get any data!");
exit(0);

}

printf("=======================================\n");

while (sqlite3_step(res) == SQLITE_ROW)
{
printf("%d|", sqlite3_column_int(res, 0));
printf("%s|", sqlite3_column_text(res, 1));
printf("%s|", sqlite3_column_text(res, 2));
printf("%s|", sqlite3_column_text(res, 3));
printf("%u\n", sqlite3_column_int(res, 4));


rec_count++;
}

printf("=======================================\n");
printf("We received %d records.\nTotal rows=%d\n", rec_count,SQLITE_ROW);

sqlite3_finalize(res);

sqlite3_close(conn);

return 0;
}
```

---

### Post by Newbie89 on 2013-04-03
My problem now is I can get the create.sql from c language,but I can't insert the data in the database.

Below is my output:
```

hong@ubuntu:~/Check$ sqlite3 hong.sl3<create.sql
hong@ubuntu:~/Check$ gcc -o insert insert.c -lsqlite3
hong@ubuntu:~/Check$ ./insert
Enter the number of data to be inserted
1
Enter the name of the student for insert
John
Enter the date, month, year of the student
12 12 2012
Enter the time
12.00
Enter the matrix number of the student for insert
091232432
=======================================
1|10/10/2012|9.35am|Kean Heng|91021434
=======================================
We received 1 records.
Total rows=100
hong@ubuntu:~/Check$
```

---

### Post by r-senior on 2013-04-03
Is the code in post #1 your latest, i.e. are you still getting the error about autoincrement?

Did you intend to use an autoincrement primary key?

[https://www.sqlite.org/autoinc.html](https://www.sqlite.org/autoinc.html)

It might help if you posted the SQL used to create the table.

---

### Post by Newbie89 on 2013-04-03
Ya,r-senior...It is the latest one...the autoincrement can work for create the table in sqlite database.But cannot show the result after insert.Can you point out the mistake that I make...I have stuck for several day...Thanks

---

### Post by spjackson on 2013-04-03
Compare
> 
[COLOR=#000000]insert into student (Date1 , Time, Name, Id_no) values[/COLOR]
[COLOR=#000000]('10/10/2012', '9.35am', 'Kean Heng', '091021434');[/COLOR]

and
> 
sprintf(sql_lite, "insert into student values ('%d/%d/%d','%.2fam','%s',%d);",date,month,year,time,name,matrix_number);

If the mistake is not obvious, print out the statement before you execute it, then copy and paste it into a sqlite3 session.

---

### Post by Newbie89 on 2013-04-03
[**[COLOR=#000000]spjackson[/COLOR]**]("http://ubuntuforums.org/member.php?u=1128302") Thanks for the hints...^^
After check,modify the stament become as below:

sprintf(sql_lite, "insert into student (Date1 , Time, Name, Id_no) values ('%d/%d/%d','%.2fam','%s', %d);",date,month,year,time,   name,matrix_number);

Finally can insert the data...Thanks again.:KS

---

