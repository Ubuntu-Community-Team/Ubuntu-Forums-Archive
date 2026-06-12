---
title: "Why can't I choose a custom application to open files with?"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by venom104 on 2011-10-21
I'm trying to open a simple shell script I wrote to open a program, and I'm trying to set the script to open using bash. I go to do this by clicking the shell script and clicking "properties" then "open with" and it won't let me select a custom application or bash! 

All I can do is select from a list of application? Why oh why would they remove this functionality out of Ubuntu? Is there anyway of getting my script to run by just clicking on it now? Is there a way I can choose to run programs with custom applications anymore?

I almost forgot to say that I'm using Ubuntu 11.10. I just upgraded so if this is something minor and stupid, I apologize for wasting time.

---

### Post by Carborundum on 2011-10-21
In order to run your script in bash, you need to mark it as executable. This is not new in 11.10.

To do this, navigate into the directory where you put the file and run this command:
```
chmod 755 filename
```

---

### Post by MG&amp;TL on 2011-10-21
And make sure it has  the thing at the top:

```
#!/bin/bash
<code here>
```

---

### Post by venom104 on 2011-10-21
> **Carborundum said:**
> In order to run your script in bash, you need to mark it as executable. This is not new in 11.10.

To do this, navigate into the directory where you put the file and run this command:
```
chmod 755 filename
```

I did make the script executable, I changed it's properties under the "permissions dialog box". That isn't the problem, my problem is getting it to run under bash. I used this program called mimetype to associate bash with .sh files, and that seemed to work...but I can't help but shake the feeling of why I wouldn't be able to select a custom app by default when I'm opening a file, when all the other versions of Ubuntu allow this. 

So to be clear, I solved my little problem with MIMEtype. Now the question is, in the future how would I add programs to that list under "open with" or hack it so it lets me select my own application?

---

### Post by Carborundum on 2011-10-21
> **venom104 said:**
> I did make the script executable, I changed it's properties under the "permissions dialog box". That isn't the problem, my problem is getting it to run under bash. I used this program called mimetype to associate bash with .sh files, and that seemed to work...but I can't help but shake the feeling of why I wouldn't be able to select a custom app by default when I'm opening a file, when all the other versions of Ubuntu allow this. 

So to be clear, I solved my little problem with MIMEtype. Now the question is, in the future how would I add programs to that list under "open with" or hack it so it lets me select my own application?

Executables are automatically run by the system's default shell; in Ubuntu this is dash. If you want it to run in bash instead, all you need to do is add the shebang MG&TL mentioned at the beginning of the script. There is no need to do anything else.

---

### Post by mc4man on 2011-10-21
In regards to the missing "use a custom command", which seemed to be your secondary question here ?

If so - 
if the past, when doing that it created a userapp-XXX-XXXXXX.desktop in ~/.local/share/applications &  added that .desktop to a line in ~/.local/share/applications/mimeapps.list

So now one way as a user is to 'go the other way', create the .desktop yourself and add it to appropriate line(s) in mimeapps.list

In that .desktop you can if desired add a MimeType= line & other lines if needed.per the particular case.

---

