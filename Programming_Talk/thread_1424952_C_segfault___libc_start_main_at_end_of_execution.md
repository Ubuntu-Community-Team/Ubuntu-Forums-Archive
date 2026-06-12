---
title: "C segfault: __libc_start_main at end of execution"
date: 2010-03-08
forum: Programming Talk
---

### Post by matmatmat on 2010-03-08
Can someone help me please, when I run my program below it gives a SIGSEGV Segmentation fault at the end of execution. When I backtraced in gdb it said:
```

#0  0xb7e05b02 in __libc_start_main () from /lib/libc.so.6
Cannot access memory at address 0x6b726f5b

```

Help is appreciated :-)

```

#include <stdio.h>
#include <string.h>
#include "proglib.h"

int main(int argc, const char *argv[]){
	setupSQLite();	
	++argv;
	--argc;
	for(; argc-->0; ++argv){
		if(strcmp(*argv, "-l") == 0){
			listAll();
		}
	}
	killSQLite();
	return 0;
}

//-----------------------------------------------
// proglib.c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <sqlite3.h>
#include "cdootlib.h"

int retval           = 0;
int q_cnt            = 5;
int q_size           = 150;
int ind              = 0;
char **queries       = 0;
sqlite3_stmt *stmt   = 0;
sqlite3      *handle = 0;


void setupSQLite(){
	queries = malloc(sizeof(char) * q_cnt * q_size);
	retval = sqlite3_open("todo.sqlite3", &handle);
	if(retval){
		printf("Database connection failed\n");
		exit(-1);
	}

	char create_table[200] = "CREATE TABLE IF NOT EXISTS todos (id INTEGER PRIMARY KEY, project TEXT, summary TEXT, done INTEGER);";
	sqlite3_exec(handle,create_table,0,0,0);
}

void listAll(){
	queries[ind++] = "SELECT * FROM todos order by project, done desc;";
	retval = sqlite3_prepare_v2(handle,queries[ind-1],-1,&stmt,0);
	if(retval){
	    printf("Selecting data from DB Failed\n");
		exit(-1);
	}
	int cols = sqlite3_column_count(stmt);

	char *project;
	while(1){
		retval = sqlite3_step(stmt);
		if(retval == SQLITE_ROW){
			for(int col=0 ; col<cols;col++){
				const char *val = (const char*)sqlite3_column_text(stmt,col);
				char *cname = sqlite3_column_name(stmt,col);

				if(strcmp(cname, "project") == 0){
					if(strcmp(val, (const char*)project) != 0){
						strcpy(project, val);
						printf("%s\n  %s | ", project, (const char*)sqlite3_column_text(stmt,col-1));
					}else
						printf("  %s | ", (const char*)sqlite3_column_text(stmt,col-1));
				}else if(strcmp(cname, "id") != 0){
					if(strcmp(cname, "done") != 0)
						printf("%-30s | ", val);
				}
			}
			printf("\n");
		}
		else if(retval == SQLITE_DONE){
			break;
		}else{
			printf("Some error encountered\n");
			exit(-1);
		}
	}
}

void killSQLite(){
	sqlite3_close(handle);
	free(queries);
}

```

---

### Post by dwhitney67 on 2010-03-08
In listAll(), it would appear as if the following variable is never initialized.  Oh the horror!
```

char *project;

```

---

