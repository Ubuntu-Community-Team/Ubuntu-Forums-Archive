---
title: "C# / Mono / MySQL library problems"
date: 2006-05-15
forum: Programming Talk
---

### Post by Kethinov on 2006-05-15
I'm working on a C# app compiled with Mono that does some work with MySQL. This development is being done in MonoDevelop on Ubuntu Dapper. When I try to import the appropriate libraries in my C# app, I get errors pertaining to the following imports:

```

using System.Data;
using MySql.Data.MySqlClient;

```

The errors are as follows:

```

The type or namespace name `System.Data' could not be found. Are you missing a using directive or an assembly reference?(CS0246)
The type or namespace name `Data' does not exist in the namespace `System'. Are you missing an assembly reference?(CS0234)
The type or namespace name `MySql.Data.MySqlClient' could not be found. Are you missing a using directive or an assembly reference?(CS0246)
The type or namespace name `MySql' could not be found. Are you missing a using directive or an assembly reference?(CS0246)

```

What am I missing?

---

### Post by aaboelela on 2009-05-22
Kethinov,

check this: [http://forums.mysql.com/read.php?47,160875,166507#msg-166507](http://forums.mysql.com/read.php?47,160875,166507#msg-166507)

Add this to your Web.config 
 
<compilation debug="true"> 
     <assemblies> 
              <add assembly="MySql.Data, Version=5.0.7.0, Culture=neutral, PublicKeyToken=C5687FC88969C44D"/> 
     </assemblies> 
</compilation>

But if your version is say: 5.0.9.0 then you have to write the right version.

Check it at the GAC, 
> 
cd /usr/lib/mono/gac/MySql.Data
lsthen you will get something like: 
> 5.0.9.0__c5687fc88969c44d which is the <version number>_<public key>

If your MySql.Data.dll is not registered in the GAC, then goto the directory of the file, then type:
> gac -i MySql.Data.dll


---

### Post by directhex on 2009-05-23
In MonoDevelop, you need to make sure you have references set. In the Project Pane, right click on References, then Edit References - make sure System.Data and MySql are enabled.

---

