---
title: "ASP.NET 4.0 on ubuntu 11.10, a pain."
date: 2011-09-09
forum: Programming Talk
---

### Post by Drenriza on 2011-09-09
So im wondering. I created a ASP.NET website in visual studio 2010 on Windows. I created it just as i wanted it. And then i boxed getting a server up to run it.

But when i upload my ASP.NET site to a ubuntu server. It works differently on windows then it does on ubuntu O.o??? Methods like writing to files with WriteLine, and environment.newline. I cannot create files with file.create. Because it says i cannot access the file i try to create???

I thought that ASP.NET on windows was suppose to work the same on ubuntu, with exceptions like process starts, paths and such. But seriously, how can a writeline or environment.newline work differently? On windows vs ubuntu.

Also, is their a silver lining on how to create a file and change it permissions in ASP.NET?

Kind regards.

---

### Post by WitchCraft on 2011-09-09
> **Drenriza said:**
> 
But when i upload my ASP.NET site to a ubuntu server. It works differently on windows then it does on ubuntu O.o??? Methods like writing to files with WriteLine, and environment.newline. 


Environment.NewLine and WriteLine both Emit \n on Linux, and \r\n on Windows. Yes, they are different, but it's not a bug. Windows line ending is "\r\n", Unix/Linux line ending is just "\n", and this has been and will always be that way.


> 
I cannot create files with file.create. Because it says i cannot access the file i try to create???


Possible reasons_
#1:
No write access in the parent folder

#2:
Backslash ('\') in path. Linux uses '/' as directory separator.

#3:
Linux is case sensitive. Filename.txt and FileName.txt are NOT the same file --> File not found.

#4:
You're trying to run the .NET exe with the wrong version of the runtime.

#5: 
AppArmor/SE Linux settings related problem


> 
I thought that ASP.NET on windows was suppose to work the same on ubuntu, with exceptions like process starts, paths and such. But seriously,

System.Diagnostics.Process.Start is no different on Linux than on Windows.
Of course, Windows programs don't usually exist on Linux.


> 
Also, is their a silver lining on how to create a file and change it permissions in ASP.NET?


The best approach is to give the server user the correct permissions so you won't have to change the permissions, because the files are already created with the correct permissions.

If you have to, use Syscall.chmod
[http://www.go-mono.com/docs/index.aspx?link=M%3aMono.Unix.Native.Syscall.stat](http://www.go-mono.com/docs/index.aspx?link=M%3aMono.Unix.Native.Syscall.stat)

See also this link:
[http://stackoverflow.com/questions/1437640/using-mono-to-recognize-executable-files-in-linux](http://stackoverflow.com/questions/1437640/using-mono-to-recognize-executable-files-in-linux)


Then, the webserver user should also have access to the file (chmod 777), for example when you run the mono server/mod-mono/fastcgi under a different user as the webserver.


And be aware that Syscall.chmod won't be available on Windows at runtime.

Use System.Environment.OSVersion.Platform to switch behaviour on runtime.
Creating abstract classes (classes that you can't instantiate, something like an interface) wouldn't be a bad idea either. Note that PlatformID.Unix will be true on Linux and Mac as well. Invoke uname if you need more precise information.

---

### Post by directhex on 2011-09-10
Is the file you're trying to read/write readable/writable by the www-data user that Apache runs as?

---

### Post by Drenriza on 2011-09-11
Hi.

I got my problem solved the day before yesterday. The solution was.
#1 Create a new folder /home/ called website. chown www-data:www-data website/
#2 all files uploaded to this folder chown www-data:www-data and chmod 666 *
#3 in /var/www/Ubuntu chown www-data:www-data *

Now it just runs.

---

