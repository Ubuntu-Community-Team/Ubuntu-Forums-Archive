---
title: "How Do I Set Up and Offline Development Site?"
date: 2011-03-01
forum: Programming Talk
---

### Post by rcayea on 2011-03-01
Hi Everyone,

I'm not sure if this is what I am looking for is called, but I want to be able to take all my content from my website and do the smart, practical thing and edit my website offline and then just upload it all when finished. I have never done this sort-of, development-test-site thing so I was wondering, would I simply just download all my content into a folder and work from there? And, then, simply upload it back up or is there something else I have to do?

Thanks,
../Randy

---

### Post by japhyr on 2011-03-01
Do you have a website hosted right now?  If so, how did you create it?  If not, what kind of site are you looking to develop?

---

### Post by rcayea on 2011-03-01
Thanks for the reply.

Right now I have a website hosted by an online webhosting company. I use cpanel to access all my content through them.

---

### Post by johnl on 2011-03-01
The simplest answer is yes, you can just download all the files, make the changes, and upload the files that you changed.  This is not particularly efficient and it could be dangerous -- imagine that you make changes through your cpanel one day (or from your laptop), and forget to sync your local copy on your desktop.  Then the next day you make some changes to the desktop copy and overwrite the same file.  Now you've lost your previous change.  

The advanced answer depends on a lot of things:  does your hosting provider allow ssh access to your hosted files?  if so,  you can use rsync over ssh to upload your changes and sync your local copy.  Does your website include PHP/perl/etc or require a database, or is it static html/css/etc?  If it's static, you can preview your changes on your local machine easily; otherwise, you might need to set up a webserver to test your changes before uploading.

Hope this helps.

---

### Post by japhyr on 2011-03-01
I have only played with this a little bit, so someone with more experience will come along and clarify this.  But to get you started, you need to install a server.  You can install apache through synaptic.  Then you copy your website's directory to the proper folder on your local system, and you will be able to develop locally.  Hopefully your original site is hosted on a linux server, that will make things easier.  I believe most hosting is done on linux servers.

---

### Post by rcayea on 2011-03-01
Thanks for the info.

@johnl - I use webhostingpad.com as my hosting. They have all the tools you mentioned and allow uploading and such. 

@japhr - they are linux based. A great company I must say. 


Maybe someone can point me to a HOWTO for this. 

Thanks!

---

