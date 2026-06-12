---
title: "[SOLVED] Get mySQL running with MonoDevelop"
date: 2008-03-06
forum: Programming Talk
---

### Post by schmendrick on 2008-03-06
Hi guys!

I hope my problem is not too special:

I am trying to get the mySQL ADO.Net provider Connector/Net 5.1 to run under mono. as far as mySQL says so, it should run under mono. 

For this i followed the steps at 
[http://mysql.mirrors.pair.com/doc/refman/5.0/en/connector-net-installation-unix.html](http://mysql.mirrors.pair.com/doc/refman/5.0/en/connector-net-installation-unix.html).

So I followed the provided steps but: 
When i add a reference to the dll i can compile the program without problems.  
but when i start it i get an error:

--------
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
-----

First question that comes to my mind is: 
what IS the exact installation folder of mono? i tried to get this info out of synaptic by looking at the properties of synaptic. 
so i then copied this DLL to /usr/lib/monodevelop/bin

after i do this and make gacutil, should the dll then be found under the "packages" tab in monodevelop when adding the reference? because it isnt there. i have to manually browse for the file under the tab .net assemby.

ah yes, and i am using GUTSY, i of course i have mySQL server 5.0 installed and i have monodevelop 0.14+dsfg-1ubuntu2. 

ok... well... any comments what i could do? actually till now i was more the ASP.NET guy under Windows .NET plus MS-SQL plus IIS guy, but i try to get familiar and seriously start using linux and for this it would be very cool if i could port my APPs to Mono and start running them under apache + ubuntu. but for porting i would need this ADO.NET :(

i hope someone can help me,

regards schmendrick

---

### Post by luisromangz on 2008-03-06
It seems that the problem isn't on the ADO.net provider for MySQL. But have you checked that you have the native requirements for that? The server isn't probably a requirement, but maybe it needs some client library that you don't have in your system.

---

### Post by schmendrick on 2008-03-06
yes thank you, there really seems to be another problem:
when i try to run the same project with this dll under SharpDevelop on Windows with target Mono 2.0 i get 

> Ausnahme System.Resources.MissingManifestResourceException wurde im ausgeführten Programm ausgelöst:
Could not find any resources appropriate for the specified culture or the neutral culture.  Make sure "MySql.Data.MySqlClient.Properties.Resources.resources" was correctly embedded or linked into assembly "MySql.Data" at compile time, or that all the satellite assemblies required are loadable and fully signed.&#31889;Oÿ&#511;&#536;&#536;&#23640;&#1258;&#38248;&#1253;

InternalGetResourceSet()
InternalGetResourceSet()
InternalGetResourceSet()
GetString()
.ctor()
Open()
Main()

i will try if i get something from mySQL. if i can solve it, i will post the solution for any enthusiast trying the same

---

### Post by schmendrick on 2008-03-06
ok i solved this now by ... well i call it native c++ style :)
this means, i compiled the DLL with monodevelop for myself. maybe such a solution is more obvious to you guys, but trust me, for a pure.NET coder this is strange. 

so here is what i did or what there is to do:

i downloaded the source code from
[http://dev.mysql.com/downloads/connector/net/5.1.html](http://dev.mysql.com/downloads/connector/net/5.1.html)

you wont be able to open the solition in monodevelop. one of the projects is missing so monodevelop will abort. 
i solved this by opening the solution in visual studio. VS complains, but opens it up anyway. delete the non-existing project. now delete every project that has ".CF" and "Test" in it. They do not compile  under monodevelop (at least not out of the box) and you dont need it anyways. 
what should be left are the projects mySQL.Data and mySQL.Web. Those should be able to compile with a small tweaking:

Open up the AssemblyInfo.cs files in both projects and comment out the last line:
//[assembly: AssemblyKeyName("ConnectorNet")]

*Now open up the project under monodevelop. 
*build it. 
*no errors. 
*hooraaay   :)

i can use this own-built DLL without any problems in my projects.
btw i did not manage to build and use this DLL under windows in sharpDevelop using the mono 2 compiler....  

hope this helps some .NET freaks out there to save some hours

---

