---
title: "Creating modules in CVS on a remote machine"
date: 2011-03-04
forum: Programming Talk
---

### Post by zslevi on 2011-03-04
I was playing around on Sourceforge, starting a dummy project to get to know CVS. I was able to check out my projects CVSROOT, and I could make folders there, put files there and commit them and check them out to different local folder. However if I query the module list, it says there are no modules, also I cannot see my files through the "CVS browse" interface of the site. 
What I put in my modules file is:
[INDENT]module2_root module2_root
[/INDENT]And of course I have a committed folder in called "module2_root" in my CVSROOT folder.


The Sourceforge support staff wasn't very keen to help, they told to move on to SVN. However I still would like to get familiar with CVS, as many project still use it.

---

### Post by gmargo on 2011-03-04
For learning purposes, just work locally; no need for sourceforge. 

You don't need any fancy servers, just a plain old directory and the CVSROOT environment variable to point to it.

---

### Post by Aikar on 2011-03-05
why in the world are you learning CVS...? Who still uses it?
SVN is the more defacto standard these days that everyone uses

If you are needing to learn a VCS system, learn GIT and SVN. SVN primarily for the business world, GIT for better workings in the open source world.

I dont think ive ever ran into a CVS project... there really is no reason to learn CVS.

Any company worth a damn will at least be using SVN.

---

### Post by zslevi on 2011-03-10
Ok, the Sourceforge staff answered me (quite quickly, I'm the slow one here) : they told to write "." in the module field when checking out. NOT "CVSROOT"!!! 
You'll actually have a **CVSROOT** directory in your checkout dir, where administrative information is kept about modules, but don't mess with it directly. Just create a directory in your checkout dir (next to CVSROOT), put a file in it, add, commit, and there you're. Your dir name is the module name, and it'll show up in the web sourceforge's web interface as well, under "browse CVS".

To the other repliers in this thread: yeah, I'm learning SVN as well, but I think it's good to know, why certain features evolved the way they had in SVN. 

"Any company worth a damn will at least be using SVN. 	"
I meant Sourceforge projects. However they're about to phase out CVS as well. I guess they'll just forbid to create new CVS repos.

---

