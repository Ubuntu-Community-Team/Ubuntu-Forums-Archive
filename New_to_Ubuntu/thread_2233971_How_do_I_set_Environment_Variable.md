---
title: "How do I set Environment Variable"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by deme2 on 2014-07-11
I am very new in Ubuntu. I am little bit confuse. I read about setting in /etc/profile but I read in other places to Export. For instance: supposing I have Java 7 and Java 8 installed in my Ubuntu and for some reason I want to set JAVA_HOME 7 certain time and in other occasion to 8. How can I change as I would do in Windows? If I type echo $JAVA_HOME or printenv JAVA_HOME I can see the variable but I can't see if I type sudo gedit /etc/profile and look for in in the file.

---

### Post by ofnuts on 2014-07-11
Don't mess with /etc/profile which is a place to change the environment for all users. Instead edit your own .profile file (/home/your_id/.profile) which is the same file for the same purpose,  but for each user  (catch: since its name starts with a dot, it will not be shown by default (file explorers, "ls" command...) and you have to ask these to display hidden files).

The .profile only sets environment variable as long as it contains export statements for this... so it's just a convenient place to put export statements. .

Second catch: if you put an "export" statement in a script (for instance to set the JAVA_HOME in your current terminal session), it won't work.... because the shell will start a child shell to execute the script, and the export will apply only to the environment of that child shell (which is destroyed when the child shell ends). You have two ways to circumvent this:
[LIST=1]
[*]write a script that does the export and calls Java. Since Java is a child of the child shell, it inherits a copy of the environment where the JAVA_HOME has been set
[*]use the "." command to invoke the script. When you use ". some_script" (instead of just 'some_script"), the script is run by your current shell without starting a child shell so changes to your environment variables apply to the environment of the current shell.
[/LIST]

---

