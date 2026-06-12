---
title: "Java JAR file and cron job problem"
date: 2012-10-26
forum: Packaging and Compiling Programs
---

### Post by jefe9 on 2012-10-26
I have a JAR file that runs fine when invoked from the terminal command line.
 
But, when I place this as an entry in crontab, the program runs and fails on an 'Invalid authorisation' issue. This is because a properties file is not found, or has incorrect information.
 
How can I ensure that the properties file is found when invoked by crontab?
 
I have tried creating a .sh file:
 
cd /working directory            # which contains the properties text file
java -jar path_to_JAR_file
 
and then I put the crontab entry to invoke the .sh file which should start the java JAR program from the correct directory. But I have hit a "not an executable file' error message here, even after i did a chmod 777 my_sh_file.sh
 
I am stumped. 
Any advice appreciated.
 
Jefe

---

### Post by lykeion on 2012-10-27
Have you tried using an absolute path to your jar file in the .sh file?

---

