---
title: "Compile C# on 10.04"
date: 2010-08-10
forum: Programming Talk
---

### Post by ugm6hr on 2010-08-10
Please forgive the absolute lack of knowledge I have...

I want to install [http://sourceforge.net/projects/ecgtoolkit-cs/files/](http://sourceforge.net/projects/ecgtoolkit-cs/files/) on Ubuntu.

It appears it comes in XP compiled exe files, but the source is also available.

Is it possible to compile using mono-devel? If so, how? If it is complicated, don't worry, I'll find an alternative.

---

### Post by VH-BIL on 2010-08-10
> **ugm6hr said:**
> Please forgive the absolute lack of knowledge I have...

I want to install [http://sourceforge.net/projects/ecgtoolkit-cs/files/](http://sourceforge.net/projects/ecgtoolkit-cs/files/) on Ubuntu.

It appears it comes in XP compiled exe files, but the source is also available.

Is it possible to compile using mono-devel? If so, how? If it is complicated, don't worry, I'll find an alternative.

If there is a .sln (Solution) file, it is as simple as loading that file in monodevelop and clicking "Build ALL" or pressing F8.

---

### Post by ugm6hr on 2010-08-10
> **VH-BIL said:**
> If there is a .sln (Solution) file, it is as simple as loading that file in monodevelop and clicking "Build ALL" or pressing F8.

Thanks.

There are a lot of .sln files, presumably I do that for each one.

---

### Post by VH-BIL on 2010-08-10
> **ugm6hr said:**
> Thanks.

There are a lot of .sln files, presumably I do that for each one.

I guess as I am not sure what you are trying to compile without downloading the file.

This may help:
A .sln (Solution) is a collection of .csproj (Project) files. So loading a solution in monodevelop will load the relevant projects and clicking "Build All" or pressing F8 will compile those projects.

If there is more then one solution there would be project(s) associated with those solutions that may need to be compiled.

The reason there can be  more then one project in a solution is if you are making an executable project it may need a .dll library project to go with it and a solution is a way of developing them all together.

Hope this helps.

---

### Post by phrostbyte on 2010-08-10
You don't necessary need monodevelop to compile. Mono-devel and the "xbuild" command will do it.

eg: xbuild <path to *.sln>

---

### Post by ugm6hr on 2010-08-11
OK. I went down the monodevelop route...

1 of the sln files appears to load 8 projects, which makes sense.

When loading, it asks to convert to Visual Basic 2005 or MonoDevelop, since it looks like it is a VS2003 file. Irrespective of which I select, it imports OK.

However, when building, there appear to 7 errors, all of which read:
Unsafe code requires the 'unsafe' command line option to be specified (CS0227) in ECGTool.cs

Unfortunately, I have no idea what I'm doing...

---

### Post by WitchCraft on 2010-08-11
Did you run file on the .exe ?
It's probably a managed executable (=.NET bytecode).
If so, you don't need to recompile, you just need to install the .NET framework (called mono on Linux).

That means you need to install mono
apt-get install mono-complete


Then you start the .exe file with:
mono /path/to/xy.exe

Just as wine.
And just as wine, if you install binfmt-support, you can just start the .exe with:
/path/to/xy.exe

(Keep in mind that the visual basic runtime ships separately. mono/monodevelop comes with C# only by default).


Also, the mono edition that ships with ubuntu is slightly outdated. 
If you need a newer version, keep to this tutorial:
[http://www.centriment.com/2009/04/01/building-mono-24-from-source-on-ubuntu-810/](http://www.centriment.com/2009/04/01/building-mono-24-from-source-on-ubuntu-810/)
and just replace 2.4 with 2.6

You should read this one first:
[http://www.mono-project.com/Parallel_Mono_Environments](http://www.mono-project.com/Parallel_Mono_Environments)

Also, keep in mind that if the .NET program makes calls to the windows API (when written in a windows-only fashion), it will crash. It can also crash because of bugs in mono, or because the mono version of ubuntu (2.4) is outdated, which means it contains a lot of bugs that have already been fixed in the 2.6 stable version.

---

### Post by VH-BIL on 2010-08-11
> **ugm6hr said:**
> Unsafe code requires the 'unsafe' command line option to be specified (CS0227) in ECGTool.cs

I have not done any unsafe code in monodevelop only in Visual Studio. I am pretty sure it is asking you to do this:

*) Right click on the project that has the ECGTool.cs file
*) Click Options
*) Click Compiler
*) Add "-unsafe" (with out quotes) in Additional arguments.
*) Click OK

The try recompile.

Let me know how you go...

---

### Post by ugm6hr on 2010-08-12
> **WitchCraft said:**
> Did you run file on the .exe ?
It's probably a managed executable (=.NET bytecode).
If so, you don't need to recompile, you just need to install the .NET framework (called mono on Linux).

That means you need to install mono
apt-get install mono-complete

It comes in a number of different forms, both as an msi (which I presume is the Windows installer - and installs OK on Windows), as well as a zipped archive of .exe and source.

I'll try this on the 4 .exe files tonight. So far, I've been using the source files, since I presumed that the exe files would be of no use.

Presumably, there should no no problem using a script to launch all 4 exe's in mono at the same time?

---

### Post by ugm6hr on 2010-08-12
> **VH-BIL said:**
> Let me know how you go...

Will do - I'll try the exe files first, cos that seems like a simple solution (assuming it works)...

---

### Post by ugm6hr on 2010-08-12
OK. Don't seem to have gotten any further...

1. Plan A:
```
mono ECGViewer.exe

Unhandled Exception: System.Runtime.Serialization.SerializationException: Field "dateTimeOffsetPattern" not found in class System.Globalization.DateTimeFormatInfo
  at System.Runtime.Serialization.Formatters.Binary.ObjectReader.ReadTypeMetadata (System.IO.BinaryReader reader, Boolean isRuntimeObject, Boolean hasTypeInfo) [0x00000] 
  at System.Runtime.Serialization.Formatters.Binary.ObjectReader.ReadObjectInstance (System.IO.BinaryReader reader, Boolean isRuntimeObject, Boolean hasTypeInfo, System.Int64& objectId, System.Object& value, System.Runtime.Serialization.SerializationInfo& info) [0x00000] 
  at System.Runtime.Serialization.Formatters.Binary.ObjectReader.ReadObject (BinaryElement element, System.IO.BinaryReader reader, System.Int64& objectId, System.Object& value, System.Runtime.Serialization.SerializationInfo& info) [0x00000] 
  at System.Runtime.Serialization.Formatters.Binary.ObjectReader.ReadNextObject (System.IO.BinaryReader reader) [0x00000] 
  at System.Runtime.Serialization.Formatters.Binary.ObjectReader.ReadObjectGraph (BinaryElement elem, System.IO.BinaryReader reader, Boolean readHeaders, System.Object& result, System.Runtime.Remoting.Messaging.Header[]& headers) [0x00000] 
  at System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.NoCheckDeserialize (System.IO.Stream serializationStream, System.Runtime.Remoting.Messaging.HeaderHandler handler) [0x00000] 
  at System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize (System.IO.Stream serializationStream) [0x00000] 
  at System.Resources.ResourceReader.ReadNonPredefinedValue (System.Type exp_type) [0x00000] 
  at System.Resources.ResourceReader.ReadValueVer2 (Int32 type_index) [0x00000] 
  at System.Resources.ResourceReader.LoadResourceValues (.ResourceCacheItem[] store) [0x00000] 
  at System.Resources.ResourceReader+ResourceEnumerator.FillCache () [0x00000] 
  at System.Resources.ResourceReader+ResourceEnumerator..ctor (System.Resources.ResourceReader readerToEnumerate) [0x00000] 
  at System.Resources.ResourceReader.GetEnumerator () [0x00000] 
  at System.Resources.ResourceSet.ReadResources () [0x00000] 
  at System.Resources.ResourceSet.GetObjectInternal (System.String name, Boolean ignoreCase) [0x00000] 
  at System.Resources.ResourceSet.GetObject (System.String name, Boolean ignoreCase) [0x00000] 
  at System.Resources.RuntimeResourceSet.GetObject (System.String name, Boolean ignoreCase) [0x00000] 
  at System.Resources.ResourceManager.GetObject (System.String name, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Resources.ResourceManager.GetObject (System.String name) [0x00000] 
  at ECGViewer.ECGViewer.InitializeComponent () [0x00000] 
  at ECGViewer.ECGViewer..ctor (System.String[] args) [0x00000] 
  at (wrapper remoting-invoke-with-check) ECGViewer.ECGViewer:.ctor (string[])
  at ECGViewer.ECGViewer.Main (System.String[] args) [0x00000]
```

2. Plan B
Adding -unsafe made no difference when compiling.

I'm going on holiday on Saturday, so may leave this til I return in 2 weeks...

---

### Post by VH-BIL on 2010-08-12
I just noticed there is a compressed package of compiled executables:
[http://sourceforge.net/projects/ecgtoolkit-cs/files/ecgtoolkit-cs/ecgtoolkit-cs-2_2/ECGToolkit-bin-2_2.zip/download](http://sourceforge.net/projects/ecgtoolkit-cs/files/ecgtoolkit-cs/ecgtoolkit-cs-2_2/ECGToolkit-bin-2_2.zip/download)

I downloaded it and got the same error so you did compile correctly. I copied the files to my WindowsXP32 VirtualBox virtual machine and ran the same file and it worked. I think they did not code for multi platform compatibility.

If you need to use the program, I am pretty sure you have to use a windows machine or a virtual machine in Linux.

---

### Post by ugm6hr on 2010-08-13
Thanks a lot.

They have published in scientific journals that it is cross-platform, which is why I thought it might work.

Thanks anyway.

---

### Post by VH-BIL on 2010-08-13
> **ugm6hr said:**
> Thanks a lot.

They have published in scientific journals that it is cross-platform, which is why I thought it might work.

Thanks anyway.
If that is the case you can try downloading an earlier binary as they may have broken the Linux compatibility.

---

### Post by ugm6hr on 2010-08-13
Apologies to all... I have resolved the problem.

The v2.2-2K3 files work with mono-complete as per WitchCraft's advice.

```
mono ECGViewer.exe
```

Thanks.

---

### Post by VH-BIL on 2010-08-13
Sorry I did not have "sudo apt-get install mono-complete" installed either, just what I needed to develop my projects. I installed mono-complete and the exe ran successfully.

---

