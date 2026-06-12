---
title: "[SOLVED] bash: '/home/william/bin/Backup.py' permission denied"
date: 2008-03-16
forum: Programming Talk
---

### Post by Wylkar on 2008-03-16
I cannot execute a file that I put into my bin folder it will say "bash: '/home/william/bin/Backup.py' permission denied" and if I try as root it says that it cannot find the file. I have several files of the same type in the directory and some of them will work and some of them will come up with the same message as the one I just described.

---

### Post by ryanhaigh on 2008-03-16
The files may not be executable, to change this:
```

chmod +x /home/william/bin/Backup.py

```
OR for all files in that directory
```

chmod +x /home/william/bin/*

```
You can also do it in the GUI by right clicking on the file, going into Properties>Permissions and allow executing file as a program.

---

### Post by Wylkar on 2008-03-16
Thanks that worked.

---

### Post by Wylkar on 2008-03-16
ok it will execute it but when I try it comes up with the syntax error:
 william@william-desktop:~$ Backup.py
/home/william/bin/Backup.py: line 6: syntax error near unexpected token `('
/home/william/bin/Backup.py: line 6: `q = raw_input('Please enter the path to the file or folder you would like to backup:')'
this only happens when I try and run it as an executable.

---

### Post by slavik on 2008-03-16
is the first line of your py file something like the following?
```
#!/usr/bin/python
```

---

### Post by ghostdog74 on 2008-03-16
show how your backup.py looks like

---

### Post by Wylkar on 2008-03-16
I had forgotten to put '#!/usr/bin/python' in the front of the program. Thank you  slavik for reminding me.

---

