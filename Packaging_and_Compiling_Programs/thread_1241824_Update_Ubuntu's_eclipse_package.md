---
title: "Update Ubuntu's eclipse package"
date: 2009-08-16
forum: Packaging and Compiling Programs
---

### Post by teh.ivo on 2009-08-16
Hi, I have very recently dual booted ubuntu on my Vista laptop.

I think eclipse is a great IDE platform, and I have no idea why the version listed on the ubuntu package manager program is 3.2.2

This is so old (3 years old) it should really be either updated or deleted completely; 3.2.2 is losing a heap of compatability with current plugins which are what make eclipse useful. People installing eclipse will find out that half the plugins they would like to put on need a major version update of eclipse. The newest out is 3.5!

So I was thinking this could be a good way to help out ubuntu...
Update the package for eclipse so that it is listed as 3.5 and that you can just get from ubuntu package manager/downloader rather than downloading manually.

I would like to know what steps I would have to do to get this from the eclipse source to a deb package that could be considered to be listed.

I know two possible complexities for it are
-the java dependancies and what java ubuntu users are using,
-It comes in seperate 32 and 64 bit packages

basically I am looking for some guidance, links, starting help on how to do this.

I am very new to linux as a whole but I think I'm pretty intelligent and can figure things out, it would be nice to be given a helping hand on where to start out learning how to do this though

like what concrete steps I need to complete
Where to learn about packages and how to make one (hopefully a few good links?)
Any advice in particular to eclipse/java for this
What/where to find out about process for getting it to be an ubuntu package

Personally I'm very dissapointed to see only the python CLI in the (hidden) programming menu on ubuntu... is it not for developers? Is there not a basic coding editor to also put here at least? These are peripheral questions though.

Any help with doing this is very much appreciated, I hope I can help / do this !

---

### Post by laborg on 2009-08-16
What's the problem with installing eclipse from eclipse.org ? I've experienced no problems when extracting the tar to my home directory and running it from there.

---

### Post by teh.ivo on 2009-08-16
What's the problem with downlaoding and running any ubuntu package straight from its compiled source?

Isn't the aim of packages to help make it easy to install things, etc...

If you argue it isn't worth updating/making the package for one program, why argue to update/package any?

Eclipse is a pretty popular IDE as far as I can tell!

---

### Post by laborg on 2009-08-17
i just wanted to point out that the installation of eclipse, since it's a java software, isn't encumbered by any real problems. further on there are a lot of eclipse flavors, so which one would you suggest to put into the packaging?

---

