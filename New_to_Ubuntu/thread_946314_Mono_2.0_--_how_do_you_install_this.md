---
title: "Mono 2.0 -- how do you install this?"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by cwmoser on 2008-10-13
I note that Mono is in the news with its just released version that supports Windows .NET 2.0.

How do you install Mono 2.0 on Ubuntu?  There seems to be some confusion.  After installing what I thought were the packages for Mono 2.0 and issue the mono --version command from a terminal window, I get "Mono JIT compiler version 1.2.6".

Also, after installing Mono 2.0, should most Windows *.exe files compiled with .NET 2.0 now work with Ubuntu? 

This seems to have a lot of promise making Windows programs work in Linux.

Carl

---

### Post by directhex on 2008-10-13
> **cwmoser said:**
> I note that Mono is in the news with its just released version that supports Windows .NET 2.0.

How do you install Mono 2.0 on Ubuntu?  There seems to be some confusion.  After installing what I thought were the packages for Mono 2.0 and issue the mono --version command from a terminal window, I get "Mono JIT compiler version 1.2.6".

That's correct. Mono 2.0 is not available in any release of Ubuntu. See [http://www.mono-project.com/Other_Downloads#Official_Packages_2](http://www.mono-project.com/Other_Downloads#Official_Packages_2) for the Mono versions included in each release.

Remember that the version numbers between Mono and Microsoft.NET do not match - Mono started to gain .NET 2.0 support in 1.1.8 - the packages you've installed with "2.0" in the name refer to the .NET version they implement, not the mono version. What mono --version reports is correct.

> Also, after installing Mono 2.0, should most Windows *.exe files compiled with .NET 2.0 now work with Ubuntu?

That depends. If they're "purely managed", i.e. they only use .NET components (and don't start making calls into gdi32.dll or other nonsense in c:\windows\system), then there's a good chance. There's a utility on the mono-project.com website called [MoMA](http://mono-project.com/MoMA) which can scan an app and tell you how cross-platform it is.

---

### Post by cwmoser on 2008-10-13
I get errors like below when I attempt to take one of my .NET 2.0 programs and run it under Mono.  I get similar errors for all my software.

Any ideas?

Thanks

Carl



$ mono ./TPP-Console.exe

** (./TPP-Console.exe:28190): WARNING **: The following assembly referenced from /media/C-Drive/TECHSUPP/Sheffield/Software Development/vb/TPP-Console/TPP-Console/bin/Release/TPP-Console.exe could not be loaded:
     Assembly:   Microsoft.VisualBasic    (assemblyref_index=1)
     Version:    8.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/media/C-Drive/TECHSUPP/Sheffield/Software Development/vb/TPP-Console/TPP-Console/bin/Release/).


** (./TPP-Console.exe:28190): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
The entry point method could not be loaded

---

### Post by ByteJuggler on 2008-10-13
Edit: Never mind, did some googling and I was talking through my neck.  I'll post back when I have a better answer...

Edit2: I believe [this thread]("http://go-mono.com/forums/#nabble-td9280423") explains the problem -- you have to install the VB runtime, in order for the VisualBasic assembly to be available to your application.  Also see [here]("http://www.mono-project.com/Visual_Basic").  There *may* be a package in synaptic to install which should give you the required assemblies (not checked myself yet.)

---

### Post by directhex on 2008-10-13
> **ByteJuggler said:**
> Edit: Never mind, did some googling and I was talking through my neck.  I'll post back when I have a better answer...

Edit2: I believe [this thread]("http://go-mono.com/forums/#nabble-td9280423") explains the problem -- you have to install the VB runtime, in order for the VisualBasic assembly to be available to your application.  Also see [here]("http://www.mono-project.com/Visual_Basic").  There *may* be a package in synaptic to install which should give you the required assemblies (not checked myself yet.)

Your diagnosis is correct - cwmoser is missing an assembly which his app is requesting, in this case Microsoft.VisualBasic 8.0.0.0.

The one just like this one:
```
directhex@mortos:~$ dpkg -L libmono-microsoft-visualbasic8.0-cil | grep dll | grep gac
/usr/lib/mono/gac/Microsoft.VisualBasic/8.0.0.0__b03f5f7f11d50a3a/Microsoft.VisualBasic.dll
```

It isn't in any official repositories right now, but can be found on badgerports (linked from my mono-project.com link above)

---

### Post by fd0man on 2008-10-13
I've created a script that will install a parallel Mono (Mono 2.0) in ${HOME}/opt.  It also installs MonoDevelop 2.0 Alpha 1 current from SVN.  See [the post on my blog]("http://www.trausch.us/2008/10/13/want-to-play-with-mono-20-so-do-i/") which talks about it and provides many, many more details.

Just to make sure it's well-known and understood, I'll repeat part of what I said there, here:  A few words about the script: ***This script is released under the terms of the GNU General Public License, Version 3. It is version 3 ONLY. There is NO SUPPORT for this software; I wrote it for myself, and it may change or it may stagnate. I provide it in the hope that it is useful to someone out there other than myself, but it is AS-IS, WITHOUT WARRANTY, UNSUPPORTED software. If it changes your dog’s gender, bursts your house into flames, destroys your whatchamacallermicroflobbermajag, do not come and yell at me.*** That having been said, I welcome any modifications (at least to view them). You can modify it for your own use, you can share it (in fact I expect you to!) and you can tinker with and tweak it. Suggestions? Welcome! Comments? Welcome! Flames? Hey, free speech is your right…

---

### Post by cwmoser on 2008-10-14
I've been waiting for .NET 2.0 functionality in Mono and MonoDevelop.  I ran the dpkg -L command and noted the following:

Package `libmono-microsoft-visualbasic8.0-cil' is not installed.

I searched for a download but could not find it.  Is it available?

Thanks four your help,

Carl

---

### Post by directhex on 2008-10-14
> **cwmoser said:**
> I've been waiting for .NET 2.0 functionality in Mono and MonoDevelop.  I ran the dpkg -L command and noted the following:

Package `libmono-microsoft-visualbasic8.0-cil' is not installed.

I searched for a download but could not find it.  Is it available?

Thanks four your help,

Carl

Read again.

> It isn't in any official repositories right now, but can be found on badgerports (linked from my mono-project.com link above)

---

### Post by cwmoser on 2008-10-14
OK, I did this:

At [http://directhex.mfgames.com/hardy.html](http://directhex.mfgames.com/hardy.html) I noted that I should install the GPG Key and Third Party deb entry.

Then I did this:
sudo apt-get install libmono-microsoft-visualbasic8.0-cil

and the output looked ok.

I did some test runs of some Visual Basic .NET 2.0 executables.

TEST#1:
e$ mono ./Guanguang.exe
**libgluezilla not found**. To have webbrowser support, you need libgluezilla installed
...but the application ran and did display the Windows form.



TEST#2:
mono ./DLPlus.exe

** (./DLPlus.exe:25857): WARNING **: The following assembly referenced from /media/C-Drive/TECHSUPP/Sheffield/Software Development/vb/DLPlus/DLPlus/bin/DLPlus.exe could not be loaded:
     **Assembly:   Microsoft.VisualBasic.Compatibility    **(assemblyref_index=6)
     Version:    8.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/media/C-Drive/TECHSUPP/Sheffield/Software Development/vb/DLPlus/DLPlus/bin/).


** (./DLPlus.exe:25857): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic.Compatibility, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'DLPlus.Mainfrm' from assembly 'DLPlus, Version=1.1.2610.15640, Culture=neutral'.
  at DLPlus.My.MyProject+MyForms.get_Mainfrm () [0x00000] 
  at DLPlus.My.MyApplication.OnCreateMainForm () [0x00000] 
  at Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun () [0x00000] 
  at Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run (System.String[] commandLine) [0x00000] 
  at DLPlus.My.MyApplication.Main (System.String[] Args) [0x00000] 
carl@klaatu:/media/C-Drive/TECHSUPP/Sheffield/Software Development/vb/DLPlus/DLPlus/bin$ 
... the application would not run.

TEST #3:
 mono ./TPP-Console.exe
**libgluezilla not found**. To have webbrowser support, you need libgluezilla installed
libgluezilla not found. To have webbrowser support, you need libgluezilla installed

Unhandled Exception: System.DllNotFoundException: gluezilla
  at (wrapper managed-to-native) Mono.Mozilla.Base:gluezilla_stringInit ()
  at Mono.Mozilla.Base.StringInit () [0x00000] 
  at Mono.Mozilla.DOM.DOMObject..ctor (Mono.Mozilla.WebBrowser control) [0x00000] 
  at Mono.Mozilla.DOM.Navigation..ctor (Mono.Mozilla.WebBrowser control, nsIWebNavigation webNav) [0x00000] 
  at Mono.Mozilla.WebBrowser.get_Navigation () [0x00000] 
  at System.Windows.Forms.WebBrowser.Navigate (System.String urlString) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.WebBrowser:Navigate (string)
  at TPP_Console.Form1.ClearHTMLWindows () [0x00000] 
  at (wrapper remoting-invoke-with-check) TPP_Console.Form1:ClearHTMLWindows ()
  at TPP_Console.Form1.ClearAllData () [0x00000] 
  at (wrapper remoting-invoke-with-check) TPP_Console.Form1:ClearAllData ()
  at TPP_Console.Form1.Form1_Load (System.Object sender, System.EventArgs e) [0x00000] 
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
  at System.Windows.Forms.Application.Run (System.Windows.Forms.ApplicationContext context) [0x00000] 
  at System.Windows.Forms.Application.Run (System.Windows.Forms.Form mainForm) [0x00000] 
  at Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun () [0x00000] 
  at Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run (System.String[] commandLine) [0x00000] 
  at TPP_Console.My.MyApplication.Main (System.String[] Args) [0x00000] 


TEST#4:
Other applications seemed to work perfectly.
Some applications failed because I did not have dependent resources such as:  Speech Engine, SQL Database, etc.

libgluzilla seemed to be the problem in Tests 1, 3.
Test 2's error is interesting.


Any help is appreciated.

This Mono looks promising.

Carl

---

### Post by directhex on 2008-10-14
libmono-mozilla0.2-cil package. And libgluezilla.

Looking into Microsoft.VisualBasic.Compatibility.

[edit] Bugger, seems libgluezilla is unavailable on Hardy. Fixing...

---

### Post by directhex on 2008-10-14
Seems Microsoft.VisualBasic.Compatibility is used only by obsolete VB6 code upgraded to VB8 by Visual Studio. Here's what a quick google found:

"2.12 Microsoft.VisualBasic.Compatibility

Do not use any methods within the Microsoft.VisualBasic.Compatibility namespace. This namespace is not to be confused with Microsoft.VisualBasic; I encourage you to use these timesaving tidbits. If your project contains a reference to the Microsoft.VisualBasic. Compatibility.dll, remove it and replace any methods that have become invalid with methods either from the Microsoft.VisualBasic or System namespaces."

If you alter your code to remove the VB6isms, it should be okay.

---

### Post by directhex on 2008-10-14
> **directhex said:**
> libmono-mozilla0.2-cil package. And libgluezilla.

Looking into Microsoft.VisualBasic.Compatibility.

[edit] Bugger, seems libgluezilla is unavailable on Hardy. Fixing...

Accepted:
 OK: gluezilla_1.9.orig.tar.gz
 OK: gluezilla_1.9-1~dhx1.diff.gz
 OK: gluezilla_1.9-1~dhx1.dsc

---

### Post by cwmoser on 2008-10-14
After extensive Googling, I found **libgluezilla **at:
[http://packages.debian.org/unstable/libs/libgluezilla](http://packages.debian.org/unstable/libs/libgluezilla)
[http://packages.debian.org/unstable/libs/libgluezilla]("http://packages.debian.org/unstable/libs/libgluezilla")

---

### Post by directhex on 2008-10-14
> **cwmoser said:**
> After extensive Googling, I found **libgluezilla **at:
[http://packages.debian.org/unstable/libs/libgluezilla](http://packages.debian.org/unstable/libs/libgluezilla)
[http://packages.debian.org/unstable/libs/libgluezilla]("http://packages.debian.org/unstable/libs/libgluezilla")

well, great, but 2 hours prior i went to the trouble of adding it to badgerports, just for you

---

### Post by cwmoser on 2008-10-15
Thanks for the help.  BTW, I'm not on the inside of development with Mono.  I have MonoDevelop on my Ubuntu at home and Visual Studio on my Windows PC at work.  What are some good websites and resources on Mono and MonoDevelop?

Thanks a bunch

Carl

---

