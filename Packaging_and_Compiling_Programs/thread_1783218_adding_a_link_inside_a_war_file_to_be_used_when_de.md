---
title: "adding a link inside a war file to be used when deployed"
date: 2011-06-15
forum: Packaging and Compiling Programs
---

### Post by jtrulen on 2011-06-15
Good afternoon everyone,

I am having a slight bit of trouble when attempting to deploy a war file to jBoss. More specifically, the problem occurs after the war has been deployed. I am using a reporting tool called BIRT, and taking the supplied war file from their website (which works quite well by itself), deploy it on one of our servers. All fine so far. 

Now, in order to access the reports we have created for the application, I need to supply a link to a separate directory located on the same machine as the war file.

From what I can tell, jBoss is a hot-swap environment that does not deploy war files into directories, but instead processes the data from within the war files. So adding a link to the deployed directory is not a viable option either.

If anyone can shed some light on this problem, I would be very appreciative.

Thank you,
Jordan Trulen

---

