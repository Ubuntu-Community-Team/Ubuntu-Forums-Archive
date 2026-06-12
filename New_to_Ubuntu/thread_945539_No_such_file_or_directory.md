---
title: "No such file or directory"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by pizzafarmer on 2008-10-12
I am trying to install the new Across Lite for Linux version, and have run across a strange problem. Maybe I'm just too new at this and there is something simple that I'm overlooking, but it looks like I have a file system problem.

When I enter the ldd command for the acrossl executable, I get this:

ldd acrossl
/usr/bin/ldd: line 117: ./acrossl: No such file or directory

The file is there and readable:

ls -lsa
total 1252
   4 drwxr-xr-x 2 root root     4096 2008-10-11 18:58 .
   4 drwxrwxrwx 7 root root     4096 2008-10-11 18:58 ..
1244 -rwxr-xr-x 1  871 users 1266040 1997-01-09 12:18 acrossl

Can anyone set me straight?

---

### Post by Pelham123 on 2008-10-12
If you dont have any joy you can try the xword package. Its in synaptic package manager

---

### Post by spiderbatdad on 2008-10-12
cd into the directory first:
```
cd /usr/bin
ldd acrossl
```

---

### Post by pizzafarmer on 2008-10-12
I did install Xword, but there are problems with printing that, according to the developer, may not have a solution in the near future. Also, any special graphics, such as circles within the grid, aren't displayed.

---

### Post by pizzafarmer on 2008-10-12
> **spiderbatdad said:**
> cd into the directory first:
```
cd /usr/bin
ldd acrossl
```
No luck there either. The system isn't having problems finding ldd; acrossl is what it can't find. I tried from the directory that acrossl is in:

/usr/bin/ldd acrossl
/usr/bin/ldd: line 117: ./acrossl: No such file or directory

---

### Post by Pelham123 on 2008-10-12
Are you running 64-bit Ubuntu?

On a trek through Google similar problems have been noted with other applications and files not being found. Solution was to install 32-bit libraries for the App.

---

### Post by spiderbatdad on 2008-10-12
> **pizzafarmer said:**
> No luck there either. The system isn't having problems finding ldd; acrossl is what it can't find. I tried from the directory that acrossl is in:

/usr/bin/ldd acrossl
/usr/bin/ldd: line 117: ./acrossl: No such file or directory

?? ldd is not a directory. ldd is a command to list the shared libraries of a program. From the directory /usr/bin you would run ldd acrossl. like so:

```
-laptop:~$ cd /usr/bin
-laptop:/usr/bin$ ldd ssh
	linux-gate.so.1 =>  (0xb7f59000)
	libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7f1a000)
	libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7dcf000)
	libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7dca000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb7db4000)
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7d9b000)
	libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7d69000)
	libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0xb7d3f000)
	libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0xb7cad000)
	libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0xb7c88000)
	libcom_err.so.2 => /lib/libcom_err.so.2 (0xb7c84000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b26000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b22000)
	libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0xb7b19000)
	libkeyutils.so.1 => /lib/libkeyutils.so.1 (0xb7b14000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7afb000)
	/lib/ld-linux.so.2 (0xb7f3f000)
-laptop:/usr/bin$ 



```

---

### Post by pizzafarmer on 2008-10-13
> **spiderbatdad said:**
> ?? ldd is not a directory. ldd is a command to list the shared libraries of a program. From the directory /usr/bin you would run ldd acrossl. like so:

```
-laptop:~$ cd /usr/bin
-laptop:/usr/bin$ ldd ssh
	linux-gate.so.1 =>  (0xb7f59000)
	libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7f1a000)
	libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7dcf000)
	libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7dca000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb7db4000)
	libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7d9b000)
	libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb7d69000)
	libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0xb7d3f000)
	libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0xb7cad000)
	libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0xb7c88000)
	libcom_err.so.2 => /lib/libcom_err.so.2 (0xb7c84000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b26000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b22000)
	libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0xb7b19000)
	libkeyutils.so.1 => /lib/libkeyutils.so.1 (0xb7b14000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7afb000)
	/lib/ld-linux.so.2 (0xb7f3f000)
-laptop:/usr/bin$ 



```

spiderbatdad, I think I have provided too little information about the error. The problem isn't with ldd; I only used that as an example. I get the same error if I try to execute the file. I should get a different error message if all of the libraries aren't there; instead I get the "no such file..." error. The strange thing is that the file appears in the directory listing. I can move the file - it was originally in the /usr/games directory, and after I started seeing this problem, I made a new subdirectory and moved the file there. There was no problem with the mv command. I still get the "no such file" error in the new directory. I used the following to move the file back to the /usr/games directory:

/usr/games$ cd across
/usr/games/across$ sudo mv acrossl ..
/usr/games/across$ cd ..
/usr/games$ ls -lsa acrossl
1244 -rwxr-xr-x 1 871 users 1266040 1997-01-09 12:18 acrossl

The file moved back, and is readable by everyone, but:

/usr/games$ acrossl
bash: /usr/games/acrossl: No such file or directory

bash defaulted to the full path to the file, but couldn't see it.

Same problem this way:

/usr/games$ ./acrossl
bash: ./acrossl: No such file or directory

Same thing with ldd:

/usr/games$ ldd acrossl
/usr/bin/ldd: line 117: ./acrossl: No such file or directory

I tried ldd on another file in the same directory:

/usr/games$ ldd banner
	linux-gate.so.1 =>  (0xb7f9a000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7e3a000)
	/lib/ld-linux.so.2 (0xb7f9b000)

No problemo.

Am I looking at a basic incompatibility here?:confused:


Pelham123, I am running a 64 bit system, but could that be the problem with not being able to see the file?

---

### Post by Pelham123 on 2008-10-13
I asked if you have 64-bit Ubuntu, because I read another post about 'ldd' command not showing files despite them being listed with the 'ls' command. The solution was to download 32-bit libraries which solved the problem on 64-bit systems.

From what I've read the libraries seem to be the most common problem with Across Lite not being able to cope with updated libraries. This was taken from the online manual:
[I]
You may also have one or more libraries that have a higher revision number than the one used in creating Across Lite. For example, you may have Motif 2.0 libraries while Across Lite on the Sun platform is built using Motif 1.x. In such cases, people have often been able to use Across Lite by creating a symbolic link to the available libraries and naming the link with a lower number as expected by Across Lite. This method is not guaranteed to work but it is worth trying.[/I]

Found here: [http://www.litsoft.com/across/alite/unix/man/](http://www.litsoft.com/across/alite/unix/man/)

##############################################

It seems other users have had the same issue:

[http://ubuntuforums.org/showthread.php?t=325510](http://ubuntuforums.org/showthread.php?t=325510)

Note that post was from 2006...

##########################################

Another approach, less than ideal I'm afraid, is to use the Wine emulator and run the windows version.

I dont know how much more help I can be I'm afraid.

Good luck ;)

---

### Post by pizzafarmer on 2008-10-13
> **Pelham123 said:**
> I asked if you have 64-bit Ubuntu, because I read another post about 'ldd' command not showing files despite them being listed with the 'ls' command. The solution was to download 32-bit libraries which solved the problem on 64-bit systems.

From what I've read the libraries seem to be the most common problem with Across Lite not being able to cope with updated libraries. This was taken from the online manual:
[I]
You may also have one or more libraries that have a higher revision number than the one used in creating Across Lite. For example, you may have Motif 2.0 libraries while Across Lite on the Sun platform is built using Motif 1.x. In such cases, people have often been able to use Across Lite by creating a symbolic link to the available libraries and naming the link with a lower number as expected by Across Lite. This method is not guaranteed to work but it is worth trying.[/I]

Found here: [http://www.litsoft.com/across/alite/unix/man/](http://www.litsoft.com/across/alite/unix/man/)

##############################################

It seems other users have had the same issue:

[http://ubuntuforums.org/showthread.php?t=325510](http://ubuntuforums.org/showthread.php?t=325510)

Note that post was from 2006...

##########################################

Another approach, less than ideal I'm afraid, is to use the Wine emulator and run the windows version.

I dont know how much more help I can be I'm afraid.

Good luck ;)


Thanks for the info. An interesting quirk, I guess, and very confusing to the uninitiated. I had not seen the post you found - perhaps I wasn't searching for all the right things. I had also thought about using Wine - I haven't installed it yet because I want to run as much stuff as I can "native", so to speak.

---

