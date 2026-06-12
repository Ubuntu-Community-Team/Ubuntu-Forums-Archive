---
title: "Debian installer"
date: 2009-06-15
forum: Programming Talk
---

### Post by roshanjose on 2009-06-15
we have locally created an OS call eswecha based on debian for engineering students in our state

 i'll give a much clearer idea...there are several streams in engineering..like CS, Mechanical, Electrical, Biotechnology etc... each stream has different softwares provided in debian....now we are creating a metapackage for each stream which installs all these packages....while installing debian...they get an option asking them to select a particular stream...for this i have to build the UI



do you remember..if you install debian, you get an option to choose Desktop systems, Web Server, Laptop, etc.....we have to buid the same UI

Yes, just after we select these options another dialog box has to appear which asks the user to which stream he belongs....(he can select more than once stream). So after he selects the stream and accept it...th metapackage is installed which installs the packages

while creating packages...there was dependency problems which i had cleared by using a command called "full resolver" or something.....so maybe if the user selects the option it has to call a script which includes installing the metapackage and then resolving the dependency   or   i should provide a list of packages instead of a metapackage.....


someone suggested me about tasksel....but i dont have much info upon this and i need to create the UI....

can anyone help me in this issue

---

### Post by bodhi.zazen on 2009-06-16
Are you working on Debian or Ubuntu ?

Since I can not make heads or tails of your post or what you need, see if these pages help:

[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

[http://manpages.ubuntu.com/manpages/karmic/en/man8/tasksel.8.html](http://manpages.ubuntu.com/manpages/karmic/en/man8/tasksel.8.html)

If you are looking to automate, I would write a few simple scripts or a custom spin.

apt-get install foo ...

---

### Post by roshanjose on 2009-06-16
i am working on debian...

---

### Post by roshanjose on 2009-06-16
I kind of found out that we can create additional tasks in tasksel..

But i dont know how to do it...Just found some manuals upon it but never understood it..

Can you help me regarding this

---

### Post by roshanjose on 2009-06-16
one more thing is that the changes are to be made on debian installer image...

i have the debian iso.... what do i need to do with this and where do i need to make the changes....

---

### Post by roshanjose on 2009-06-16
here's one manual that i received...

[http://www.dit.gov.bt/admin/index.php/D-i#Customization_of_packages_included_on_CDs_and_installed_by_the_installer](http://www.dit.gov.bt/admin/index.php/D-i#Customization_of_packages_included_on_CDs_and_installed_by_the_installer)


i didnt understand the customizing tasksel section in this manual...

If possible can you explain me and clear some of my doubts

---

