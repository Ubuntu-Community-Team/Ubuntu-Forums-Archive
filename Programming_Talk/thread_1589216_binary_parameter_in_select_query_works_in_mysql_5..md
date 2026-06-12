---
title: "binary parameter in select query works in mysql 5.0 but not 5.1"
date: 2010-10-06
forum: Programming Talk
---

### Post by cputoaster on 2010-10-06
(this is a crosspost from the mysql forums, as this might involve ubuntu specific problems)

Hi there,

I have a problem changing from an old 5.0 debian installation to a current 5.1.41-3ubuntu12.6. I am using the most recent connector (6.3.4) under mono 2.4.4~svn151842-1ubuntu4.

The code below used to work fine with mysql 5.0, now it returns with an exception (see below).

Any ideas? I know I could just use "?phex > hex(t1.f2)" and insert the phex parameter as a hexadecimal string, but that will result in really bad, non-indexable performance as the hex value will have to be calculated all the time.

I also checked that sql_mode is not set to NO_BACKSLASH_ESCAPES, just to be sure (even if its clear from the debug message, that it actually escapes, which is fine).

Cheers,
Andres


f2 is a binary(16) field.


```
cmd.CommandText = "select f1 from t1 where ?p > t1.f2";

MySqlParameter param = cmd.CreateParameter();
param.DbType = DbType.Binary;
param.ParameterName = "?p";
param.Value = new byte[] {0x80, 0x00, 0x12, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x12, 0x10, 0x00, 0x00, 0x00, 0x00 };
cmd.Parameters.Add(param);

MySqlDataAdapter da = new MySqlDataAdapter((MySqlCommand)cmd);

DataSet ds = new DataSet();
da.Fill(ds);
```


->

```
Unhandled Exception: MySql.Data.MySqlClient.MySqlException: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 't1 where _binary '€\0\0\0\0\0\0\0\0\0\0\0\0' > t1.f2' at line 1
at MySql.Data.MySqlClient.MySqlStream.ReadPacket () [0x00000]

```

---

