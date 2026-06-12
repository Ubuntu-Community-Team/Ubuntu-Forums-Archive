---
title: "can't seem to compile prebuild2.0"
date: 2007-11-15
forum: Packaging and Compiling Programs
---

### Post by strungoutfan78 on 2007-11-15
hi all.  i've recently discovered the fleow project for the banshee music player and it looks like it could be pretty cool.  unfortunately it requires Tao framework which i cant seem to compile without prebuild.  now for the life of me i can't figure out how to get prebuild compiled.  i follow the tutorial here: [http://anonsvn.mono-project.com/source/trunk/tao/README.autotools]("http://anonsvn.mono-project.com/source/trunk/tao/README.autotools")
but this is th output i get:
```
neil@neil-laptop:~/tao$ ./Prebuild.exe /target autotools
Prebuild v2.0.2
Copyright (c) Matthew Holmes, Dan Moorehead and David Hudson
See 'prebuild /usage' for help

Unhandled error:        ApplicationName='gmcs', CommandLine='/target:library /debug- /optimize+ /out:"/tmp/Tao.DevIl-temp.dll"  -- "/home/neil/tao/src/Tao.DevIl/Properties/AssemblyInfo.cs" ', CurrentDirectory='', PATH='/home/neil/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'
  at System.Diagnostics.Process.Start_noshell (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] 
  at System.Diagnostics.Process.Start_common (System.Diagnostics.ProcessStartInfo startInfo, System.Diagnostics.Process process) [0x00000] 
  at System.Diagnostics.Process.Start () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Diagnostics.Process:Start ()
  at Mono.CSharp.CSharpCodeCompiler.CompileFromFileBatch (System.CodeDom.Compiler.CompilerParameters options, System.String[] fileNames) [0x00000] 
  at Mono.CSharp.CSharpCodeCompiler.CompileAssemblyFromFileBatch (System.CodeDom.Compiler.CompilerParameters options, System.String[] fileNames) [0x00000] 
  at System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile (System.CodeDom.Compiler.CompilerParameters options, System.String[] fileNames) [0x00000] 
  at Prebuild.Core.Targets.AutotoolsTarget.WriteProject (Prebuild.Core.Nodes.SolutionNode solution, Prebuild.Core.Nodes.ProjectNode project) [0x00000] 
  at Prebuild.Core.Targets.AutotoolsTarget.WriteCombine (Prebuild.Core.Nodes.SolutionNode solution) [0x00000] 
  at Prebuild.Core.Targets.AutotoolsTarget.Write (Prebuild.Core.Kernel kern) [0x00000] 
  at Prebuild.Core.Kernel.Process () [0x00000] 
  at Prebuild.Prebuild.Main (System.String[] args) [0x00000] 

```

now i'm no code whiz so i'm really not sure what all this means so i was hoping someone could point me in the right direction, as the install docs that come with the svn bundle are of no use and i cant seem to find much of anything relating to this program on my google searches.

thanks!

---

### Post by strungoutfan78 on 2007-11-18
hmmm.  seems i'm not the only one with little knowledge on the subject...](*,)

---

