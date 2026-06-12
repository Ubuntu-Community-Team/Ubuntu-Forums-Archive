---
title: "Python version question"
date: 2011-10-29
forum: Programming Talk
---

### Post by Diametric on 2011-10-29
Can someone answer or provide a link to a clear explanation as to the issue with Ubuntu and how it interacts with both python 2.x and 3.x?

For example - I ran "apt-get install python3" and all appears to have gone well.  However, when I type "python" at the bash terminal it says I am using 2.7.2 - I don't get it.  From my end it looks as if both version are installed and I can't seem figure out how to run 3.x only, like I'd like.  

Thank you...

PS: I'm running my first version of Unity (11.10), so if my frustration is seeping out, it's also due to me not finding Unity very intuitive - or rather, it trying to be too inuitive.

Cheers...

---

### Post by gsmanners on 2011-10-29
For Python 3.x you type:

```
python3 whatever.py
```

And that runs your whatever script.

---

### Post by Diametric on 2011-10-29
Does your answer suggest that both version of python run in parallel and I, as the user, must designate which to implement both from a code writing and code execution perspective?

---

### Post by gsmanners on 2011-10-29
Yeah... That sounds about right.

Support for Python 3 isn't quite up to snuff just yet (I'd really like to see python3-qt4 and python3-gtk in the repos).

---

### Post by Diametric on 2011-10-29
Sheeesh.  Talk about not making it easy.  Cool, I appreciate your reply - thank you.

---

### Post by simeon87 on 2011-10-29
Most software depends on Python 2. It wouldn't make sense to replace the default python by python3 as it wouldn't work well. That's why, even after installing Python 3, the system still uses Python 2 because most installed Python software hasn't been ported to 3 yet. In the future Python 3 should become the default python though.

---

### Post by gsmanners on 2011-10-29
Maybe it'll be standard for 12.10, but I doubt they'd want to make a big leap like that just before a 5-year LTS.

---

### Post by Arndt on 2011-10-29
> **Diametric said:**
> Does your answer suggest that both version of python run in parallel and I, as the user, must designate which to implement both from a code writing and code execution perspective?

The user of your program doesn't need to know which python to use (though it must have been installed, of course). If the first line of the python program is

#!/usr/bin/python3

and you've set the execute bit on it, you can run it as any other executable:

./whatever.py

---

### Post by crdlb on 2011-10-29
> **gsmanners said:**
> Maybe it'll be standard for 12.10, but I doubt they'd want to make a big leap like that just before a 5-year LTS.

If by 'standard', you mean the /usr/bin/python symlink, that may never happen. Ubuntu doesn't even have a 'python2' symlink, so there's no upgrade path. If Debian and Ubuntu ever do add 'python2' and start using it consistently, perhaps 'python' could be changed some time this decade.

---

### Post by wmcbrine on 2011-10-30
Don't hold your breath.

---

### Post by MadCow108 on 2011-10-30
debian (and thus likely ubuntu) will never change the default.
The opinion under the debian python maintainers is very strong is this regard and I agree with them.
They'll also only add the python2 option if they are forced to due the pep being accepted.

changing the default will break a billion packages and far more user scripts for basically no gain.
I don't see the issue with adding a 3 to your shebang/commandline

---

### Post by StephenF on 2011-10-30
> **MadCow108 said:**
> I don't see the issue with adding a 3 to your shebang/commandline
All those scripts that call Python3 are going to break when Python4 replaces it.

---

### Post by crdlb on 2011-10-30
> **StephenF said:**
> All those scripts that call Python3 are going to break when Python4 replaces it.

I suspect that a Python4 would break compatibility again, though perhaps not to the same extent that Python3 did.

---

### Post by MadCow108 on 2011-10-30
> **StephenF said:**
> All those scripts that call Python3 are going to break when Python4 replaces it.

then you add a python4 shebang and keep python3 poionting to python3...
if the transition is easier for 4, then you can replace python3 with a symlink to 4 and do not even have to update old scripts.
But this requires backward compatibility. python3 does not have this so one cannot do that.

I hope python will not break backwards compatibility again ever... the python 3 transition is such a huge mess already.

---

### Post by Diametric on 2011-10-31
As a coding/python newbie - am I correct - from reading these posts that the following are true:

1. Python2 scripts are (largely) used to run various apps/utilites in a given distro
2. If I write and wish to run my own Python apps, I must head my files with the #!/usr/bin/python3 and then source then as usual to ge the desired effects?
3.  there might be a Python 4?

Just trying to make sure I get what's up....

Thanks ya'll

---

### Post by MadCow108 on 2011-11-01
> **Diametric said:**
> As a coding/python newbie - am I correct - from reading these posts that the following are true:

1. Python2 scripts are (largely) used to run various apps/utilites in a given distro

yes, currently most packaged applications are python2. python3 packages begin with a python3- prefix.
Unfortunatly there aren't very many yet.
> 2. If I write and wish to run my own Python apps, I must head my files with the #!/usr/bin/python3 and then source then as usual to ge the desired effects?
if you want to run your script under python3 this and explicitly running *python3 script.py * are currently the only way that will always work.
> 3.  there might be a Python 4?
probably not in near future, hopefully never.

---

### Post by wmcbrine on 2011-11-03
> **Diametric said:**
> 1. Python2 scripts are (largely) used to run various apps/utilites in a given distroPython 2 is used to run pretty much every Python program you're likely to use, because it's still the de facto standard, because the transition takes some work, and you end up with everyone waiting on everyone else to do it, not to mention old unmaintained code that will never be ported.

It's not that Python 3 isn't *better*, in an abstract sense. It is. But sometimes that's not enough.

> *3.  there might be a Python 4?*

That was just a joke.

---

### Post by Diametric on 2011-11-04
Awesome.  That clears things up for me a bit.  I appreciate everyones input.

---

