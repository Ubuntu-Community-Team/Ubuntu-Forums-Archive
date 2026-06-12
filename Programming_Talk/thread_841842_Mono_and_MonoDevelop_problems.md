---
title: "Mono and MonoDevelop problems"
date: 2008-06-26
forum: Programming Talk
---

### Post by Zeikcied on 2008-06-26
I have a question about MonoDevelop, and a problem with Mono in relation to an old program/game of mine.

1. I thought I read that MonoDevelop had an integrated GUI designer, but I cannot figure out how to access it.  But it might have something to do with my next problem.

2. For some reason, System.Windows.Forms won't load.  Mono can't seem to find it for some reason.  It's required by MonoDevelop, and it was installed, but it won't load.

The (extremely basic) game I wrote is in C# and was written on Windows, using Visual Studio .NET 2003 (back in 2004).  It passes the Mono Migration Analyzer test with no errors.  Yet it won't load because Mono can't seem to see System.Windows.Forms.

3. When trying to build the solution (after converting it to a Visual Studio 2005 solution), I get an error on the .resx file.  It didn't prevent the build from what I can tell.  I'm just curious what that was about.

---

### Post by LaRoza on 2008-06-26
> **Zeikcied said:**
> 
2. For some reason, System.Windows.Forms won't load.  Mono can't seem to find it for some reason.  It's required by MonoDevelop, and it was installed, but it won't load.


You have to install them, as it isn't installed by default.

```

~$search mono | grep "forms"
libmono-winforms1.0-cil - Mono System.Windows.Forms library
libmono-winforms2.0-cil - Mono System.Windows.Forms library
ironpython - A Python implementation targeting the .NET and Mono platforms
~$

```

---

### Post by Zeikcied on 2008-06-26
> **LaRoza said:**
> You have to install them, as it isn't installed by default.

```

~$search mono | grep "forms"
libmono-winforms1.0-cil - Mono System.Windows.Forms library
libmono-winforms2.0-cil - Mono System.Windows.Forms library
ironpython - A Python implementation targeting the .NET and Mono platforms
~$

```
When I try that, I get "bash: search: command not found".

Regardless, I do have libmono-winforms2.0-cil installed.  That was installed along with MonoDevelop.  I don't have libmono-winforms1.0-cil, though.

But my program still won't open, and complains that it couldn't load System.Windows.Forms.

Here's the output from my program:

```
** (xx.exe:12292): WARNING **: The following assembly referenced from /media/sda3/My Documents 1/xx/xx.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=1)
     Version:    1.0.5000.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/media/sda3/My Documents 1/xx/).


** (xx.exe:12292): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
The entry point method could not be loaded
```

---

### Post by LaRoza on 2008-06-26
> **Zeikcied said:**
> When I try that, I get "bash: search: command not found".

Regardless, I do have libmono-winforms2.0-cil installed.  That was installed along with MonoDevelop.  I don't have libmono-winforms1.0-cil, though.

But my program still won't open, and complains that it couldn't load System.Windows.Forms.

Here's the output from my program:


Yes, "search" is an alias defined in my .bashrc. (alias search='apt-cache search')

I think you have to manually link to the winforms code. The magic of the IDE is unknown to me, and I would only know with the command line.

---

### Post by Zeikcied on 2008-06-26
> **LaRoza said:**
> Yes, "search" is an alias defined in my .bashrc. (alias search='apt-cache search')

I think you have to manually link to the winforms code. The magic of the IDE is unknown to me, and I would only know with the command line.
It seems like I would have to link the winforms library to Mono, though.  I'm trying to run the program just through the mono command (that was my command line output, not from MonoDevelop).

It's not that the IDE isn't recognizing it, but Mono itself isn't recognizing it.

How would I go about linking it, or checking to see what the problem is?

---

### Post by LaRoza on 2008-06-26
> **Zeikcied said:**
> 
How would I go about linking it, or checking to see what the problem is?

```

~$cat p.cs
using System;
using System.Windows.Forms;

namespace p
{
   class Welcome
   {
      public static void Main( string[] args )
      {
         MessageBox.Show( "Welcome\nto\nC#\nprogramming!" );
      }
   }
}
~$mcs p.cs /r:System.Windows.Forms.dll
~$mono p.exe

```

---

### Post by LaRoza on 2008-06-26
If it uses more than just the winforms thingy, you can do similiar things for the others.

---

### Post by Zeikcied on 2008-06-26
> **LaRoza said:**
> ```

~$cat p.cs
using System;
using System.Windows.Forms;

namespace p
{
   class Welcome
   {
      public static void Main( string[] args )
      {
         MessageBox.Show( "Welcome\nto\nC#\nprogramming!" );
      }
   }
}
~$mcs p.cs /r:System.Windows.Forms.dll
~$mono p.exe

```
Okay, I created the file, and ran the commands.  What I get is:

```
~$ mcs p.cs /r:System.Windows.Forms.dll
error CS0006: cannot find metadata file `System.Windows.Forms.dll'
Compilation failed: 1 error(s), 0 warnings
```

EDIT: I entered the full path to the dll file, and now it's throwing errors on several other libraries that it can't load.  I'm guessing that something didn't get configured properly, although Adept didn't show any errors in processing the files.

---

### Post by LaRoza on 2008-06-27
> **Zeikcied said:**
> Okay, I created the file, and ran the commands.  What I get is:

```
~$ mcs p.cs /r:System.Windows.Forms.dll
error CS0006: cannot find metadata file `System.Windows.Forms.dll'
Compilation failed: 1 error(s), 0 warnings
```

EDIT: I entered the full path to the dll file, and now it's throwing errors on several other libraries that it can't load.  I'm guessing that something didn't get configured properly, although Adept didn't show any errors in processing the files.

Could you post the code?

(If you can't post the entire code, just post the "using" lines)

---

### Post by Zeikcied on 2008-06-27
> **LaRoza said:**
> Could you post the code?

(If you can't post the entire code, just post the "using" lines)
I just attempted to compile your example.  It gave me that error when I used the same line you did.  When I added the full path to the DLL, it threw a bunch of other errors.

I'm guessing that a lot of libraries aren't working properly.  Here's the full error block.

```
~$ mcs p.cs /r:/usr/lib/mono/2.0/System.Windows.Forms.dll

** (/usr/lib/mono/1.0/mcs.exe:13207): WARNING **: The class System.Runtime.InteropServices.StandardOleMarshalObject could not be loaded, used in System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

** (/usr/lib/mono/1.0/mcs.exe:13207): WARNING **: The class System.Runtime.InteropServices.StandardOleMarshalObject could not be loaded, used in System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

** (/usr/lib/mono/1.0/mcs.exe:13207): WARNING **: The class System.Runtime.InteropServices.StandardOleMarshalObject could not be loaded, used in System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

** (/usr/lib/mono/1.0/mcs.exe:13207): WARNING **: The class System.Runtime.InteropServices.StandardOleMarshalObject could not be loaded, used in System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
**
** ERROR:(class.c:2561):mono_class_setup_vtable_general: assertion failed: (cm->slot < max_vtsize)
Stacktrace:

  at (wrapper managed-to-native) System.MonoType.GetNestedTypes (System.Reflection.BindingFlags) <0x00004>
  at (wrapper managed-to-native) System.MonoType.GetNestedTypes (System.Reflection.BindingFlags) <0xffffffff>
  at System.Type.FindMembers (System.Reflection.MemberTypes,System.Reflection.BindingFlags,System.Reflection.MemberFilter,object) <0x003f3>
  at Mono.CSharp.TypeHandle.GetMembers (System.Reflection.MemberTypes,System.Reflection.BindingFlags) <0x00048>
  at Mono.CSharp.MemberCache.AddMembers (System.Reflection.MemberTypes,System.Reflection.BindingFlags,Mono.CSharp.IMemberContainer) <0x0002a>
  at Mono.CSharp.MemberCache.AddMembers (Mono.CSharp.IMemberContainer) <0x0007e>
  at Mono.CSharp.MemberCache..ctor (Mono.CSharp.IMemberContainer) <0x00167>
  at Mono.CSharp.TypeHandle..ctor (System.Type) <0x0015c>
  at Mono.CSharp.TypeHandle.GetTypeHandle (System.Type) <0x0004e>
  at Mono.CSharp.TypeHandle.GetMemberCache (System.Type) <0x0000b>
  at Mono.CSharp.TypeManager.MemberLookup_FindMembers (System.Type,System.Reflection.MemberTypes,System.Reflection.BindingFlags,string,bool&) <0x0017c>
  at Mono.CSharp.TypeManager.RealMemberLookup (System.Type,System.Type,System.Type,System.Reflection.MemberTypes,System.Reflection.BindingFlags,string,System.Collections.IList) <0x00152>
  at Mono.CSharp.TypeManager.MemberLookup (System.Type,System.Type,System.Type,System.Reflection.MemberTypes,System.Reflection.BindingFlags,string,System.Collections.IList) <0x0001f>
  at Mono.CSharp.Expression.MemberLookup (System.Type,System.Type,System.Type,string,System.Reflection.MemberTypes,System.Reflection.BindingFlags,Mono.CSharp.Location) <0x00042>
  at Mono.CSharp.Expression.MemberLookup (System.Type,System.Type,System.Type,string,Mono.CSharp.Location) <0x0001d>
  at Mono.CSharp.MemberAccess.DoResolve (Mono.CSharp.EmitContext,Mono.CSharp.Expression) <0x00240>
  at Mono.CSharp.MemberAccess.DoResolve (Mono.CSharp.EmitContext) <0x0000f>
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext,Mono.CSharp.ResolveFlags) <0x00134>
  at Mono.CSharp.Invocation.DoResolve (Mono.CSharp.EmitContext) <0x00025>
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext,Mono.CSharp.ResolveFlags) <0x00134>
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext) <0x00012>
  at Mono.CSharp.ExpressionStatement.ResolveStatement (Mono.CSharp.EmitContext) <0x00014>
  at Mono.CSharp.StatementExpression.Resolve (Mono.CSharp.EmitContext) <0x0001f>
  at Mono.CSharp.Block.Resolve (Mono.CSharp.EmitContext) <0x001e1>
  at Mono.CSharp.EmitContext.ResolveTopBlock (Mono.CSharp.EmitContext,Mono.CSharp.ToplevelBlock,Mono.CSharp.Parameters,Mono.CSharp.IMethodData,bool&) <0x0019a>
  at Mono.CSharp.EmitContext.EmitTopBlock (Mono.CSharp.IMethodData,Mono.CSharp.ToplevelBlock) <0x00047>
  at Mono.CSharp.MethodData.Emit (Mono.CSharp.DeclSpace) <0x0014c>
  at Mono.CSharp.Method.Emit () <0x000a7>
  at Mono.CSharp.TypeContainer.EmitType () <0x001e1>
  at Mono.CSharp.RootContext.EmitCode () <0x0007e>
  at Mono.CSharp.Driver.MainDriver (string[]) <0x00962>
  at Mono.CSharp.Driver.Main (string[]) <0x00055>
  at (wrapper runtime-invoke) Mono.CSharp.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

        /usr/bin/mono [0x816b1fa]
        [0xb7fb6440]
        /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7d75a01]
        /usr/lib/libglib-2.0.so.0(g_assertion_message+0x121) [0xb7f353e1]
        /usr/lib/libglib-2.0.so.0 [0xb7f3593d]
        /usr/bin/mono [0x80fce60]
        /usr/bin/mono [0x80fd2fb]
        /usr/bin/mono [0x80fba51]
        /usr/bin/mono [0x80fd2fb]
        /usr/bin/mono(mono_class_init+0x902) [0x80fdc62]
        /usr/bin/mono(mono_class_init+0xbb7) [0x80fdf17]
        /usr/bin/mono(mono_type_get_object+0x85) [0x817a1b5]
        /usr/bin/mono [0x80a454c]
        [0xb705ea4a]
        [0xb705e3cc]
        [0xb705df99]
        [0xb705dcab]
        [0xb705dbf7]
        [0xb705d168]
        [0xb707cdfd]
        [0xb707cc5f]
        [0xb707cb8c]
        [0xb704ed0d]
        [0xb704e68b]
        [0xb704e520]
        [0xb704ddb3]
        [0xb7053b76]
        [0xb704baf1]
        [0xb704b898]
        [0xb704b05d]
        [0xb704b28e]
        [0xb704b05d]
        [0xb704aeb3]
        [0xb704ae5d]
        [0xb704ae20]
        [0xb7051b0a]
        [0xb7051533]
        [0xb704ad50]
        [0xb704a81d]
        [0xb704a5f8]
        [0xb706951a]
        [0xb7068f4f]
        [0xb78eb1fb]
        [0xb78e9da6]
        [0xb78e61c4]
        /usr/bin/mono(mono_runtime_exec_main+0x10e) [0x809c68e]
        /usr/bin/mono(mono_runtime_run_main+0x173) [0x809c933]
        /usr/bin/mono(mono_main+0x6a9) [0x805acd9]
        /usr/bin/mono [0x805a122]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d5f450]
        /usr/bin/mono [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7d07940 (LWP 13207)]
[New Thread 0xb7363b90 (LWP 13209)]
[New Thread 0xb78e5b90 (LWP 13208)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7fb6410 in __kernel_vsyscall ()
  3 Thread 0xb78e5b90 (LWP 13208)  0xb7fb6410 in __kernel_vsyscall ()
  2 Thread 0xb7363b90 (LWP 13209)  0xb7fb6410 in __kernel_vsyscall ()
  1 Thread 0xb7d07940 (LWP 13207)  0xb7fb6410 in __kernel_vsyscall ()

Thread 3 (Thread 0xb78e5b90 (LWP 13208)):
#0  0xb7fb6410 in __kernel_vsyscall ()
#1  0xb7eca196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb7ec24fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7e1fe5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb7363b90 (LWP 13209)):
#0  0xb7fb6410 in __kernel_vsyscall ()
#1  0xb7ec6aa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080b1c0a in ?? ()
#7  0x080cef04 in ?? ()
#8  0x0811a7c2 in ?? ()
#9  0x081317a5 in ?? ()
#10 0xb7ec24fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7e1fe5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7d07940 (LWP 13207)):
#0  0xb7fb6410 in __kernel_vsyscall ()
#1  0xb7dded89 in fork () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7ecc034 in fork () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb7f460f9 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb7f46d1d in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#5  0xb7f471dc in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#6  0x0816b295 in ?? ()
#7  <signal handler called>
#8  0xb7fb6410 in __kernel_vsyscall ()
#9  0xb7d74085 in raise () from /lib/tls/i686/cmov/libc.so.6
#10 0xb7d75a01 in abort () from /lib/tls/i686/cmov/libc.so.6
#11 0xb7f353e1 in g_assertion_message () from /usr/lib/libglib-2.0.so.0
#12 0xb7f3593d in g_assertion_message_expr () from /usr/lib/libglib-2.0.so.0
#13 0x080fce60 in ?? ()
#14 0x080fd2fb in ?? ()
#15 0x080fba51 in ?? ()
#16 0x080fd2fb in ?? ()
#17 0x080fdc62 in mono_class_init ()
#18 0x080fdf17 in mono_class_init ()
#19 0x0817a1b5 in mono_type_get_object ()
#20 0x080a454c in ?? ()
#21 0xb705ea4a in ?? ()
#22 0xb705e3cc in ?? ()
#23 0xb705df99 in ?? ()
#24 0xb705dcab in ?? ()
#25 0xb705dbf7 in ?? ()
#26 0xb705d168 in ?? ()
#27 0xb707cdfd in ?? ()
#28 0xb707cc5f in ?? ()
#29 0xb707cb8c in ?? ()
#30 0xb704ed0d in ?? ()
#31 0xb704e68b in ?? ()
#32 0xb704e520 in ?? ()
#33 0xb704ddb3 in ?? ()
#34 0xb7053b76 in ?? ()
#35 0xb704baf1 in ?? ()
#36 0xb704b898 in ?? ()
#37 0xb704b05d in ?? ()
#38 0xb704b28e in ?? ()
#39 0xb704b05d in ?? ()
#40 0xb704aeb3 in ?? ()
#41 0xb704ae5d in ?? ()
#42 0xb704ae20 in ?? ()
#43 0xb7051b0a in ?? ()
#44 0xb7051533 in ?? ()
#45 0xb704ad50 in ?? ()
#46 0xb704a81d in ?? ()
#47 0xb704a5f8 in ?? ()
#48 0xb706951a in ?? ()
#49 0xb7068f4f in ?? ()
#50 0xb78eb1fb in ?? ()
#51 0xb78e9da6 in ?? ()
#52 0xb78e61c4 in ?? ()
#53 0x0809c68e in mono_runtime_exec_main ()
#54 0x0809c933 in mono_runtime_run_main ()
#55 0x0805acd9 in mono_main ()
#56 0x0805a122 in ?? ()
#57 0xb7d5f450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#58 0x0805a091 in ?? ()
#0  0xb7fb6410 in __kernel_vsyscall ()


=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Aborted
```

Again, that's just using the example you gave, with just System and System.Windows.Forms.

My guess is that I should probably uninstall Mono and try again.

---

### Post by LaRoza on 2008-06-27
> **Zeikcied said:**
> I just attempted to compile your example.  It gave me that error when I used the same line you did.  When I added the full path to the DLL, it threw a bunch of other errors.

I'm guessing that a lot of libraries aren't working properly.  Here's the full error block.

Again, that's just using the example you gave, with just System and System.Windows.Forms.

My guess is that I should probably uninstall Mono and try again.

Odd. What version of everything are you using (including the winforms)?

I really don't know what else to do; I am not a C# programmer.

---

### Post by Zeikcied on 2008-06-27
> **LaRoza said:**
> Odd. What version of everything are you using (including the winforms)?

I really don't know what else to do; I am not a C# programmer.
I installed everything fresh from the repositories yesterday.

I had a similar problem with System.Windows.Forms when I tried Mono last year.  I guess I just have bad luck or something.  I could attempt to reinstall Mono, and see if that helps.

EDIT: I got it to work now.  Yay. :)  Thanks for your help.  I really appreciate it.

---

### Post by sickasabat on 2008-11-14
Hi, I am having a similar problem. Could you post what steps you took to resolve your issue?

---

### Post by SouthOfHell on 2009-11-14
> **Zeikcied said:**
> I installed everything fresh from the repositories yesterday.

I had a similar problem with System.Windows.Forms when I tried Mono last year.  I guess I just have bad luck or something.  I could attempt to reinstall Mono, and see if that helps.

EDIT: I got it to work now.  Yay. :)  Thanks for your help.  I really appreciate it.

Do you mind posting exactly what you did to get it working, I'm experiencing the exact same problem's you describe..

```
apt-get install libmono-winforms2.0-cil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmono-winforms2.0-cil is already the newest version.
```


```
 error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?
```

---

### Post by directhex on 2009-11-14
> **SouthOfHell said:**
> Do you mind posting exactly what you did to get it working, I'm experiencing the exact same problem's you describe..

```
apt-get install libmono-winforms2.0-cil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmono-winforms2.0-cil is already the newest version.
```


```
 error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?
```

Do you have a reference on that assembly?

---

