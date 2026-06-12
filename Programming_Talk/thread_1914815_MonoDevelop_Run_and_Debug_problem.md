---
title: "MonoDevelop Run and Debug problem"
date: 2012-01-25
forum: Programming Talk
---

### Post by JRz_ on 2012-01-25
Hello,

I've recently changed to Ubuntu 11.10 (from Windows Vista).I use mono (2.8.5) as my IDE (C# VS.net before) to program.

As a quick test I want to make a console program with the following code:
```
using System;

namespace DeleteMe1
{
	class MainClass
	{
		public static void Main (string[] args)
		{
			Console.WriteLine ("Hello World!");
			Console.ReadKey ();
		}
	}
}
```

If I run the program I see a screen appear and disappear (very quickly). When I debug I get the following error:

```
Could not open port for debugger. Another process may be using the port.
```

Is someone familiar with these messages? I've already tried the following:

[http://stackoverflow.com/questions/8649919/could-not-open-port-for-debugger-another-process-may-be-using-the-port](http://stackoverflow.com/questions/8649919/could-not-open-port-for-debugger-another-process-may-be-using-the-port)

But the  property key (<Property key="MonoTouch.Debugger.Port" value="10000" />) is not available.

Whats wrong?

Thanks in advance and with best regards.

---

### Post by directhex on 2012-01-25
You're using the Mono Soft Debugger, right? The old mono-debugger won't work (and shouldn't be in the archive)

---

### Post by JRz_ on 2012-01-26
Yes, I am using the soft debugger.

---

### Post by directhex on 2012-01-26
And where are your mono/monodevelop from? 11.10 shipped with Mono 2.6.7 and MonoDevelop 2.6

---

### Post by JRz_ on 2012-01-26
This is the version information:

Version 2.8.2

Build information:
	Git revision: unknown
	Build date: 2011-11-01 19:27:44+0000
Operating System:
	Linux 
	Linux ubuntu 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Runtime:
	Mono 2.10.5 (Debian 2.10.5-1) (64-bit)
	GTK 2.24.6 (GTK# 2.12.0.0)
Loaded assemblies:
ICSharpCode.SharpZipLib      2.84.0.0 /usr/lib/mono/gac/ICSharpCode.SharpZipLib/2.84.0.0__1b03e6acf1164f73/ICSharpCode.SharpZipLib.dll
Mono.Security                4.0.0.0  /usr/lib/mono/gac/Mono.Security/4.0.0.0__0738eb9f132ed756/Mono.Security.dll
MonoDevelop.GtkCore          2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/MonoDevelop.GtkCore/MonoDevelop.GtkCore.dll
libsteticui                  0.0.0.0  /opt/monodevelop/lib/monodevelop/AddIns/MonoDevelop.GtkCore/libsteticui.dll
libstetic                    0.0.0.0  /opt/monodevelop/lib/monodevelop/AddIns/MonoDevelop.GtkCore/libstetic.dll
MonoDevelop.Deployment.Linux 2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/MonoDevelop.Deployment/MonoDevelop.Deployment.Linux.dll
MonoDevelop.Moonlight        2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/MonoDevelop.Moonlight/MonoDevelop.Moonlight.dll
MonoDevelop.AspNet           2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/MonoDevelop.AspNet/MonoDevelop.AspNet.dll
MonoDevelop.XmlEditor        2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/MonoDevelop.XmlEditor/MonoDevelop.XmlEditor.dll
MonoDevelop.Deployment       2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/MonoDevelop.Deployment/MonoDevelop.Deployment.dll
nunit.util                   2.4.8.0  /opt/monodevelop/lib/monodevelop/AddIns/NUnit/nunit.util.dll
nunit.framework              2.4.8.0  /opt/monodevelop/lib/monodevelop/AddIns/NUnit/nunit.framework.dll
nunit.core.interfaces        2.4.8.0  /opt/monodevelop/lib/monodevelop/AddIns/NUnit/nunit.core.interfaces.dll
nunit.core                   2.4.8.0  /opt/monodevelop/lib/monodevelop/AddIns/NUnit/nunit.core.dll
MonoDevelop.NUnit            2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/NUnit/MonoDevelop.NUnit.dll
MonoDevelop.DesignerSupport  2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/MonoDevelop.DesignerSupport/MonoDevelop.DesignerSupport.dll
MonoDeveloperExtensions      2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/MonoDeveloperExtensions/MonoDeveloperExtensions.dll
Mono.Debugging               0.0.0.0  /opt/monodevelop/lib/monodevelop/bin/Mono.Debugging.dll
pango-sharp                  2.12.0.0 /usr/lib/mono/gac/pango-sharp/2.12.0.0__35e10195dab3c99f/pango-sharp.dll
MonoDevelop.VersionControl   2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/VersionControl/MonoDevelop.VersionControl.dll
MonoDevelop.SourceEditor2    2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/MonoDevelop.SourceEditor2.dll
MonoDevelop.Debugger         2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/MonoDevelop.Debugger/MonoDevelop.Debugger.dll
monodoc                      1.0.0.0  /usr/lib/mono/gac/monodoc/1.0.0.0__0738eb9f132ed756/monodoc.dll
System.Drawing               4.0.0.0  /usr/lib/mono/gac/System.Drawing/4.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll
Mono.Cecil                   0.9.4.0  /opt/monodevelop/lib/monodevelop/bin/Mono.Cecil.dll
gnome-vfs-sharp              2.24.0.0 /usr/lib/mono/gac/gnome-vfs-sharp/2.24.0.0__35e10195dab3c99f/gnome-vfs-sharp.dll
gnome-sharp                  2.24.0.0 /usr/lib/mono/gac/gnome-sharp/2.24.0.0__35e10195dab3c99f/gnome-sharp.dll
GnomePlatform                2.6.0.0  /opt/monodevelop/lib/monodevelop/AddIns/GnomePlatform/GnomePlatform.dll
System.Configuration         4.0.0.0  /usr/lib/mono/gac/System.Configuration/4.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll
Mono.Cairo                   4.0.0.0  /usr/lib/mono/gac/Mono.Cairo/4.0.0.0__0738eb9f132ed756/Mono.Cairo.dll
gdk-sharp                    2.12.0.0 /usr/lib/mono/gac/gdk-sharp/2.12.0.0__35e10195dab3c99f/gdk-sharp.dll
Mono.TextEditor              1.0.0.0  /opt/monodevelop/lib/monodevelop/bin/Mono.TextEditor.dll
atk-sharp                    2.12.0.0 /usr/lib/mono/gac/atk-sharp/2.12.0.0__35e10195dab3c99f/atk-sharp.dll
gtk-sharp                    2.12.0.0 /usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll
Mono.Posix                   4.0.0.0  /usr/lib/mono/gac/Mono.Posix/4.0.0.0__0738eb9f132ed756/Mono.Posix.dll
Mono.Addins                  0.6.0.0  /usr/lib/mono/gac/Mono.Addins/0.6.0.0__0738eb9f132ed756/Mono.Addins.dll
Mono.Addins.Setup            0.6.0.0  /usr/lib/mono/gac/Mono.Addins.Setup/0.6.0.0__0738eb9f132ed756/Mono.Addins.Setup.dll
System.Xml                   4.0.0.0  /usr/lib/mono/gac/System.Xml/4.0.0.0__b77a5c561934e089/System.Xml.dll
System.Xml.Linq              4.0.0.0  /usr/lib/mono/gac/System.Xml.Linq/4.0.0.0__b77a5c561934e089/System.Xml.Linq.dll
System.Core                  4.0.0.0  /usr/lib/mono/gac/System.Core/4.0.0.0__b77a5c561934e089/System.Core.dll
glib-sharp                   2.12.0.0 /usr/lib/mono/gac/glib-sharp/2.12.0.0__35e10195dab3c99f/glib-sharp.dll
System                       4.0.0.0  /usr/lib/mono/gac/System/4.0.0.0__b77a5c561934e089/System.dll
MonoDevelop.Core             2.6.0.0  /opt/monodevelop/lib/monodevelop/bin/MonoDevelop.Core.dll
MonoDevelop.Ide              2.6.0.0  /opt/monodevelop/lib/monodevelop/bin/MonoDevelop.Ide.dll
MonoDevelop                  2.6.0.0  /opt/monodevelop/lib/monodevelop/bin/MonoDevelop.exe
mscorlib                     4.0.0.0  /usr/lib/mono/4.0/mscorlib.dll

---

### Post by directhex on 2012-01-26
So that looks like... Mono from Debian Experimental circa a month ago, plus self-compiled MonoDevelop?

---

### Post by JRz_ on 2012-01-26
I've been trying to get the "latest" version from git but without success.......

I've used the first option.

[http://chornsokun.wordpress.com/2011/11/11/build-monodevelop-on-ubuntu-11-10/](http://chornsokun.wordpress.com/2011/11/11/build-monodevelop-on-ubuntu-11-10/)

What is the best way to update get a good (recent) working version?

Thanks in advance and with best regards!!

---

### Post by JRz_ on 2012-01-26
I basicially got it working :D. I've scratched all and started using this guide (I think the accidental installation of a mac and meego package caused most of the problems):

[http://askubuntu.com/questions/91527/problem-installing-monodevelop-2-10-5-on-ubuntu-11-10](http://askubuntu.com/questions/91527/problem-installing-monodevelop-2-10-5-on-ubuntu-11-10)

The steps:

```
> git clone git://github.com/mono/monodevelop.git
```

```
> cd monodevelop
```

```
> ./configure
```

I selected the following packages:

```
1. [X] main
2. [X] extras/JavaBinding
3. [X] extras/ValaBinding
4. [X] extras/MonoDevelop.Database
5. [X] extras/MonoDevelop.Debugger.Gdb
6. [ ] extras/PyBinding
7. [ ] extras/MonoDevelop.MonoMac
8. [ ] extras/MonoDevelop.MeeGo
```

```
>sudo make
```

```
>make install
```

```
>monodevelop
```

Monodevelop is started and I've created a new console project:


```
using System;

namespace deleteme
{
	class MainClass
	{
		public static void Main (string[] args)
		{
			Console.WriteLine ("Hello World!");
		}
	}
}
```

When I run the console program everything goes fine. However, when I debug I get the following error:

```
System.NullReferenceException: Object reference not set to an instance of an object
  at MonoDevelop.Debugger.GtkConnectionDialog.RunDialog (System.String message) [0x0000c] in /home/jr/monodevelop/main/src/addins/MonoDevelop.Debugger/MonoDevelop.Debugger/DebuggingService.cs:979 
  at MonoDevelop.Debugger.GtkConnectionDialog+<SetMessage>c__AnonStoreyF.<>m__1C (System.Object , System.EventArgs ) [0x00000] in /home/jr/monodevelop/main/src/addins/MonoDevelop.Debugger/MonoDevelop.Debugger/DebuggingService.cs:968 
  at Gtk.Application+InvokeCB.Invoke () [0x00000] in <filename unknown>:0 
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] in <filename unknown>:0 
```

Preferred debugger: Mono soft debugger.

Monodevelop information:


```
MonoDevelop 2.8.6

Runtime:
	Mono 2.10.5 (Debian 2.10.5-1) (64-bit)
	GTK 2.24.6
	GTK# (2.12.0.0)
Build information:
	Git revision: 9c750e9a2ec4f6819de27acfb9b98317525da773-dirty
	Build date: 2012-01-26 22:48:32+0000
Operating System:
	Linux
	Linux ubuntu 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Loaded assemblies:
MonoDevelop.Debugger.Soft                  2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Debugger.Soft/MonoDevelop.Debugger.Soft.dll
Mono.Debugger.Soft                         0.0.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Debugger.Soft/Mono.Debugger.Soft.dll
Mono.Debugging.Soft                        0.0.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Debugger.Soft/Mono.Debugging.Soft.dll
MonoDevelop.DocFood                        1.0.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.DocFood.dll
gconf-sharp                                2.24.0.0       /usr/lib/mono/gac/gconf-sharp/2.24.0.0__35e10195dab3c99f/gconf-sharp.dll
MonoDevelop.HexEditor                      2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.HexEditor.dll
MonoDevelop.AssemblyBrowser                2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.AssemblyBrowser.dll
MonoDevelop.Database.Sql.Sqlite            2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Database/MonoDevelop.Database.Sql.Sqlite.dll
MonoDevelop.Database.Sql.MySql             2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Database/MonoDevelop.Database.Sql.MySql.dll
MonoDevelop.Database.Sql.SqlServer         2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Database/MonoDevelop.Database.Sql.SqlServer.dll
MonoDevelop.Database.Sql.Npgsql            2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Database/MonoDevelop.Database.Sql.Npgsql.dll
MonoDevelop.Database.Designer              2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Database/MonoDevelop.Database.Designer.dll
MonoDevelop.Database.Query                 2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Database/MonoDevelop.Database.Query.dll
MonoDevelop.Database.Components            2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Database/MonoDevelop.Database.Components.dll
MonoDevelop.Database.Sql                   2.2.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Database/MonoDevelop.Database.Sql.dll
ChangeLogAddIn                             2.6.0.0        /usr/local/lib/monodevelop/AddIns/ChangeLogAddIn/ChangeLogAddIn.dll
MonoDevelop.Projects.Formats.MSBuild       1.0.0.0        /usr/local/lib/monodevelop/bin/MonoDevelop.Projects.Formats.MSBuild.exe
ILAsmBinding                               2.6.0.0        /usr/local/lib/monodevelop/AddIns/BackendBindings/ILAsmBinding.dll
OldNRefactory                              2.1.1.0        /usr/local/lib/monodevelop/bin/OldNRefactory.dll
ICSharpCode.NRefactory                     1.0.4408.42568 /usr/local/lib/monodevelop/bin/ICSharpCode.NRefactory.dll
JavaBinding                                2.6.0.0        /usr/local/lib/monodevelop/AddIns/JavaBinding/JavaBinding.dll
I18N.Rare                                  4.0.0.0        /usr/lib/mono/gac/I18N.Rare/4.0.0.0__0738eb9f132ed756/I18N.Rare.dll
I18N.CJK                                   4.0.0.0        /usr/lib/mono/gac/I18N.CJK/4.0.0.0__0738eb9f132ed756/I18N.CJK.dll
I18N.MidEast                               4.0.0.0        /usr/lib/mono/gac/I18N.MidEast/4.0.0.0__0738eb9f132ed756/I18N.MidEast.dll
I18N.Other                                 4.0.0.0        /usr/lib/mono/gac/I18N.Other/4.0.0.0__0738eb9f132ed756/I18N.Other.dll
I18N.West                                  4.0.0.0        /usr/lib/mono/gac/I18N.West/4.0.0.0__0738eb9f132ed756/I18N.West.dll
I18N                                       4.0.0.0        /usr/lib/mono/gac/I18N/4.0.0.0__0738eb9f132ed756/I18N.dll
ICSharpCode.SharpZipLib                    2.84.0.0       /usr/lib/mono/gac/ICSharpCode.SharpZipLib/2.84.0.0__1b03e6acf1164f73/ICSharpCode.SharpZipLib.dll
Mono.Security                              4.0.0.0        /usr/lib/mono/gac/Mono.Security/4.0.0.0__0738eb9f132ed756/Mono.Security.dll
mdhost                                     1.0.0.0        /usr/local/lib/monodevelop/bin/mdhost.exe
System.Runtime.Remoting                    4.0.0.0        /usr/lib/mono/gac/System.Runtime.Remoting/4.0.0.0__b77a5c561934e089/System.Runtime.Remoting.dll
MonoDeveloperExtensions_nunit              0.0.0.0        /usr/local/lib/monodevelop/AddIns/MonoDeveloperExtensions/MonoDeveloperExtensions_nunit.dll
MonoDevelop.MsVisualStudio                 2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.MsVisualStudio/MonoDevelop.MsVisualStudio.dll
MonoDevelop.VBNetBinding                   2.6.0.0        /usr/local/lib/monodevelop/AddIns/BackendBindings/MonoDevelop.VBNetBinding.dll
MonoDevelop.CSharpBinding                  2.6.0.0        /usr/local/lib/monodevelop/AddIns/BackendBindings/MonoDevelop.CSharpBinding.dll
MonoDevelop.AspNet.Mvc                     2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.AspNet.Mvc/MonoDevelop.AspNet.Mvc.dll
MonoDevelop.TextTemplating                 2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.TextTemplating/MonoDevelop.TextTemplating.dll
Mono.TextTemplating                        0.0.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.TextTemplating/Mono.TextTemplating.dll
MonoDevelop.CBinding                       2.6.0.0        /usr/local/lib/monodevelop/AddIns/BackendBindings/MonoDevelop.CBinding.dll
MonoDevelop.Refactoring                    2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Refactoring/MonoDevelop.Refactoring.dll
MonoDevelop.WebReferences                  2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.WebReferences/MonoDevelop.WebReferences.dll
MonoDevelop.ValaBinding                    2.6.0.0        /usr/local/lib/monodevelop/AddIns/BackendBindings/MonoDevelop.ValaBinding.dll
MonoDevelop.Deployment.Linux               2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Deployment/MonoDevelop.Deployment.Linux.dll
MonoDevelop.GtkCore                        2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.GtkCore/MonoDevelop.GtkCore.dll
libsteticui                                0.0.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.GtkCore/libsteticui.dll
libstetic                                  0.0.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.GtkCore/libstetic.dll
MonoDevelop.Gettext                        2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Gettext/MonoDevelop.Gettext.dll
MonoDevelop.Autotools                      2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Autotools/MonoDevelop.Autotools.dll
Sharpen                                    1.0.0.0        /usr/local/lib/monodevelop/AddIns/VersionControl/Sharpen.dll
NGit                                       1.0.0.0        /usr/local/lib/monodevelop/AddIns/VersionControl/NGit.dll
MonoDevelop.VersionControl.Git             2.6.0.0        /usr/local/lib/monodevelop/AddIns/VersionControl/MonoDevelop.VersionControl.Git.dll
MonoDevelop.VersionControl.Subversion.Unix 2.6.0.0        /usr/local/lib/monodevelop/AddIns/VersionControl/MonoDevelop.VersionControl.Subversion.Unix.dll
MonoDevelop.VersionControl.Subversion      2.6.0.0        /usr/local/lib/monodevelop/AddIns/VersionControl/MonoDevelop.VersionControl.Subversion.dll
MonoDevelop.CodeMetrics                    2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.CodeMetrics/MonoDevelop.CodeMetrics.dll
nunit.util                                 2.4.8.0        /usr/local/lib/monodevelop/AddIns/NUnit/nunit.util.dll
nunit.framework                            2.4.8.0        /usr/local/lib/monodevelop/AddIns/NUnit/nunit.framework.dll
nunit.core.interfaces                      2.4.8.0        /usr/local/lib/monodevelop/AddIns/NUnit/nunit.core.interfaces.dll
nunit.core                                 2.4.8.0        /usr/local/lib/monodevelop/AddIns/NUnit/nunit.core.dll
MonoDevelop.NUnit                          2.6.0.0        /usr/local/lib/monodevelop/AddIns/NUnit/MonoDevelop.NUnit.dll
MonoDevelop.Moonlight                      2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Moonlight/MonoDevelop.Moonlight.dll
MonoDevelop.AspNet                         2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.AspNet/MonoDevelop.AspNet.dll
MonoDevelop.XmlEditor                      2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.XmlEditor/MonoDevelop.XmlEditor.dll
MonoDevelop.Deployment                     2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Deployment/MonoDevelop.Deployment.dll
MonoDevelop.DesignerSupport                2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.DesignerSupport/MonoDevelop.DesignerSupport.dll
MonoDeveloperExtensions                    2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDeveloperExtensions/MonoDeveloperExtensions.dll
Mono.Debugging                             0.0.0.0        /usr/local/lib/monodevelop/bin/Mono.Debugging.dll
pango-sharp                                2.12.0.0       /usr/lib/mono/gac/pango-sharp/2.12.0.0__35e10195dab3c99f/pango-sharp.dll
MonoDevelop.VersionControl                 2.6.0.0        /usr/local/lib/monodevelop/AddIns/VersionControl/MonoDevelop.VersionControl.dll
MonoDevelop.SourceEditor2                  2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.SourceEditor2.dll
MonoDevelop.Debugger                       2.6.0.0        /usr/local/lib/monodevelop/AddIns/MonoDevelop.Debugger/MonoDevelop.Debugger.dll
monodoc                                    1.0.0.0        /usr/lib/mono/gac/monodoc/1.0.0.0__0738eb9f132ed756/monodoc.dll
System.Drawing                             4.0.0.0        /usr/lib/mono/gac/System.Drawing/4.0.0.0__b03f5f7f11d50a3a/System.Drawing.dll
Mono.Cecil                                 0.9.4.0        /usr/local/lib/monodevelop/bin/Mono.Cecil.dll
gnome-vfs-sharp                            2.24.0.0       /usr/lib/mono/gac/gnome-vfs-sharp/2.24.0.0__35e10195dab3c99f/gnome-vfs-sharp.dll
gnome-sharp                                2.24.0.0       /usr/lib/mono/gac/gnome-sharp/2.24.0.0__35e10195dab3c99f/gnome-sharp.dll
GnomePlatform                              2.6.0.0        /usr/local/lib/monodevelop/AddIns/GnomePlatform/GnomePlatform.dll
System.Configuration                       4.0.0.0        /usr/lib/mono/gac/System.Configuration/4.0.0.0__b03f5f7f11d50a3a/System.Configuration.dll
Mono.Cairo                                 2.0.0.0        /usr/lib/mono/gac/Mono.Cairo/2.0.0.0__0738eb9f132ed756/Mono.Cairo.dll
gdk-sharp                                  2.12.0.0       /usr/lib/mono/gac/gdk-sharp/2.12.0.0__35e10195dab3c99f/gdk-sharp.dll
Mono.TextEditor                            1.0.0.0        /usr/local/lib/monodevelop/bin/Mono.TextEditor.dll
atk-sharp                                  2.12.0.0       /usr/lib/mono/gac/atk-sharp/2.12.0.0__35e10195dab3c99f/atk-sharp.dll
glib-sharp                                 2.12.0.0       /usr/lib/mono/gac/glib-sharp/2.12.0.0__35e10195dab3c99f/glib-sharp.dll
gtk-sharp                                  2.12.0.0       /usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll
Mono.Posix                                 4.0.0.0        /usr/lib/mono/gac/Mono.Posix/4.0.0.0__0738eb9f132ed756/Mono.Posix.dll
Mono.Addins                                0.6.0.0        /usr/lib/mono/gac/Mono.Addins/0.6.0.0__0738eb9f132ed756/Mono.Addins.dll
Mono.Addins.Setup                          0.6.0.0        /usr/lib/mono/gac/Mono.Addins.Setup/0.6.0.0__0738eb9f132ed756/Mono.Addins.Setup.dll
System.Xml                                 4.0.0.0        /usr/lib/mono/gac/System.Xml/4.0.0.0__b77a5c561934e089/System.Xml.dll
System.Xml.Linq                            4.0.0.0        /usr/lib/mono/gac/System.Xml.Linq/4.0.0.0__b77a5c561934e089/System.Xml.Linq.dll
System.Core                                4.0.0.0        /usr/lib/mono/gac/System.Core/4.0.0.0__b77a5c561934e089/System.Core.dll
System                                     4.0.0.0        /usr/lib/mono/gac/System/4.0.0.0__b77a5c561934e089/System.dll
MonoDevelop.Core                           2.6.0.0        /usr/local/lib/monodevelop/bin/MonoDevelop.Core.dll
MonoDevelop.Ide                            2.6.0.0        /usr/local/lib/monodevelop/bin/MonoDevelop.Ide.dll
MonoDevelop                                2.6.0.0        /usr/local/lib/monodevelop/bin/MonoDevelop.exe
mscorlib                                   4.0.0.0        /usr/lib/mono/4.0/mscorlib.dll
```

---

### Post by directhex on 2012-01-28
Your error looks like a transient error with MonoDevelop git master

Basically, I can't reproduce your issues locally

---

