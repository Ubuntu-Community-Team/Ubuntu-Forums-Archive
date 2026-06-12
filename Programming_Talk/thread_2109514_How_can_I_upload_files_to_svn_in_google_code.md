---
title: "How can I upload files to svn in google code"
date: 2013-01-27
forum: Programming Talk
---

### Post by DaviesX on 2013-01-27
I want to upload some files to the svn. I used svn import command, and it works. But how can I upload some specific files to the repository? Can I reserve the files from older version to the new version because I don't want to import everything every time I submit changes, it's too slow :(

Any help? please

---

### Post by slickymaster on 2013-01-27
Use [TortoiseSVN]("http://tortoisesvn.net/downloads").

After installing it, create a folder to hold all your files that you will work on.
Right-click on this folder and choose “SVN Checkout…” and in the “URL of repository:” enter your project’s URL,  press OK and enter your Google username and your GoogleCode.com password.
With that done, right click again on your folder and chose "TortoiseSVN/Add…" and select the files you want to upload to the SVN.

---

### Post by DaviesX on 2013-01-27
How about in linux?

---

### Post by slickymaster on 2013-01-27
> **DaviesX said:**
> How about in linux?

Take a look at this tutorial: [How to use SVN (Subversion) on Google Code hosting]("How to use SVN (Subversion) on Google Code hosting").

See if that's what you're looking for.

---

### Post by DaviesX on 2013-01-29
The link is broken, but I got it now.
I'll write the solution down so everybody else sees it will know exactly what to do.

To handle the svn properly,  
First you need to create a repository of the project in YOUR computer. It will become what is called a "working copy". You will use command "svnadmin" to do that
```

svnadmin create "PATH ON YOUR COMPUTER"

```

Then check out your project on Google code, you'll find the command on your project site. That will be something like,
```

svn checkout https://XXX.XXX.XXX/svn/ "PROJECT NAME" --username="YOUR USER NAME"

```

If you change the code, copy it to the repository (working copy), then use
```

svn add "CHANGED FILES' PATH"
svn commit "CHANGED FILES' FOLDERS' PATH"

```

And that's almost everything about it. :)

For more information, here is the website I've got most information from: 
[http://civicactions.com/blog/2010/may/25/how_set_svn_repository_7_simple_steps]("http://civicactions.com/blog/2010/may/25/how_set_svn_repository_7_simple_steps") (How To Set Up An SVN Repository In 7 Simple Steps)

---

