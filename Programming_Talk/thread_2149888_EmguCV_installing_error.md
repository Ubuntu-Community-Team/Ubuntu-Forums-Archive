---
title: "EmguCV installing error"
date: 2013-05-30
forum: Programming Talk
---

### Post by GatoMaster1 on 2013-05-30
Hello

I'm trying to install EmguCV on Ubuntu 12.04.


 I followed the emguCV installation steps for Ubuntu 12.04 from emguCV website.


 The process is correct until try to build Emgu.Util, which shows the following error:


 Building bin/Emgu.Util.dll
/home/rsanchez/emgucv/Emgu.Util/Toolbox.cs(7,18): error CS0234: The type or namespace name Linq' does not exist in the namespaceSystem.Xml'. Are you missing an assembly reference?
/home/rsanchez/emgucv/Emgu.Util/Toolbox.cs(44,21): error CS0246: The type or namespace name XDocument' could not be found. Are you missing a using directive or an assembly reference? /home/rsanchez/emgucv/Emgu.Util/Toolbox.cs(58,41): error CS0246: The type or namespace nameXDocument' could not be found. Are you missing a using directive or an assembly reference?
/home/rsanchez/emgucv/Emgu.Util/Toolbox.cs(78,41): error CS0246: The  type or namespace name `XDocument' could not be found. Are you missing a  using directive or an assembly reference?
Compilation failed: 4 error(s), 0 warnings
make[2]: [B][I] [Emgu.Util] Error 1
make[1]: [/I][/B] [Emgu.Util/CMakeFiles/Emgu.Util.dir/all] Error 2
make: *** [all] Error 2


 Anyone know how to fix this?


 Thanks.

---

