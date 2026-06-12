---
title: "Java's .jar permission bit"
date: 2010-07-19
forum: Programming Talk
---

### Post by kahumba on 2010-07-19
Hi,
until recently one could run "java -jar file.jar" to run a Java app, now one first has to make the jar file executable.
To me as a Linux user and Java dev it's a waste of time - a broken excuse about security on the desktop because it's not the same issue as with executable shell files because you can't run a Java app directly like "./file.jar", but you have to write "java -jar file.jar", thus you make yourself clear that you do mean to run it, hence to me the additional need for the "permission bit" is just more waste of time for the user/dev along with more irritations and bureaucracy.

Question primarily to Java devs, do you like this new "innovation/security" with the permission bit? Why?

---

### Post by patrickaupperle on 2010-07-19
> **kahumba said:**
> Hi,
until recently one could run "java -jar file.jar" to run a Java app, now one first has to make the jar file executable.
To me as a Linux user and Java dev it's a waste of time - a broken excuse about security on the desktop because it's not the same issue as with executable shell files because you can't run a Java app directly like "./file.jar", but you have to write "java -jar file.jar", thus you make yourself clear that you do mean to run it, hence to me the additional need for the "permission bit" is just more waste of time for the user/dev along with more irritations and bureaucracy.

Question primarily to Java devs, do you like this new "innovation/security" with the permission bit? Why?

If I had to guess as to the reason for the forcing you to make it executable, I would guess that it is for people who would double click on it.

---

### Post by Sanjeevtrip on 2010-07-19
I think you need to know about MANIFEST.MF file

check this 
[http://www.ibm.com/developerworks/java/library/j-5things6.html](http://www.ibm.com/developerworks/java/library/j-5things6.html)

---

### Post by kahumba on 2010-07-20
> **Sanjeevtrip said:**
> I think you need to know about MANIFEST.MF file

check this 
[http://www.ibm.com/developerworks/java/library/j-5things6.html](http://www.ibm.com/developerworks/java/library/j-5things6.html)

If you're referring to "1. JARs are executable" from that article - they mean a different thing: allowing people to double click a jar to run it, nothing to do with setting the file's executable bit, for instance of window$ you don't have to set a jar executable to run it at double click.

I could believe in [patrickaupperle]("http://ubuntuforums.org/member.php?u=282156")'s double-click concern about people who have no clue what they're doing but even that is far fetched since Java on Linux by default doesn't associate itself as the default handler of .jar files (the archive manager is) so the user has to do it manually or choose Java explicitly.

---

### Post by SasiPrabha on 2011-01-25
I also tried chmod but it was nt successful, even nautilus didnt work when I was in the same directory.......:confused:

BUT......:KS\\:D/

This is an easy graphical method to solve the problem,
first in terminal run,

user@user-pc:/$ sudo nautilus

then in nautilus window go to the *.jar file
R-Click and chose copy-to -> Home folder
on the left side of your window you will see the root home folder
in there you will find the jar file
R-Click -> properties
in the permissions tab tick "allow executing file as program" check box
:popcorn:

---

