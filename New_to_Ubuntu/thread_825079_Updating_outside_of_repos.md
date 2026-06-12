---
title: "Updating outside of repos"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by tadcan on 2008-06-10
Ok, I hope this will make sense.

I installed celtx awhile back and kept it in the home folder. (Its for writing film scripts)

I downloaded the new version and unpacked it with archive manager and it went to the desktop. I could launch Celtx from applications and the new one was launched. (I had pointed it to the previous version) So I deleted the folder on the desktop. When I launched again, I had lost the project. 

I can rebuild it, but if someone can explain how to retrieve that would be useful. 

So even though I had two celtx folders, it still updated the previous one, why? 

Can someone explain to me how I should update if the software is not in the repos.   

Am just getting a headache trying to understand how this works in linux.

---

### Post by Paqman on 2008-06-10
> **tadcan said:**
> 
Am just getting a headache trying to understand how this works in linux.

I've just taken a quick look at the app you've mentioned, and it looks like it comes as a tarball. What's inside, a script that you use to install?

In the case of an app installed with a custom script, it's really up to whoever wrote the script to decide how it behaves. Any packages installed using the package manager (ie: stuff from the repos or .debs) will behave very consistently, but once you stray into the wilds it's a bit fuzzy.

---

### Post by tadcan on 2008-06-10
Yes its a tar.gz

I have unpacked it with the terminal and done some with archive manager. 

I have included a screen shot of inside the folder. I would have expected to see a project folder. When I do a 'save as' I see it in master tadcan folder (folder with house symbol) and it has a cardboard box like shape beside it. (Don't what type of file the box refers to)

I am used to windows giving me a dialog box saying the software is installed. Archive manager just does stuff really fast and I'm never sure what I've done.

Had a quick look at the celtx forum and someone else mentioned losing their project, but not what OS they are using. No one has responded, that forum is not very technical.

---

### Post by tadcan on 2008-06-13
I want to uninstall and reinstall celtx because I think I messed it up.

I went to add/remove programs, but it wasn't there. I presume because its not in the repo's.

Do I use the much warned about rm to remove it?

And if so what is the correct code to use?

---

### Post by tadcan on 2008-06-13
Deleted the folder and reinstalled. Worked fine. But would still like to know if there is a better way.

---

