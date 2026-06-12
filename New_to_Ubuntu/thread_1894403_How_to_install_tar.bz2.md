---
title: "How to install tar.bz2"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by rjwinters on 2011-12-12
[SIZE="1"][/SIZE]
Hello All

I have downloaded this GTK2-EasyListening.tar.bz2

I would like to know how to install it from "GNOME". I am new to Ubuntu 11.10 but not to running windows7.
I am real impressed with Ubuntu 11.10.I have Ubuntu running in VM-VirtualBox.If i have to download a installer i will do.

Thanks for your help.:popcorn:

---

### Post by Lars Noodén on 2011-12-12
The usual way is to make a new directory and then uncompress the file inside that directory.

```

mkdir /tmp/foo
cd /tmp/foo
tar jxf GTK2-EasyListening.tar.bz2

```

Then look for a file named either README or INSTALL.  That should contain the instructions for installation.  

Before you do any of that, you might want to double check the Ubuntu repository to see if the file is available there first.  That's much easier.

---

### Post by rjwinters on 2011-12-12
> **Lars Noodén said:**
> The usual way is to make a new directory and then uncompress the file inside that directory.

```

mkdir /tmp/foo
cd /tmp/foo
tar jxf GTK2-EasyListening.tar.bz2

```

Then look for a file named either README or INSTALL.  That should contain the instructions for installation.  

Before you do any of that, you might want to double check the Ubuntu repository to see if the file is available there first.  That's much easier.

Hello
On your suggestion i put the [code] in and did not work.When i downloaded the file i put the file on desktop so i can find it.

Thanks
 Bob:confused:

---

### Post by Lars Noodén on 2011-12-12
You have to be in the same directory as the tarball for the command to work.  If it is the Desktop, then you need something like this first:

```

cd ~rjwinters/Desktop/

```

---

### Post by Lars Noodén on 2011-12-12
Alternately, you could double click on the file in Nautilus and extract the files that way.

---

### Post by rjwinters on 2011-12-12
Hello 
This is what i have now.
When i had Ubuntu years ago,when i downloaded from Gnome it would install the files automatically.
I am sorry if i am not understanding you! I have the file on desktop has a zip i think!

Thanks

Bob

---

### Post by nothingspecial on 2011-12-12
Double click the tar thingy on your desktop then click extract.

---

### Post by Lars Noodén on 2011-12-12
Try double clicking on the icon in the Desktop

OR

Try the following in the terminal.

```

mkdir /tmp/foo
cd /tmp/foo
tar jxf ~/Desktop/GTK2-EasyListening.tar.bz2

```

---

### Post by rjwinters on 2011-12-12
Well i guess i don't know what i am doing!!It is nice to here your remark so i can get help i what i am doing!!:popcorn:

---

### Post by nothingspecial on 2011-12-12
> **rjwinters said:**
> Well i guess i don't know what i am doing!!It is nice to here your remark so i can get help i what i am doing!!:popcorn:

That is not directed at you :D

It says that at the bottom of all my posts, it is a signature :)

---

### Post by rjwinters on 2011-12-12
> **Lars Noodén said:**
> Try double clicking on the icon in the Desktop

OR

Try the following in the terminal.

```

mkdir /tmp/foo
cd /tmp/foo
tar jxf ~/Desktop/GTK2-EasyListening.tar.bz2

```

Hello Lars Nooden

Thanks for your help.

Bob

---

### Post by rjwinters on 2011-12-12
Hey I am sorry i am new to this!!I should have known that.:KS

---

### Post by rjwinters on 2011-12-12
Hello

This is what i have when i double click it!

---

### Post by nothingspecial on 2011-12-12
Click extract

---

### Post by rjwinters on 2011-12-12
> **nothingspecial said:**
> Click extract

Hello Thanks for your help:)

This is what i have when i extract the file.

---

### Post by rjwinters on 2011-12-12
Hello

This is what i am trying to do with gnome files!Put them on Ubuntu 11.10

---

### Post by gandaran on 2011-12-12
> **rjwinters said:**
> Hello

This is what i am trying to do with gnome files!Put them on Ubuntu 11.10
gnome2 themes styles don't work on ubuntu 11.10, look for gnome3 (GTK3) themes in [gnome look]("http://gnome-look.org/")

---

### Post by rjwinters on 2011-12-12
Thanks so much!!

---

