---
title: "Problems with Mono, C# and MySQL"
date: 2007-02-01
forum: Programming Talk
---

### Post by gynther on 2007-02-01
Hi, I've written a small program in C# that connects to a MySql database and gets/sets records there. It's just a skeleton right now to learn how to use Mono/C#/MySql together. It's not working swimmingly ;)

I use MonoDevelop to write the code in, I have created a project, added MySql.Data.dll and System.Data.dll under references and have written the code to connect and retrieve information from the database as it's described [here]("http://www.mono-project.com/MySQL")

I get the following errors and searching for them on Google or here renders nothing. If anyone could point me towards whats causing this I'd be grateful. I've uploaded the source files if you need them.

[COLOR="Red"]Errormessages[/COLOR]
Description=Could not load type 'System.Data.Common.DbConnection' from assembly 'System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'.(Exception: System.TypeLoadException)

Description=Could not load type 'System.Data.Common.DbConnection' from assembly 'System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'.(.TypeLoadException)

Description=libBOcrm/DBConn.cs(18,10):(that caused the problem begin at)

Thanks in advance. Let me know if you need anything else.

---

### Post by LordHunter317 on 2007-02-01
Can you show us a build log or somehting?  I'm wondering if the references weren't properly supplied.  Are you using System.Data.dll and Mysql.DAta.dll from the GAC or are they in your project dir?

---

### Post by LordHunter317 on 2007-02-01
As a completly unrelated note, use using() to ensure proper resource management.  I have some code for running SQL commands that uses delegates that ensures proper resource management in most situations.

---

### Post by gynther on 2007-02-01
> **LordHunter317 said:**
> As a completly unrelated note, use using() to ensure proper resource management.  I have some code for running SQL commands that uses delegates that ensures proper resource management in most situations.

Um, didn't quite get what you meant by that. Could you clarify it a bit?

I'm referencing System.Data.dll from the GAC and the MySql.Data.dll is referenced to the file I have in the build directory. So "System" is GAC and "MySql" is local.

As for a build log this is what I can get from MonoDevelop:

Building Solution libBOcrm

Building Project: libBOcrm Configuration: Debug
Performing main compilation...
Exception caught by the compiler while compiling:
   Block that caused the problem begin at: /home/christian/projekt/libBOcrm/libBOcrm/DBConn.cs(18,10):
                     Block being compiled: [/home/christian/projekt/libBOcrm/libBOcrm/DBConn.cs(19,3):,/home/christian/projekt/libBOcrm/libBOcrm/DBConn.cs(29,3):]
System.TypeLoadException: Could not load type 'System.Data.Common.DbConnection' from assembly 'System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'.


** (/usr/lib/mono/1.0/mcs.exe:16524): WARNING **: The class System.Data.Common.DbConnection could not be loaded, used in System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

Unhandled Exception: System.TypeLoadException: Could not load type 'System.Data.Common.DbConnection' from assembly 'System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'.
  at <0x00000> <unknown method>
  at Mono.CSharp.NamespaceEntry.Error_NamespaceNotFound (Location loc, System.String name) [0x00000] 
  at Mono.CSharp.SimpleName.ResolveAsTypeStep (IResolveContext ec, Boolean silent) [0x00000] 
  at Mono.CSharp.Expression.ResolveAsBaseTerminal (IResolveContext ec, Boolean silent) [0x00000] 
  at Mono.CSharp.Expression.ResolveAsTypeTerminal (IResolveContext ec, Boolean silent) [0x00000] 
  at Mono.CSharp.New.DoResolve (Mono.CSharp.EmitContext ec) [0x00000] 
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext ec, ResolveFlags flags) [0x00000] 
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext ec) [0x00000] 
  at Mono.CSharp.Assign.DoResolve (Mono.CSharp.EmitContext ec) [0x00000] 
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext ec, ResolveFlags flags) [0x00000] 
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext ec) [0x00000] 
  at Mono.CSharp.ExpressionStatement.ResolveStatement (Mono.CSharp.EmitContext ec) [0x00000] 
  at Mono.CSharp.StatementExpression.Resolve (Mono.CSharp.EmitContext ec) [0x00000] 
  at Mono.CSharp.Block.Resolve (Mono.CSharp.EmitContext ec) [0x00000] 
  at Mono.CSharp.EmitContext.ResolveTopBlock (Mono.CSharp.EmitContext anonymous_method_host, Mono.CSharp.ToplevelBlock block, Mono.CSharp.Parameters ip, IMethodData md, System.Boolean unreachable) [0x00000] 


Build complete -- 4 errors, 0 warnings

---------------------- Done ----------------------

Build: 4 errors, 0 warnings

Thanks.

---

### Post by LordHunter317 on 2007-02-01
It seems the FX 2.0 implementation is simply missing that class, according to the Mono docs.  I'm not in Linux on my development machine right now so I can't easily check more thoroughly than that.

You have to switch back to using FX 1.1.  I don't know how to make Monodevelop do that.  You're not using generics, so no real loss by doing this.

As for using, it's a construct that ensures that .Dispose() gets called on objects that support it automatically when they go out of scope.  You should make use of it to ensure that unmanaged resources, like DB connection handles, don't get leaked.  The connection and the commands are both disposable.  MSDN has documentation on this.  I can post an example if you want.

---

### Post by gynther on 2007-02-01
> **LordHunter317 said:**
> It seems the FX 2.0 implementation is simply missing that class, according to the Mono docs.  I'm not in Linux on my development machine right now so I can't easily check more thoroughly than that.

You have to switch back to using FX 1.1.  I don't know how to make Monodevelop do that.  You're not using generics, so no real loss by doing this.

I couldn't find anything in the doc either, I suppose that System.Data.Common.DbConnection has been replaced by System.Data.Common.DbDataAdapter, but there were no documentation on that class. I'll go check with the Mono people and see if they know. Must be written somewhere... :)

You don't need to give an example if you don't *really* want to, I'll just read up on it myself. But thanks for the tip!

---

### Post by LordHunter317 on 2007-02-01
> **gynther said:**
> I couldn't find anything in the doc either, I suppose that System.Data.Common.DbConnection has been replaced by System.Data.Common.DbDataAdapter, but there were no documentation on that class.No, vice-versa.  DbDataAdapter existed in 1.1, but not DBConnection.  DBConnection was new in 2.0.  I think Mono just hasn't gotten there yet, and most of the DB people write drivers that will work on MS.NET 2.0, so Mono tends to lag.

[edit]To be clear, I'm obviously talking about hte System.Data.Common stuff, since implementations of that stuff exist in other namespaces with the same or similiar names.

As a point of reference, having a window open to [http://msdn2.microsoft.com/library/](http://msdn2.microsoft.com/library/) is pretty useful, as it documents all this.  Mono's reference on what's complete is difficult to follow IME, so I have to cross-check MS all the time.

> You don't need to give an example if you don't *really* want to, I'll just read up on it myself. But thanks for the tip!I'd rather not since it'd look just like the ones available online, on MSDN and else where.  But if you don't understand one, post it and I'd be glad to explain.

---

