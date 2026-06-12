---
title: "How to set a file as executable"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by ruslan kim on 2012-11-26
Hey guys,

I have a TrueImageServer9.1_s_en.i686 file and I need to set it as an executable file.

I guess it is pretty simple. How do I do that?

Thanks for any help!

---

### Post by dniMretsaM on 2012-11-26
Right click on the file, go to the permissions tab and check the executable box. Or run this in the command line:
```
chmod +x /path/to/executable
```

---

### Post by ruslan kim on 2012-11-26
Thanks, but it is still not running. How to run the file? 
Maybe I am just not doing it properly...

---

### Post by HeroOfCanton on 2012-11-27
According to their own help section that should work.
[URL="http://kb.acronis.com/content/1535"]
Link[/URL]

Maybe you need to sudo when trying to execute? Their help file says root, but that shouldn't be necessary in Ubuntu.

---

### Post by ruslan kim on 2012-11-27
Well, the main problem is this - I am very new to Linux =)

Can you explain step-by-step, please, how to:
Open terminal (console)
Log in as "root"
Make the installation file executable: # chmod +x file_name.i686
Run the binary: # ./file_name.i686

Thanks.

---

### Post by lisati on 2012-11-27
With Ubuntu, logging in as "root" is usually discouraged. If you need the "superuser" privileges usually associated with being "root", the preferred method is via the "sudo" command. For more information, please see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ruslan kim on 2012-11-27
Well, the main problem is this - I am very new to Linux =)

Can you explain step-by-step, please, how to:
Open terminal (console)
Log in as "root"
Make the installation file executable: # chmod +x file_name.i686
Run the binary: # ./file_name.i686

Thanks.

---

### Post by pkadeel on 2012-11-27
> **ruslan kim said:**
> Well, the main problem is this - I am very new to Linux =)

Can you explain step-by-step, please, how to:
Open terminal (console)
Log in as "root"
Make the installation file executable: # chmod +x file_name.i686
Run the binary: # ./file_name.i686

Thanks.
You yourself solved your problem

Open terminal: Ctrl + Alt + T (default shortcut on ubuntu unity if you have not changed it yet)
Login as root and make a file executable:~$ sudo chmod +x filename.whatever
Run the file :~$ ./filename.whatever (from the folder where it is located)

---

### Post by newb85 on 2012-11-27
If you need to run the file as root, that last line would be
```
sudo ./file_name.i686
```

---

