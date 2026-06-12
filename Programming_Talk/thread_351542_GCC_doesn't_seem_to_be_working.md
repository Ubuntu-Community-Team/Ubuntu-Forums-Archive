---
title: "GCC doesn't seem to be working"
date: 2007-02-02
forum: Programming Talk
---

### Post by aijazbaig1 on 2007-02-02
Hello freinds.
A linux newbie here.
I wanted to use the gcc compiler to compile C  source files and make them into executables but despite installing the GNU C Compiler gcc-4.0 from the synaptic package manager I still get the follwing error message when i use the gcc command with the filename as its arguments.
To be more specific when I type:
```

gcc -Wall myfile.c -o myfile

```

I get the following error:
```

bash: gcc: command not found

```

Would someone please help me as Im rather new to the world of linux and command line compilation in general.

Looking to hear from you guys! and girls too lol!!..no im not stereotypical ;)

Best Regards,
Aijaz.

---

### Post by Wybiral on 2007-02-02
Have you tried "sudo apt-get install build-essential"
It installs most of the stuff you will need to compile basic c/c++ programs.

---

### Post by aijazbaig1 on 2007-02-02
Hello.
I did just what u had told me to do and I got the following error:

> 
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build


Hope to hear from u soon,

Best Regards,
Aijaz.

---

### Post by moma on 2007-02-02
You must spell it right.  It's "build-essential" not "build". Do as Wybiral told:

$ [COLOR="SeaGreen"]sudo apt-get install build-essential[/COLOR]

---

### Post by aijazbaig1 on 2007-02-02
Hello.
Finally it has worked for me.
But could anyone elaborate a little upon what that command actually did and why was it needed.
This would help me get the feel of isntalling stuff like that in Linux in general and Ubuntu in particular :)

Additionally I use the gcc compiler in school and the procedure they adopt their is that we create source file and then we use the make utility (is it a utility?? ) and then we end up creating executables.

Would someone kindly shed some light on that too??

Best Regards,
Aijaz.

---

### Post by moma on 2007-02-10
Visit [this...]("http://www.futuredesktop.org/#guides") page, and find + read these howtos: 
"[How to install this & that...]("http://monkeyblog.org/ubuntu/installing/")"   
"[Apt-get and dpkg guide...]("http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html")" 
"[Debian's apt guide...]("http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html")" 

Cheers,
   Moma

---

