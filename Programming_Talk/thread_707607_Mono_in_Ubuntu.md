---
title: "Mono in Ubuntu"
date: 2008-02-25
forum: Programming Talk
---

### Post by DrMega on 2008-02-25
Hi

For my work, I have to develop in C#.Net (we use Windows at work). I want to work on some stuff at home, but ideally I wanted my work to be compatible with Ubuntu as well.

The problem is, although Mono includes the System.Windows and System.Data namespaces, which according to Synaptic are installed on my machine, I can't access these two namespaces.

Any ideas?

Please note while I'm sure Python, C and C++ are all great languages, I have no choice but to use C#.net.

---

### Post by LaRoza on 2008-02-25
For this, I highly suggest using Windows and the tools that your work uses.

---

### Post by DrMega on 2008-02-25
> **LaRoza said:**
> For this, I highly suggest using Windows and the tools that your work uses.

Thanks, but I am determined to make as much of my work as possible work cross platform. Some of the stuff I do will be of use to me personally as well as work, and at home I really don't want to be dependant on Windows.

Mono can (apparently) do this, and I'm not going to give up at the first hurdle.

---

### Post by a9bejo on 2008-02-25
> **DrMega said:**
> Hi

For my work, I have to develop in C#.Net (we use Windows at work). I want to work on some stuff at home, but ideally I wanted my work to be compatible with Ubuntu as well.

The problem is, although Mono includes the System.Windows and System.Data namespaces, which according to Synaptic are installed on my machine, I can't access these two namespaces.

Any ideas?

Please note while I'm sure Python, C and C++ are all great languages, I have no choice but to use C#.net.

I have no idea why you can't access the System.Windows namespace - I could use them  after installing the winforms package (libmono-winforms1.0-cil). Same goes for System.Data. At least from within Monodevelop.

But I also think that it is not a good idea to develop a .NET application that is targeted for Windows Users with Mono.  At least not unless your coworkers and you target this application to be truly cross platform (In this case I suggest you guys all use Mono on Windows too).

> **DrMega said:**
> 
Mono can (apparently) do this, and I'm not going to give up at the first hurdle.


I really hope this works for you.

---

### Post by DrMega on 2008-02-25
> **a9bejo said:**
> IBut I also think that it is not a good idea to develop a .NET application that is targeted for Windows Users with Mono.  At least not unless your coworkers and you target this application to be truly cross platform (In this case I suggest you guys all use Mono on Windows too).

I would agree with you if it was an entire app that I was trying to develop for both, but to be honest my objectives are two fold as follows:

1. Develop a number of components that will be platform independent. I won't use the compiled code between the two platforms, I'll share the source and use it in seperate builds.

2. This is my attempt at migrating from Windows to Linux development in what I hoped would be easy steps. I figured if I can just get something working using techniques that I'm familiar with from my Windows development experience, then bit by bit I can start experimenting with GTK.

---

### Post by DrMega on 2008-02-25
Ok I've made some progress.

My initial problem was simple (something I didn't think of at first as I take it from granted in Windows). I hadn't created a reference to the System.Windows.Forms assembly.

Now I've done that, the code completion correctly recognises everything within that namespace, the app compiles OK, but fails at runtime. Here is the output. Any ideas?

```


** (WinTest3:8065): WARNING **: The following assembly referenced from /home/me/Projects/WinTest3/WinTest3/bin/Debug/System.Windows.Forms.dll could not be loaded:
     Assembly:   Accessibility    (assemblyref_index=6)
     Version:    2.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/me/Projects/WinTest3/WinTest3/bin/Debug).


** (WinTest3:8065): WARNING **: Could not load file or assembly 'Accessibility, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
Stacktrace:

  at MainWindow..ctor () [0x00018] in /home/me/Projects/WinTest3/WinTest3/MainWindow.cs:16
  at MainWindow..ctor () [0x0000d] in /home/me/Projects/WinTest3/WinTest3/MainWindow.cs:15
  at WinTest3.MainClass.Main (string[]) [0x00005] in /home/me/Projects/WinTest3/WinTest3/Main.cs:17
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	/usr/bin/mono [0x8194ca6]
	/usr/bin/mono [0x81770ed]
	[0xffffe440]
	/usr/bin/mono(mono_object_new+0x18) [0x80b596a]
	/usr/bin/mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
	/usr/bin/mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
	/usr/bin/mono [0x810f9a7]
	/usr/bin/mono [0x811a390]
	/usr/bin/mono(mono_class_vtable+0x181) [0x80b29b3]
	/usr/bin/mono(mono_object_new+0x18) [0x80b596a]
	/usr/bin/mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
	/usr/bin/mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
	/usr/bin/mono [0x810f9a7]
	/usr/bin/mono [0x8176370]
	/usr/bin/mono [0x817699e]
	/usr/bin/mono [0x8176a98]
	/usr/bin/mono(mono_compile_method+0x3b) [0x80b13bd]
	/usr/bin/mono [0x808fe5a]
	[0xb7c27032]
	[0xb7473e7e]
	[0xb74737d5]
	/usr/bin/mono [0x8176f50]
	/usr/bin/mono(mono_runtime_invoke+0x27) [0x80b0b2f]
	/usr/bin/mono(mono_runtime_exec_main+0x142) [0x80b5383]
	/usr/bin/mono(mono_runtime_run_main+0x27e) [0x80b5631]
	/usr/bin/mono(mono_jit_exec+0xbd) [0x805a4cb]
	/usr/bin/mono [0x805a5a8]
	/usr/bin/mono(mono_main+0x1683) [0x805bdc9]
	/usr/bin/mono [0x8059636]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d7d050]
	/usr/bin/mono [0x80595b1]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210685744 (LWP 8065)]
[New Thread -1220076656 (LWP 8069)]
[New Thread -1219994736 (LWP 8067)]
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
  3 Thread -1219994736 (LWP 8067)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1220076656 (LWP 8069)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1210685744 (LWP 8065)  0xffffe410 in __kernel_vsyscall ()

Thread 3 (Thread -1219994736 (LWP 8067)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ee39f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb74853ac in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread -1220076656 (LWP 8069)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ee0676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb795f1dc in ?? ()
#4  0xb795f1c4 in ?? ()
#5  0xb7ede541 in pthread_mutex_lock ()
   from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb795f1dc in ?? ()
#8  0xb795f1c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1210685744 (LWP 8065)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e332a1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f53780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f53b4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7c26844 in ?? ()
#6  0xb7c2682c in ?? ()
#7  0xb7c26828 in ?? ()
#8  0xb7c26824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================



```

---

### Post by DrMega on 2008-02-25
OK. I'm giving up. MonoDevelop doesn't work. For the last 10 or so attempts at narrowing down the problem, I got the same results (A simple Hello World write to the console), even AFTER I'd removed the line that writes it and rebuilt my code. I found an option to "clean" the project so I did that. Then it tells me it built the project successfully but guess what, it didn't build anything at all.

Its a real shame, but never mind.

---

### Post by a9bejo on 2008-02-25
This works for me:

```

ben@kafka: ls
test.cs  
ben@kafka: cat test.cs 
using System;
using System.Windows.Forms;

namespace test{

   public class HelloWorld : Form{
     static public void Main(){
       Application.Run (new HelloWorld ());
     }
 
     public HelloWorld(){
       Button b = new Button ();
       b.Text = "Click Me!";
       b.Click += new EventHandler (Button_Click);
       Controls.Add (b);
     }
 
     private void Button_Click (object sender, EventArgs e){
       MessageBox.Show ("Button Clicked!");
     }
  }
}
ben@kafka: gmcs -r:System.Windows.Forms test.cs 
ben@kafka: mono test.exe


```

```

ben@kafka: sudo aptitude search mono | grep -v "^p.*$"
id  kde-icons-mono                  - a monochromatic icons theme for KDE       
iBA libmono-accessibility1.0-cil    - Mono Accessibility library                
idA libmono-accessibility2.0-cil    - Mono Accessibility library                
iBA libmono-addins-gui0.2-cil       - GTK# frontend library for Mono.Addins     
iBA libmono-addins0.2-cil           - addin framework for creating extensible CL
id  libmono-cairo1.0-cil            - Mono Cairo library                        
iBA libmono-cairo2.0-cil            - Mono Cairo library                        
iBA libmono-cecil0.5-cil            - library to generate and inspect CIL assemb
id  libmono-corlib1.0-cil           - Mono core library (1.0)                   
id  libmono-corlib2.0-cil           - Mono core library (2.0)                   
idA libmono-data-tds1.0-cil         - Mono Data library                         
id  libmono-data-tds2.0-cil         - Mono Data Library                         
idA libmono-microsoft-build2.0-cil  - Mono Microsoft.Build libraries            
iBA libmono-peapi1.0-cil            - Mono PEAPI library                        
idA libmono-peapi2.0-cil            - Mono PEAPI library                        
iBA libmono-relaxng1.0-cil          - Mono Relaxng library                      
idA libmono-security1.0-cil         - Mono Security library                     
id  libmono-security2.0-cil         - Mono Security library                     
idA libmono-sharpzip0.84-cil        - Mono SharpZipLib library                  
id  libmono-sharpzip2.84-cil        - Mono SharpZipLib library                  
id  libmono-sqlite2.0-cil           - Mono Sqlite library                       
idA libmono-system-data1.0-cil      - Mono System.Data library                  
id  libmono-system-data2.0-cil      - Mono System.Data Library                  
iBA libmono-system-runtime1.0-cil   - Mono System.Runtime library               
iBA libmono-system-runtime2.0-cil   - Mono System.Runtime Library               
idA libmono-system-web1.0-cil       - Mono System.Web library                   
id  libmono-system-web2.0-cil       - Mono System.Web Library                   
id  libmono-system1.0-cil           - Mono System libraries (1.0)               
id  libmono-system2.0-cil           - Mono System libraries (2.0)               
iB  libmono-winforms1.0-cil         - Mono System.Windows.Forms library         
id  libmono-winforms2.0-cil         - Mono System.Windows.Forms library         
id  libmono0                        - libraries for the Mono JIT                
id  libmono1.0-cil                  - Mono libraries (1.0)                      
id  libmono2.0-cil                  - Mono libraries (2.0)                      
id  mono                            - Mono CLI (.NET) runtime                   
id  mono-common                     - common files for Mono                     
id  mono-gac                        - Mono GAC tool                             
id  mono-gmcs                       - Mono C# 2.0 compiler                      
id  mono-jit                        - fast CLI JIT/AOT compiler for Mono        
iBA mono-mcs                        - Mono C# compiler                          
id  mono-runtime                    - Mono runtime                              
iB  monodevelop                     - C#/Boo/Java/Nemerle/ILasm/ASP.NET Developm
iBA monodoc-base                    - shared MonoDoc binaries                   
i A monodoc-manual                  - compiled XML documentation from the Mono p
v   monodoc-viewer                  -                                           
ben@kafka: 

```

---

### Post by CptPicard on 2008-02-25
> 
1. Develop a number of components that will be platform independent. I won't use the compiled code between the two platforms, I'll share the source and use it in seperate builds.

Could work if you're building libraries that do not have much dependencies on the outside world -- algorithms and such...

> 2. This is my attempt at migrating from Windows to Linux development in what I hoped would be easy steps. I figured if I can just get something working using techniques that I'm familiar with from my Windows development experience, then bit by bit I can start experimenting with GTK.

This is where your logic goes wrong. You should not assume that you'll be able to transfer much experience from your Windows C#.Net development experience to doing anything the "Linux way" using GTK, or whatever. You're just wasting time trying to force a migration path that isn't there... you're better off learning doing stuff on Linux "right" from the start.

---

### Post by reverseblade on 2008-02-26
Both System.Data and System.Windows.Forms namespaces works perfectly on my ubuntu

---

