---
title: "Looking for Code Repository Solution"
date: 2008-03-31
forum: Programming Talk
---

### Post by the ev on 2008-03-31
(Thought I'd ask here for ideas...)

I work for a web design/hosting firm, and we're looking for a web-based repository where we can store snippets of code from our clients projects to be recycled and used again in future projects (so we don't have to reinvent the wheel for each new client: just tweak it).  Ideally, it would be nice if such a system played nice with Joomla! CMS, but I don't want to get too picky.  ;)

Any suggestions?  If you need more info (as in, my description wasn't clear enough), please don't hesitate to tell me!

Thanks everyone!

---

### Post by pmasiar on 2008-03-31
wiki, without doubt

You can create hyperlinks between snippets, and onthologies as gateway pages. And good wikis have version control for every page.

Pick a wiki in language you use. If in doubt, use TRAC: [http://trac.edgewall.org/](http://trac.edgewall.org/) - it has wiki, Subversion, code viewer (with diffs), and bug tracker. You can use one wiki for tech docs for each project, and another for common snippets.

---

### Post by Quikee on 2008-03-31
> **pmasiar said:**
> wiki, without doubt

You can create hyperlinks between snippets, and onthologies as gateway pages. And good wikis have version control for every page.

Pick a wiki in language you use. If in doubt, use TRAC: [http://trac.edgewall.org/](http://trac.edgewall.org/) - it has wiki, Subversion, code viewer (with diffs), and bug tracker. You can use one wiki for tech docs for each project, and another for common snippets.

But.. this doesn't "solve" the code duplication - IMHO common well documented library (stored in a VCS) that is gradually improved (if it is open source - even better) is a lot better than "code snippet repository".

---

### Post by pmasiar on 2008-03-31
Well I assume they do have code repository, and want something different and easier to search for snippets.

BTW: Trac is excellent code repository (Subversion), integrated as I said with code viewer and wiki, so you can have special wiki markup to link to files or even versions of files in repository.

---

### Post by wrightee on 2008-03-31
We use a wiki for code snippets, and subversion for everything else.  Some of the developers have their own secret code dbs for those embarrassing / competitive bits they like to hang on to :)

---

### Post by the ev on 2008-03-31
Thanks for all the input!  We don't currently have a code repository, but it looks like Trac will definitely be worth checking out. 

@wrightee - Currently, our super-secret code DBs are our massive, genetically-modified and radioactive brains! Muhahaha... (Old school; I know). :)

---

### Post by the ev on 2008-04-09
Well, from what I can tell from the website, TRAC looks very promising, but setting up is hard!  Does anyone know of a more beginner-friendly version of Edgewall's setup instructions for running TRAC on a web server?  I think I got it installed, but I've no idea how to access it from the web...

Thanks!

---

