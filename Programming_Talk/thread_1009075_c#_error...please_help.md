---
title: "c# error...please help"
date: 2008-12-12
forum: Programming Talk
---

### Post by gg_creature on 2008-12-12
im kind of new to c# and i have a error in my code and id don't know what i did wrong.
the error i receive is the following: 
System.NullReferenceException: Object reference not set to an instance of an object.

my code:
```
 string st, my_query;
        int[] arr = new int[6];
        DataSet ds = new DataSet();
        DataTable dt = new DataTable();
        DataRow dr = dt.NewRow();
        st = @"Provider=Microsoft.jet.oledb.4.0;Data Source=" +
            Server.MapPath("~/App_Data/db1.mdb");

        my_query = "Select * from Shifts";

        OleDbConnection conn = new OleDbConnection(st);

        conn.Open();

        OleDbCommand cmmd = new OleDbCommand(my_query, conn);

        OleDbDataAdapter da = new OleDbDataAdapter(cmmd);
        
         da.Fill(ds);
         dt = ds.Tables["Shifts"];
         dr = dt.Select("#" + a.shift_dates + "#")[0];
        for (int x = 1; x < 7; x++)
        {
            if (int.Parse(dr.ItemArray.GetValue(x).ToString()) != 0)
                arr[x - 1] = 1;
        }
        conn.Close();

        return arr;
```

thx for the help :)

---

### Post by jespdj on 2008-12-12
Look carefully at the error message. It tells you in which line the error occurs. Then look at that line, and find out what is **null** there that isn't supposed to be **null**.

---

### Post by gg_creature on 2008-12-12
i run the code through a differnt one so the line the error occurs is on the line in which i call for this code...so i dont know what line isn't coded properly

---

### Post by Majorix on 2008-12-12
Try writing a testing mechanism inside THAT source file and see what line raises an error.

I believe you *might* be having difficulties while connecting to the database so you get a Null Reference.

---

