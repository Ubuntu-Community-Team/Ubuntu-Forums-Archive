---
title: "Subversion - Project Copied from Windows"
date: 2010-01-25
forum: Programming Talk
---

### Post by sdemills on 2010-01-25
I copied a project from Eclipse running under Windows 7 to Eclipse running under Ubuntu to prove it would work without modification under Ubuntu despite having reasonably complex graphics and being driven by a MySQL database. All worked fine.

Now I would like to check it in to a Subversion repository under Ubuntu through Subclipse. However Subclipse/Eclipse (not quite sure which) can still see the SVN repository references on the files that was used on Windows 7 and insists on trying to "share" the project back to that repository.

Does anyone know how I can ZAP that information so that I can treat it like a new project and "share" it into the Ubuntu SVN repository on my machine?

Thanks and Kind Regards
Steve

---

### Post by myrtle1908 on 2010-01-25
I assume you pasted the project into your eclipse workspace and went from there.  It will work but you need to change some settings files etc.  Too much effort.  Instead, when I need to move a project from one place to another I tend to create a new project, then share with the repository and get the source.  Much less pain this way.

---

### Post by sdemills on 2010-01-26
Thanks for the reply. Here's how I went about it...

I copied the folder on Windows 7 to a network drive, then on Ubuntu copied the network folder to a local folder.

In the Eclipse workspace I create a new project. Then I imported the local folder asking Eclipse to create the required set of folders. Then I did a project Refresh and Rebuild - I changed something then changed it back again to ensure that something got built.

Later when I tried to use Subclipse, it reported that it was already sync'd with a repository and named the Windows 7 repository as that repo.

I would have thought that it would be commonplace to copy something taken from one project in one repository and make a new project in a different repository. For example: I might want to share something that I developed locally with a group out on the internet so taking it from my local repository and sharing it out on a global repository.

How would that be done I wonder?

Kind Regards
Steve

---

### Post by sdemills on 2010-01-27
I have managed to resolve this now. For those that follow and who would like to know how...

I went to the project folder in the Eclipse workspace and renamed the .svn folder to some other name.

Then when I attempted to share the project, Subclipse reported that there appeared to be an incomplete set of SVN control files and offered to erase them all and recreate them for me.

Regards
Steve

---

