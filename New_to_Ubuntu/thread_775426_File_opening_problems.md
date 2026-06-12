---
title: "File opening problems"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by mak_20789 on 2008-04-30
I searched on net for Linux commands and saved it on the desktop. Then I booted in Ubuntu and tried to open those files to try the commands, but here is message I got:
 chapter1.mht is an executable file. Do you want to "run in terminal"  or "display" or "run"?
First I chose display contents, which opened it in Firefox in source code.
Then run in terminal or may be run gave a file of plain text type and size 0 bytes with no name.
When I tried to open even a text file, it gives the same message.
I dont know if questions about the commands are answered here, but am asking as its a beginners forum. 

Regarding wubi, I just want to be sure so I am asking:
I have only one C:\ drive with Vista. From what I understand about wubi, I dont need to create a new partition but just choose the option "Install inside Windows", it will get installed on the same C:\ drive.
And the screenshots show the option of "Installation size" in GB and "desktop environment"
What options do I choose there?
And in future, if I want to reinstall Vista will Ubuntu get deleted?
Vista came preloaded and I dont have a CD but its stored on the hard disk itself. Will there be any problem because of this in installing ubuntu inside windows?


Can anyone please help?

---

### Post by Afif K fiska on 2008-04-30
> **mak_20789 said:**
> 
Regarding wubi, I just want to be sure so I am asking:
I have only one C:\ drive with Vista. From what I understand about wubi, I dont need to create a new partition but just choose the option "Install inside Windows", it will get installed on the same C:\ drive.
And the screenshots show the option of "Installation size" in GB and "desktop environment"
What options do I choose there?
And in future, if I want to reinstall Vista will Ubuntu get deleted?
Vista came preloaded and I dont have a CD but its stored on the hard disk itself. Will there be any problem because of this in installing ubuntu inside windows?


Can anyone please help?

I have a litle experience in installing ubuntu with wubi, u don't need partitioning anything with wubi, it will partitioned it self, and yes u're right, it will be the same partition with vista. Just try wubi first, its easy, and wouldn't damaging your vista installation. For the case if u reistall vista, i guess that ubuntu partition wouldn't get deleted. Cause it work in diferent file partition from vista, unless the partition is formated. If u want to reistall vista, just leave the file system, don't format it. Sorry for my bad english, hope this will help u

---

### Post by erginemr on 2008-04-30
Pretty much the same response; since Wubi creates a virtual file system in a big, big file in your Vista partition, you don't repartition your drive. In return, you will lose Ubuntu if you re-install Vista after formatting your hard drive.

"*.mht" files are containers that hold both the "*.html" source and other data on the page as pictures in a single file. They can be created and viewed with Internet Explorer, but not with Firefox (unless someone has developed an add-on lately to view them). 

I know that Opera supports "*.mht" out of the box, but I believe the best way would be to save the same file from Vista as "web page, complete", which will create a subfolder to put the images into. Then, you can view the saved page with Firefox by selecting "display" when you double click on it.

---

