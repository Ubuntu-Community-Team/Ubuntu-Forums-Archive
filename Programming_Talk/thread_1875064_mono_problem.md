---
title: "mono problem"
date: 2011-11-04
forum: Programming Talk
---

### Post by mfleming on 2011-11-04
Hi,

I am trying to run (and build) an open source electronic medical application called OpenVistaCIS, which is dependent on mono. It runs and builds fine on Ubuntu 10.04 LTS. On Ubuntu 11.10 desktop, I get the following errors when I try to run OpenVistaCIS.exe:

mfleming@mgf-desktop:~/openvista/openvistacis-0.9.96-client$ ./OpenVistaCIS.exe
Missing method System.Reflection.Assembly::op_Equality(Assembly,Assembly) in assembly /usr/lib/mono/2.0/mscorlib.dll, referenced in assembly /usr/lib/mono/gac/gdk-sharp/2.12.0.0__35e10195dab3c99f/gdk-sharp.dll
---Initial Exception---
Method not found: 'System.Reflection.Assembly.op_Equality'.
  at Medsphere.OpenVista.CIS.OVMain.Run (System.String[] args) [0x00000] in <filename unknown>:0
  at Medsphere.OpenVista.CIS.OVMain.Main (System.String[] args) [0x00000] in <filename unknown>:0


---Second Exception---
An exception was thrown by the type initializer for Nest
  at Medsphere.OpenVista.CIS.OVMain.ShowUnhandledException (System.Exception ex) [0x00000] in <filename unknown>:0
[ERROR] FATAL UNHANDLED EXCEPTION: System.MissingMethodException: Method not found: 'System.Reflection.Assembly.op_Equality'.
  at Medsphere.OpenVista.CIS.OVMain.Run (System.String[] args) [0x00000] in <filename unknown>:0
  at Medsphere.OpenVista.CIS.OVMain.Main (System.String[] args) [0x00000] in <filename unknown>:0

It appears that mono is not configured properly in 11.10, at least for this application. I have seen similar errors reported for another mono app, banshee, under 11.10.

Any idea how to fix this? Because otherwise I'll have to replace my 11.10 installation with 10.04, which would be a shame (and a nuisance).

Thanks much,

Matthew Fleming

---

### Post by gsmanners on 2011-11-04
Your "configuration" seems to be missing libmono-corlib2.0-cil (and possibly some other stuff). Dependency hell, Microsoft style. :D

---

### Post by mfleming on 2011-11-04
> **gsmanners said:**
> Your "configuration" seems to be missing libmono-corlib2.0-cil (and possibly some other stuff). Dependency hell, Microsoft style. :D

Thanks. I don't know why the Ubuntu 11.10 distro would lack this while the 10.04 distro does not, but I'll check when I get home tonight. It does seem likely that there is something wrong with the mono packages built into 11.10. 

With respect to your last comment, I'm mostly a java and iOS programmer and, believe me, wouldn't be touching this wretchedness if I could avoid it.

Thanks again, 

Matthew

---

### Post by MadCow108 on 2011-11-04
try this:
```
mono --runtime=v4.0 ./OpenVistaCIS.exe
```
[http://orangesquash.org.uk/~laney/blog/posts/2011/10/mono-gotcha/](http://orangesquash.org.uk/~laney/blog/posts/2011/10/mono-gotcha/)

---

