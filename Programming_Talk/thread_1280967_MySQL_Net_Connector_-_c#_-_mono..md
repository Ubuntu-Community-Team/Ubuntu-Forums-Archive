---
title: "MySQL Net Connector - c# - mono."
date: 2009-10-02
forum: Programming Talk
---

### Post by dchurch24 on 2009-10-02
Hi all,

I have the following code: (it was actually copied from the MySQL net connector for c# site - my original code was much more complex and was also using SDL - I reverted to using the sample code in desperation but get the exact same error.)

```

 using System;
 using System.Data;
 using MySql.Data.MySqlClient;
 
 public class Test
 {
    public static void Main(string[] args)
    {
       string connectionString =
          "Server=192.168.1.7;" +
          "Database=automation;" +
          "User ID=xxxxxx;" +
          "Password=xxxxxxxxx;" +
          "Pooling=true";
       IDbConnection dbcon;
       dbcon = new MySqlConnection(connectionString);
       dbcon.Open();
       IDbCommand dbcmd = dbcon.CreateCommand();
       
       string sql =
           "SELECT firstname, lastname " +
           "FROM employee";
       dbcmd.CommandText = sql;
       IDataReader reader = dbcmd.ExecuteReader();
       while(reader.Read()) {
            string FirstName = (string) reader["firstname"];
            string LastName = (string) reader["lastname"];
            Console.WriteLine("Name: " +
                  FirstName + " " + LastName);
       }
       // clean up
       reader.Close();
       reader = null;
       dbcmd.Dispose();
       dbcmd = null;
       dbcon.Close();
       dbcon = null;
    }
 }

```

It all compiles fine, but when I attempt to open the connection, I get the following error:

```


Unhandled Exception: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.ArgumentException: Stream is not a valid .resources file, magic=0x6d783f3c
  at System.Resources.ResourceReader.ReadHeaders () [0x00017] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.Resources/ResourceReader.cs:118 
  at System.Resources.ResourceReader..ctor (System.IO.Stream stream) [0x00054] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.Resources/ResourceReader.cs:98 
  at System.Resources.ResourceSet..ctor (System.IO.Stream stream) [0x0002d] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.Resources/ResourceSet.cs:79 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x0003f] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.Reflection/MonoMethod.cs:404 --- End of inner exception stack trace ---

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00064] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.Reflection/MonoMethod.cs:414 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.Reflection/MonoMethod.cs:419 
  at System.Activator.CreateInstance (System.Type type, BindingFlags bindingAttr, System.Reflection.Binder binder, System.Object[] args, System.Globalization.CultureInfo culture, System.Object[] activationAttributes) [0x00140] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System/Activator.cs:285 
  at System.Activator.CreateInstance (System.Type type, System.Object[] args, System.Object[] activationAttributes) [0x00000] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System/Activator.cs:226 
  at System.Activator.CreateInstance (System.Type type, System.Object[] args) [0x00000] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System/Activator.cs:221 
  at System.Resources.ResourceManager.InternalGetResourceSet (System.Globalization.CultureInfo culture, Boolean Createifnotexists, Boolean tryParents) [0x000dd] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.Resources/ResourceManager.cs:356 
  at System.Resources.ResourceManager.InternalGetResourceSet (System.Globalization.CultureInfo culture, Boolean Createifnotexists, Boolean tryParents) [0x001d1] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.Resources/ResourceManager.cs:387 
  at System.Resources.ResourceManager.InternalGetResourceSet (System.Globalization.CultureInfo culture, Boolean Createifnotexists, Boolean tryParents) [0x001d1] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.Resources/ResourceManager.cs:387 
  at System.Resources.ResourceManager.GetString (System.String name, System.Globalization.CultureInfo culture) [0x00026] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.Resources/ResourceManager.cs:235 
  at MySql.Data.MySqlClient.Resources.get_PerfMonCategoryName () [0x00000] 
  at MySql.Data.MySqlClient.PerformanceMonitor..ctor (MySql.Data.MySqlClient.MySqlConnection connection) [0x00000] 
  at MySql.Data.MySqlClient.MySqlConnection.Open () [0x00000] 
  at Test.Main (System.String[] args) [0x0000d] in /home/dave/sdl_frontend/sdl_frontend/Main.cs:17 


```

I'm really stumped. The version of mysql cli is 5.2.x.x and apparently this 'bug' was fixed in an earlier version.

The odd thing is, if I run this code on a Windows machine using VS with c# it runs fine. I have run it on another xubuntu machine (the one that it is intended for) and it runs fine too. That machine is running Myth and is plugged into my TV so runs at 800x600 and is far too difficult to use for development - plus if I were to interupt Holloaks, I think the misses would kick me out on the street.

I have developed this in Mono on a Virtual Machine (xubuntu 8.10), so I can get an idea of the look and feel of the app on it's intended machine.

I have created a bridge and can see my local network perfectly through the VM - indeed, I am posting this from inside the VM, so the networking seems to be ok.

Any thoughts? I am on my 5th hour of trying to get this working and am now desperate!

---

### Post by directhex on 2009-10-02
Smells like [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=491407](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=491407) to me

It's broken in Intrepid, fixed in Jaunty & above

---

### Post by dchurch24 on 2009-10-03
Ahh what a pain!

That's what I was afraid of!

Oh well, upgrade here I come!

Thank you.

---

### Post by Jordanwb on 2009-12-11
What package did you install to get the Mysql classes for Mono? I want to use MySQL with my C# program aswell.

---

