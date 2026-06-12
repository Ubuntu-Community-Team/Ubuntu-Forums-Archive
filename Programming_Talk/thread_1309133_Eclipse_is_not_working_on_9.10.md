---
title: "Eclipse is not working on 9.10"
date: 2009-11-01
forum: Programming Talk
---

### Post by hoboy on 2009-11-01
I am terribly sorry if this mail is duplicated.

I have download eclipse from [www.eclipse.org](www.eclipse.org).
then installed it, but when I try to installed plugin it doesn't work.
Aad site.
name=I give some name
location:http:// plus the link of the plugin
when I click on ok nothing happen.
I have tried also to change the jdk when I click on OK for the final action nothing happen.

---

### Post by albandy on 2009-11-01
> **hoboy said:**
> I am terribly sorry if this mail is duplicated.

I have download eclipse from [www.eclipse.org](www.eclipse.org).
then installed it, but when I try to installed plugin it doesn't work.
Aad site.
name=I give some name
location:http:// plus the link of the plugin
when I click on ok nothing happen.
I have tried also to change the jdk when I click on OK for the final action nothing happen.

I'm having the same problem with webspere (an extended version of eclipse),  after clic press enter.

---

### Post by teachop on 2009-11-01
Yes.  I use avr32studio which is built from eclipse, and found the same thing.  Select the button with the mouse, then press enter...  Found an idea here that works:  [http://www.norio.be/blog/2009/10/problems-eclipse-buttons-ubuntu-910](http://www.norio.be/blog/2009/10/problems-eclipse-buttons-ubuntu-910)

For avr32studio case it turned out to be:

#!/bin/sh
export GDK_NATIVE_WINDOWS=1
/home/name/avr32studio/avr32studio

---

### Post by samlabs821 on 2009-11-01
I have found that in eclipse button  is not listening my mouse ... only keyboard, means button is pressed only when enter key is pressed... have any ideas or it is bug?

---

### Post by albandy on 2009-11-02
> **samlabs821 said:**
> I have found that in eclipse button  is not listening my mouse ... only keyboard, means button is pressed only when enter key is pressed... have any ideas or it is bug?

read the posts

---

### Post by mthalis on 2009-11-16
Thank you, Now eclipse work fine, below show how I did it
> 
#!/bin/sh
export GDK_NATIVE_WINDOWS=1
/home/dinesh/Documents/eclipse/eclipse


---

### Post by ubuwwyy on 2009-11-26
> **samlabs821 said:**
> I have found that in eclipse button  is not listening my mouse ... only keyboard, means button is pressed only when enter key is pressed... have any ideas or it is bug?

Hi&#65292;i have the same problem ,i installed this version:[Eclipse IDE for C/C++ Developers (79 MB)]("http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/galileo/SR1/eclipse-cpp-galileo-SR1-linux-gtk.tar.gz"), can you tell me the step in detail? Thanks.I am new in eclipse ,Thank you again

---

