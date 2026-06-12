---
title: "Monodevelop make error"
date: 2010-09-17
forum: Packaging and Compiling Programs
---

### Post by hauk142 on 2010-09-17
hi. well, i'm new to this forum, so please be nice.

I'm currently having some trouble on compiling Monodevelop 2.4 on a more or less fresh install of Lucid. I followed the instructions here :[http://monodevelop.com/Developers/Articles/Building_MonoDevelop_on_Ubuntu](http://monodevelop.com/Developers/Articles/Building_MonoDevelop_on_Ubuntu)
It went ok 'till step 8. when make-ing I get the following error:
```

./MonoDevelop.Projects.Dom.Serialization/SimpleCodeCompletionDatabase.cs(40,24): error CS0108: `MonoDevelop.Projects.Dom.Serialization.SimpleCodeCompletionDatabase.rwlock' hides inherited member `MonoDevelop.Projects.Dom.Serialization.SerializationCodeCompletionDatabase.rwlock'. Use the new keyword if hiding was intended
./MonoDevelop.Projects.Dom.Serialization/CodeCompletionDatabase.cs(91,34): (Location of the symbol related to previous error)
Compilation failed: 1 error(s), 0 warnings
make[4]: *** [../../../build/bin/MonoDevelop.Core.dll] Error 1






```I am trying to install Monodevelop 'cause I wanna use Ubuntu instead of Windows(i do programming in VB and C#/XNA)( I play BF2 so this dream will not become 100% true;))

If ya can't help me with this please tell me if you know bout some other way to install MD on 10.04 :D

regards, hauk

---

### Post by SevenMachines on 2010-09-17
> $ sudo apt-get install monodevelopMonodevelop and lots of mono related libraries, apps, development tools are all included in 10.04. You can search in synaptic or the software centre thing to find them, but i havent used software centre yet so i dont know how to do that!
In general, if you need something its probably already available in the repositories, always look there first, itll make your life much easier

---

### Post by hauk142 on 2010-09-17
i know all that:p. actually i have tried both apt-get, software center and synaptic and noone works for me(not a surprise really, its probably same packages ^^). BTW the software center is fine, but the Vuze there is not working, use apt-get instead... i tried running MD from terminal, and this i get:
```


WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:7561): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Core.dll could not be loaded:
     Assembly:   Mono.Addins.Setup    (assemblyref_index=9)
     Version:    0.4.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/).


** (/usr/lib/monodevelop/bin/MonoDevelop.exe:7561): WARNING **: Could not load file or assembly 'Mono.Addins.Setup, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:7561): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Ide.dll could not be loaded:
     Assembly:   glib-sharp    (assemblyref_index=5)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/).


** (/usr/lib/monodevelop/bin/MonoDevelop.exe:7561): WARNING **: Could not load file or assembly 'glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.



```



...help?...

regards, hauk

---

### Post by SevenMachines on 2010-09-17
Probably a better question for the support forums, there more likely to have seen it before and to have a solution. Monodevelop works fine on lucid i386 here.
I'd try reinstalling some things, sometimes installation/upgrade order can cause confusion... particularly,

$ sudo apt-get install --reinstall libglib2.0-cil libmono-addins0.2-cil

---

### Post by hauk142 on 2010-09-17
i tried the code you gave me, no luck... i have i686(at least according to uname)...
someone else having a solution?

how do i move to support? new to forums, have always fixed stuff myself or googled it;)
well thanks anyway for help :p

regards, hauk

---

### Post by SevenMachines on 2010-09-17
I wont have lucid handy til at least tomorrow so i cant double check these directory versions but... You could try manually installing to the global assemblies
> $ sudo gacutil -i /usr/lib/cli/Mono.Addins-0.2/Mono.Addins.dll
Installed /usr/lib/cli/Mono.Addins-0.2/Mono.Addins.dll into the gac (/usr/lib/mono/gac)
$ sudo  gacutil -i /usr/lib/cli/glib-sharp-2.0/glib-sharp.dll
Installed /usr/lib/cli/glib-sharp-2.0/glib-sharp.dll into the gac (/usr/lib/mono/gac)


Hopefully then you'll have,
> $ gacutil -l|grep Mono.Addins
Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Mono.Addins.Gui, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Mono.Addins.Setup, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
policy.0.2.Mono.Addins, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
policy.0.2.Mono.Addins.Gui, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
policy.0.2.Mono.Addins.Setup, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
policy.0.3.Mono.Addins, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
policy.0.3.Mono.Addins.Gui, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
policy.0.3.Mono.Addins.Setup, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756

$ gacutil -l|grep glib-sharp
glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.0.taglib-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=db62eba44689b5b0
policy.2.10.glib-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.4.glib-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.6.glib-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.8.glib-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
taglib-sharp, Version=2.0.3.7, Culture=neutral, PublicKeyToken=db62eba44689b5b0

Maybe that'll work.

The main support forums are
[http://ubuntuforums.org/forumdisplay.php?f=327](http://ubuntuforums.org/forumdisplay.php?f=327)

But if you need to compile MonoDevelop then this is the right place, i dont know anything about mono though so someone else would need to look at that

---

### Post by hauk142 on 2010-09-17
the two first commands are correct.
well this is what i get on the teo last ones:

```

$ gacutil -l|grep glib-sharp
 glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f

``````

$ gacutil -l|grep Mono.Addins
Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756

```(Mono.Addins and glib-sharp is written in red.)
what now??

---

### Post by SevenMachines on 2010-09-17
Reds fine. If it doesnt work after that i really dont know.

---

### Post by hauk142 on 2010-09-18
Still doesnt work. i'm wondering if it has something to do with this?
[http://www.mono-project.com/Parallel_Mono_Environments](http://www.mono-project.com/Parallel_Mono_Environments)

think this looks right...

regards, hauk

---

### Post by SevenMachines on 2010-09-18
Did you follow that guide? How far through did you get?

---

### Post by SevenMachines on 2010-09-18
I was thinking mainly of environmental variables you might have changed, MONO_GAC_PREFIX, MONO_PATH, that sort of thing. they're blank by default
> $ echo $MONO_GAC_PREFIX



---

### Post by directhex on 2010-09-18
> **SevenMachines said:**
> I was thinking mainly of environmental variables you might have changed, MONO_GAC_PREFIX, MONO_PATH, that sort of thing. they're blank by default

You're thinking along the right lines.

I think "which mono" will reveal something non-packaged, hence the usual results of GAC poisoning.

---

### Post by hauk142 on 2010-09-18
i followed it all the way through with gnome-sharp without mono-tools. then i compiled monodevelop with /opt/mono as a prefix. now i get an error on startup from source ~/mono-dev-env that monodevelop. gnomeplatform, 2 is missing. it starts though. but it makes GUI look kinda Win95-ish...lol:p

```

[mono] ~ @ monodevelop
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.
ERROR [2010-09-18 16:19:50Z]: Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Stack trace: 
   at Gtk.Application.do_init(System.String progname, System.String[] ByRef args, Boolean check)
   at Gtk.Application.Init(System.String progname, System.String[] ByRef args)
   at MonoDevelop.Ide.IdeStartup.Run(System.String[] args)
   at MonoDevelop.Startup.MonoDevelopMain.Main(System.String[] args)

** (MonoDevelop:2851): WARNING **: The following assembly referenced from /opt/mono/lib/monodevelop/AddIns/GnomePlatform/GnomePlatform.dll could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=3)
     Version:    2.24.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/opt/mono/lib/monodevelop/AddIns/GnomePlatform/).


** (MonoDevelop:2851): WARNING **: Could not load file or assembly 'gnome-sharp, Version=2.24.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
ERROR [2010-09-18 16:19:50Z]: Add-in error (MonoDevelop.GnomePlatform,2.4): Error while getting object for node in path '/MonoDevelop/Core/PlatformService'.
System.TypeLoadException: Could not load type 'MonoDevelop.Platform.GnomePlatform' from assembly 'GnomePlatform, Version=2.4.0.0, Culture=neutral, PublicKeyToken=null'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] in <filename unknown>:0 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] in <filename unknown>:0 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] in <filename unknown>:0 
  at System.MonoType.GetDefaultConstructor () [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] in <filename unknown>:0 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] in <filename unknown>:0 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] in <filename unknown>:0 
  at Mono.Addins.ExtensionNode.GetChildObjectsInternal (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] in <filename unknown>:0 
FATAL ERROR [2010-09-18 16:19:50Z]: A platform service implementation has not been found.
WARNING [2010-09-18 16:19:50Z]: Inotify watch limit is too low (8192).
MonoDevelop will switch to managed file watching.
See http://monodevelop.com/Inotify_Watches_Limit for more info.



```regards, hauk

---

### Post by hauk142 on 2010-09-18
```

$ echo $MONO_GAC_PREFIX

```gives me a blank line only


regards, hauk

---

### Post by directhex on 2010-09-18
> **hauk142 said:**
> i followed it all the way through with gnome-sharp without mono-tools. then i compiled monodevelop with /opt/mono as a prefix. now i get an error on startup from source ~/mono-dev-env that monodevelop. gnomeplatform, 2 is missing. it starts though. but it makes GUI look kinda Win95-ish...lol:p

Looks like fairly standard GAC poisoning to me. Make sure you "gacutil -i"'d the libs you built, if they weren't added to your non-distro Mono GAC automatically.

---

### Post by hauk142 on 2010-09-18
well now i m not sure what you mean. what should i gacutil -i?

regards, hauk

---

### Post by SevenMachines on 2010-09-19
Is running the system monodevelop working yet? Not using ~/mono-dev-env at all. 
$ monodevelop 
in a new terminal

---

### Post by hauk142 on 2010-09-19
```

****@****-PC:~$ monodevelop
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:5844): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Core.dll could not be loaded:
     Assembly:   Mono.Addins.Setup    (assemblyref_index=9)
     Version:    0.4.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/).


** (/usr/lib/monodevelop/bin/MonoDevelop.exe:5844): WARNING **: Could not load file or assembly 'Mono.Addins.Setup, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:5844): WARNING **: The class MonoDevelop.Core.Runtime could not be loaded, used in MonoDevelop.Core, Version=2.4.0.0, Culture=neutral, PublicKeyToken=null

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:5844): WARNING **: Missing method Shutdown in assembly /usr/lib/monodevelop/bin/MonoDevelop.exe, type MonoDevelop.Core.Runtime

Unhandled Exception: System.TypeLoadException: Could not load type 'MonoDevelop.Core.Runtime' from assembly 'MonoDevelop.Core, Version=2.4.0.0, Culture=neutral, PublicKeyToken=null'.

```

---

### Post by hauk142 on 2010-09-20
was just thinking of this:

you:

```
$ gacutil -l|grep Mono.Addins
Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Mono.Addins.CecilReflector, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Mono.Addins.Gui, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
Mono.Addins.Setup, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
policy.0.2.Mono.Addins, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
policy.0.2.Mono.Addins.Gui, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
policy.0.2.Mono.Addins.Setup, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
policy.0.3.Mono.Addins, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
policy.0.3.Mono.Addins.Gui, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
policy.0.3.Mono.Addins.Setup, Version=0.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756

$ gacutil -l|grep glib-sharp
glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.0.taglib-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=db62eba44689b5b0
policy.2.10.glib-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.4.glib-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.6.glib-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
policy.2.8.glib-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f
taglib-sharp, Version=2.0.3.7, Culture=neutral, PublicKeyToken=db62eba44689b5b0                      
```me:

```
****@****-PC:~$ gacutil -l|grep Mono.Addins
Mono.Addins, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756
****@****-PC:~$ gacutil -l|grep glib-sharp
glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f


``````
****@****-PC:~$ monodevelop
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:23621): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Core.dll could not be loaded:
     Assembly:   Mono.Addins.Setup    (assemblyref_index=9)
     Version:    0.4.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin/).


** (/usr/lib/monodevelop/bin/MonoDevelop.exe:23621): WARNING **: Could not load file or assembly 'Mono.Addins.Setup, Version=0.4.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:23621): WARNING **: The class MonoDevelop.Core.Runtime could not be loaded, used in MonoDevelop.Core, Version=2.4.0.0, Culture=neutral, PublicKeyToken=null

** (/usr/lib/monodevelop/bin/MonoDevelop.exe:23621): WARNING **: Missing method Shutdown in assembly /usr/lib/monodevelop/bin/MonoDevelop.exe, type MonoDevelop.Core.Runtime

Unhandled Exception: System.TypeLoadException: Could not load type 'MonoDevelop.Core.Runtime' from assembly 'MonoDevelop.Core, Version=2.4.0.0, Culture=neutral, PublicKeyToken=null'.

```see the link?

---

### Post by hauk142 on 2010-09-20
OMYGOSHOMYGOSH I FIXED IT!!:P:P:P:P:D:D:D

ok so i just gacutil -i the missing assemblies in usr/lib/cli, and now it works!! wouldnt have fixed it without yer help guys, thanks alot... now over to refreshing my VB knowledge and installing Mono.XNA. oh and how do ya do that? (am i hijacking my own thread or...)

:confused:

---

### Post by directhex on 2010-09-20
This was a lot of hard work, considering there are PPA packages of Mono 2.6.7 and MonoDevelop 2.4

---

### Post by hauk142 on 2010-09-21
oh, ppa? how do you use that? I've heard of it...something to do w/ lauchpad?(whatever that is...) :D:D

BTW, i hope they can mix up a Visual Basic visual desginer thingy...

---

