---
title: "subversion and apache"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by moose4204l on 2008-11-11
Ok, my question is a bit tricky i think. 

I have a server that is running apache and subversion server as well as others. Anyways, i write files in php and even basic html. I then commit them to my repository from my working laptop to my server laptop. I want to be able to test the html file in the web browser on my laptop i am working on. is there a way to link the svn file to a visible html file. I know i can look at files by [http://myserver/svn](http://myserver/svn) but thats the repository not the html/apache website thing. 

so...

i already would be sshed in to server laptop and ..
basically is what envision in my head is a script, that i could make if given the steps how to, to commit my work to svn, run a script to link/whatever it is on the server laptop, then browse to my public htmls on my working laptop.

or would i have to copy and paste them into the public_html folder which then would defeat the svn committing


if you could understand what i am talkin about, THANKS

---

### Post by pdwerryhouse on 2008-11-11
Why not just check them out of the SVN repository into the location on your laptop where you want to test them?

eg:
```
cd /var/www/location/
svn co http://blahblah/path/to/repo

```

---

### Post by moose4204l on 2008-11-11
I dont think you follow. The svn and apache server are both on the server laptop. I work with files on my workspace laptop then i commit them to the server laptop. So when i test them i have to move them over to the public_html folder on the server laptop and then on my local laptop I would go to [www.serverDomainName.com/public_htmlFolder](www.serverDomainName.com/public_htmlFolder) and see if they worked. As of now I have a short script that just scp's all the files over to the public_html folder so I can test them while using the svn as a backup storage device. I thik the scp is really the only way but I was hoping for another.

---

