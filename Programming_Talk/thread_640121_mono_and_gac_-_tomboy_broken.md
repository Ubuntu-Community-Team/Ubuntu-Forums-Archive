---
title: "mono and gac - tomboy broken"
date: 2007-12-13
forum: Programming Talk
---

### Post by mp035 on 2007-12-13
Hello all, this is as much a question about mono as a help request for tomboy so I hope I'm posting this in the right place.

Basically, tomboy stopped working after I installed mono from the binary installer mono-1.2.5.1_3-installer.bin.

I installed the new verson of mono to ~/bin/mono so that it would not affect my existing mono installation, but this obviously did not help.

Running tomboy from the console produces:
```
mark@linuxbox:~$ tomboy

** (/usr/lib/tomboy/Tomboy.exe:8239): WARNING **: The following assembly referenced from /usr/lib/tomboy/Tomboy.exe could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=2)
     Version:    2.16.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/tomboy).


** (/usr/lib/tomboy/Tomboy.exe:8239): WARNING **: Could not load file or assembly 'gnome-sharp, Version=2.16.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

** (/usr/lib/tomboy/Tomboy.exe:8239): WARNING **: The following assembly referenced from /usr/lib/tomboy/Tomboy.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.10.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/tomboy).


** (/usr/lib/tomboy/Tomboy.exe:8239): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Tomboy.Tomboy' from assembly 'Tomboy, Version=0.0.0.0, Culture=neutral'.
```

so I googled a bit and checked the mono gac contents with:

```
mark@linuxbox:~$ gacutil -l |grep gtk
gtk-dotnet, Version=2.8.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
gtk-sharp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
gtk-sharp, Version=2.8.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
gtkhtml-sharp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
gtkhtml-sharp, Version=2.8.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
gtksourceview-sharp, Version=1.0.0.2, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.4.gtk-dotnet, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.4.gtk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.4.gtkhtml-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.6.gtk-dotnet, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.6.gtk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.6.gtkhtml-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
```

and

```
mark@linuxbox:~$ gacutil -l |grep gnome
gnome-sharp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
gnome-sharp, Version=2.8.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
gnome-vfs-sharp, Version=2.8.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.4.gnome-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.4.gnome-vfs-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.6.gnome-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.6.gnome-vfs-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
```

obviously the versions in the gac are older than the required libraries, so I checked the installed files with:

```
mark@linuxbox:~$ ls /usr/lib/mono/gac/gnome-sharp/
1.0.0.0__35e10195dab3c99f  2.16.0.0__35e10195dab3c99f
```
and
```
mark@linuxbox:~$ ls /usr/lib/mono/gac/gtk-sharp/
1.0.0.0__35e10195dab3c99f  2.10.0.0__35e10195dab3c99f
```

and it looks like the files are there, but the gac is somehow not recognizing it. Does anyone know how I can make the mono gac recognize these assemblies? or how to install them again to make tomboy work?

Thanks and Best Regards.

---

### Post by sirjuh on 2008-04-04
Hello,

Try using *gacutil -i path_to_dll* to register the required dlls.

I had the same issue with Tomboy, and I've finally got rid of it with: 

```

gacutil -i /usr/lib/mono/gac/gnome-sharp/2.16.0.0__35e10195dab3c99f/gnome-sharp.dll
gacutil -i /usr/lib/mono/gac/gtk-sharp/2.10.0.0__35e10195dab3c99f/gtk-sharp.dll
gacutil -i /usr/lib/mono/gac/glib-sharp/2.10.0.0__35e10195dab3c99f/
gacutil -i /usr/lib/mono/gac/glib-sharp/2.10.0.0__35e10195dab3c99f/glib-sharp.dll
gacutil -i /usr/lib/mono/gac/atk-sharp/2.10.0.0__35e10195dab3c99f/atk-sharp.dll
gacutil -i /usr/lib/mono/gac/gdk-sharp/2.10.0.0__35e10195dab3c99f/gdk-sharp.dll
gacutil -i /usr/lib/mono/gac/gconf-sharp/2.16.0.0__35e10195dab3c99f/gconf-sharp.dll
gacutil -i /usr/lib/mono/gac/pango-sharp/2.10.0.0__35e10195dab3c99f/pango-sharp.dll
gacutil -i /usr/lib/mono/gac/NDesk.DBus/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.dll
gacutil -i /usr/lib/mono/gac/NDesk.DBus.GLib/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.GLib.dll
gacutil -i /usr/lib/mono/gac/gmime-sharp/2.2.0.0__677013d4cb5910f0/gmime-sharp.dll

```

I hope it will help.

Best regards,

---

### Post by BhRaviKiran on 2008-04-04
HI,
    How did u install the mono on Ubuntu using bin file. Plz help us.

Thanks & regards,
Ravi.

---

### Post by nkijak on 2008-04-27
I'm having similar problems with anything that runs on mono after updating to 8.04 from 7.10.  When I tried the steps listed here it would remove the values from the gac directory.  So I tried re-installing the .dll's to the gac and this is what happens (I had tried this with gtk-sharp first but the output is the same):
```

 sudo gacutil -i /usr/lib/mono/gtk-sharp-2.0/gtk-dotnet.dll 

Unhandled Exception: System.IO.FileNotFoundException: Could not find file "/usr/lib/mono/gtk-sharp-2.0/gtk-dotnet.dll" or "/usr/lib/mono/gac/gtk-dotnet/2.12.0.0__35e10195dab3c99f/gtk-dotnet.dll"
File name: "/usr/lib/mono/gtk-sharp-2.0/gtk-dotnet.dll" or "/usr/lib/mono/gac/gtk-dotnet/2.12.0.0__35e10195dab3c99f/gtk-dotnet.dll"
  at System.IO.File.Copy (System.String src, System.String dest, Boolean overwrite) [0x00000] 
  at Mono.Tools.Driver.Copy (System.String source, System.String target, Boolean v) [0x00000] 
  at Mono.Tools.Driver.Install (Boolean check_refs, System.String name, System.String package, System.String gacdir, System.String link_gacdir, System.String libdir, System.String link_libdir) [0x00000] 
  at Mono.Tools.Driver.Main (System.String[] args) [0x00000] 

```
Then when I try to run the exact command immediately following I get a different error:
```

 sudo gacutil -i /usr/lib/mono/gtk-sharp-2.0/gtk-dotnet.dll 
Failure adding assembly to the cache: The file specified is not a valid assembly.

```
I'm not familiar with mono at all, I'm just trying to get my mono applications working again.

---

### Post by nEbhotep on 2008-07-17
Im with the same problem :S. Can somebody help us?

I try to remove all mono and reinstall but didn't work...

Thank u!

---

### Post by guardante on 2009-02-10
For some reason when, for example, manually compiled, gnome-sharp and other libs are not registered in GAC, though are put in the correct location.
So, you have to manually rescan GAC:

cd /usr/lib/mono/gac # assuming this is your main gac
sudo find . */*/*.dll -exec gacutil -i '{}' \;

Ignore all the warnings.

---

### Post by directhex on 2009-02-10
> **guardante said:**
> For some reason when, for example, manually compiled, gnome-sharp and other libs are not registered in GAC, though are put in the correct location.
So, you have to manually rescan GAC:

cd /usr/lib/mono/gac # assuming this is your main gac
sudo find . */*/*.dll -exec gacutil -i '{}' \;

Ignore all the warnings.

And don't expect an iota of support if you file any bugs via launchpad

---

### Post by akvik on 2009-11-11
> **guardante said:**
> 

cd /usr/lib/mono/gac # assuming this is your main gac
sudo find . */*/*.dll -exec gacutil -i '{}' \;

Ignore all the warnings.

Yep, this worked for me :-)

---

### Post by cblair2k2 on 2010-01-15
> **guardante said:**
> For some reason when, for example, manually compiled, gnome-sharp and other libs are not registered in GAC, though are put in the correct location.
So, you have to manually rescan GAC:

cd /usr/lib/mono/gac # assuming this is your main gac
sudo find . */*/*.dll -exec gacutil -i '{}' \;

Ignore all the warnings.

[guardante]("http://ubuntuforums.org/member.php?u=766939") fixed all my problems.  I looked FOREVER googling monodevelop with multiple different forums never giving me an answer that worked.  I ran across something saying that F-Spot and Tomboy use mono and should be installed by default with Ubuntu 9.10 so you should have mono and monodevelop should work.  Anyhow this fixed it and am VERY GRATEFUL there are people like him to solve my stupid issues.!  Thanks

---

