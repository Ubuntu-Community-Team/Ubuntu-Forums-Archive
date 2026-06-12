---
title: "Bash script in a ppa."
date: 2012-11-30
forum: Programming Talk
---

### Post by ntzrmtthihu777 on 2012-11-30
Hello all,
Bit of a Linux/Ubuntu n00b, have been using it about as long as I have been a member of this forum, but am learning pretty quick and loving every minute of it :D

I have created a script that uses awk and sed to convert .ust files between romaji and kana. I placed it in /usr/bin so I could call it globally, basic script such-stuffs. However, I want to be able to place this file in a ppa for install by other users via apt-get. Unfortunately, I have no idea how to do this, lol, and most of what I have found googling deals with "actual programs" that need to be compiled and such. All I want is a way that:

1. The script itself (luct) be saved into /usr/bin
2. A file used by the script named luct.lst be saved into /usr/bin.
3. Allow for updates via apt-get update.

A simple request, I think. I just have no idea where to look, lol.

---

### Post by Vaphell on 2012-11-30
your script has to create its own dotfile in user home (if it needs some local config) when it runs for the first time for that user.
consider this scenario:
- you install stuff, including putting files in homes
- you create new user
where would that new user get the files from?

imho these sed scripts should be packaged in a way that will install them somewhere in system directories, /usr/share maybe (i never packaged anything so i don't know where things exactly belong)?

---

### Post by ntzrmtthihu777 on 2012-11-30
> **Vaphell said:**
> your script has to create its own dotfile in user home (if it needs some local config) when it runs for the first time for that user.
consider this scenario:
- you install stuff, including putting files in homes
- you create new user
where would that new user get the files from?

imho these sed scripts should be packaged in a way that will install them somewhere in system directories, /usr/share maybe (i never packaged anything so i don't know where things exactly belong)?
Holy lol, I can't escape you! OK, that is fine and true, did not consider the possibility of other users. I am using IO redirects (< and > as you well know) to write the output of certain actions to the sedscripts. Problem is I don't know how to make it write to /usr/bin without using sudo, and that end up making the resultant converted files property of root, which is not desirable. How can I do this?

Example
[/FONT]```

[FONT=Courier New]#!/bin/bash
awk '{yada yada}' < infile > outfile
sed -f outfile original > converted
[/FONT]
```
[FONT=Courier New]
Running it with sudo makes converted property of root.

...just re-read your post, you said /usr/share, can you write to that without being root?
...seems not, so original problem remains. I think I may have a solution, going to tinker a bit.

---

### Post by Vaphell on 2012-11-30
my 'score' should tell you that i lurk here quite often ;-)

well, i don't know what your setup looks like.
What is the minimal set of files that is needed to produce the working setup? I see you generate sed files so they don't count. Script+infile+original?

---

### Post by ntzrmtthihu777 on 2012-11-30
> **Vaphell said:**
> my 'score' should tell you that i lurk here quite often ;-)

well, i don't know what your setup looks like.
What is the minimal set of files that is needed to produce the working setup? I see you generate sed files so they don't count. Script+infile+original?
Script and infile. Original is chosen via a prompt within the script itself and will vary from use to use. I tried

```

#!/bin/bash
awk '{yada yada}' < infile > ~/.outfile
sed -f ~/.outfile original > converted

```
but original and converted are still the exact  same as if none of the sed operations had matched up. I know the outfile  generated is correct because I have not changed the contents created  only the location, and it did the conversions just fine before. Am I  calling outfile wrong, is there some syntax I screwed up?

Nevermind, figured it out. I had copied a section of the script and pasted it again to use as a template, but did not change everything that needed changing. It now works fine, and should for any user.

---

### Post by Vaphell on 2012-11-30
i don't see anything wrong with that code.
Are you sure there are no \r chars that mess things up or something like that?

---

### Post by drmrgd on 2012-11-30
Maybe I'm not understanding something, but are you processing the output of the first awk command with sed?  Also do you need the intermediate file?  If you don't need the intermediate file, perhaps piping the output with the pipe command '|' would be a better way.  If it's a file that needs to be held for a while until the script completes, then perhaps writing it to /tmp would be an option there instead of writing it to any /usr/bin folder.

You could change the permissions of the /usr/share/bin/<script> folder so that it's writable by everyone.  But, I think that's a messy and less than ideal solution to the problem.  Those /bin folders are really not intended for writing by general users.

---

### Post by ntzrmtthihu777 on 2012-11-30
> **drmrgd said:**
> Maybe I'm not understanding something, but are you processing the output of the first awk command with sed?  Also do you need the intermediate file?  If you don't need the intermediate file, perhaps piping the output with the pipe command '|' would be a better way.  If it's a file that needs to be held for a while until the script completes, then perhaps writing it to /tmp would be an option there instead of writing it to any /usr/bin folder.

You could change the permissions of the /usr/share/bin/<script> folder so that it's writable by everyone.  But, I think that's a messy and less than ideal solution to the problem.  Those /bin folders are really not intended for writing by general users.

The first awk command creates a [sedscript](http://www.grymoire.com/Unix/Sed.html#uh-16) which is used by sed to process the original file and produce the converted file. I have figured out the writing issue (I just had it write to ~ as a dotfile), and thank you for the /tmp idea, that would be perfect. My only issue now is getting it into the ppa, and the only info on that I can find is for packages compiled from source, and there is no compilation needed for this, just saving two files into /usr/bin. I know I could just instruct people to just do that, but I want to make it more or less fool-proof.

Vaphell I caught my error.

---

### Post by drmrgd on 2012-11-30
Whoops!  Totally missed that 'sedscript' bit in your original posts.  Sorry about that!

As for packaging it for a PPA, not sure how to do that.  Out of curiosity though, had a quick look at Launchpads docs, and it seems like a bit of work and slightly complex.  Not sure if you've seen this already, but here's the start of the documentation on how to set up a PPA and create a package for distribution:

[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA)

Hope that helps!

---

### Post by ntzrmtthihu777 on 2012-11-30
> **drmrgd said:**
> Whoops!  Totally missed that 'sedscript' bit in your original posts.  Sorry about that!

As for packaging it for a PPA, not sure how to do that.  Out of curiosity though, had a quick look at Launchpads docs, and it seems like a bit of work and slightly complex.  Not sure if you've seen this already, but here's the start of the documentation on how to set up a PPA and create a package for distribution:

[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA)

Hope that helps![FONT=Courier New]
Yes, I have been to that very page and read it. But as I said, this mainly deals with actual "programs" compiled from source, I just have 2 files (very small ones, at that) that I need saved to /usr/bin. Seems overkill to add it to a ppa, yes, but I want this to be installable and updatable like any other ubuntu package. If need be I will actually write into a program with source code, but that is even more overkill, lol.[/FONT]

---

### Post by drmrgd on 2012-11-30
My impression, though, is that that level of complexity is the rationale for PPAs in the first place.  To get that level of being able to update things on the fly like that, you sort of have to do all of what's required.

Another alternative might be to create a very simple install file as part of your package, and then put it up on Github for others to use.  If you sign up with a public account (anyone can download your stuff, but not contribute to the branch (I think)), it's free.  Then people who want it can just clone the latest branch to their computers and run your installer to set it up the way you want.  The installer probably doesn't need to be any more than a few lines of code just to put the files where they need to be and maybe check for a dependency or two if need be.  

Me personally, for such a simple project (as you're describing it), I'd go the Github route for distribution.

---

### Post by ntzrmtthihu777 on 2012-11-30
[FONT=Courier New]You know, I had a look at github... I may end up going that way. I eventually want to port the bash script to c++ for windows users, if I do that I could use its source to make the package for ppa instead, yes? We will see. I am atm recovering from a catastrophic attempt at installing arch, lol, so this has been back-burnered
[/FONT]

---

### Post by ntzrmtthihu777 on 2012-12-02
[FONT=Courier New]Success! The information needed for this sort of project can be found [here]("http://wiki.debian.org/CreateDummyPackage") and can be used to create .deb for simple bash scripts, and presumably other scripts.
[/FONT]

---

