---
title: "ASP.NET on Linux?"
date: 2009-05-31
forum: Programming Talk
---

### Post by WitchCraft on 2009-05-31
I've a question: I used to work with Linux at work.
Now I've gotten a far better-paid job, but there I have to work with Windows, unfortunately...
 
I personally like Linux much more, and I used to take some code created at work home, for personal usage in my private projects, e.g. JAVA/C++/PHP SQL etc.
 
Now, Java, C++ and SQL remained, but I have to switch to ASP.NET instead of PHP...
 
I would like to be able to let ASP.NET pages run on my Apache Linux server at home, without having to change to windows and/or giving up on PHP.
 
Is it possible to let ASP.NET pages (in VB.NET) run on Apache using mono?
Anybody tried it? Does it work (reasonably)?

---

### Post by Tibuda on 2009-05-31
You can run ASP.NET 2.0 code, but not 3.0.
See also [http://www.mono-project.com/ASP.NET](http://www.mono-project.com/ASP.NET)

---

### Post by WitchCraft on 2009-06-01
Ok, it works this way:

First, install apache if necessary, including all dependencies
```

*apt-get install apache2 apache2-mpm-prefork apache2-threaded-dev*

```
Download and compile mono from
[http://ftp.novell.com/pub/mono/sources-stable/](http://ftp.novell.com/pub/mono/sources-stable/)
```

[I]./configure --prefix=/usr
make
make install[/I]

```Then, while it compiles, install these:
```

apt-get install mono-apache-server libapache2-mod-mono
apt-get install mono-gmcs mono-gac 
apt-get install mono-apache-server2
apt-get install mono-utils monodevelop monodoc-browser monodevelop-nunit monodevelop-versioncontrol

```

Then download the xsp server:
```

apt-get install mono-xsp mono-xsp2

```
or build it from source according to this thread:
[http://ubuntuforums.org/showthread.php?t=225454&page=3](http://ubuntuforums.org/showthread.php?t=225454&page=3)


then download the asp.net examples
```

apt-get install asp.net2-examples

```The apache root on debian/ubuntu is in:
```

/var/www

```(in openSUSE it is /srv/www/hdtocs)
which is where you want the xsp root to be, too.


now add mod mono to your apache configuration file

gedit /etc/apache2/httpd.conf
```

Include /etc/apache2/mod_mono.conf

```
restart apache:
/etc/init.d/apache2 restart

other options are:
```

sudo /etc/init.d/apache2  xxx
xxx = {start|stop|restart|reload|force-reload|start-htcacheclean|stop-htcacheclean|status}.

```Now copy the asp.net examples to your wwwroot.
They are in:
```

/usr/lib/xsp/test 
or
/usr/local/lib/xsp/test 

```**now go to /var/www** and start xsp
```

xsp

```Note: xsp root folder is where you start xsp from.
If you don't start it from /var/www, it won't find the files you put in /var/www


if you don't find the examples, copy this file in /var/www/

hello.aspx
```

<%@ Page language="c#"%>

<script language="c#" runat=server>

public void Page_Load(object sender, EventArgs e)
{

    //Why break tradition?
    Response.Write( "Hello, World!" );

}

</script>
<html>
    <head>
        <title>Response.Write</title>
    </head>
    <body>
    </body>
</html>

```
and this file **(important)**

web.config
```

<?xml version="1.0" encoding="utf-8"?>
<configuration>
<!-- Enable this if you want gzip compression. Also uncomment the <mono.aspnet> section below
    <configSections>
        <sectionGroup name="mono.aspnet">
        <section name="acceptEncoding" type="Mono.Http.Configuration.AcceptEncodingSectionHandler, Mono.Http, Version=1.0.5000.0, PublicKeyToken=0738eb9f132ed756"/>
        </sectionGroup>
    </configSections>
-->
    <system.web>
        <customErrors mode="Off"/>
    <!--
    <webServices>
        <soapExtensionTypes>
            <add type="DumpExtension, extensions" priority="0" group="0" />
            <add type="EncryptExtension, extensions" priority="1" group="0" />
        </soapExtensionTypes>
    </webServices>
    -->
    <authentication mode="Forms">
        <forms name=".MONOAUTH" loginUrl="/1.1/authtest/login.aspx" />
    </authentication>

        <httpModules>
    <!-- Some modules available in Mono.Http -->
    <!--
            <add name="AcceptEncodingModule" type="Mono.Http.Modules.AcceptEncodingModule, Mono.Http, Version=1.0.5000.0, PublicKeyToken=0738eb9f132ed756"/>
    -->
            <!--<add name="BasicAuthenticationModule"
             type="Mono.Http.Modules.BasicAuthenticationModule, Mono.Http"/>-->
            <!--<add name="DigestAuthenticationModule"
             type="Mono.Http.Modules.DigestAuthenticationModule, Mono.Http"/>-->
    </httpModules>
    </system.web>

<!-- If you use AcceptEncodingModule, you need this too
    
    <mono.aspnet>
        <acceptEncoding>
        <add encoding="gzip" type="Mono.Http.GZipWriteFilter, Mono.Http, Version=1.0.5000.0, PublicKeyToken=0738eb9f132ed756" disabled="no" />
    </acceptEncoding>
    </mono.aspnet>
-->

    <appSettings>
<!--    <add key="MonoServerDefaultIndexFiles"
         value="index.aspx, Default.aspx, default.aspx, index.html, index.htm" />
    <add key="DBProviderAssembly"
         value="Npgsql"/>
    <add key="DBConnectionType"
         value="Npgsql.NpgsqlConnection"/>
    <add key="DBConnectionString"
         value="server=127.0.0.1;user id=monotest;password=monotest;dbname=monotest"/> -->
    <!--<add key="Authentication" value="Basic" />
    <add key="Basic.Users" value="basic-auth.txt" />-->
    <!--<add key="Authentication" value="Digest" />
    <add key="Digest.Users" value="basic-auth.txt" />-->
    </appSettings>
</configuration>


```Now go to [http://localhost/index.aspx](http://localhost/index.aspx)
or
[http://localhost:8080/index.aspx](http://localhost:8080/index.aspx)

And you should see the asp.net site !

---

### Post by WitchCraft on 2009-06-01
OK, C# works now, but VB doesn't?

```

<%@ Page Language="vb" %>

<html>
<head>
<title>ASP.NET Hello World</title>
</head>
<body bgcolor="#FFFFFF">
<%
response.write("<H1>Hello World!</H1>")
%>

</body>
</html>


```



Error message when running VB:
> 
**Server Error in '/' Application**

***Process has not been started.***

 **Description: **HTTP 500. Error processing request.
 **Stack Trace: **
 System.InvalidOperationException: Process has not been started.
  at System.Diagnostics.Process.get_ExitCode () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Diagnostics.Process:get_ExitCode ()
  at Microsoft.VisualBasic.VBCodeCompiler.CompileFromFileBatch (System.CodeDom.Compiler.CompilerParameters options, System.String[] fileNames) [0x00000] 
  at Microsoft.VisualBasic.VBCodeCompiler.CompileAssemblyFromFileBatch (System.CodeDom.Compiler.CompilerParameters options, System.String[] fileNames) [0x00000] 
  at System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile (System.CodeDom.Compiler.CompilerParameters options, System.String[] fileNames) [0x00000] 
  at System.Web.Compilation.AssemblyBuilder.BuildAssembly (System.Web.VirtualPath virtualPath, System.CodeDom.Compiler.CompilerParameters options) [0x00000] 
  at System.Web.Compilation.AssemblyBuilder.BuildAssembly (System.Web.VirtualPath virtualPath) [0x00000] 
  at System.Web.Compilation.BuildManager.GenerateAssembly (System.Web.Compilation.AssemblyBuilder abuilder, System.Collections.Generic.List`1 buildItems, System.Web.VirtualPath virtualPath, BuildKind buildKind) [0x00000] 
  at System.Web.Compilation.BuildManager.BuildAssembly (System.Web.VirtualPath virtualPath) [0x00000] 
  at System.Web.Compilation.BuildManager.GetCompiledType (System.String virtualPath) [0x00000] 
  at System.Web.Compilation.BuildManager.CreateInstanceFromVirtualPath (System.String virtualPath, System.Type requiredBaseType) [0x00000] 
  at System.Web.UI.PageParser.GetCompiledPageInstance (System.String virtualPath, System.String inputFile, System.Web.HttpContext context) [0x00000] 
  at System.Web.UI.PageHandlerFactory.GetHandler (System.Web.HttpContext context, System.String requestType, System.String url, System.String path) [0x00000] 
  at System.Web.HttpApplication.GetHandler (System.Web.HttpContext context, System.String url, Boolean ignoreContextHandler) [0x00000] 
  at System.Web.HttpApplication.GetHandler (System.Web.HttpContext context, System.String url) [0x00000] 
  at System.Web.HttpApplication+<Pipeline>c__Iterator2.MoveNext () [0x00000]   **Version information: ** Mono Version: 2.0.50727.1433; ASP.NET Version: 2.0.50727.1433


---

### Post by WitchCraft on 2009-06-01
Aha, for VB.net you need additional files:
```

 apt-get install libmono-microsoft-visualbasic8.0-cil mono-basic-dbg

```and you should use xsp2, btw

or get the sources
[http://www.mono-project.com/Visual_Basic](http://www.mono-project.com/Visual_Basic)

It works!

[SIZE=7]**Hello World!**[/SIZE]

---

### Post by WitchCraft on 2009-06-01
Writing the first mono program:
[http://beans.seartipy.com/2006/06/28/writing-your-first-program-with-mono-and-monodevelop/](http://beans.seartipy.com/2006/06/28/writing-your-first-program-with-mono-and-monodevelop/)


And some info on configuring
[http://gonzalo.name/blog/files/mod_mono.html](http://gonzalo.name/blog/files/mod_mono.html)

Ubuntu help pages has instructions on setting up virtual hosts with mono
[https://help.ubuntu.com/community/ModMono](https://help.ubuntu.com/community/ModMono)

And the homepage of the mono project for further information:
[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

---

### Post by Tibuda on 2009-06-01
Missed this. Good you figured it out yourself.

---

### Post by doas777 on 2009-06-01
> **WitchCraft said:**
> I've a question: I used to work with Linux at work.
Now I've gotten a far better-paid job, but there I have to work with Windows, unfortunately...
 
I personally like Linux much more, and I used to take some code created at work home, for personal usage in my private projects, e.g. JAVA/C++/PHP SQL etc.
 
Now, Java, C++ and SQL remained, but I have to switch to ASP.NET instead of PHP...
 
I would like to be able to let ASP.NET pages run on my Apache Linux server at home, without having to change to windows and/or giving up on PHP.
 
Is it possible to let ASP.NET pages (in VB.NET) run on Apache using mono?
Anybody tried it? Does it work (reasonably)?

you've just hit on exactly the reason I have to keep at least one wintel workhorse box arround the house.

also, your SQLs are not nearly the same. unless you are using odbc at work, i wouldn't recomend refactoring your app to do mysql or postgre, just so you can work at home. forking a datalayer is a real pain. 

I would install a VM of XP, or whatever to do your dev work.

---

### Post by directhex on 2009-06-01
Um... wow. That's some terrible advice up there. I mean really truly system-killing awful.

First question: "Is it possible to let ASP.NET pages (in VB.NET) run on Apache using mono?" - yes. Doing it via Apache is harder than just generally doing it for dev work, so I'll get to it.

First sub-question is "how can I use ASP.NET", and the easy answer is "XSP". XSP is Mono's test ASP.NET server. Install the mono-xsp package for ASP.NET 1.1, or mono-xsp2 for ASP.NET 2.0.

If you want to write VB.NET, install mono-vbnc.

Now, generally speaking, just type "xsp" or "xsp2" in any folder to fire up a web server on the port shown on-screen, with that folder as the document root.




Okay, so next, getting Apache involved. First things first, install mono-apache-server or mono-apache-server2 (for 1.1 and 2.0 respectively), then libapache2-mod-mono for the apache module. To pick between serving 1.0 and 2.0 content, take a look at the text in /etc/apache2/mods-available/mod_mono.conf, namely:

```
# If want want to use ASP.NET 1.1 (via mono-apache-server), use:
# Include /etc/mono-server/mono-server-hosts.conf
#
# If you want to use ASP.NET 2.0 (via mono-apache-server2), use:
# Include /etc/mono-server2/mono-server2-hosts.conf
```

One of these (probably 2.0) will already be set. Oh, and be sure to use "a2enmod mod_mono" to turn on that module in Apache.

Now, the files it says to Include here are auto-generated files, which the mono-server(2)-update tool generates from input. Input files live in /etc/mono-server(2)/conf.d/sitename/ and look something like this:

```
jms@osc-bigmac:~$ cat /etc/mono-server2/conf.d/asp.net2-examples/10_asp.net2-examples 
# This is the configuration file
# for the aspnet-examples virtualhost
path = /usr/share/asp.net2-demos
alias = /samples
libs = /usr/lib/mono/2.0
```

Knock together an input file for your own site anywhere on disk, re-run the update to make a new config file, restart apache, and that should be it

---

### Post by WitchCraft on 2009-06-02
> **doas777 said:**
> you've just hit on exactly the reason I have to keep at least one wintel workhorse box arround the house.

also, your SQLs are not nearly the same. unless you are using odbc at work, i wouldn't recomend refactoring your app to do mysql or postgre, just so you can work at home. forking a datalayer is a real pain. 

I would install a VM of XP, or whatever to do your dev work.

You're right, you have a point there that I didn't consider.

Fortunately, I've got more luck than sanity - we're using ODBC :D:D:D

I anyway always wondered how compatible ODBC really is...
On Linux I usually use/used PostgreSQL, not MySQL, since I tested all my projects and found PostgreSQL to be a lot faster for my purposes - overall.

---

### Post by phrostbyte on 2009-06-02
directhex,

Do you ever think it could be a one step process in the future? You see Ubuntu Server can be installed with LAMP mostly (completely?) configured. It would be cool to have an ASP.NET option as well. Yes I know DRAMA DRAMA boo Mono. :(

---

### Post by WitchCraft on 2009-06-02
> **directhex said:**
> 
If you want to write VB.NET, install mono-vbnc.



Interesting, looks like libmono-microsoft-visualbasic8.0-cil or some other package includes that, since my system says it's already installed...

---

### Post by WitchCraft on 2009-06-02
> **phrostbyte said:**
> directhex,

Do you ever think it could be a one step process in the future? You see Ubuntu Server can be installed with LAMP mostly (completely?) configured. It would be cool to have an ASP.NET option as well. Yes I know DRAMA DRAMA boo Mono. :(

Haha, yes I was thinking of this myself.
And I came to the conclusion, that apart from XSP/MONO's inherent instability/insecurity, it would probably be too redundant for the apache project to port mono to windows :lolflag:


On the other hand, installing mono wasn't difficult (but searching together a decent & accurate documentation was a really annoying and time-consuming process), and once you now what not to do, it stops crashing, too.

For a challenge, try installing Java Server pages (Apache Tomcat) on IIS 7 (and i mean 7, not 6) on Vista  IA64 (and I mean on Win64 on IA64, not Win32 on IA64)...


If you can't, I managed to find out. Took me only 1 hour...

---

### Post by directhex on 2009-06-02
> **WitchCraft said:**
> Interesting, looks like libmono-microsoft-visualbasic8.0-cil or some other package includes that, since my system says it's already installed...

You installed mono-vbnc-dbg which depends on mono-vbnc. the -dbg package contains debug symbol files (.mdb) for use with the Mono debugger.

---

### Post by directhex on 2009-06-02
> **WitchCraft said:**
> For a challenge, try installing Java Server pages (Apache Tomcat) on IIS 7 (and i mean 7, not 6) on Vista  IA64 (and I mean on Win64 on IA64, not Win32 on IA64)..

I assume you mean AMD64, since there is no Itanium version of Windows Vista

---

### Post by directhex on 2009-06-02
> **phrostbyte said:**
> directhex,

Do you ever think it could be a one step process in the future? You see Ubuntu Server can be installed with LAMP mostly (completely?) configured. It would be cool to have an ASP.NET option as well. Yes I know DRAMA DRAMA boo Mono. :(

Yes, it could - but it needs some patching work to work properly - patching work in (C-based) mod-mono which makes me feel quite ill.

Essentially, the problem is the 1.1/2.0 split. In itself, we don't care too much about this (and we deprecated 1.0 support last release - we may drop it entirely in Mono 2.6 or 2.8 packages). mod-mono supports a 100% auto-configured mode requiring no setup (just renders any aspx files from /var/www) but it ONLY works with 1.1, due to some stupid assumptions in the C. If we can patch it to be switchable between 2.0 and 1.1, then I'll make mod-mono-auto the default module, and the whole thing will be automagic. But I need that ability to use 2.0 sites without needing to do something as sick as ln -s in /usr/bin to put the 2.0 server in the 1.1 server's location

---

### Post by WitchCraft on 2009-06-04
> **directhex said:**
> 
 But I need that ability to use 2.0 sites without needing to do something as sick as ln -s in /usr/bin to put the 2.0 server in the 1.1 server's location


Maybe I might have a look at it, but at the moment I'm preoccupied with reverse engineering a dwg viewer...

Hell, don't even have the time for games.

---

