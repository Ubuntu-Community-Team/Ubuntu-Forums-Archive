---
title: "C problem with parsing date with strptime"
date: 2010-03-16
forum: Programming Talk
---

### Post by matmatmat on 2010-03-16
I am using a SQlite database to hold some dates, I have made a program to enter them and get them out. But when they are entered they are changed to a completely different date:
```

[matio@myhost CDoot]$ ./cdoot -cdu 1 "1/3/2010"
 Due 10/1/2000 Due 1/2/2000 Due 13/2/2000 Due 14/2/2000 Due 5/3/2000Todo changed
[matio@myhost CDoot]$ sqlite3 todo.sqlite3 
SQLite version 3.6.22
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite> select * from todos;
1|Program this|Basic functions (add, remove, list, change)|1|100|10/2/2010
2|Program this|Allow users to export to ods|3|5|5/4/2010
3|Program this|Allow users to export to txt|2|0|1/3/2010
4|Program this|Allow users to filter list (by project/priority)|2|100|13/3/2010
5|Program this|Add date field, check if overdue|2|90|14/3/2010
sqlite> [matio@myhost CDoot]$ ./cdoot -l
Program this
  0 | Basic functions (add, remove, list, change)        | 100% done | Due 10/1/2000
  1 | Allow users to export to txt                       |   0% done | Due 1/2/2000
  2 | Allow users to filter list (by project/priority)   | 100% done | Due 13/2/2000
  3 | Add date field, check if overdue                   |  90% done | Due 14/2/2000
  4 | Allow users to export to ods                       |   5% done | Due 5/3/2000
Project 59% done
[matio@myhost CDoot]$ # the -l is listing the data, the -cdu is changing the dates

```
Does anyone know what is going on here? Help is appreciated! :)

```

void changeDate(int id, char *date){
	char myq[200];
	sprintf(myq, "update todos set date=\"%s\" where id=%i;", date, id);
	retval = sqlite3_exec(handle, myq, 0, 0, 0);
	if(retval == 0)
		printf("Todo changed\n");	
}

int* list(int print){
	int cols = sqlite3_column_count(stmt);

	char project[20];
	int pdone = 0;
	int pcount = 0;
	int id = 0;
	int ids[100];
	while(1){
		retval = sqlite3_step(stmt);
		if(retval == SQLITE_ROW){
			for(int col=0 ; col<cols;col++){
				const char *val = (const char*)sqlite3_column_text(stmt,col);
				char *cname = sqlite3_column_name(stmt,col);

				if(strcmp(cname, "project") == 0){
					if(strcmp(val, (const char*)project) != 0){
						if(pcount != 0){	
							pdone /= pcount;
							if(print)
								printf("\E[34m\033[1mProject %i%% done\033[0m\n\n", pdone);
							pdone = pcount = 0;
						}
						strcpy(project, val);
						if(print)
							printf("\E[34m\033[1m%s\033[0m\n", val);
					}
					if(strcmp(sqlite3_column_text(stmt,col+2), "1") == 0){
						if(print)
							printf("\E[31m\033[1m");
					}
					else if(strcmp(sqlite3_column_text(stmt,col+2), "2") == 0){
						if(print)
							printf("\E[33m\033[1m");
					}else if(strcmp(sqlite3_column_text(stmt,col+2), "3") == 0){
						if(print)
							printf("\E[32m\033[1m");						
					}
					ids[id++] = atoi(sqlite3_column_text(stmt,col-1));
					if(print)
						printf("  %i | ", id-1);
				}else if(strcmp(cname, "id") != 0){
					if(strcmp(cname, "summary") == 0){
						if(print)
							printf("%-50s | ", val);
						
					}else if(strcmp(cname, "done") == 0){
						pcount++;
						pdone += atoi(val);
						if(print)
							printf("%3s%% done |", val);
					}else if(strcmp(cname, "date") == 0){
						if(val != NULL){
							struct tm due;
							time_t ltime2;
							struct tm *ltime;
							ltime2=time(NULL);
							ltime = localtime(&ltime2);
							strptime(val, "%d/%m/%Y", &due);
							due.tm_year += 1890;
							ltime->tm_year += 1890;
							if((due.tm_year >= ltime->tm_year && due.tm_mon >= ltime->tm_mon) &&
										(due.tm_mon >= ltime->tm_mon && due.tm_mday >= ltime->tm_mday) &&
										(due.tm_year >= ltime->tm_year && due.tm_mday >= ltime->tm_mday)){
								if(print)
									printf(" Overdue");
							}else{
								printf(" Due %i/%i/%i", due.tm_mday, due.tm_mon, due.tm_year);
							}
						}
					}
				}
			}
			if(print){
				printf("\033[0m");
				printf("\n");
			}			
		}else if(retval == SQLITE_DONE){
			if(pcount != 0){	
				pdone /= pcount;
				if(print)
					printf("\E[34m\033[1mProject %i%% done\033[0m\n", pdone);
			}
			break;
		}else{
			printf("Some error encountered\n");
			exit(-1);
		}
	}
	return ids;	
}

```

---

### Post by MindSz on 2010-03-16
I believe you need to add 1900 and not 1890 to get the correct date (and maybe add 1 to month...can't remember).

What kind of difference are you getting in the dates?

---

### Post by matmatmat on 2010-03-16
Thanks for replying, when I tried changing the date of one of them to the "1/3/2010", in the database and the program said "10/1/2010" (after making your change).

---

### Post by MadCow108 on 2010-03-16
you also have to add one to tm_mon
[http://www.cplusplus.com/reference/clibrary/ctime/tm/](http://www.cplusplus.com/reference/clibrary/ctime/tm/)

check what value the variable val has before passing it into strptime
I guess something is wrong there

---

### Post by dwhitney67 on 2010-03-16
matmatmat, matmatmat, matmatmat -

Learn to test your programming issues with smaller programs...

```

#include <time.h>
#include <stdio.h>

int main(void)
{
   const char* due_date = "1/3/2010";   // 01-Mar-2010
   const char* format   = "%d/%m/%Y";
   struct tm   tm;

   strptime(due_date, format, &tm);

   printf("The date   = %s\n", due_date);
   printf("format     = %s\n", format);
   printf("tm.tm_mday = %d\n", tm.tm_mday);
   printf("tm.tm_mon  = %d\n", tm.tm_mon);
   printf("tm.tm_year = %d\n", tm.tm_year);

   return 0;
}

```

Results:
```

The date   = 1/3/2010
format     = %d/%m/%Y
tm.tm_mday = 1
tm.tm_mon  = 2
tm.tm_year = 110

```
I do have some pity for you because it appears that the man-page for strptime() *appears* incorrect; well, at least on my 9.10 system.

Here are the *possible* mistakes:
```

...

%m     The month number (1-12).

...

%Y     The year, including century (for example, 1991).

```

You might (probably will) get better luck referencing the man-page for asctime(), which does list the proper documentation for struct tm.

I believe MindSz and MadCow108 derived their responses from their familiarity with asctime() or related functions.

P.S.  Maybe on the flip-side of the 'coin', the author(s) of the strptime() man-page were referring to the fields within the time string, not the resulting values within the struct tm.  Either they were clear, and I missed that point, or as I stated earlier, they were wrong/misleading.

P.S. #2  I beginning to believe that it is time for me to go to bed, and more importantly that the man-page for strptime() is actually correct; unfortunately it does not delve into the details of the struct tm fields.

---

