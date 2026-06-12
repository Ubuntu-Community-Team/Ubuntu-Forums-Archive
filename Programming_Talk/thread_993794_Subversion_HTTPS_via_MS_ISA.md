---
title: "Subversion HTTPS via MS ISA"
date: 2008-11-26
forum: Programming Talk
---

### Post by arcanus on 2008-11-26
I have a small issue with subversion and connection via a MS ISA server (company policy server, i cant do anything about it...).

When running the CLI version (ie. "svn ls https://external.fqdn/svn/repo" in a shell) it prints the content of the repo, and hangs for ~2 minutes. But when I run it against the local host (NOT via the ISA server) (ie. "svn ls https://local.winsname/svn/repo") it returns immediatly after printing the content of the repository. (This also happens when using it through Netbeans.)

When running a grafical client (SyncroSVN), which uses the same CLI backend as mentioned, this is not a issue. The commands return instantly, regardless. This leads me to believe there is a configuration option i just have to enable or disable, but surely there must be someone out there who has cracked this, or knows the subversion configuration in and out.

I cant remember this being a problem in hardy tho (1.4.6dfsg1-2ubuntu1).

This is however NOT the case when running the client on a Macbook or from windows, so I am baffled, and have no idea what the problem is :confused:

SVN clients tested:
1.5.1dfsg1-1ubuntu2
1.5.4dfsg1-1ubuntu1 (backported as 1.5.4dfsg1-1ubuntu1~8.10prevu1)

OS:
Kubuntu 8.10
Ubuntu 8.10

Cheers
Magne

---

