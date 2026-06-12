---
title: "run as administrator"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by seeker.k3 on 2012-09-03
Hello
I want to update TexLive using tlmgr. The documentation says I don't need administrator previleges, but my terminal sees it differently.

(BTW, I have installed a native version from TUG because Synaptic doesn't have everything I need. I now have both, which *shouldn't* be a problem.)

```
rip@Duck:~$ tlmgr update -all
```[HTML]You don't have permission to change the installation in any way,
specifically, the directory /usr/local/texlive/2012/tlpkg/ is not writable.
Please run this program as administrator, or contact your local admin.[/HTML]I tried this:

```
rip@Duck:~$ sudo tlmgr update -all
```[HTML]sudo: tlmgr: command not found[/HTML]Any help greatly appreciated---as always.
Thank you.

---

### Post by codemaniac on 2012-09-03
Have you tried to run tlmgr with absolute path .Something like below .

```
/path/to/tlmgr update -all
```

---

### Post by seeker.k3 on 2012-09-03
Ah ha. 
Thank you. 
Does that mean I haven't set my PATH correctly? I've asked about this in another thread: How to set PATH? I thought I was winning, but maybe not. I have two copies of Texlive in different places on the disk, but I need to use the most recent one. 

BTW, here's what I typed.

```
~$ sudo /usr/local/texlive/2012/bin/x86_64-linux/tlmgr update -all
```

Thank you for your help.

---

### Post by raja.genupula on 2012-09-03
glad news for us , now please mark your thread as solved . thank you.

---

### Post by seeker.k3 on 2012-09-03
The TexLive update manager didn't work until I typed the full path, so I'm asking: 

Does that mean the PATH in .profile is not being recognized? 

Before I close the thread, I'm hoping someone can say whether the failure of tlmgr to work as it should suggests my new version of TexLive is not working (given that an older Synaptic version is also on the disk).
Thank you.

---

### Post by Lars Noodén on 2012-09-03
Somehow the new version you have installed is not in the right place for you to find it with the existing $PATH variable.  It's not from the repository is it?

You could modify $PATH in .bashrc or .profile to something like this:

```

PATH="$PATH:/usr/local/texlive/2012/bin/x86_64-linux/tlmgr"

```

---

### Post by seeker.k3 on 2012-09-03
Thank you. Correct; it's not from the repository. I do have a version that I got via Synaptic, but it doesn't have everything I need, so I installed a fuller, up-to-date version of TexLive from Tex Users Group.

I need help with this because I don't understand path syntax. (Or even anything about paths.) I put this in .profile. Is this correct?

```
PATH=/usr/local/texlive/2012/bin/x86_64-linux:$PATH; export PATH
```

Do I have to add an additional line in the TexLive update manager: tlmgr?
Thank you again.

---

### Post by codemaniac on 2012-09-04
> **seeker.k3 said:**
> Thank you. Correct; it's not from the repository. I do have a version that I got via Synaptic, but it doesn't have everything I need, so I installed a fuller, up-to-date version of TexLive from Tex Users Group.

I need help with this because I don't understand path syntax. (Or even anything about paths.) I put this in .profile. Is this correct?

```
PATH=/usr/local/texlive/2012/bin/x86_64-linux:$PATH; export PATH
```

Do I have to add an additional line in the TexLive update manager: tlmgr?
Thank you again.

Linux determines the executable search path with the $PATH environment variable. To add directory /usr/local/texlive/2012/bin/x86_64-linux to the beginning of the $PATH environment variable, the following is used .
```
PATH=/usr/local/texlive/2012/bin/x86_64-linux:$PATH
```

And because of the export statement, any programs called by bash have the altered $PATH variable.

---

