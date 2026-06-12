---
title: "Still Need Help!"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by phoenixrising888 on 2008-04-23
****Still having trouble getting into my Synaptic Package Mangager.Keeps having the error E:dpkg was interrupted,you must manually run 'dpkg --configure -a' to correct the problem. I opened terminal and tried this many 
times but to no avail. I have tried the apt-get -f,apt-get install,apt-get upgrade but still shows the same error as above. Have tried every command I can think of that would help,but nothing. I can't even get updates.please help!

---

### Post by joselin on 2008-04-23
Try the following and paste the output:
```
sudo dpkg --configure -a
```

---

### Post by phoenixrising888 on 2008-04-23
joselin,

i already tried that

---

### Post by hermes0710 on 2008-04-23
Are you sure you use "sudo" before the command?

Please attach the output when entering the command:

```
sudo dpkg --configure -a
```

---

### Post by phoenixrising888 on 2008-04-23
yes i'm sure

---

### Post by joselin on 2008-04-23
> **phoenixrising888 said:**
> joselin,

i already tried that

Ok, paste the full output that let us see if there is a problem.

Regards

---

### Post by phoenixrising888 on 2008-04-23
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by joselin on 2008-04-23
Perhaps I'm wrong (because I don't use java), but seems that you must donwload one of the following files:      jdk-6-doc.zip jdk-6-doc-ja.zip from [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/) and then move it to /tmp directory, giving them root.root permisions.

Do the following:
```

wget [http://java.sun.com/javase/downloads/jdk-6-doc.zip]("http://java.sun.com/javase/downloads/")
wget [http://java.sun.com/javase/downloads/jdk-6-doc-ja.zip]("http://java.sun.com/javase/downloads/")
cp jdk* /tmp
sudo chmod root.root /tmp/jdk*

```

And then execute:
```
sudo dpkg --configure -a
```... yep, again.

Regards,

---

### Post by hermes0710 on 2008-04-23
Joselin I think you are right. I also think that you should use java :)

I am a little confused though... The problem was that you couldn't launch synaptic right??? Is this fixed now?

---

### Post by phoenixrising888 on 2008-04-23
wget [http://java.sun.com/javase/downloads/jdk-6-doc.zip](http://java.sun.com/javase/downloads/jdk-6-doc.zip)
--10:31:36--  [http://java.sun.com/javase/downloads/jdk-6-doc.zip](http://java.sun.com/javase/downloads/jdk-6-doc.zip)
           => `jdk-6-doc.zip'
Resolving java.sun.com... 72.5.124.55
Connecting to java.sun.com|72.5.124.55|:80... connected.
HTTP request sent, awaiting response... 404 Not found
10:31:36 ERROR 404: Not found.

---

### Post by hermes0710 on 2008-04-23
Go here and download it manually

[http://java.sun.com/javase/downloads/index.jsp]("http://java.sun.com/javase/downloads/index.jsp")
(Java SE 6 Documentation)

---

### Post by phoenixrising888 on 2008-04-23
ok hermes,

it says select directory for downloaded files.where should i put it?

---

### Post by joselin on 2008-04-23
> **phoenixrising888 said:**
> ok hermes,

it says select directory for downloaded files.where should i put it?

In $HOME (/home/your_username) for example.

The do the following:
```
cp $HOME/jdk* /tmp
sudo chmod root.root /tmp/jdk*
```

And [hermes0710]("http://ubuntuforums.org/member.php?u=558668"), I can promisse that never use it. Just read the messages ;)

---

### Post by phoenixrising888 on 2008-04-23
joselin,

do i type all that in the browse box?

---

### Post by joselin on 2008-04-23
> **phoenixrising888 said:**
> joselin,

do i type all that in the browse box?

No, no... just select home folder on the box. Other comands you must enter in a terminal window.

---

### Post by phoenixrising888 on 2008-04-23
im sorry joselin tryin to get used to this. i clicked browse and put it in my 
home. just click ok to download? then do terminal?

---

### Post by joselin on 2008-04-23
> **phoenixrising888 said:**
> im sorry joselin tryin to get used to this. i clicked browse and put it in my 
home. just click ok to download? then do terminal?

Then wait until the download finish and open Accesories / Terminal and type the following (one per line):
```
cp $HOME/jdk* /tmp
sudo chmod root.root /tmp/jdk*
```

---

### Post by phoenixrising888 on 2008-04-23
cp $HOME/jdk* /tmp
iansaylor@iansaylor-desktop:~$ sudo chmod root.root /tmp/jdk*
[sudo] password for iansaylor:
chmod: invalid mode: `root.root'
Try `chmod --help' for more information.

---

### Post by joselin on 2008-04-23
> **phoenixrising888 said:**
> cp $HOME/jdk* /tmp
iansaylor@iansaylor-desktop:~$ sudo chmod root.root /tmp/jdk*
[sudo] password for iansaylor:
chmod: invalid mode: `root.root'
Try `chmod --help' for more information.

Sorry, my mistake. Use this:
```

sudo chown root.root /tmp/jdk*

```

---

### Post by hermes0710 on 2008-04-23
I think you are already set. You don't have to change permissions. Try ```
sudo dpkg-reconfigure sun-java6-doc
```

---

### Post by phoenixrising888 on 2008-04-23
should i try the cp $HOME command and then the next one you just sent?

---

### Post by joselin on 2008-04-23
> **phoenixrising888 said:**
> should i try the cp $HOME command and then the next one you just sent?

You copied it before, so it's not necesary. Only the sudo chown command, and then the configure.

---

### Post by phoenixrising888 on 2008-04-23
sudo chown root.root /tmp/jdk*
iansaylor@iansaylor-desktop:~$ sudo dpkg-reconfigure sun-java6-doc
/usr/sbin/dpkg-reconfigure: sun-java6-doc is broken or not fully installed

---

### Post by joselin on 2008-04-23
> **phoenixrising888 said:**
> sudo chown root.root /tmp/jdk*
iansaylor@iansaylor-desktop:~$ sudo dpkg-reconfigure sun-java6-doc
/usr/sbin/dpkg-reconfigure: sun-java6-doc is broken or not fully installed

Use this command instead:
```

sudo dpkg --configure -a
```

---

### Post by phoenixrising888 on 2008-04-23
sudo dpkg --configure -a
Setting up sun-java6-doc (6-03-0ubuntu2) ...
/tmp/jdk-6-doc.zip has been unpacked and installed.
You can now delete it, if you wish.

i should be set now. i should be able to get back into my synaptic,right?

---

### Post by joselin on 2008-04-23
> **phoenixrising888 said:**
> sudo dpkg --configure -a
Setting up sun-java6-doc (6-03-0ubuntu2) ...
/tmp/jdk-6-doc.zip has been unpacked and installed.
You can now delete it, if you wish.

i should be set now. i should be able to get back into my synaptic,right?

Sure, you should be able to get back to synaptic. And now, if you want, you can delete files in /tmp, by using:
```
sudo rm /tmp/jdk*
```

---

### Post by phoenixrising888 on 2008-04-23
THANK YOU SO MUCH!!!i'm back in!THANK YOU!THANK YOU!lol!been tryin everything for days. concerning the /tmp is it necessary to delete? it wont mess anything up?

---

### Post by joselin on 2008-04-23
> **phoenixrising888 said:**
> THANK YOU SO MUCH!!!i'm back in!THANK YOU!THANK YOU!lol!been tryin everything for days. concerning the /tmp is it necessary to delete? it wont mess anything up?

No problem. And about delete the files, is not really necessary.

Have a nice day :-({|=

---

