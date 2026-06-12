---
title: "use git to host my project for the first time"
date: 2010-11-25
forum: Programming Talk
---

### Post by jamesbon on 2010-11-25
Ok by now I have wasted a couple of hours.Scratching my head and searching for information reading blogs documents etc etc.Finally I decided to create this thread.
I decided to put my programs on Google Code and since  I found git to be a popular thing I decided to use it.
 I want to host my codes as 
[http://code.google.com/p/something/](http://code.google.com/p/something/)
On my local machine I have a folder named bond which I want to commit to above url.
I have checked 
[http://flashsim.wordpress.com/category/google-code/](http://flashsim.wordpress.com/category/google-code/)
the guy seems to be quite frustrated with git.
Google gives a link to read a doc
[http://hgbook.red-bean.com/read/file-names-and-pattern-matching.html](http://hgbook.red-bean.com/read/file-names-and-pattern-matching.html)
read it completely and this actually did not helped me a bit.
In the comments section of following link
[http://google-opensource.blogspot.com/2008/05/develop-with-git-on-google-code-project.html](http://google-opensource.blogspot.com/2008/05/develop-with-git-on-google-code-project.html)
I get a URL 
[http://linuxsagas.wordpress.com/2009/06/05/adding-a-project-to-git-and-google-code/](http://linuxsagas.wordpress.com/2009/06/05/adding-a-project-to-git-and-google-code/)
this guy seems reasonably mature to write how to begin.

So now in my directory I go and here are the steps which till now I have done.
```

mkdir st/bond
cp -r $HOME/st/*.c $HOME/st/bond
cd bond
git init 
git commit -m "Initial Release Candidate"
```

and then I do 
```

git svn clone --username me  https://myproject.googlecode.com/svn/trunk
git: 'svn' is not a git command. See 'git --help'.

Did you mean one of these?
	fsck
	show


```
Now what do I do to get rid of above message.I have been searching all across internet and I have not found correct thing with respect to my question.

---

### Post by Arndt on 2010-11-25
> **jamesbon said:**
> Ok by now I have wasted a couple of hours.Scratching my head and searching for information reading blogs documents etc etc.Finally I decided to create this thread.
I decided to put my programs on Google Code and since  I found git to be a popular thing I decided to use it.
 I want to host my codes as 
[http://code.google.com/p/something/](http://code.google.com/p/something/)
On my local machine I have a folder named bond which I want to commit to above url.
I have checked 
[http://flashsim.wordpress.com/category/google-code/](http://flashsim.wordpress.com/category/google-code/)
the guy seems to be quite frustrated with git.
Google gives a link to read a doc
[http://hgbook.red-bean.com/read/file-names-and-pattern-matching.html](http://hgbook.red-bean.com/read/file-names-and-pattern-matching.html)
read it completely and this actually did not helped me a bit.
In the comments section of following link
[http://google-opensource.blogspot.com/2008/05/develop-with-git-on-google-code-project.html](http://google-opensource.blogspot.com/2008/05/develop-with-git-on-google-code-project.html)
I get a URL 
[http://linuxsagas.wordpress.com/2009/06/05/adding-a-project-to-git-and-google-code/](http://linuxsagas.wordpress.com/2009/06/05/adding-a-project-to-git-and-google-code/)
this guy seems reasonably mature to write how to begin.

So now in my directory I go and here are the steps which till now I have done.
```

mkdir st/bond
cp -r $HOME/st/*.c $HOME/st/bond
cd bond
git init 
git commit -m "Initial Release Candidate"
```

and then I do 
```

git svn clone --username me  https://myproject.googlecode.com/svn/trunk
git: 'svn' is not a git command. See 'git --help'.

Did you mean one of these?
	fsck
	show


```
Now what do I do to get rid of above message.I have been searching all across internet and I have not found correct thing with respect to my question.

Did you also google for "'svn' is not a git command"?

---

### Post by Arndt on 2010-11-25
I'll shorten the pain: you need to install git-svn.

---

### Post by lovinglinux on 2010-11-25
My advice would be to use [GitHub]("http://goo.gl/un5E"). 

When I used Google Code, git wasn't an option, so I used svn. Recently I decided to move to GitHub and my workflow became a lot simpler and easier.

All you need is git installed. When you create a new repository on GitHub, you get instructions on how to setup your local repository. Just follow the instructions and you will be ready in less than 5 minutes.

I also use Giggle to browse the repositories.

```
sudo apt-get install giggle
```

---

### Post by jamesbon on 2010-11-26
> **lovinglinux said:**
> My advice would be to use [GitHub]("http://goo.gl/un5E"). 

When I used Google Code, git wasn't an option, so I used svn. Recently I decided to move to GitHub and my workflow became a lot simpler and easier.

All you need is git installed. When you create a new repository on GitHub, you get instructions on how to setup your local repository. Just follow the instructions and you will be ready in less than 5 minutes.

I also use Giggle to browse the repositories.


Its quite costly to learn. 600 USD

> **Arndt said:**
> I'll shorten the pain: you need to install git-svn.
Ok I did it.
Step1 )After that I went to a folder named bond this is what I want to host on internet.
Step 2) git init
Step 3) git add **.**
After this what do I need to do?

---

### Post by lovinglinux on 2010-11-26
> **jamesbon said:**
> Its quite costly to learn. 600 USD

It is free for public open source projects.

---

### Post by jamesbon on 2010-11-26
I am referring to cost of training.

---

