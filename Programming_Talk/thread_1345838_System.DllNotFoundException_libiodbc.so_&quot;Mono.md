---
title: "System.DllNotFoundException: libiodbc.so &quot;Mono&quot;"
date: 2009-12-04
forum: Programming Talk
---

### Post by shafi on 2009-12-04
Dear All,
I am using mono develop and I'm getting an exception while retrieving an image from mysql server.
Actually the exception is because of the OdbcConnection that I have used for connecting to mysql database.
can some one help me , how can I resolve this exception?
I visit some bug reports but they didn't solve my problem.

Exception:
```

System.DllNotFoundException: libiodbc.so
at (wrapper managed-to-native) System.Data.Odbc.libodbc:SQLAllocHandle(System.Data.Odbc.OdbcHandleType,intptr,intptr&)
at System.Data.Odbc.OdbcConnection.Open () [0x00000] 

```

method for retrieving image from mysql Database:
```

public static byte[] getImage(){
    OdbcConnection objConn =new OdbcConnection
    ("DRIVER={MySQL ODBC 5.1 Driver};Database=ITCOdb;SERVER=localhost; 
    USER=shafi;PASSWORD=password;OPTION=3;");
    string strSql = "SELECT * FROM images";
    DataSet ds = new DataSet("Image");
    OdbcDataAdapter tempAP = new OdbcDataAdapter(strSql, objConn);
    OdbcCommandBuilder objCommand = new OdbcCommandBuilder(tempAP);
    tempAP.Fill(ds, "Table");
    try{
        objConn.Open();
        byte[] buffer = (byte[])ds.Tables["Table"].Rows[0]["image"];
        return buffer;
     }
     catch { objConn.Close(); return null; }
        finally { objConn.Close(); 
     }
}

```

**Note:** If I use the IdbConnection for connecting to mysql then i am getting no exception , but actually I couldn't figure it out how to retrieve an image via the IdbConnection.

This is my IdbConnection:
```

string sql = String.Format("Sql statement here");
using(IDbConnection dbcon = openConnection())
// create a database command
using(IDbCommand dbcmd = dbcon.CreateCommand()){
 // execute it
 dbcmd.CommandText = sql;
 dbcmd.ExecuteNonQuery();                
 }

```

---

### Post by Zugzwang on 2009-12-04
Maybe you need to install some additional package?

[http://packages.ubuntu.com/search?searchon=contents&keywords=libiodbc.so&mode=exactfilename&suite=karmic&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libiodbc.so&mode=exactfilename&suite=karmic&arch=any)

---

### Post by shafi on 2009-12-04
> **Zugzwang said:**
> Maybe you need to install some additional package?

[http://packages.ubuntu.com/search?searchon=contents&keywords=libiodbc.so&mode=exactfilename&suite=karmic&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libiodbc.so&mode=exactfilename&suite=karmic&arch=any)

Hi,
Thanks for the reply , the exception been resolved now.
but now I am getting another exception.
I have also follow this tutorial [https://help.ubuntu.com/community/ODBC](https://help.ubuntu.com/community/ODBC) , but it doesn't solve the problem.
```

System.Data.Odbc.OdbcException: ERROR [I

```

---

