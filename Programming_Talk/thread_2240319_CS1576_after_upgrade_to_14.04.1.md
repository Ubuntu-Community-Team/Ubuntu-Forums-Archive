---
title: "CS1576 after upgrade to 14.04.1"
date: 2014-08-19
forum: Programming Talk
---

### Post by lordbah2 on 2014-08-19
Upgraded from 13.10 to 14.04.1 and my web site stopped working. What changed with mod-mono, mono, apache, etc. between 13.10 and 14.04.1?

Error CS1576. I don't use the #line directive at all. Something during on-demand compilation of an ASP.NET page?

[COLOR=#000000][FONT=Verdana][COLOR=#FFFFFF]**Application Exception**[/COLOR]
[/FONT][/COLOR]
[COLOR=#696969][FONT=Verdana]**System.Web.Compilation.CompilationException**

**CS1576: The line number specified for #line directive is missing or invalid**

**Description:** Error compiling a resource required to service this request. Review your source file and modify it to fix this error.
**Details:** CS1576: The line number specified for #line directive is missing or invalid
**Error origin: **Compiler
**Error source file: **/Standings.aspx
**Exception stack trace:**
[FONT=monospace]  at System.Web.Compilation.AssemblyBuilder.BuildAssembly (System.Web.VirtualPath virtualPath, System.CodeDom.Compiler.CompilerParameters options) [0x00000] in <filename unknown>:0   at System.Web.Compilation.AssemblyBuilder.BuildAssembly (System.Web.VirtualPath virtualPath) [0x00000] in <filename unknown>:0   at System.Web.Compilation.BuildManager.GenerateAssembly (System.Web.Compilation.AssemblyBuilder abuilder, System.Web.Compilation.BuildProviderGroup group, System.Web.VirtualPath vp, Boolean debug) [0x00000] in <filename unknown>:0   at System.Web.Compilation.BuildManager.BuildInner (System.Web.VirtualPath vp, Boolean debug) [0x00000] in <filename unknown>:0 [/FONT]
[COLOR=#999999][COLOR=black]**Version Information:** 3.2.8 (Debian 3.2.8+dfsg-4ubuntu1); ASP.NET Version: 4.0.30319.17020[/COLOR]
[/COLOR]
[/FONT][/COLOR]

---

### Post by lordbah2 on 2014-08-19
Well, that's weird. The first line of the .aspx file is

<%@ Page Language="C#" MasterPageFile="~/UserPageTemplate.master" %>

and I get the error. If I add    Trace="true"    then I do not get the error and the page works (not counting the gobs of trace info in it).

---

### Post by lordbah2 on 2014-08-20
And weirder. I added the Xamarin repository and upgraded mono from 3.2.8 to 3.6.0 and restarted apache2. One page which previously had that failure now works. Other pages still fail the same way.

Edit: actually, that one success is not repeatable. I have no idea what's going on ...

---

### Post by lordbah2 on 2014-08-21
Maybe I should downgrade mono back to the version it was in Ubuntu 13.10. Is there a way to get synaptic to use [https://launchpad.net/ubuntu/trusty/amd64/mono-complete/2.10.8.1-5ubuntu2?](https://launchpad.net/ubuntu/trusty/amd64/mono-complete/2.10.8.1-5ubuntu2?)

---

