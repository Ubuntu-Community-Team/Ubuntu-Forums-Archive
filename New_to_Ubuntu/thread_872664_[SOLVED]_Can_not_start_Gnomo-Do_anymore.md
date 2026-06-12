---
title: "[SOLVED] Can not start Gnomo-Do anymore"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by wariskampar on 2008-07-28
I don't know what have I done but today I can not start this great program anymore. However I remember, I change it theme to Glass theme from default and afterward I can not launch it (Super+Spacebar or At+F2 or Click on icon). Already restart several times but problem persist. Hope anyone can suggest me a good solution. Thanks in advance

---

### Post by billgoldberg on 2008-07-28
Open a terminal (applications -> accessories -> terminal) and type

```
gnome-do
```

Then post the errors here.

---

### Post by wariskampar on 2008-07-28
Thanks man! I forget how easy it is to troubleshoot problem in Linux. Btw, here is the error message. Now, I just remember that I did upgrade Evolution plugin for Gnome Do. Now, what should I do 


aznan@aznan-laptop:~$ gnome-do

** (Do:8885): WARNING **: The following assembly referenced from /home/aznan/.local/share/gnome-do/plugins/addins/Do.Evolution.1.2/Evolution.dll could not be loaded:
     Assembly:   evolution-sharp    (assemblyref_index=2)
     Version:    3.0.0.0
     Public Key: 457eed85bd9370df
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/aznan/.local/share/gnome-do/plugins/addins/Do.Evolution.1.2).


** (Do:8885): WARNING **: Could not load file or assembly 'evolution-sharp, Version=3.0.0.0, Culture=neutral, PublicKeyToken=457eed85bd9370df' or one of its dependencies.
Stacktrace:

Segmentation fault

---

### Post by billgoldberg on 2008-07-28
> **wariskampar said:**
> Thanks man! I forget how easy it is to troubleshoot problem in Linux. Btw, here is the error message. Now, I just remember that I did upgrade Evolution plugin for Gnome Do. Now, what should I do 


aznan@aznan-laptop:~$ gnome-do

** (Do:8885): WARNING **: The following assembly referenced from /home/aznan/.local/share/gnome-do/plugins/addins/Do.Evolution.1.2/Evolution.dll could not be loaded:
     Assembly:   evolution-sharp    (assemblyref_index=2)
     Version:    3.0.0.0
     Public Key: 457eed85bd9370df
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/aznan/.local/share/gnome-do/plugins/addins/Do.Evolution.1.2).


** (Do:8885): WARNING **: Could not load file or assembly 'evolution-sharp, Version=3.0.0.0, Culture=neutral, PublicKeyToken=457eed85bd9370df' or one of its dependencies.
Stacktrace:

Segmentation fault

I don't use gnome-do but judging by the errors, removing the evolution add on should do it.

---

### Post by wariskampar on 2008-07-28
How do I remove the add-on if I can not even launch the program.

---

### Post by wariskampar on 2008-07-28
Problem solved! I purge gnome-do and the plugin folder from my sys and re-install. Everything back to normal now. Thanks billgoldberg. You shed some light on my problem

---

### Post by billgoldberg on 2008-07-28
> **wariskampar said:**
> How do I remove the add-on if I can not even launch the program.

Remove Do.Evolution.1.2 from here: ```
/home/aznan/.local/share/gnome-do/plugins/addins/
```

---

### Post by billgoldberg on 2008-07-28
No problem.

---

### Post by tehtrk on 2008-09-19
Hey guys, if you're like me and want to use the Evolution plugin for Gnome-do, then the problem is easily remedied with:

```
sudo apt-get install libevolution3.0-cil
```The problem is that it's missing a MONO assembly for Evolution, as stated in the errors given when you try to run Gnome-Do without it. More info can be found here:

[https://bugs.launchpad.net/do/+bug/254350](https://bugs.launchpad.net/do/+bug/254350)

HTH,


JP

---

### Post by kanamor on 2009-04-18
> **tehtrk said:**
> Hey guys, if you're like me and want to use the Evolution plugin for Gnome-do, then the problem is easily remedied with:

```
sudo apt-get install libevolution3.0-cil
```The problem is that it's missing a MONO assembly for Evolution, as stated in the errors given when you try to run Gnome-Do without it. More info can be found here:

[https://bugs.launchpad.net/do/+bug/254350](https://bugs.launchpad.net/do/+bug/254350)

HTH,


JP


Thank you very much tehtrk!

---

### Post by yogeshg1987 on 2009-08-02
Hi, pls help me out:

yogesh@yogesh-laptop:~$ gnome-do

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Stdlib ---> System.DllNotFoundException: libMonoPosixHelper.so
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:GetDefaultSignal ()
  at Mono.Unix.Native.Stdlib..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Unix.UnixMarshal.AllocHeap (Int64 size) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, Int32 index, Int32 count, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s) [0x00000] 
  at Mono.Unix.Catalog.MarshalStrings (System.String s1, System.IntPtr& p1, System.String s2, System.IntPtr& p2, System.String s3, System.IntPtr& p3) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Stdlib ---> System.DllNotFoundException: libMonoPosixHelper.so
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:GetDefaultSignal ()
  at Mono.Unix.Native.Stdlib..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Unix.UnixMarshal.AllocHeap (Int64 size) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, Int32 index, Int32 count, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s) [0x00000] 
  at Mono.Unix.Catalog.MarshalStrings (System.String s1, System.IntPtr& p1, System.String s2, System.IntPtr& p2, System.String s3, System.IntPtr& p3) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 
yogesh@yogesh-laptop:~$

---

