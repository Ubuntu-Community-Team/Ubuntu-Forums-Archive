---
title: "Eclipse wont start, problem with virtual machine?"
date: 2009-03-12
forum: Programming Talk
---

### Post by TMachado on 2009-03-12
I've just downloaded this package:

[http://www.eclipse.org/pdt/](http://www.eclipse.org/pdt/)

And extracted the folder to Desktop. So, started Eclipse and now have three problems:

First, Eclipse is very very slow. Then, when I reach to choose the workspace, I have the information: "GCJ has been detected as the current Virtual Machine. Use of GCJ is untested and unsupported.".

And then when Eclipse finally start, has a lot of errors "not initialized(...)".

Can you please help me?

I'm using Ubuntu 8.04.02.

---

### Post by TMachado on 2009-03-12
I've done sudo aptitude install sun-java6-jre, and now Eclipse dont even start :(

I've dont eclipse -vm /full/path/to/java/bin/java, and it says "no java virtual machine found"...

---

### Post by cabalas on 2009-03-12
To get your java back up and running try running this:

```
sudo update-java-alternatives -l
```

Which will give you a list of all the versions of java that is installed then run:

```
sudo update-java-alternatives -s XXXX
```

where XXXX is the name of suns java that is installed which should be something like 'java-6-sun'

I stole this information from [here]("https://help.ubuntu.com/community/Java")

---

### Post by TMachado on 2009-03-12
> **cabalas said:**
> To get your java back up and running try running this:

```
sudo update-java-alternatives -l
```

Which will give you a list of all the versions of java that is installed then run:

```
sudo update-java-alternatives -s XXXX
```

where XXXX is the name of suns java that is installed which should be something like 'java-6-sun'

I stole this information from [here]("https://help.ubuntu.com/community/Java")

Now, instead saying there's no virtual machine, nothing happens. I run, and nothing appears.. appears a little window with nothing in it...

What strange is my eclipse 3.2.2 works fine, but the one I downloaded (home/tiago/Desktop/eclipse/eclipse, nothing happens :(

---

### Post by Can+~ on 2009-03-12
Just a little tip, if you're onto web development, I recommend aptana (which is also based on eclipse) and that plugin.

---

### Post by TMachado on 2009-03-13
> **Can+~ said:**
> Just a little tip, if you're onto web development, I recommend aptana (which is also based on eclipse) and that plugin.

Why?

---

