---
title: "java. odbc driver confusion (win 7)"
date: 2010-01-06
forum: Programming Talk
---

### Post by JayKay3000 on 2010-01-06
_**Preeamble**_

I'm following a book called Ivor Horton's Beginning Java 2 jdk5 ed and am a little stuck on chapter 24 (if anyone has used it).

Having learnt a great deal in java since my last post including login, menus and controlling mutliple windows using setVisible, exit, loops and such I thought i'd try Databases with Java. It seemd a simpler way to acomplish my end program goal and was raring to test the books complimentary code to see if it was a good idea.
[B]
_Problem_[/B]

I need an odbc driver.

My problem is that have followed the books instructions but i'm using windows 7x64 and what the book says does not seem to relate to what windows 7 says when setting an ODBC data source. I'm also using OpenOffice (can use acess 2000 if I have to)

I've been to the sun website and looked for drivers there but found that you have to pay for them or the links are broken. (they mostly say they come with software which i'm not inclined to download just for a driver) 

I'm a student so can't really afford to go buying this driver as sites claim to want money for it.

I have read that java apparetly comes with and odbc driver but i'm confused on how to install it.

So i'm stuck and frustrated after wating all afternoon fetting nowhere because as you can imagine, i'm raring to go as I can do the sql bit. 

It's probably something simple to someone that knows.

Thanks

Joss.

---

### Post by Axos on 2010-01-06
The Sun JDK includes the Apache Derby database. There are sample programs and documentation in the JDK's db subdirectory. I haven't tried them but I will if you have problems getting them to work.

---

### Post by Axos on 2010-01-06
Well, I booted Windows just to make sure it's in the same directory in the Windows version of the JDK and, of course, it isn't. If you are using Windows, look in \Program Files\Sun\JavaDB.

---

### Post by JayKay3000 on 2010-01-11
I'm running win 7 x64. 

I finally managed to get this to work by loading the 32 bit version of the ODBC program in windows and also installed my old copy of Office 2000 so have the ODBC driver installed.

My program though when I run it says 'the specified DSN contains an architecture missmatch between the driver and application'

Not quite sure how to get the program to point to the file :S

The ODBC.ini file  states this "Driver32=C:\Windows\system32\odbcjt32.dll
[technical_library]" 

I'll try re-compiling i guess

---

### Post by JayKay3000 on 2010-01-11
ok, I fixed this.

I simply went back to the SysWOW32 folder in windows and ran the cmd aaplication from that folder (being the 32 bit version I assume), compiled the java prog and now it now workes.

Dunno why I didn't think to run the program from there in the first place!

---

