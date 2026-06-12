---
title: "Windows Forms Application with Mono"
date: 2008-08-10
forum: Programming Talk
---

### Post by kjohansen on 2008-08-10
I have successfully run a .NET console application on linux using mono but can not run a simple Windows form application.

I updated my mono and used the Moma tool to analyze my forms application.  The forms application passed but when I try to run it I get the following error:

```

johank@johank-laptop:~/Desktop/CSE655$ mono RGui.exe

** (RGui.exe:23613): WARNING **: The following assembly referenced from /home/johank/Desktop/CSE655/RGui.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=1)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/johank/Desktop/CSE655/).


** (RGui.exe:23613): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (RGui.exe:23613): WARNING **: Missing method EnableVisualStyles in assembly /home/johank/Desktop/CSE655/RGui.exe, type System.Windows.Forms.Application

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
File name: 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'


```

Is it possible to run a windows form application through mono and are there any special commands I need to issue?

thanks.

---

### Post by kjohansen on 2008-08-10
apt-get mono-winforms* solves everything.

---

### Post by Alpha7 on 2008-09-09
I've having close to the same issue, however after installing the mono-winforums* packages I still have numerous errors:


```

When I run: 'mono ServiceConsole2.exe ' I get:

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Shared.Config ---> System.EntryPointNotFoundException: RegisterWindowMessage
  at (wrapper managed-to-native) Shared.Win32:RegisterWindowMessage (string)
  at Shared.Config..cctor () [0x00000] --- End of inner exception stack trace ---

  at ServiceConsole2.LoginForm.LoginForm_Load (System.Object sender, System.EventArgs e) [0x00000] 
  at System.Windows.Forms.Form.OnLoad (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.Form.OnLoadInternal (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.Form.OnCreateControl () [0x00000] 
  at System.Windows.Forms.Control.CreateControl () [0x00000] 
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Form.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.NativeWindow.WndProc (IntPtr hWnd, Msg msg, IntPtr wParam, IntPtr lParam) [0x00000] 
  at System.Windows.Forms.XplatUIX11.SendMessage (IntPtr hwnd, Msg message, IntPtr wParam, IntPtr lParam) [0x00000] 
  at System.Windows.Forms.XplatUIX11.MapWindow (System.Windows.Forms.Hwnd hwnd, WindowType windows) [0x00000] 
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] 
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams cp) [0x00000] 
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams create_params) [0x00000] 
  at System.Windows.Forms.Control.CreateHandle () [0x00000] 
  at System.Windows.Forms.Form.CreateHandle () [0x00000] 
  at System.Windows.Forms.Control.CreateControl () [0x00000] 
  at System.Windows.Forms.Control.SetVisibleCore (Boolean value) [0x00000] 
  at System.Windows.Forms.Form.SetVisibleCore (Boolean value) [0x00000] 
  at System.Windows.Forms.Control.set_Visible (Boolean value) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control:set_Visible (bool)
  at System.Windows.Forms.Application.RunLoop (Boolean Modal, System.Windows.Forms.ApplicationContext context) [0x00000] 
  at System.Windows.Forms.Form.ShowDialog (IWin32Window ownerWin32) [0x00000] 
  at System.Windows.Forms.Form.ShowDialog () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Form:ShowDialog ()
  at ServiceConsole2.Form1.Main () [0x00000] 

```
Because it is an executable I'm not even sure I can run it with mono, but Wine comes up with its own set of errors and I installed the windows version of mono for Wine. I got a little further but it stills errors out no matter what I do.

Any info or suggestions would be greatly appreciated.

---

### Post by kjohansen on 2008-09-09
You can run executables with mono.  After I installed mono-winforms* everything worked for me.

Have you run this exe on a windows machine to know it works?  The first error " System.EntryPointNotFoundException:" makes me think the executable has an error.

---

### Post by Alpha7 on 2008-09-09
Yes, I have it running on 30+ windows computers and am looking at moving away from relying on windows, but this would be one of the program that would prevent the switch from happening. Before installing the winform it did nothing, so installing the packages helped, but there is something else that is missing.

---

### Post by kjohansen on 2008-09-09
Have you run it through moma, mono's migration analyzer?  It may provide some more insight...

[http://www.mono-project.com/MoMA](http://www.mono-project.com/MoMA)

---

### Post by Alpha7 on 2008-09-09
No problems found when I ran MoMA

---

### Post by kjohansen on 2008-09-09
Im running out of ideas but...

What version of mono are you using(mono --version)?

Can you list the namespaces you use in the file?

---

### Post by Alpha7 on 2008-09-09
I'm not exactly sure what you mean by the namespaces, I am not building this from scratch and do not have much experience in this area.

 If what you mean is similar to doing a tasklist -m in windows I can get that for you with out any problems. If there is another way I am listening.

and my version:

Mono JIT compiler version 1.9.1 (tarball)
Copyright (C) 2002-2007 Novell, Inc and Contributors. [www.mono-project.com](www.mono-project.com)
	TLS:           __thread
	GC:            Included Boehm (with typed GC)
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  x86
	Disabled:      none

---

### Post by true_friend on 2008-09-10
I personally find mono's winform implementation buggy. Even on different distros it differs. [Corsis]("http://sourceforge.net/projects/corsis/"), a corpus analysis tool has screen shot running on debian but on Ubuntu I couldn't do the same thing with mono. So I try to do things in gtk# or perhaps in Qt in futrue (if it implemented wholly and provided a visual designer as well).
Regards

---

### Post by kjohansen on 2008-09-10
> **Alpha7 said:**
> 
and my version:

Mono JIT compiler version 1.9.1 (tarball)
Copyright (C) 2002-2007 Novell, Inc and Contributors. [www.mono-project.com](www.mono-project.com)
	TLS:           __thread
	GC:            Included Boehm (with typed GC)
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  x86
	Disabled:      none

I have an older version 1.2.6.  Interesting...

For the namespaces, those would be in the source (if you have it). From what I have read there are a lot of problems with the System.Runtime libraries on mono, so if you use those there is no real workaround

---

### Post by jethro10 on 2009-02-02
are you running :-

wine prog.exe

instead of 

mono prog.exe ?

---

