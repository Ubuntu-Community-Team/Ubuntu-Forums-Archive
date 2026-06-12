---
title: "not able to install restricted extras"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by shady2 on 2014-01-27
When clicking install on restricted extras I get message (before installing must remove-Libav codec library and Libav utility library).
This has me stumped. Anybody know what these are ???

---

### Post by andrew.46 on 2014-01-27
I believe that the Ubuntu restricted extras meta package has replacements for some of the libav components, these are the ones that you have seen being replaced or have been asked to remove.

---

### Post by shady2 on 2014-01-27
> **andrew.46 said:**
> I believe that the Ubuntu restricted extras meta package has replacements for some of the libav components, these are the ones that you have seen being replaced or have been asked to remove.



It is telling me to remove those before installing !
How do I remove them ? Thanks for help !!!

---

### Post by Bashing-om on 2014-01-27
shady2; Hi !

Let's take a look at what is going to happen, and we can then advise you explicitly:
Post back the outputs of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -s ubuntu-restricted-extras

```
Where the '-s' = Simulate.
We will have a much better idea of what is and what will be.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by shady2 on 2014-01-27
this seemed to work. Thanks

---

### Post by Bashing-om on 2014-01-27
shady2; Hey .

Possible that update/upgrade resolved the problem.
If your system is now stable and ubuntu-restricted-extras is installed;
Please mark this thread as solved.
1st post ->thread tools Aids others seeking a similar solution and helps keep the forum tidy.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

### Post by shady2 on 2014-01-28
Correction. I am not sure? I have several new apps. But, resricted extras still shows up as available for download.

---

### Post by Bashing-om on 2014-01-28
shady2; Morning .

Not to panic, let's see what the errors are and then we can fix them;
Post the out put - BetweeN Code Tags - of terminal codes:
```

sudo apt-get update
sudo apt-get - upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Mind you, we have not "installed" ubuntu-restricted-extras ! We have only to this time asked the system what it would do .

Little steps ->
[INDENT][INDENT]but we will get there
[/INDENT][/INDENT]

---

