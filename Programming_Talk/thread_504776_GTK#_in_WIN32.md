---
title: "GTK# in WIN32"
date: 2007-07-19
forum: Programming Talk
---

### Post by Lycaon on 2007-07-19
So i had this great idea, make an app in MonoDevelop and the gui with GTK#. It claims to be platform independent and simple to run on both os's (ubuntu <-> winxp).

To safe you guys all the stuff i've done i will keep it simple. With monodevelop you can create an example GTK# project, if you run this it will display an empty window. Great so it works on ubuntu!

Now the problem, try to run that simple exe in winxp sp2 with .net 2.0 installed. First you should have downloaded the gtk# runtime libraries for win32. So i got redirected by the gtk sharp page to: [http://forge.novell.com/modules/xfmod/project/?gtks-inst4win](http://forge.novell.com/modules/xfmod/project/?gtks-inst4win).
After downloading i installed the runtime packages. In the readme isn't anything special written about installing, so i assumed everything went ok. Well it's not, the example program just fails. 

If i run this progam via msprompt i can get some error output, and here it is:
>  Unhandled Exception: System.IO.FileNotFoundException: Could not load file or ***
embly 'glade-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195da
b3c99f' or one of its dependencies. Het systeem kan het opgegeven bestand niet v
inden.
File name: 'glade-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10
195dab3c99f'
   at GladeApp..ctor(String[] args)
   at GladeApp.Main(String[] args)

WRN: Assembly binding logging is turned OFF.
To enable assembly bind failure logging, set the registry value [HKLM\Software\M
icrosoft\Fusion!EnableLog] (DWORD) to 1.
Note: There is some performance penalty associated with assembly bind failure lo
gging.
To turn this feature off, remove the registry value [HKLM\Software\Microsoft\Fus
ion!EnableLog].

But i did install the library, does it matter that this library is for .net 1.1? 
I've read some discussion's on google about registering .dll's with GAC, but i'm fairly new to .net and have no clue what i should do now. (im a c/c++ programmer). 

Is there a nice solution to this? For example, i don't wanna give a program to a windows user and with it a 5 pages long manual how to get GTK# working on his machine.

Thanks in advance!

---

### Post by Lycaon on 2007-07-24
OK i've spoken with some developers, and the issue would be that ubuntu by default uses GTK# libraries wich have version 2.10.0. Windows instead does only have the GTK# libraries with version 2.08.0.
So i browsed the web again, asked allot of people and none could really help me. There was one solution, copy all dll's that are gtk# related from your windows box onto ubuntu, in your project directory. When building a new GTK# application you should manually reference every dll (from the windows box) into you project instead of those that are shipped with ubuntu. 

So i did that now i get this error while running in linux (didnt try at windows):
> 
Unhandled Exception: System.DllNotFoundEception: libgtk-win32-2.0.0.dll
  at (wrapper managed-to-native) Gtk.Application:gtk_init(int&,intptr&)
  at (Gtk.Application.Init() [0x00000]


Does anyone have some ideas about this?

Does it mean it wants to malloc something at address 0x00000?? Because that can never be done..well once again im clueless.

Thanks in advance!

---

