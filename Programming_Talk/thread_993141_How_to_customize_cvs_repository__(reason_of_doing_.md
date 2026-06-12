---
title: "How to customize cvs repository?  (reason of doing so?)"
date: 2008-11-25
forum: Programming Talk
---

### Post by yilin on 2008-11-25
I'm trying to separate system and data whenever possible.

So I put /home to a separate partition and hope web root, database data and cvs repository can put into that partition also. If this can be done with little setup efforts, my data backup will be a simple affair without any concern about the system; and the system backup / restoration will not involve much custom data manipulations.

I'm confused about how to customize cvs repository. The cvsd installation defaults the parent directory of repository as /var/lib/cvsd and actually when I specified /var/lib/cvsd/repos to be the repository and everything worked just fine. But that not what I want. I like to put my repository to some where like /home/cvsrepository/

There is a command
cvs -d <custom repos path> init
which supposed to specify any customized repository path. But after that, how can I sepecify CVSROOT since in
cvs -d :pserver:username@localhost:/<repos path> login

where <repos path> is still relative to /var/lib/cvsd/

I guess a step by step example untile a user can login is what I need.
THANKS for any help.  
[email]el.debian@gmail.com[/email]



/*********** Ref for web and DB *************/
For the web doc root, I moved the contents of /var/www info /home/www/htdocs, removed directory /var/www and made /var/www a soft link pointing to /home/www/htdocs. That worked for now and I know apache has the conf file for custom document root.

For mysql database data, I did as
[http://www.ubuntu-howto.info/howto/how-to-move-mysql-databases-to-another-location-partition-or-hard-drive](http://www.ubuntu-howto.info/howto/how-to-move-mysql-databases-to-another-location-partition-or-hard-drive)
posted. You have to read the whole thing to make it work

---

### Post by dwhitney67 on 2008-11-25
If all you want to do is setup your own (personal) cvs staging area, then you are correct in using CVSROOT.

I generally define CVSROOT, and a few other cvs environment flags, in my ~/.bashrc file.  For example:

```

export CVSROOT=iceland:/home/cvs-repo
export CVS_RSH=/usr/bin/ssh
export CVSEDITOR=/usr/bin/vim

```
In the example above, "iceland" is the remote host.  The path following this hostname is where the cvs repo will reside.

The CVS_RSH instructs cvs to use SSH in lieu of the outdated RSH (remote shell).

The CVSEDITOR is set to vim, so that when I am prompted for change-history information, I am placed into vi.  If you prefer another editor, then specify it.  (I believe the default is nano, but I may be wrong).

P.S.  Wrt the CVSEDITOR, I would avoid specifying a GUI editor (e.g. gedit).  I do not know if cvs passes the -X option to SSH.

---

### Post by yilin on 2008-11-25
Thanks dwhitney67. your setting is very useful for me.
But I also like to move cvs repository physically from /var/lib/cvsd/repos
to /home/Repositories/cvsrepos. And I tried use xinetd. But not working as  some posts said to me.

I'm on ubuntu 8.10, the cvsd is newly installed. I tried to use s-link but that not working. Currently my repository have to stay at /var/lib/cvsd/repos as a choice a made at installation time (it asked a directory name under /var/lib/cvsd/).

So the cvsserver is running ok. Just the problem of set up the new repository path and login to the new repository accordingly...

---

### Post by dwhitney67 on 2008-11-25
I'm not quite sure why you insist that cvs forces one to use a particular directory (as perhaps was specified during the installation of cvs).

cvs will use the directory (if it exists) as specified by CVSROOT.

After you create your repo, you are free to move it to some other place.  Just make sure you update CVSROOT to reference that new location.

Btw, the proper way to move a directory from one place to another is to specify the -a option with the 'cp' command.  For example:
```

sudo cp -a /var/lib/cvsd /home/cvs-repo

```

---

### Post by yilin on 2008-11-26
Thanks dwhitney67. I've wrong understanding about cvs server as it accept repositories under specific parent directory. And I think you are right: repository can be relocated anywhere, say /home/cvs_repos.

My qustion is, after the relocation, how to specify the CVSROOT?

dvs -d :pserver:me@localhost:/home/cvs_repos login

give me error msg:

cvs [login aborted]: unrecognized auth response from localhost: cvs [pserver aborted]: /home/cvsd_repos: no such repository

---

### Post by dwhitney67 on 2008-11-26
I normally do not use a CVS server on my system.  However when I enabled it and ran a similar command to what you ran, I received the same error indicating that the repo (e.g. /home/cvs-repo) was not found.

The CVS server must be configured, somehow, to use a repo in /var/cvs (or on your system, /var/lib/cvsd).  If I could find the configuration file for the CVS server, then perhaps I could tweak this; but I could not find it.

Is there any particular reason you are using the CVS server?  Could you not just use CVS using SSH?  That's what I normally do.

---

