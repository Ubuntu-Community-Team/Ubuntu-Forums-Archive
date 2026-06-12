---
title: "Cross-platform filesystem navigation in Mono"
date: 2010-08-04
forum: Programming Talk
---

### Post by Dragonbite on 2010-08-04
I am wondering, how do you compensate for different file structures between Linux and Windows when programming for a cross-platform application?

For example, if I want to scan my /home directory in Linux, and my "My Documents" in Windows with something made in Mono (C# or VB.NET)?

Or scanning a network folder in Linux (smb://<server>/<folder>) as opposed to Windows (\\<server>\<folder>).

Or even just that Windows uses the back slash ("\") and Linux uses the forward slash ("/")?

I am not very experienced with client programming (work in ASP.NET) so I am taking Mono as an opportunity to "re-use" my (minuscule) .NET experience.

Thanks.

---

### Post by soltanis on 2010-08-04
I don't know much about .NET, although in other cross-platform systems like Python, you compensate for this by using a set of library functions, such as those in os.path:

```

# joining a path:
os.path.join("home", "user", "bin")

# -> on posix
"/home/user/bin"

# -> on windows
'C:\home\user\bin'

```

You should investigate .NET's equivalent of this library (I'm sure it has one...well...it should have one) which might have functions for doing what you're talking about. If it doesn't, you might have to go ahead and roll your own system, which would involve detecting which OS you're running on and tailoring the directories accordingly.

---

### Post by cszikszoy on 2010-08-04
Look at the members of System.IO.Path, particularly Path.DirectorySeparatorChar, and Path.Join ().

The MSDN docs are very thorough and complete, and will apply equally to Mono on Linux/OSX as they do to .NET on Windows.

[http://msdn.microsoft.com/en-us/library/system.io.path.aspx](http://msdn.microsoft.com/en-us/library/system.io.path.aspx)

---

