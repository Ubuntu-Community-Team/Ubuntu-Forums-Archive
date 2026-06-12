---
title: "Subversion - Getting current version of repo on apache"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by steve.klebanoff on 2008-05-07
Hi Guys,

I've set up a subversion server with web access on my Hardy Heron machine.  I've got a repo and I'm able to commit files and all that good stuff.

Now for the fancy stuff....

I want the current version of the repo to always be up on my apache server.  I can view all the files with the subversion web access control by going to [http://localhost/svn](http://localhost/svn).  But, .php files aren't actually handled as PHP files, they just display the PHP code in the browser.  

How can I set this up so the current repo is displayed as an actual website w/ php files handled as php files?

Thanks. Ubuntu Rules. :guitar:

Steve

---

### Post by steve.klebanoff on 2008-05-08
I ended up checking out the current repo to a directory in my documentroot (/var/www/) I then set up WebMin and setup custom commands that would update the current version of the repo to that directory.

---

### Post by sewmyheadon on 2008-05-10
Steve,

There's another way to do this, which is to serve the docs up with a different MIME type.  That way, your repository and active site can co-exist.

You can read about Subversion MIME types here:
[http://svnbook.red-bean.com/en/1.0/svn-book.html#svn-ch-7-sect-2.3.2](http://svnbook.red-bean.com/en/1.0/svn-book.html#svn-ch-7-sect-2.3.2)

I heard about it on the [WebDAV episode of the FLOSS Weekly podcast]("http://twit.tv/floss28") and have yet to try it.

Another possibility you could look at is to use one of the Subversion 'hooks' to automatically publish your latest files to the appropriate folder in your /var/www directory.

You can read about Subversion hooks here:
[http://svnbook.red-bean.com/en/1.0/svn-book.html#svn-ch-5-sect-2.1](http://svnbook.red-bean.com/en/1.0/svn-book.html#svn-ch-5-sect-2.1)

Hope that helps.

---

