---
title: "Form Validation to Check File Existance"
date: 2008-11-16
forum: Programming Talk
---

### Post by dyous87 on 2008-11-16
Hello,

I am working on a simple content management system that has an HTML form allowing the user to create a new file from. The form gets sent to a php script which reads the values and creates a .txt file and a .js file based on those values. The user can then edit the .txt files with a built in rich text editor I set up on the site.

I am trying to come up with a way to set up validation on the form so that it does not allow the user to create a file which already exists. Right now if a file exits and a user tries to create a file with the same name it overwrites the original file which I cannot have happen. 

Does anyone know if there is a way to get this done. It would be nice if it could be done in javascript because I currently have javascript validation on some fields in the form however I am open to other methods. 

I thank you all very much in advanced for your time and help :)

David

---

### Post by exhume on 2008-11-16
the file_exists(string $filepath) lets you check if a file exists in your filesystem (if you have multiple folders you might have to wrap this in some kind of loop to check the whole tree).

Then all you have to do is put the file creation portion of your script in an if block:


```
if(!file_exists($file))
{
// code to make the file.
}
else
{
//give the user some kind of error message
}
```

---

### Post by dyous87 on 2008-11-16
Thanks a lot exhume that was a big help!

I am certain I know how I am going to go about doing this now, I will post here how it goes once I get to it!

:) David

---

### Post by dyous87 on 2008-11-16
Ok I added the If, Else statement you gave me with the file_exists function and it worked. Thanks again so much for your help, it was greatly appreciated!

David :biggrin:

---

### Post by drubin on 2008-11-17
Take a look at the php.net man pages they are quite useful. 

Also be VERY carefull about allowing people to edit/add files to your webserver.

lets take for instance I upload a script that deletes all the files in the webroot. There goes all your information. Or even worse one that reads the config files and gives me your username/passwords to the servers.

[http://en.wikipedia.org/wiki/Code_injection](http://en.wikipedia.org/wiki/Code_injection)

---

### Post by dyous87 on 2008-11-17
> **drubin said:**
> Take a look at the php.net man pages they are quite useful. 

Also be VERY carefull about allowing people to edit/add files to your webserver.

lets take for instance I upload a script that deletes all the files in the webroot. There goes all your information. Or even worse one that reads the config files and gives me your username/passwords to the servers.

[http://en.wikipedia.org/wiki/Code_injection](http://en.wikipedia.org/wiki/Code_injection)

Thanks for the tips :)

This CMS system I developed will only be available via a password protected directory that only the site's admin and myself will have so this is not an issue. It was a way for me to easily come up with a way for him to edit and create pages.

---

