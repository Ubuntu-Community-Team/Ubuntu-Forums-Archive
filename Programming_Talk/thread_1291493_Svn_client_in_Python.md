---
title: "Svn client in Python"
date: 2009-10-14
forum: Programming Talk
---

### Post by djbushido on 2009-10-14
Is there an svn client written in pure Python? Such that I don't have to install an svn client executable in a Windows/Linux environment, I can use the same script. Or at least something that doesn't require platform-dependent files.

---

### Post by Zugzwang on 2009-10-15
It's unlikely that anyone would want to re-implement a mature piece of software in another language. If that's an option, you might want to use mercurial instead of subversion. Mercurial is a distributed SCM and is fully written in Python.

---

### Post by djbushido on 2009-10-15
No - what I'm trying to do is be able to check out a revision from Sourceforge (current repo is SVN) while not having to make a separate copy of a script for windows and linux (and mac). Any ideas?

---

### Post by G|N| on 2009-10-15
Maybe "pysvn" is what you are looking for?

---

### Post by djbushido on 2009-10-15
Closer, I guess. I can just include a linux .so of svn, which is what it depends on. I would still prefer something written entirely in python if possible. If not, I can make do though.

---

### Post by jpkotta on 2009-10-15
So you just want to be able to run svn from the command line (or script as the case may be) in Windows?  You don't need a Python implementation for that.  Install [SlikSVN]("http://www.sliksvn.com/en/download") and make sure it's in the PATH.

---

### Post by djbushido on 2009-10-16
That's the problem - I am trying to avoid installing anything because the script I'm writing is an installer. I'm trying to see if I can make it such that all the person has to download is the installer script + python, and then the script handles everything else. Installing unspecified programs is against etiquette for an installer. Sorry if I didn't specify that at the beginning.

---

