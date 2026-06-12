---
title: "tmp?"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by Matrix01 on 2011-12-31
does tmp folder in file system have temporary files?
i like to delete temp. files, hoping OS will run smoother.

---

### Post by lisati on 2011-12-31
The contents of /tmp - which are indeed temporary files - are usually deleted automatically when you (re)boot.

---

### Post by Matrix01 on 2011-12-31
[ATTACH]210033[/ATTACH]
well....
after i restarted this netbook a couple of times,
contents remain in tmp folder.

> **lisati said:**
> The contents of /tmp - which are indeed temporary files - are usually deleted automatically when you (re)boot.

---

### Post by sammiev on 2011-12-31
> **Matrix01 said:**
> [ATTACH]210033[/ATTACH]
well....
after i restarted this netbook a couple of times,
contents remain in tmp folder.

Make a backup of those files with a different extension name and delete the others. Reboot and if all is good delete the backups you made.

---

### Post by snowpine on 2011-12-31
These files are normal, and deleting them will not help your OS "run smoother." I see that you have 6.9gb of free space.

---

### Post by Matrix01 on 2011-12-31
guess these files  are useless.

> **snowpine said:**
> These files are normal, and deleting them will not help your OS "run smoother." I see that you have 6.9gb of free space.

---

### Post by bodhi.zazen on 2011-12-31
> **snowpine said:**
> These files are normal, and deleting them will not help your OS "run smoother." I see that you have 6.9gb of free space.

+1

> **Matrix01 said:**
> guess these files  are useless.

The files in /tmp are not useless simply becuse you do not understand them ;)

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/tmp.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/tmp.html)

> Many programs use this to create lock files and for temporary storage of data. Do not remove files from this directory unless you know exactly what you are doing! Many of these files are important for currently running programs and deleting them may result in a system crash. 

You should not delete system files, /tmp or otherwise, if you do not understand what they are for. Doing so is not going to improve performance.

---

### Post by Matrix01 on 2011-12-31
that's not what this web page says;

[http://www.ubuntugeek.com/tag/delete-temporary-files-ubuntu](http://www.ubuntugeek.com/tag/delete-temporary-files-ubuntu)

> **bodhi.zazen said:**
> +1



The files in /tmp are not useless simply becuse you do not understand them ;)

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/tmp.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/tmp.html)



You should not delete system files, /tmp or otherwise, if you do not understand what they are for. Doing so is not going to improve performance.

---

### Post by syerges on 2011-12-31
He gave you a link to what the files are... they are system files, not really temp files. Your website does not say it deletes those exact files... Those exact files are meant to be there for the system to work properly. If there were more than those files, the software you refer to would delete the additional files.

> **Matrix01 said:**
> that's not what this web page says;

[http://www.ubuntugeek.com/tag/delete-temporary-files-ubuntu](http://www.ubuntugeek.com/tag/delete-temporary-files-ubuntu)

---

### Post by bodhi.zazen on 2011-12-31
> **Matrix01 said:**
> that's not what this web page says;

[http://www.ubuntugeek.com/tag/delete-temporary-files-ubuntu](http://www.ubuntugeek.com/tag/delete-temporary-files-ubuntu)

Good luck to you. You would not be the first person to do a re-install after deleting things they did not understand.

You are probably going to be "OK" deleting things in /tmp, either the files will be re-created or you will crash X or your entire system.

But if you keep going, deleting things you do not understand, eventually you are going to create a more serious problem.

Be sure to keep a back up of any data you do not want to loose.

---

### Post by Matrix01 on 2011-12-31
i read article in your link,
and 
will not delete them.

you have saved my day,
thank u.

by the way,
is article which i found trash?
or 
does it  refer to something else?

> **bodhi.zazen said:**
> Good luck to you. You would not be the first person to do a re-install after deleting things they did not understand.

You are probably going to be "OK" deleting things in /tmp, either the files will be re-created or you will crash X or your entire system.

But if you keep going, deleting things you do not understand, eventually you are going to create a more serious problem.

Be sure to keep a back up of any data you do not want to loose.

---

### Post by syerges on 2011-12-31
The article you read did not say any specific files... It said it would delete temporary files. just because those files are in a /temp folder does not mean they are temporary files. That is why the folder is admin locked. Therefore we can't make mistakes deleting them as we could in Widows. The only time I adjust any admin locked files/folders is to add to the background files... add... I will never delete anything with admin access. Ubutnu isn't Windows, It doesn't lag your system over time to make you buy the new version. What you got for speed now is what you will always have.

> **Matrix01 said:**
> i read article in your link,
and 
will not delete them.

you have saved my day,
thank u.

by the way,
is article which i found trash?
or 
does it  refer to something else?

---

