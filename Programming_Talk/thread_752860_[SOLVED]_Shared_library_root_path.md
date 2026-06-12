---
title: "[SOLVED] Shared library root path"
date: 2008-04-12
forum: Programming Talk
---

### Post by WitchCraft on 2008-04-12
Hi!

Question: If I have a shared library e.g. libsomething.so
in /home/username/arbitraryFolder/libsomething.so

and load this shared library into a program, e.g.
/home/username/tools/sometool

how can I get the path of the shared library?
Meaning i want /home/username/arbitraryFolder/ back, 
and not  /home/username/tools/sometool

---

### Post by WW on 2008-04-12
Use the **ldd** command.  For example, this shows the shared libraries used by the program aptitude:
[php]
$ ldd /usr/bin/aptitude
        libapt-pkg-libc6.6-6.so.4.5 => /usr/lib/libapt-pkg-libc6.6-6.so.4.5 (0x00002ac9cbf4a000)
        libncursesw.so.5 => /lib/libncursesw.so.5 (0x00002ac9cc217000)
        libsigc-2.0.so.0 => /usr/lib/libsigc-2.0.so.0 (0x00002ac9cc47f000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002ac9cc684000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00002ac9cc8a0000)
        libm.so.6 => /lib/libm.so.6 (0x00002ac9ccbab000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00002ac9cce2c000)
        libc.so.6 => /lib/libc.so.6 (0x00002ac9cd03b000)
        libutil.so.1 => /lib/libutil.so.1 (0x00002ac9cd396000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002ac9cd599000)
        /lib64/ld-linux-x86-64.so.2 (0x00002ac9cbd2c000)
$ 
[/php]

---

### Post by arkangel on 2008-04-12
the ldd  command  will show you the path only if the library is either on a location point by LD_LIBRARY_PATH ,  in a trusted directory (/lib, /usr/lib , etc )  or it is in a directory  listed on  /etc/ld.so.conf

I assume you library is not any of this places  so ldd  will giye you the name of the library but not its path,  

if you can compile the application,  one way to make it to remember where  the library  is (even if it is not in any of the places I mentioned before ) is to use the rpath switch

gcc -W1,rpath,/path/library/lib     -L /path/library/lib  my_file.c  -lsomething

---

### Post by stroyan on 2008-04-12
A program can find the paths of the shared libraries it has loaded using        dl_iterate_phdr().
There is  a small complete example in "man dl_iterate_phdr".
That function is specific to linux and not portable to other posix systems.

---

### Post by WitchCraft on 2008-08-19
> **stroyan said:**
> A program can find the paths of the shared libraries it has loaded using        dl_iterate_phdr().
There is  a small complete example in "man dl_iterate_phdr".
That function is specific to linux and not portable to other posix systems.

This is what i search, for Linux.
Is there a POSIX portable equivalent?

---

### Post by WitchCraft on 2008-12-09
Bump. Anybody knows how this is done on UNIX ?

---

### Post by WitchCraft on 2009-01-10
bump. Need it to work on UNIX, too...

---

### Post by WitchCraft on 2011-03-26
It's actually simple:

Read /proc/self/maps and parse it.
On FreeBSD, one has to remember it's called
/proc/curproc/maps

So to do it universially: /proc/<pid>/maps

[PHP]
string strMaps = System.IO.File.ReadAllText("/proc/self/maps");
	
string strPattern = @"([\w-]+)\s+([\w-]+)\s+([\w\d]+)\s+([\w\d:]+)\s+(\d+)\s+(.*)?";
System.Text.RegularExpressions.Regex myreg = new System.Text.RegularExpressions.Regex(strPattern);
	
// http://www.csharp411.com/c-read-string-line-by-line/
using (System.IO.StringReader reader = new System.IO.StringReader( strMaps ))
{
	string strThisLine;
	while ((strThisLine = reader.ReadLine()) != null)
	{
		Console.WriteLine("Line: " + strThisLine );
	
		System.Text.RegularExpressions.Match mLineMatch = myreg.Match(strThisLine);
		if(mLineMatch.Success)
		{
			foreach(System.Text.RegularExpressions.Group gThisGroup in mLineMatch.Groups)
			{
				Console.WriteLine("Group: " + gThisGroup.Value.ToString());	
			}
		}
		else
		{
			Console.WriteLine("Crap");
		}
	} // Whend
} // End Using
			
[/PHP]

---

