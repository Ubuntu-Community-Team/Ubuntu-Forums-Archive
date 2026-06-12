---
title: "how do change permissions on folders with padlock and X icons"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by hanzj on 2012-05-08
Hi, everyone. 
I'm in a folder containing subfolders with the Padlock icon and an X icon on them. I can't copy these folders or compress them. 

What must I do?

Thank you.

---

### Post by westie457 on 2012-05-08
Hi **leave them be**.

Those are system files and folders protected by the system. Moving, compressing or doing pretty much anything to them can and probably will hose your system.

---

### Post by hanzj on 2012-05-08
but these are wordpress files i was working on. and now i need to compress them to upload them to our website.

---

### Post by westie457 on 2012-05-08
Understand my caution about your first question. Now we know they are not system files but Wordpress files you need to use the chown command ```
man chown
``` or ```
chown --help
``` for more info.

Have never used it myself so cannot offer further advice.

---

### Post by plant on 2012-05-08
ok, take terminal and enter as root. cd to the folder where you have the wordpress files and change permissions for this file. Use the following command

chmod a=rw <filename>

To enter as root type: sudo su
and enter your password

---

### Post by hanzj on 2012-05-08
how do change permission for a  folder and all its contents?

---

### Post by lifeluvr on 2012-05-08
From the sound of it. You either protected the folder too well or you created active dependencies. Right click folder go to properties>permissions but, you probably already did that.
    Have you tried downloading 'samba'? This is really useful for changing the share properties on a lot of files.
    There is also the 'chmod' command. Which will also change properties of a folder. I'll let you look that up because, you will get a better answer better suited to your needs. Maybe just go and download your pages to get them back? Gotta love the cloud. 

                                Peace

---

### Post by sadaruwan12 on 2012-05-08
I'll tell you a easy way but use it at your own risk. Run the below command and get root access to the nautilus.

```
$ gksudo nautilus
```

Now brows to your home folder or to the drive you have your file right click on the folder goto the permissions tab and set the permission to your user name and group thats it.

to set file permissions you can use the terminal command that plant told you or can use my method.

---

### Post by plant on 2012-05-08
Inorder to change permission of a folder and all the contents it it 
use:

chmod -R a=rwx <folder_name>

This command will give permission to all users to read and write your document.
You can check the documentation for chmod to see what all possibilities are there with chmod.

---

### Post by hanzj on 2012-05-08
Thanks, plant.

I added "sudo" to your command to make it work.

---

### Post by Morbius1 on 2012-05-08
> chmod -R a=rwx <folder_name>The only problem with that command is that it will not only make every directory and subdirectory executable ( which it must be ) but also every file ( which you probably don't want to do ).
You might consider making just one change to that command for future use:
```
chmod -R a=rwX  <folder_name>
```That's a big X not a little x. Every folder will be rwx and that's what you want. Every file will be rw- unless the file had already been made executable in the past in which case it will be rwx.

---

