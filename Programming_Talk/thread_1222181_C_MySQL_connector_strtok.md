---
title: "C MySQL connector strtok"
date: 2009-07-24
forum: Programming Talk
---

### Post by stuffradio on 2009-07-24
I'm trying to use the C mysql connector to insert data from comma delimited data.

The string is separated liked this:
strtok("," str);

Does anyone know how to take the different results from the strtok function and separate it into different fields?

---

### Post by jero3n on 2009-07-24
> **stuffradio said:**
> I'm trying to use the C mysql connector to insert data from comma delimited data.

The string is separated liked this:
strtok("," str);

Does anyone know how to take the different results from the strtok function and separate it into different fields?

this could do the job 

```
#include <string.h>
#include <stdio.h>

#define MAX_STR_LEN 50
#define MAX_COLUMNS 50

int main()
{

    char data[50] = "foo,bar,123,42", columns[MAX_COLUMNS][MAX_STR_LEN], *p;
    int i = 0, k;

    p = strtok(data, ",");
    while(p)
    {
        strncpy(columns[i++], p, MAX_STR_LEN);
        p = strtok(NULL, ",");
    }

    for(k=0; k<i; k++) printf("%s\n", columns[k]);
    return 0;
}

```

However beware if there is any escape character in your file, when the comma ',' is part of the data and not used as a separator

---

### Post by stuffradio on 2009-07-24
Here is my code now

```

/* Simple C program that connects to MySQL Database server*/
#include "/mnt/ext/opt/mysql/include/mysql/mysql.h"
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_STR_LEN 100
#define MAX_COLUMNS 100

main() {
   int i = 0, k;
   MYSQL *conn;
   MYSQL_RES *res;
   MYSQL_ROW row;

   char *server = "xxxx";
   char *user = "xxx";
   char *password = "xxxx"; /* set me first */
   char *database = "xxx";
   char str[100] = "07/24/09,310640101057789,ON,OFF,ON,ON,OFF,513,2,7,0,0", columns[MAX_COLUMNS][MAX_STR_LEN], *p;
   char * pch;
   char strvals[] = "";
   const int strsize = sizeof(str);
   conn = mysql_init(NULL);

   /* Connect to database */
   if (!mysql_real_connect(conn, server,
         user, password, database, 0, NULL, 0)) {
      fprintf(stderr, "%s\n", mysql_error(conn));
      exit(1);
   }

   /* send SQL query */
   if (mysql_query(conn, "show tables")) {
      fprintf(stderr, "%s\n", mysql_error(conn));
      exit(1);
   }

   res = mysql_use_result(conn);

   /* output table name */
   printf("MySQL Tables in mysql database:\n");
   while ((row = mysql_fetch_row(res)) != NULL)
      printf("%s \n", row[0]);

   

p = strtok (str, ",");
while (p)
{
strncpy(columns[i++],p,MAX_STR_LEN);
p = strtok(NULL, ",");
}
printf ("%s\n", columns[3]);

mysql_query(conn,"INSERT INTO `systemreports` (ReportDate, IDNumber, PowerStatus, Telemetry, WaterPumpA, WaterPumpB, AirPumpA, AirPumpB, DailyWaterUse, WaterQuality, UVStatus, OtherStatus) VALUES(columns[0], columns[1], columns[2], columns[3], columns[4], 'columns[5], columns[6], columns[7], columns[8], columns[9], columns[10], columns[11])");


/* close connection */
   mysql_free_result(res);
   mysql_close(conn);
return 0;
}

```

It won't let me insert data like that, I can insert data if I use commas around the values, but that's not what I want to do.

Any ideas how I can insert array values?

---

### Post by MadCow108 on 2009-07-24
that won't work in C.
you will have to build your query string with snprintf.
snprintf(dest_string,dest_size,"stuff (%s,%s) more stuff",column[0],column[1]);

if you don't need to quote your comma seperated values then you could directly insert "str" into the query string without tokenizing.

---

### Post by stuffradio on 2009-07-24
Can you show me an example of what you mean using some of my variables? or how I would do it and insert it in the mysql query?

---

