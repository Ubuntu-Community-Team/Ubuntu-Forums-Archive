---
title: "Unable to locate package"
date: 2015-03-14
forum: New to Ubuntu
---

### Post by dhiraj2 on 2015-03-14
i just install ubuntu 13.04 in my laptop sucessfully. Now when i tried to install package using  sudo apt-get install apache2 , i am getting unable to locate package 

and i googled many time some say dong sudo apt-get update will solve the problem, i also tried to update but  i am getting 404 page not found in may sections. so could any body help me ............................

---

### Post by deadflowr on 2015-03-14
13.04 is a dead release and the repos are no longer accessible.
Your best option is to install either the 12.04 or 14.04 long-term-support release.
Or the current standard release 14.10.

I think the best option currently would be the 14.04 long-term support release.
12.04 is almost 3 years old now And 14.10 will be supported for a only a few months longer, now.

---

### Post by dhiraj2 on 2015-03-14
thanks mate,
 is there any solution to upgrade to new version like your said, or i think i have to reinstall the new os(newer version), is that right..

---

### Post by ansus on 2015-03-14
Software updates, under Updates tab, 'Notify me of a new Ubuntu version - Pull down menu - Long Term Support versions

---

### Post by deadflowr on 2015-03-14
Download a fresh copy and do a fresh install.

From memory I don't think they made it where you could upgrade from 13.04 to 14.04 straight.
Meaning first, because it is a dead release, you have to re-configure the repository information that you have.
Then upgrade to 13.10, which is also a dead release.
Then upgrade again to 14.04.

And being dead releases it is unclear what might happen.
And chances are it'll take longer than it should, since there is only one place that has the archived repositories for old-releases.

(A supported release grabs packages from what the system has determined is the fastest and closest repository mirror to you, 
but since there is only one old release archive, it is unclear how well the connection you would have to it might be) 

Simply put, I foresee nothing but headaches by going that route.

---

