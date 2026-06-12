---
title: "Apache, Mysql, Subversion, Django, Python"
date: 2007-04-16
forum: Programming Talk
---

### Post by ebullient on 2007-04-16
Overview:

Edgy server.  Want to do a coding  project with my friends.  They have non-admin accounts, can ssh into the machine just fine.

What I have working:

Subversion and python work with apache.  We can view the subversion repository via html and can check it out, apache shows python code.  Mysql is installed and started, I've only set a root password.  Django is installed and partially configured.

Where I'm having problems:

Following the tutorials on the django site, I've reached this method:
Step 1, do everything here, including following the link for using django with mod_python.
[http://www.djangoproject.com/documentation/install/](http://www.djangoproject.com/documentation/install/)
In [http://www.djangoproject.com/documentation/modpython/](http://www.djangoproject.com/documentation/modpython/), my .settings hasn't been generate yet, but I go ahead and set it to /var/svn/project/project.settings .  Restart apache.
Step 2, do everything here.
[http://www.djangoproject.com/documentation/tutorial01/](http://www.djangoproject.com/documentation/tutorial01/)
Here's where I run into trouble.  I want the project to be in the svn directory, /var/svn/project.  However when I run sudo django-admin project in /var/svn it of course complains that the directory already exists.  I want the project to be in there so my friends can check it out and view it, everything is password protected already so there is some measure of security.  This is all for development so no one else needs to see it yet.

Not to mention mysql...

So does any of this make sense?  Am I crazy?  Can you help me?

---

### Post by Mirrorball on 2007-04-16
Shouldn't the project be created elsewhere? Then subversion would move it to /var/svn/project when you commit, including project.settings.

---

### Post by ebullient on 2007-04-16
Yes, thank you.  Sorry, I suppose I'd been banging my head against for so long I forgot where I was.

---

