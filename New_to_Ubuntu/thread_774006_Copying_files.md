---
title: "Copying files"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by timswait on 2008-04-29
I'm trying to install ImageJ (This: [http://http://rsb.info.nih.gov/ij/docs/install/linux.html]("http://http://rsb.info.nih.gov/ij/docs/install/linux.html")).
Where should I save the directory to? I was going to put it in the /usr folder, is that OK?
The problem I'm having is that I can't drag and drop the folder to copy it, I don't have access. When I had version 7.10 I typed the following code into terminal: ```
sudo apt-get install nautilus-gksu
```
and it put an "open as administrator" option when I right click a folder which let me copy files. However since upgrading to 8.04 the "Open as Administrator" option has gone and typing that code into terminal doesn't bring it back. Please help.

---

### Post by hackle577 on 2008-04-29
You probably want to save the program in the /opt directory.

To install it there you will need to use the "sudo" command. For example, if you saved ImageJ to your desktop, then:

```
sudo mv ~/Desktop/ImageJ /opt/
```

would do it

---

### Post by em3raldxiii on 2008-04-29
I am not familiar with nautilus-gksu, but I think I can help a little;

If you open a terminal and enter this:

```
gksu nautilus
```it will open a nautilus window with privelages.  *THIS CAN BE DANGEROUS* ... don't do this any more than you absolutely must do.  It's not exactly a "secure" habit.

Anyway, with that you can now copy/paste at will.

Alternatively (and a safer option) is that you can use the terminal to copy and paste the directory:

```
sudo mv ~/myfolder/myfile /opt/mynewlocation/formyfolderorfile
```And then you can change the privelages of that file or folder so that it has stuff like excecutable and/or read/write.

But all of this may not be necessary ... why not just put the stuff you need into your ~/home directory?

---

