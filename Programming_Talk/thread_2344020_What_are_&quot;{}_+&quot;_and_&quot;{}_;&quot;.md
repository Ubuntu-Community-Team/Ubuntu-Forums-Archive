---
title: "What are &quot;{} +&quot; and &quot;{} \;&quot;?"
date: 2016-11-21
forum: Programming Talk
---

### Post by vasa1 on 2016-11-21
What are their technical names? Are they placeholders? Is "{}" always followed by "\;" or "+"?

Both seem to do nearly the same thing. For example:```
cd /etc/grub.d
/etc/grub.d $ find . -type f -exec du {} \;
12	./30_os-prober
12	./20_linux_xen
4	./README
12	./10_linux
4	./30_uefi-firmware
4	./41_custom
4	./20_memtest86+
8	./05_debian_theme
12	./00_header
4	./40_custom
/etc/grub.d $ find . -type f -exec du {} +
12	./30_os-prober
12	./20_linux_xen
4	./README
12	./10_linux
4	./30_uefi-firmware
4	./41_custom
4	./20_memtest86+
8	./05_debian_theme
12	./00_header
4	./40_custom
/etc/grub.d $ find . -type f -exec ls -l {} \;
-rwxr-xr-x 1 root root 11692 May 16  2014 ./30_os-prober
-rwxr-xr-x 1 root root 11082 Apr 16  2016 ./20_linux_xen
-rw-r--r-- 1 root root 483 May 16  2014 ./README
-rwxr-xr-x 1 root root 12261 Apr 16  2016 ./10_linux
-rwxr-xr-x 1 root root 1418 Apr 16  2016 ./30_uefi-firmware
-rwxr-xr-x 1 root root 216 May 16  2014 ./41_custom
-rwxr-xr-x 1 root root 1992 Mar 12  2014 ./20_memtest86+
-rwxr-xr-x 1 root root 6258 Mar 15  2016 ./05_debian_theme
-rwxr-xr-x 1 root root 9791 Dec 17  2015 ./00_header
-rwxr-xr-x 1 root root 214 May 16  2014 ./40_custom
05:33 AM /etc/grub.d $ find . -type f -exec ls -l {} +
-rwxr-xr-x 1 root root  9791 Dec 17  2015 ./00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 ./05_debian_theme
-rwxr-xr-x 1 root root 12261 Apr 16  2016 ./10_linux
-rwxr-xr-x 1 root root 11082 Apr 16  2016 ./20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 ./20_memtest86+
-rwxr-xr-x 1 root root 11692 May 16  2014 ./30_os-prober
-rwxr-xr-x 1 root root  1418 Apr 16  2016 ./30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 16  2014 ./40_custom
-rwxr-xr-x 1 root root   216 May 16  2014 ./41_custom
-rw-r--r-- 1 root root   483 May 16  2014 ./README
05:33 AM /etc/grub.d $ 
```If "{} \;" and "{} +" are essentially equivalent, is there any reason to prefer one over the other? In the example, above the output of "ls -l {} +" is neater.

---

### Post by steeldriver on 2016-11-21
From `man find`

```

       -exec command ;
              Execute  command;  true  if 0 status is returned.  All following
              arguments to find are taken to be arguments to the command until
              an  argument  consisting of `;' is encountered.  The string `{}'
              is replaced by the current file name being processed  everywhere
              it occurs in the arguments to the command, not just in arguments
              where it is alone, as in some versions of find.  Both  of  these
              constructions might need to be escaped (with a `\') or quoted to
              protect them from expansion by the shell.  See the EXAMPLES sec&#8208;
              tion for examples of the use of the -exec option.  The specified
              command is run once for each matched file.  The command is  exe&#8208;
              cuted  in  the starting directory.   There are unavoidable secu&#8208;
              rity problems surrounding use of the -exec  action;  you  should
              use the -execdir option instead.

       -exec command {} +
              This  variant  of the -exec action runs the specified command on
              the selected files, [B]but the command line is built  by  appending
              each  selected file name at the end; the total number of invoca&#8208;
              tions of the command will  be  much  less  than  the  number  of
              matched  files.[/B]   The command line is built in much the same way
              that xargs builds its command lines.  Only one instance of  `{}'
              is  allowed  within the command.  The command is executed in the
              starting directory.

```

I tend to think of the `{} +` form as find's built-in equivalent of xargs

I don't think the find documentation names {} as such - but the xargs man page refers to it as REPLACE-STR

---

### Post by kpatz on 2016-11-21
The {} is a placeholder, where the output of the find command is inserted to build the command to be executed.

If you use {} \; it executes the command once for each file/directory found.  For example, let's say there's file1, file2, and file3 in the current directory, and you run:
```
find . -type f -exec ls -l {} \;
```what will be executed is:```
ls -l ./file1
ls -l ./file2
ls -l ./file3
```The command will be invoked once per found item.
If you run ```
find . -type f -exec ls -l {} +
```what will be executed is:```
ls -l ./file1 ./file2 ./file3
```The command will be invoked once with all the found items listed on the command line, similar to how xargs works.

---

### Post by vasa1 on 2016-11-21
Thank you, steeldriver and kpatz!

Going by what's been quoted from *man find*, the + route seems more efficient than the ; one. It would also explain when the ls -l results using the + route appear tidier.

The + route will *always* return *true*; I'm guessing that may matter to advanced users. 

And, it appears that *-execdir* maybe better than plain *-exec*:```
              Like -exec, but the specified command is run from the  subdirectory
              containing the matched file, which is not normally the directory in
              which you started find.  This a much more secure method for  invok&#8208;
              ing commands, as it avoids race conditions during resolution of the
              paths to the matched files.  As with the -exec action, the `+' form
              of  -execdir  will  build  a  command line to process more than one
              matched file, but any given invocation of command  will  only  list
              files that exist in the same subdirectory.  If you use this option,
              you must ensure that your $PATH environment variable does not  ref&#8208;
              erence  `.';  otherwise, an attacker can run any commands they like
              by leaving an appropriately-named file in a directory in which  you
              will  run  -execdir.   
```

---

