---
title: "tar + ssh between ubuntu and windows"
date: 2014-01-01
forum: Programming Talk
---

### Post by erotavlas on 2014-01-01
[SIZE=2][FONT=times new roman]Hi,

I  would like to send many files compressed as a single file using ssh and  tar in a pipe. I'm able to realize this using unix in both sides:  server and client. The command is the following

```

ssh user@ip 'tar -jcf - /path1/file1 /path1/file2 /path2/file3' | tar -C /path/ -jxf -

```

Now in the client side I would like to use windows and then I have to use 7zip. The following command does not work properly. Where is the mistake?

```

ssh user@ip 'tar -jcf - /path1/file1 /path1/file2 /path2/file3' | 7za -si -tbzip2 x -o/path/

```

For the command in windows I use putty.

Thank you

Salvatore

[/FONT][/SIZE]

---

### Post by ju2wheels on 2014-01-02
Do you have any more details on the particular error/output issue you are having?

In your second command, /path/ is not a valid windows output path if its absolute (you need to add the drive letter).

---

### Post by erotavlas on 2014-01-02
I partially solved with this 
```

    ssh user@ip 'tar -cf - file1 file2 ' | 7za a -si file.tar.7z | 7za x -so file.tar.7z | tar -C /path -xf -

```
Partially means that it works well in Ubuntu but not in windows. I'm using putty and 7zip. It seems that putty is not able to manage the pipe. The command for windows is this

```

&#8220;C:\path\&#8221;putty.exe -ssh user@ip 'tar -cf - file1 file2 ' | "c:\path\"7z.exe a -si file.tar.7z | "c:\path\"7z.exe x -so file.tar.7z -o"c:\path"

```
Do you have any idea?
Thank

---

### Post by sudodus on 2014-01-02
I suggest that you let the Ubuntu computer be an ssh server (it is already, if I understand correctly).

Then you can use an sftp client and use ftp transfer with ssh encryption. There are at least two free clients that can do that from Windows:

WinSCP and Filezilla.

---

### Post by erotavlas on 2014-01-03
Yes, Ubuntu is the server. I know and I'm using Filezilla. I would like to use something like tar+ssh since it is faster than the other options sftp, scp. Moreover I would like to use command line.
Thank you for you help.

---

### Post by sudodus on 2014-01-03
Well, it is possible to use the '***dosprompt***' command line in Windows, and there are several programs, that can be installed from the unix/linux world, for example tar and ftp.

Another option is to install ***Cygwin*** into Windows and emulate linux. Then you have almost the whole linux environment including ***rsync***, that is a good tool to copy, backup and synchronizing directory trees within and between computers.

Finally you can install ***VirtualBox*** and run real linux in a virtual machine in the Windows machine.

-o-

Out of these alternatives, I suggest that you try [Cygwin]("http://www.cygwin.com/"). I used it a lot several years ago. I don't know how good it is now (probably much better). It is worth trying.

---

### Post by steeldriver on 2014-01-03
Have you taken a step back and tested piping to 7z WITHOUT ssh in the mix? I couldn't even get that to work. The help for my version of 7z (9.20 64-bit) says 

> Note: The current version of 7-Zip support reading of archives from stdin  only for xz, lzma, tar, gzip and bzip2 archives.

and sure enough

```

>type myfile.7z | "C:\Program Files\7-Zip\7z.exe" x -si -t7z myfile

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18

Processing archive:

[B]Error: Not implemented
[/B]
```

however when I try a gzip archive it says "Everything is Ok" but doesn't actually produce any output

```

>type myfile.gz | "C:\Program Files\7-Zip\7z.exe" x -si -tgzip myfile

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18

Processing archive:


** Everything is Ok**

Files: 0
Size:       0
Compressed: 0

>type myfile
The system cannot find the file specified.

```

---

### Post by erotavlas on 2014-01-03
Ok, thank for the informations. On linux 7zip works with ssh and the command in my previous post. On windows I don't know, I will try.

---

### Post by sudodus on 2014-01-03
If it does not work in Windows, you can try with Cygwin, where you can also try xz (instead of 7zip)

---

### Post by bashiergui on 2014-01-03
Any reason not to use powershell on the Windows client?

---

