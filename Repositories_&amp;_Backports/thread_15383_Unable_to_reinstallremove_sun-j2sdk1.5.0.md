---
title: "Unable to reinstall/remove sun-j2sdk1.5.0"
date: 2005-02-14
forum: Repositories &amp; Backports
---

### Post by nanaban on 2005-02-14
I followed the instructures [here](http://www.ubuntulinux.org/wiki/Java15) to install java-ubuntu and sun-j2sdk1.5.0, but installation of j2sdk gave me an error.

I decided to remove everything but apt-get won't let me remove j2sdk.

> Reading Package Lists... Done
Building Dependency Tree... Done
The following packages will be REMOVED:
  sun-j2sdk1.5.0
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 140MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 87693 files and directories currently installed.)
Removing sun-j2sdk1.5.0 ...
rm: cannot remove `/usr/bin/idlj': No such file or directory
dpkg: error processing sun-j2sdk1.5.0 (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 sun-j2sdk1.5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have also tried the following:
[list=1]
[*]reinstall
[*]remove
[*]remove completely
[*]clean the cache
[/list] 

Any suggestion on what to do?

---

### Post by scoon on 2005-02-14
[QUOTE=nanaban]I followed the instructures [here](http://www.ubuntulinux.org/wiki/Java15) to install java-ubuntu and sun-j2sdk1.5.0, but installation of j2sdk gave me an error.

I decided to remove everything but apt-get won't let me remove j2sdk.



I have also tried the following:
[list=1]
[*]reinstall
[*]remove
[*]remove completely
[*]clean the cache
[/list] 

Any suggestion on what to do?[/QUOTE]


Hey there, 

What was the error that you got when you tried to install it the first time ?

scoon

---

### Post by piedamaro on 2005-02-14
If that file is missing accidentaly, you can fix it like this:
sudo touch /usr/bin/idlj

then apt should be happy.

---

### Post by nanaban on 2005-02-14
[QUOTE=piedamaro]If that file is missing accidentaly, you can fix it like this:
sudo touch /usr/bin/idlj

then apt should be happy.[/QUOTE]

I tried that, but it recursively bragged for idlj, apt, jar, idlj, apt .....

---

### Post by nanaban on 2005-02-14
solved! Had to remove a mozilla plugin and reinstall.
Thanks.

---

### Post by flashdog on 2005-02-26
Hello,
I have same problem. I try 
```
  sudo touch /usr/bin/idlj /usr/bin/apt /usr/bin/jar /usr/bin/jdb /usr/bin/jps /usr/bin/serialver /usr/bin/java /usr/bin/jmap /usr/bin/ktab /usr/bin/orbd /usr/bin/rmic /usr/bin/rmid /usr/bin/native2ascii /usr/bin/extcheck /usr/bin/keytool /usr/bin/javac /usr/bin/javah /usr/bin/javap /usr/bin/jinfo /usr/bin/jstat /usr/bin/kinit /usr/bin/klist /usr/bin/unpack200 /usr/bin/appletviewer /usr/bin/java-rmi.cgi /usr/bin/ControlPanel /usr/bin/jstack /usr/bin/jstatd /usr/bin/tnameserv /usr/bin/servertool /usr/bin/jarsigner /usr/bin/pack200 /usr/bin/HtmlConverter /usr/bin/jsadebugd /usr/bin/javadoc /usr/bin/rmiregistry /usr/bin/policytool /usr/bin/jconsole /usr/bin/jconsole

``` 

but, 
```

 dpkg -r sun-j2sdk1.5.0 (Reading database ... 66088 files and directories currently installed.) Removing sun-j2sdk1.5.0 ... rm: cannot remove `/usr/bin/jconsole': No such file or directory dpkg: error processing sun-j2sdk1.5.0 (--remove):  subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 sun-j2sdk1.5.0


``` 

Can anyone help me?

---

### Post by flashdog on 2005-02-26
I find solve:
dpkg -i --force-all /var/cache/apt/sun-j2sdk1.5.0_01-1_i386.deb

For Firefox:
ln -s /usr/lib/sun-j2sdk1.5.0/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins

---

