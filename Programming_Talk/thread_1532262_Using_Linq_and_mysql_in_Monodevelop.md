---
title: "Using Linq and mysql in Monodevelop"
date: 2010-07-16
forum: Programming Talk
---

### Post by margemoosh on 2010-07-16
i want to use Linq and mysql in monodevelop but i cant!
when i use generate linq class from tools>database and select a connection and press ok it gave me this error:
i use monodevelop 2.4.
if i need to install anything else or doing some configuration please help me with them i dont have enough information about monodevelop
thanks in advance

```
MonoDevelop.Database.Sql.SqlMetalExecException: sqlmetal failed:ByteFX.Data.MySqlClient.MySqlException: Client does not support authentication protocol requested by server; consider upgrading MySQL client
  at ByteFX.Data.MySqlClient.Driver.ReadPacket () [0x00000] in <filename unknown>:0 
  at ByteFX.Data.MySqlClient.Driver.Authenticate (System.String userid, System.String password, Boolean UseCompression) [0x00000] in <filename unknown>:0 
  at ByteFX.Data.MySqlClient.Driver.Open (ByteFX.Data.MySqlClient.MySqlConnectionString settings) [0x00000] in <filename unknown>:0 
  at ByteFX.Data.MySqlClient.MySqlInternalConnection.Open () [0x00000] in <filename unknown>:0 
  at ByteFX.Data.MySqlClient.MySqlPool.CreateNewPooledConnection () [0x00000] in <filename unknown>:0 
  at ByteFX.Data.MySqlClient.MySqlPool.GetPooledConnection () [0x00000] in <filename unknown>:0 
  at ByteFX.Data.MySqlClient.MySqlPool.GetConnection () [0x00000] in <filename unknown>:0 
  at ByteFX.Data.MySqlClient.MySqlPoolManager.GetConnection (ByteFX.Data.MySqlClient.MySqlConnectionString settings) [0x00000] in <filename unknown>:0 
  at ByteFX.Data.MySqlClient.MySqlConnection.Open () [0x00000] in <filename unknown>:0 

```

---

### Post by ph8 on 2011-02-08
Hi!

Did you ever get this solved? It's 7 months on and i'm getting the same problem.

From what I gather it's sqlmetal using something which uses bytefx (i.e. the wrong/no longer supported library)

Would love a fix/workaround!

---

### Post by lives4him06 on 2011-03-22
I am getting the same error, any luck?

---

