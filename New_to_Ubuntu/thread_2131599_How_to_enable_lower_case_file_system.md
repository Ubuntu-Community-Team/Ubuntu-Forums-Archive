---
title: "How to enable lower_case_file_system"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by neskire on 2013-04-02
Hi all,

On Ubuntu 12.04 - i'm trying to set mysql 5.5 to be case insensitive, by setting

lower_case_table_names  = 1
lower_case_file_system=1

Doing so I'm unable to start mysql again, so i'm only setting:

lower_case_table_names  = 1
#lower_case_file_system=1

But this does not work - the mysql documentation states that lower_case_file_system:

[COLOR=#000000][FONT=Helvetica]"This variable is read only because it reflects a file system attribute and setting it would have no effect on the file system."
[/FONT][/COLOR]http://dev.mysql.com/doc/refman/5.5/en/server-system-variables.html#sysvar_lower_case_file_system
[COLOR=#000000][FONT=Helvetica]
How do I set the file system attribute for case insensitivity ?

--
Best
Soren[/FONT][/COLOR]

---

### Post by Wim Sturkenboom on 2013-04-02
You can't. The file system in Linux IS case sensitive.

---

### Post by Nutster on 2013-04-02
That system variable is for telling MySQL, which can be compiled for many different operating systems, that it is on an operating system or using a file system that is already case-insensitive, such as FAT.  All of the standard Linux file systems are case-sensitive.  Because MySQL relies on the operating system to provide the access to the files, as it should, it must rely on the case-sensitivity of that operating system and file system.

One problem with trying to do case-insensitive activity on a case-sensitive file system is that the file system can store two or more different files with the same name, except for case, in the same place.  In *ext4*, the usual file system for Ubuntu these days, I could have files in the same directory named **Testing**, **TESTING** and **testing**, with each being a distinct file having no connection to the other files.  In a case-insensitive mode, how can I choose which file I should be using?  I guess I am saying this is a **bad** idea.  

Before using this system variable, you would need to change the underlying file system to one that is case-insensitive.  There are several case-insensitive file systems available, but most are older and have storage limitations, such as FAT (from the days of MS-DOS) and FAT32 (Windows 9X).  NTFS, used on Windows for more than a decade now, is case-sensitive, but some older software still accesses the file system in a case-insensitive way and the operating system and NTFS has to accommodate this.

Is there a specific reason you want case-insensitive access to the file system?

---

### Post by neskire on 2013-04-02
So in other words, its not possible to get the settings:

[COLOR=#000000]lower_case_table_names = 1[/COLOR]
[COLOR=#000000]lower_case_file_system=1

or ?

- I'm trying to configure a webapp that explicit tells me to set these two settings, i have been using it before running on mysql (though on Debian I think).


[/COLOR]

---

### Post by Nutster on 2013-04-02
For a normal Linux system, these variables should be set as:
```
lower_case_file_system=off
lower_case_table_names=0/1
```
If **lower_case_table_names** is set to 0, then the table names are case-sensitive and the files names will be as entered, case-wise.  If it is set to 1, then all the table names will be converted to lower case and the table names will be case-insensitive.  It is recommended that **lower_case_table_names** be set to 1 if using InnoDB tables.

Check out the documentation on the MySQL website: [http://dev.mysql.com/doc/refman/5.1/en/server-system-variables.html#sysvar_lower_case_table_names]("http://dev.mysql.com/doc/refman/5.1/en/server-system-variables.html#sysvar_lower_case_table_names")

---

