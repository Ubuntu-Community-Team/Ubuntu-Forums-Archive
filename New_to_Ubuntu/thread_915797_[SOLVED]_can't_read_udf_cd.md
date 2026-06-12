---
title: "[SOLVED] can't read udf cd"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by ejv on 2008-09-10
Hi 

I can't read a cd with images on it;  apparently it's on **udf** format.  I found some forums with similar problems but couldn't really follow them.  there is an old thread named   **UDF 2.5 support** where you have to download the following file

udf-filesystem-2.5.tar.gz

but I'm missing an associate application in order to be able to open it. I've got version 8.04, downloaded about a week ago.

I already edited my fstab and it sees as in the attachment.

Thanks for any advice!

ejv

---

### Post by Pro-reason on 2008-09-10
There are many points there.

Firstly, you don't need to download that .tar.gz file to be able to work with UDF filesystems.  When you need software on Ubuntu, your first port of call should ***always*** be the repositories (accessible via “Synaptic” or “Add and Remove Applications”).

The software package for working with UDF is called “udftools”.  Install it in Synaptic, or type this into a terminal: “sudo apt-get install udftools”.

It is also not the case that you need any special software to open .tar.gz files.  You can use the “file-roller” application to open them, or else the “tar -xzvf” command in the terminal.

You don't need to post screenshots of text files.  Simply paste their contents here.

---

### Post by ejv on 2008-09-10
All right.

i downloaded the udf tools but i still recieve the following message when opening the cd:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

the cd was burnt using windows vista

thanks

ejv

---

### Post by Pro-reason on 2008-09-11
OK, I've been reading through some support threads on this issue, and it seems to be a case of Ubuntu Hardy Heron not being able to read multi-session UDF DVDs created by Windows Vista.

Apparently, the upcoming Ubuntu Intrepid Ibex handles them just fine.

You will indeed need to do some fiddling around to make this work on Hardy.  I can see that the instructions in the various threads require some knowledge to implement.  So, I've simplified it into one list of things that need to be entered into a terminal, with no modifications.

Open a terminal and enter each of these in turn.  Use copy and paste.

```

sudo apt-get install build-essential linux-headers-`uname -r`
cd ~/Desktop
wget -O udf-filesystem-2.5.tar.gz http://ubuntuforums.org/attachment.php?attachmentid=61993&d=1205001057
tar -xvzf udf-filesystem-2.5.tar.gz 
cd udf-filesystem-2.5 && ls
echo "1150a1151" > tinypatch.patch
echo "> (le16_to_cpu(((__le16 *)upm2->partIdent.identSuffix)[0]) == 0x0201) ||" >> tinypatch.patch
patch src/super.c < tinypatch.patch 
make
sudo rmmod  udf
sudo insmod src/udf.ko
sudo cp  src/udf.ko  /lib/modules/`uname -r`/kernel/fs/udf/

```

With that many commands, the chances are that something will go wrong, but give it a chance.

After all that, you will allegedly be able to play your DVDs.  Perhaps a restart is required.

I'm not able to check any of this, because I don't have Windows Vista.

---

### Post by ejv on 2008-09-11
Hello  

I began the process but when i try

cd udf-filesystem-2.5 && ls

it answers that it doesn't exist.

In my desktop I can see the box icon named "cd udf-filesystem-2.5.tar.gz" and i can open it and navigate through it.

Thanks once more

ejv

---

### Post by Pro-reason on 2008-09-11
Try again, and paste here everything that the terminal gives you.  Unless you do that, I can't know what went wrong.

Put [noparse]```
[/noparse] at the beginning of it and [noparse]
```[/noparse] at the end, for legibility.

---

### Post by ejv on 2008-09-12
Hi

I tryed again and posted the complete terminal. 

My system is in spanish. so "Desktop" is "Escritorio".  

After the first wget command, at the end the cursor never comes to "edna@edna-desktop:~$" and that's why i typed the first time "cd udf-filesystem-2.5 && ls" there where you see it.


```
edna@edna-desktop:~$ sudo apt-get install build-essential linux-headers-`uname -r`
[sudo] password for edna: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
build-essential ya está en su versión más reciente.
linux-headers-2.6.24-19-generic ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
edna@edna-desktop:~$ cd ~/Escritorio
edna@edna-desktop:~/Escritorio$ wget -O udf-filesystem-2.5.tar.gz http://ubuntuforums.org/attachment.php?attachmentid=61993&d=1205001057
[1] 5950
edna@edna-desktop:~/Escritorio$ tar -xvzf udf-filesystem-2.5.tar.gz 
--10:47:16--  http://ubuntuforums.org/attachment.php?attachmentid=61993
           => `udf-filesystem-2.5.tar.gz'

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Salida con error demorada desde errores anteriores
edna@edna-desktop:~/Escritorio$ Resolviendo ubuntuforums.org... 91.189.94.12
Conectando a ubuntuforums.org|91.189.94.12|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 84,633 (83K) [unknown/unknown]

100%[====================================>] 84,633       252.60K/s             

10:47:16 (251.80 KB/s) - `udf-filesystem-2.5.tar.gz' guardado [84633/84633]

cd udf-filesystem-2.5 && ls
bash: cd: udf-filesystem-2.5: No existe el fichero ó directorio
[1]+  Done                    wget -O udf-filesystem-2.5.tar.gz http://ubuntuforums.org/attachment.php?attachmentid=61993
edna@edna-desktop:~/Escritorio$ cd udf-filesystem-2.5 && ls
bash: cd: udf-filesystem-2.5: No existe el fichero ó directorio
edna@edna-desktop:~/Escritorio$
```

and there's where it says that the file or folder doesn't exist.  The box named udf-filesystem-2.5.tar.gz is in my "Escritorio"

---

### Post by Pro-reason on 2008-09-12
One step failed.  We have to fix that.

I've just tried it again, and it worked.  I don't know why it doesn't work for you.

Let's do it differently.  Instead of using the *wget* command, go to [the other thread]("http://ubuntuforums.org/showthread.php?t=718744") and download the attachment there.  Save it to your desktop.  Then continue from there.

---

### Post by ejv on 2008-09-12
I erased the first one and downloaded from the "other thread".  But the result is the same.


> edna@edna-desktop:~$ cd ~/Escritorio
edna@edna-desktop:~/Escritorio$ cd udf-filesystem-2.5 && ls
bash: cd: udf-filesystem-2.5: No existe el fichero ó directorio
edna@edna-desktop:~/Escritorio$ 


Shouldn't it be easy?  We're just trying to get "into the box", aren't we?

---

### Post by Pro-reason on 2008-09-12
> **ejv said:**
> I erased the first one and downloaded from the "other thread".  But the result is the same.




Shouldn't it be easy?  We're just trying to get "into the box", aren't we?

As far as I can see, you've just done “cd” again, but you need to do the “tar” command first to extract the archive.  After that you can “cd” into it.

---

### Post by ejv on 2008-09-12
Everything worked out fine, i restarted, but with the cd the message is the same:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I've got some questions:

1) When in the terminal, after giving an order, if you press the "enter" key in the middle of a process, does it affect it?  Sometimes the cursor just blinks for a long time on the left edge and by pressing enter the process continues.

2) What should i do with the newly opened folder udf-filesystem-2.5 and with the "box" (.tar.gz)?  They're now on my desktop and on my personal folder in /home.

And thanks once more for your time, pro-reason.

ejv

---

### Post by Pro-reason on 2008-09-12
Pressing keys while a command is executing generally doesn't affect it.

---------

You just need to follow the steps, and if there are errors from a step, react to them.

If you have downloaded the archive to your desktop, then extract it with the command I gave.

Does that work?  If not, then make it work.  If so, then do the next step.

Use the “cd” command to enter the directory.  Does that work?  If not, make it work.  If so, then do the next step.

---

### Post by ejv on 2008-09-12
Oh yes, the commands worked out fine 'till the end. I followed your steps until the end and then restarted the computer, tried to open the cd but... it didn't work.  It says it can't mount it. Then in Places>Computer>UDF Volume (i'm translating from spanish) I rightclick and try to open it, and there's where i get the message i pasted.

I never in my life typed orders on a terminal so i have no idea how to "react" to an error, or how to "make something work".  In the past weeks i've just begun to understand a bit, but that's all.

---

### Post by ejv on 2008-09-12
No wait!!!

It's now working fine.  I did the process once more from the beginning and now i can see the images on the cd.  I'm sorry for the clumsiness...

Thanks a lot man!!!

---

### Post by Pro-reason on 2008-09-12
Here are the commands again.

**STEP 1**:

```

sudo apt-get install build-essential linux-headers-`uname -r`

```

This is just to install some software that we will need.  You only have to do this once.
[B]
STEP 2:[/B]

```

cd ~/Desktop

```

This is just to go to a convenient location.  It doesn't really matter where.  You can make it ~/Escritorio or anywhere else in your home directory.

**STEP 3:**

```

wget -O udf-filesystem-2.5.tar.gz http://ubuntuforums.org/attachment.php?attachmentid=61993&d=1205001057

```

This is to download an archive file that we need.  If it does not download correctly, then visit [the other thread]("http://ubuntuforums.org/showthread.php?t=718744") and download it from your browser.  Put the downloaded file on your desktop (or whatever directory you chose in step 2).

**STEP 4:**

```

tar -xvzf udf-filesystem-2.5.tar.gz 

```
This extracts the contents of the archive.  You should see a list of the contents of the archive at this point.  If an error occurs, then do not continue to step 5.  Download a copy of the archive without errors instead.

If you like, instead of typing this command, you can right-click on the archive on your desktop, and choose “Extract here”.
[B]
STEP 5:[/B]

```

cd udf-filesystem-2.5 && ls

```
This “cd” (“change directory”) command simply moves you into the directory that step 4 extracted from the archive.  You can also do “cd ~/Escritorio/udf-filesystem-2.5”.

The “&& ls” on the end simply prints a list of the contents of the directory, so that you can check that you are in the right one.

**STEP 6:**

```

echo "1150a1151" > tinypatch.patch
echo "> (le16_to_cpu(((__le16 *)upm2->partIdent.identSuffix)[0]) == 0x0201) ||" >> tinypatch.patch

```

These two lines create a new file called “tinypatch.patch”.  We will use it later.

**STEP 7:**

```

patch src/super.c < tinypatch.patch 

```
This uses the patch we created in order to fix an error in the software we downloaded in step 3.

**STEP 8:**

```

make

```
This compiles the software.  It is a complicated process, but you don't have to understand it.  You just have to type that one word.
[B]
STEP 9:[/B]

```

sudo rmmod  udf
sudo insmod src/udf.ko
sudo cp  src/udf.ko  /lib/modules/`uname -r`/kernel/fs/udf/

```
This installs the software.  It won't produce much output on the terminal, but it will apparently fix your problem.

If you just go through each step one by one, it will work.

---

### Post by Pro-reason on 2008-09-12
> **ejv said:**
> No wait!!!

It's now working fine.  I did the process once more from the beginning and now i can see the images on the cd.  I'm sorry for the clumsiness...

Thanks a lot man!!!

OK, glad to see it worked OK.  Espero que no tengas más problemitas con eso.

---

### Post by ejv on 2008-09-12
PERO SI HABLAS ESPAÑOL!!!!!
 
Yo soy colombiano.  Sólo me falta por saber qué hago con las carpetas que andan molestando en mi escritorio. La caja y la carpeta de los udf filesystem.  Como tambien están en mi carpeta personal, no pasa nada si las mando a la papelera, cierto?

Un saludo y otra vez muchas gracias!

ejv

---

### Post by Pro-reason on 2008-09-12
Yes, you can safely delete all those files now.  We've finished with them.

I am a Spanish teacher.  But the forum rules say we have to use English here, except in the LoCo forums.  You can use Spanish in private messages if you like, though.

---

### Post by davemc on 2009-02-04
Yes, the above fix does work.  The patched UDF file system will now open those troublesome UDF DVD's

tail /var/log/syslog
Feb  4 20:05:19 boxen kernel: [15806.462906] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume '^P', timestamp 2008/11/18 14:00 (130c)

Thanks to those patiently posting the exact steps.

---

### Post by ozguitarplayer on 2009-02-11
I know this item isi solved and I don't know if it is ok to restart it like this however....
I followed the execllent steps above until the 'make' command and all I get is a heap of error messages as can be seen.....can anyone advise me as to why all the error messages?


nigel@Master:~/Desktop/udf-filesystem-2.5$ cd ~/Desktop                                                 
nigel@Master:~/Desktop$ cd ~/
nigel@Master:~$ downloads    
bash: downloads: command not found
nigel@Master:~$ cd ~/Downloads
nigel@Master:~/Downloads$ wget -O udf-filesystem-2.5.tar.gz [http://ubuntuforums.org/attachment.php?attachmentid=61993&d=1205001057](http://ubuntuforums.org/attachment.php?attachmentid=61993&d=1205001057)
[1] 6812                                                                                                                          
nigel@Master:~/Downloads$ --2009-02-12 10:09:29--  [http://ubuntuforums.org/attachment.php?attachmentid=61993](http://ubuntuforums.org/attachment.php?attachmentid=61993)                      
Resolving ubuntuforums.org... 91.189.94.12                                                                                        
Connecting to ubuntuforums.org|91.189.94.12|:80... connected.                                                                     
HTTP request sent, awaiting response... 200 OK                                                                                    
Length: 84633 (83K) [unknown/unknown]                                                                                             
Saving to: `udf-filesystem-2.5.tar.gz'                                                                                            

100%[===================================================================================================>] 84,633      42.5K/s   in 1.9s    

2009-02-12 10:09:32 (42.5 KB/s) - `udf-filesystem-2.5.tar.gz' saved [84633/84633]

tar -xvzf udf-filesystem-2.5.tar.gz
udf-filesystem-2.5/                
udf-filesystem-2.5/Kbuild          
udf-filesystem-2.5/COPYING         
udf-filesystem-2.5/Makefile        
udf-filesystem-2.5/src/            
udf-filesystem-2.5/src/super.c     
udf-filesystem-2.5/src/udftime.c   
udf-filesystem-2.5/src/inode.c     
udf-filesystem-2.5/src/namei.c     
udf-filesystem-2.5/src/udf_fs_sb.h 
udf-filesystem-2.5/src/osta_udf.h  
udf-filesystem-2.5/src/partition.c 
udf-filesystem-2.5/src/fsync.c     
udf-filesystem-2.5/src/udfdecl.h   
udf-filesystem-2.5/src/UDF_2.50-linux-2.6.24.patch
udf-filesystem-2.5/src/dir.c                      
udf-filesystem-2.5/src/udf_i.h                    
udf-filesystem-2.5/src/misc.c                     
udf-filesystem-2.5/src/ecma_167.h                 
udf-filesystem-2.5/src/unicode.c                  
udf-filesystem-2.5/src/symlink.c                  
udf-filesystem-2.5/src/ialloc.c                   
udf-filesystem-2.5/src/udfend.h                   
udf-filesystem-2.5/src/lowlevel.c                 
udf-filesystem-2.5/src/file.c                     
udf-filesystem-2.5/src/udf_fs.h                   
udf-filesystem-2.5/src/udf_sb.h                   
udf-filesystem-2.5/src/truncate.c                 
udf-filesystem-2.5/src/directory.c                
udf-filesystem-2.5/src/crc.c                      
udf-filesystem-2.5/src/balloc.c                   
udf-filesystem-2.5/src/Makefile                   
udf-filesystem-2.5/src/.tmp_versions/
[1]+  Done                    wget -O udf-filesystem-2.5.tar.gz [http://ubuntuforums.org/attachment.php?attachmentid=61993](http://ubuntuforums.org/attachment.php?attachmentid=61993)
nigel@Master:~/Downloads$ cd udf-filesystem-2.5 && ls
COPYING  Kbuild  Makefile  src
nigel@Master:~/Downloads/udf-filesystem-2.5$ echo "1150a1151" > tinypatch.patch
nigel@Master:~/Downloads/udf-filesystem-2.5$ echo "> (le16_to_cpu(((__le16 *)upm2->partIdent.identSuffix)[0]) == 0x0201) ||" >> tinypatch.patch
nigel@Master:~/Downloads/udf-filesystem-2.5$ patch src/super.c < tinypatch.patch
patching file src/super.c
nigel@Master:~/Downloads/udf-filesystem-2.5$ make
make -C /lib/modules/2.6.27-11-generic/build M=/home/nigel/Downloads/udf-filesystem-2.5 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/nigel/Downloads/udf-filesystem-2.5/src/balloc.o
In file included from /home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:22:
/home/nigel/Downloads/udf-filesystem-2.5/src/udfdecl.h:4:26: error: linux/udf_fs.h: No such file or directory
In file included from /home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:28:
/home/nigel/Downloads/udf-filesystem-2.5/src/udf_i.h: In function &#8216;UDF_I&#8217;:
/home/nigel/Downloads/udf-filesystem-2.5/src/udf_i.h:7: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/udf_i.h:7: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;__mptr&#8217;
/home/nigel/Downloads/udf-filesystem-2.5/src/udf_i.h:7: warning: initialization from incompatible pointer type
/home/nigel/Downloads/udf-filesystem-2.5/src/udf_i.h:7: error: invalid use of undefined type &#8216;struct udf_inode_info&#8217;
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c: In function &#8216;__load_block_bitmap&#8217;:
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:109: error: implicit declaration of function &#8216;udf_debug&#8217;
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c: In function &#8216;udf_table_free_blocks&#8217;:
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:446: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:512: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:514: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:543: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:556: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:557: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:569: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:597: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c: In function &#8216;udf_table_prealloc_blocks&#8217;:
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:633: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:635: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:642: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c: In function &#8216;udf_table_new_block&#8217;:
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:698: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:700: error: dereferencing pointer to incomplete type
/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.c:715: error: dereferencing pointer to incomplete type
make[3]: *** [/home/nigel/Downloads/udf-filesystem-2.5/src/balloc.o] Error 1
make[2]: *** [/home/nigel/Downloads/udf-filesystem-2.5/src] Error 2
make[1]: *** [_module_/home/nigel/Downloads/udf-filesystem-2.5] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Error 2
nigel@Master:~/Downloads/udf-filesystem-2.5$

---

### Post by Pablo Rodríguez on 2009-10-19
Hello,

I have the same problem with Vista DVDs but I cannot download udf-filesystem-2.5.tar.gz from these addresses:

[http://ubuntuforums.org/showthread.php?t=718744](http://ubuntuforums.org/showthread.php?t=718744)
[http://ubuntuforums.org/attachment.php?attachmentid=61993&d=1205001057](http://ubuntuforums.org/attachment.php?attachmentid=61993&d=1205001057)

Would it be posible to have an updated link?

Many thanks in advance for your help.

Regards,

---

### Post by Pro-reason on 2009-10-19
I believe that this fix is probably out of date by now.  Advances in the Linux kernel probably make it unnecessary.

Type ‘uname -a’ on the command line.  What is the output?

---

