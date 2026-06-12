---
title: "ASP.NET through mono."
date: 2008-11-28
forum: Programming Talk
---

### Post by xplicit-ru on 2008-11-28
I try to start web application on apache, but in the apache error logs I found  this record:

[Sun Nov 16 19:48:10 2008] [error] Failed running '/usr/bin/mono /usr/lib/mono/2.0/mod-mono-server2.exe --filename /tmp/.mod_mono_server2 --nonstop --appconfigdir /etc/mono-server2 (null) (null) (null) (null) (null) (null) (null)'. Reason: No such file or directory
[Sun Nov 16 19:48:10 2008] [notice] Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 mod_mono/1.2.5 configured -- resuming normal operations
[Sun Nov 16 19:48:10 2008] [info] Server built: Jun 25 2008 13:50:52
[Sun Nov 16 19:48:56 2008] [error] (107)Transport endpoint is not connected: write_data failed
[Sun Nov 16 19:48:56 2008] [alert] Failed to send initial data. Transport endpoint is not connected


If I copy string '/usr/bin/mono /usr/lib/mono/2.0/mod-mono-server2.exe --filename /tmp/.mod_mono_server2 --nonstop --appconfigdir /etc/mono-server2' and run it from the command string mod web server was started successfuly. How to correctly configure mono-server2-hosts.conf so apache2 would start with mono?

now, my configuration file has following lines:

# Default configuration, don't edit it!
<IfModule mod_mono.c>
  MonoUnixSocket default /tmp/.mod_mono_server2
  MonoServerPath default "/usr/bin/mono /usr/lib/mono/2.0/mod-mono-server2.exe"
  AddType application/x-asp-net .aspx .ashx .asmx .ascx .asax .config .ascx
  MonoApplicationsConfigDir default /etc/mono-server2
  MonoPath default /usr/lib/mono/2.0:/usr/lib
</IfModule>

And where can I find manuals for this configuration file?

---

### Post by directhex on 2008-11-28
1.2.5?

Which Ubuntu release is this?

---

### Post by xplicit-ru on 2008-11-28
Ubuntu Hardy 8.04
Mono JIT compiler version 1.2.6 (tarball)

---

### Post by directhex on 2008-11-28
> **xplicit-ru said:**
> 
# Default configuration, don't edit it!
<IfModule mod_mono.c>
  MonoUnixSocket default /tmp/.mod_mono_server2
  MonoServerPath default "/usr/bin/mono /usr/lib/mono/2.0/mod-mono-server2.exe"
  AddType application/x-asp-net .aspx .ashx .asmx .ascx .asax .config .ascx
  MonoApplicationsConfigDir default /etc/mono-server2
  MonoPath default /usr/lib/mono/2.0:/usr/lib
</IfModule>

Did you ignore the comment, and edit this - or was it just broken on hardy?

Try:

  MonoServerPath default /usr/bin/mod-mono-server2

 instead of

  MonoServerPath default "/usr/bin/mono /usr/lib/mono/2.0/mod-mono-server2.exe"

The asp.net2-examples package should give you an idea of what to expect in /etc/mono-server2

---

### Post by xplicit-ru on 2008-11-30
Yes, I edited the default conf file, because in the default version of confs apache said, that it could not start mod-mono-server2.exe, because type is not regognized as executable. So I tried to help apache, and made a hint to start mod-mono-server2.exe with mono. That did not work too. 

Today I again tried to replace the config to the original variant, and apache hosts ASP.NET applications for now correctly. This looks very strange, because I did not register 'MZ' files as mono scripts files manually. Maybe some the latest updates of ubuntu has done it.

Thanks for help, problem is resolved.

---

### Post by directhex on 2008-11-30
> **xplicit-ru said:**
> Yes, I edited the default conf file, because in the default version of confs apache said, that it could not start mod-mono-server2.exe, because type is not regognized as executable. So I tried to help apache, and made a hint to start mod-mono-server2.exe with mono. That did not work too. 

Today I again tried to replace the config to the original variant, and apache hosts ASP.NET applications for now correctly. This looks very strange, because I did not register 'MZ' files as mono scripts files manually. Maybe some the latest updates of ubuntu has done it.

Thanks for help, problem is resolved.

"binfmt-support" is the package allowing CLI executables to be run directly (./foo.exe rather than mono foo.exe)

---

