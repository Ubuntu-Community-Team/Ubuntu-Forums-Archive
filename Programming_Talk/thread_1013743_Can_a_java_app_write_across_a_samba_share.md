---
title: "Can a java app write across a samba share"
date: 2008-12-17
forum: Programming Talk
---

### Post by jnorthr on 2008-12-17
Hardware config:
windows XP home has shared folder with audit.txt file
ubuntu 8.10 laptop can see shared folder and audit.txt file.
I can use gedit from ubuntu to open and write audit entries into the audit.txt file then close it and audit trail entries are there. Great !

Is there any way using java/groovy client app on ubuntu, i can write a java program to write directly into audit.txt across the samba shared folder - or i am missing something :confused:

---

### Post by SeanHodges on 2008-12-17
2 options that I can think of:

You can reference the mount-point that GVFS has placed when you first accessed the share (which will be in ~/.gvfs/):

```
String server = "myserver";
String share = "shared";
File myfile = new File(System.getProperty("user.dir") + "/.gvfs/" + share + " on " + server + "/audit.txt");
myfile.createNewFile();
```

Obviously, this will mean that you need to authenticate with the server before the program will work (the same as Windows).

Alternatively, you could try using an SMB client library for Java to handle all the browsing and authentication for you. Something like [JCIFS]("http://jcifs.samba.org/") will probably be what you're looking for.

Also, it might be worth looking at the GEdit source code to see how it is interacting with Samba/GVFS (after all, thats partly what it is there for :)).

---

### Post by drubin on 2008-12-17
> **jnorthr said:**
> Hardware config:
windows XP home has shared folder with audit.txt file
ubuntu 8.10 laptop can see shared folder and audit.txt file.
I can use gedit from ubuntu to open and write audit entries into the audit.txt file then close it and audit trail entries are there. Great !

Is there any way using java/groovy client app on ubuntu, i can write a java program to write directly into audit.txt across the samba shared folder - or i am missing something :confused:

I have never done this from linux to windows, but from windows to linux works perfectly. Provided you have the correct permisions.

Also remember that as far as the Java is concerend this is just another file/folder the OS(driver being samba - driver might be the wrong term but close enough...) handles how the data is transfered/written.

---

### Post by SeanHodges on 2008-12-17
> **drubin said:**
> I have never done this from linux to windows, but from windows to linux works perfectly. Provided you have the correct permisions.

Also remember that as far as the Java is concerend this is just another file/folder the OS(driver being samba - driver might be the wrong term but close enough...) handles how the data is transfered/written.

Yeah, it will work fine accessing Linux shares from Windows, but Linux does not support UNC paths so unfortunately it doesn't work the other way around.

You cannot, for example do:

```
File myfile = new File("\\\\server\\share");
```

Because the path will not be valid on non-Windows systems. Neither can you do:

```
File myfile = new File("smb://server/share");
```

Because smb:/ depends on a Samba client, which lies in user space and is not understood by Java.

Any of my suggestions above should work around this problem, personally I would try using the ~/.gvfs/ path, unless you need something more sophisticated.

Out of interest, I took a look at Gedit's source code. It uses the GVFS library directly to retrieve files from a share. However, so far I have not been able to find java bindings for GVFS, so if my first suggestion doesn't cut it you will need to scout around for a decent CIFS/SMB library for Java.

---

### Post by jnorthr on 2008-12-17
Great ! Many thanx for that advice.I was hoping i could code something like:

[COLOR="SeaGreen"]File myfile = new File("smb://server/share");[/COLOR]

but perhaps not. I do not understand UNC notations so am lost there.

There is a possibility i can re-design things to keep the audit.txt on my ubuntu system to capture audit messages and place a java client on the XP as you suggest to write 'backwards' across the samba connection.

Where is Bruce Eckel of 'Thinking in Java' when i need him ):P

---

### Post by jnorthr on 2008-12-18
ok, my terminal session fix on ubuntu 8.10 looked like this:
read this guide from rmh on another ubuntu forum:

[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=332575&highlight=smbfs
[/COLOR]

[COLOR="Magenta"]sudo apt-get install smbfs[/COLOR]

when successful:

[COLOR="Magenta"]mkdir /mnt/web

sudo  mount -t cifs -o rw,username=fred,workgroup=mshome //fredserver/web  /mnt/web

df[/COLOR]

notes: the mkdir creates a folder name that's visible to ubuntu file system called 'web' - yours can be any valid folder name but suggest you just go with this till you get the hang of it.

on my system i had to use sudo user to have enough permissions to mount; 
your username= will need to change to your sudo user name; your workgroup name may be different if 1) your server is not a windows system or 2) you've changed the workgroup name on your windows box;
the 'df' command just confirms you have a connection:
[COLOR="Magenta"]

jim@tiny:~/groovy$ cd /mnt
jim@tiny:/mnt$ ls -al
total 8
drwxr-xr-x  3 root root 4096 2008-12-18 00:17 .
drwxr-xr-x 20 root root 4096 2008-11-28 07:56 ..
drwxrwxrwx  1 root root    0 2008-12-18 00:03 web
jim@tiny:/mnt$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             30233928   3598380  25099736  13% /
tmpfs                   127324         0    127324   0% /lib/init/rw
varrun                  127324       344    126980   1% /var/run
varlock                 127324         0    127324   0% /var/lock
udev                    127324      2752    124572   3% /dev
tmpfs                   127324        20    127304   1% /dev/shm
lrm                     127324      2000    125324   2% /lib/modules/2.6.27-9-generic/volatile
/dev/sda2             20161204   1485900  17651164   8% /home
/dev/sda5             16126420    533280  14773828   4% /usr/local
/dev/sda6              9533248         8   9533240   1% /windows
/dev/sdb1              2004160    494880   1509280  25% /media/UBUNTU
//fredserver/web     149990396  48588684 101401712  33% /mnt/web
[/COLOR]


jim@tiny:/mnt$ 
jim@tiny:/mnt$ ls
[COLOR="Magenta"]web[/COLOR]
jim@tiny:/mnt$ cd web
jim@tiny:/mnt/web$ ls -al
[COLOR="Magenta"]total 3922
drwxrwxrwx 1 root root      0 2008-12-18 00:03 .
drwxr-xr-x 3 root root   4096 2008-12-18 00:17 ..
-rwxrwSrwx 1 root root 107247 2008-12-16 19:50 beret2.jpg
-rwxrwSrwx 1 root root 108325 2008-12-16 19:47 beret.jpg
-rwxrwSrwx 1 root root 128071 2008-12-16 19:59 bottle.jpg

[/COLOR]





Now a little groovy script:
[COLOR="Magenta"]jim@tiny:/mnt$ groovy -version
Groovy Version: 1.6-beta-2 JVM: 1.6.0_10
[/COLOR]
created a groovy script named 'smbio.groovy' with:
[COLOR="Red"]
// this logic works well in getSysProperties and does not need flush() or close() methods to do it
    def today = new Date()
    def home="/mnt/web"
    def thisName = home+'/fred3.txt'
    def outFile = new File(thisName)
    println "writing :"+outFile
    outFile.delete()
    outFile.write("title := Java System Properties"+"\n")
    outFile.append("author := Fred"+"\n")
    outFile.append("date := $today"+"\n")[/COLOR]

then cd into your groovy folder, if installed
[COLOR="Magenta"]
jim@tiny:~/groovy$ groovyc smbio.groovy
jim@tiny:~/groovy$ groovy smbio
writing :/mnt/web/fred3.txt[/COLOR]

[COLOR="Magenta"]cd /mnt/web
ls -al
jim@tiny:/mnt/web$ ls -al
total 3922
drwxrwxrwx 1 root root      0 2008-12-18 08:43 .
drwxr-xr-x 3 root root   4096 2008-12-18 00:17 ..
-rwxrwSrwx 1 root root 107247 2008-12-16 19:50 beret2.jpg
-rwxrwSrwx 1 root root 108325 2008-12-16 19:47 beret.jpg
-rwxrwSrwx 1 root root 128071 2008-12-16 19:59 bottle.jpg
-rwxrwSrwx 1 root root 104456 2008-12-16 19:56 boyincakeshop.jpg
-rwxrwSrwx 1 root root 119210 2008-12-16 19:34 bubbling.jpg
-rwxrwSrwx 1 root root 115757 2008-12-16 19:54 cake.jpg
-rwxrwSrwx 1 root root 117348 2008-12-16 20:00 dishes.jpg
-rwxrwSrwx 1 root root 104362 2008-12-14 13:47 eve2.jpg
-rwxrwSrwx 1 root root    319 2008-12-17 23:27 fred2.txt
-rwxrwSrwx 1 root root     84 2008-12-18 08:43 fred3.txt[/COLOR]

then examine fred3.txt and bingo - writing across a samba share from ubuntu to windows xp home/sp2

jim@tiny:/mnt/web$ cat fred3.txt
[COLOR="Red"]title := Java System Properties
author := Fred
date := Thu Dec 18 09:43:47 GMT 2008[/COLOR]

---

### Post by SeanHodges on 2008-12-18
Good stuff, well done.

Remember your mount will not be there after you reboot, so you either need to automate the mount task on system boot (probably using fstab), or call it at the beginning of your script:

```
Runtime rt = Runtime.getRuntime();
Process proc;
proc = rt.exec("gksudo umount /mnt/web");
proc = rt.exec("gksudo mount -t cifs -o rw,username=fred,workgroup=mshome //fredserver/web /mnt/web");
```

---

### Post by grire974 on 2011-07-28
I realize that this thread is getting a bit old in the tooth; however I presume this might be useful for others than the original poster...

One way to solve this is to use the java.awt.Desktop class.  It works on Mac OS X anyways.  If you open up your browser & type in smb://yourServerName/folderName, low and behold the folder opens in finder.  In OS X it works better in Safari, as it opens finder straight up; others such as fire fox may ask you what to open the link with (e.g. you have to choose finder from the list that pops up).  Also if you call Desktop.browse & Safari is your default browser, safari doesn't even open, it just goes straight to finder.  So if you can't count on safari being your default browser, you can always invoke it from the command line (using the java Process class).  Opening safari from the command line is also a good option if you're on OS X 10.5, and/or only have java 1.5 (the Desktop class doesn't exist in java 1.5).

This solution worked for me, as all I wanted to do was to open up a folder in windows explorer/ OS X finder that was on our company active directory drive...

Anyways; a quick code sample to top it all off...

```
URI uri = new URI("smb://yourServerName/YourFolderName");
Desktop dsk = Desktop.getDesktop();
dsk.browse(uri);
```

---

