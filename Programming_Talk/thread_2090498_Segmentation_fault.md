---
title: "Segmentation fault"
date: 2012-12-02
forum: Programming Talk
---

### Post by MTariq on 2012-12-02
Code in my DataBase.cpp file:

```

#include "DataBase.h"
 
#include <sqlite3.h>
#include <string.h>
#include <wx/msgdlg.h>
 
 
bool CanClose(void)
{
    sqlite3 *Sqlite;
    sqlite3_stmt *sqlstmt;
    char *result;
    if(sqlite3_open("SysConfig",&Sqlite)==SQLITE_OK)
    {
        sqlite3_prepare(Sqlite,"SELECT config_value FROM configuration WHERE config_id = 1;",-1,&sqlstmt,NULL);
        sqlite3_step(sqlstmt);
        result = (char*)sqlite3_column_text(sqlstmt,0);
        sqlite3_close(Sqlite);
        if(strcmp(result,"YES")==1)    //Error Here
            return true;
        else
            return false;
    }
    else
    {
        wxMessageBox(_("Cannot Find System File!"),_("Error!"));
        sqlite3_close(Sqlite);
        return false;
    }
}

```
My program was behaving abruptly..
When I started debuging the line indicated above (line 19) is giving some error as

program recieved signal SIGSEGV, Segmentation fault.

further dissasembly of the statement show error at a assembly instruction

call 0x80500b0 <strcmp@plt>

Please Help.
I am using CodeBlocks with GCC

---

### Post by MadCow108 on 2012-12-02
I don't know the sqlite api very well but my guess is that either the result string is deleted by sqlite3_close(Sqlite) before you use it or it is NULL in the first place

also don't check the return of strcmp against 1, it is not defined to do that and also probably won't in all cases you expect it too.
only compare against equal zero or greater/smaller

---

### Post by MTariq on 2012-12-02
> **MadCow108 said:**
> I don't know the sqlite api very well but my guess is that either the result string is deleted by sqlite3_close(Sqlite) before you use it or it is NULL in the first place

also don't check the return of strcmp against 1, it is not defined to do that and also probably won't in all cases you expect it too.
only compare against equal zero or greater/smaller

I see....

Well using strcpy would Help?

---

### Post by Zugzwang on 2012-12-02
> **MTariq said:**
> I see....

Well using strcpy would Help?

Too complicated (and will introduce a memory leak, as you would have to free the the string again before returning, and there goes your old problem). Something like this would be more appropriate:

```

result = (char*)sqlite3_column_text(sqlstmt,0);
bool result = (strcmp(result,"YES")==1);
sqlite3_close(Sqlite);
return result;

```

In other words: First compute your result, then clean up, and finally return the result, and everything is in order.

---

### Post by MTariq on 2012-12-03
Not working even..
Seems that
result = (char*)sqlite3_column_text(sqlstmt,0);

is returning nothing. And result is empty..
I found this bug by printing it on the message box...
But why is it so.. I mean why 
result = (char*)sqlite3_column_text(sqlstmt,0);
is returning an empty memory space....

---

### Post by PaulM1985 on 2012-12-03
After having a read of the documentation it would be interesting to know what "sqlite3_step" returned.  The information here ([http://www.sqlite.org/c3ref/step.html](http://www.sqlite.org/c3ref/step.html)) indicates that there are a few different options.  Maybe you are failing and don't know about it.

Do you know if the values in the column you are looking to return are strings?  Are you definitely returning the correct datatype?  Here is some more documentation: [http://www.sqlite.org/c3ref/column_blob.html](http://www.sqlite.org/c3ref/column_blob.html)

In addition, the first link implies that there are newer versions of the "prepare" function and the one that you are using could be a legacy version.  It would be worth updating to use the new interface.

Paul

---

### Post by MTariq on 2012-12-03
Putting Some More checks revealed that sqlite3_prepare() is returning a SQLITE_ERROR where
#define SQLITE_ERROR 1 /* SQL error or missing database */

---

### Post by muteXe on 2012-12-03
Well there you go then. Nothing to do with your code.

well, not your C. Is that sql statement definitely correct?

---

### Post by MTariq on 2012-12-03
I copied the statement from my c Code, pasted it in [SQLiteman]("http://sqliteman.com/"). Statement is working well and result is as desired!

---

