---
title: "Simultaneous usage of local and pserver CVS"
date: 2015-11-09
forum: Programming Talk
---

### Post by ofnuts on 2015-11-09
So, I'll be scripting some somewhat large CVS checkouts for semi-automated builds. These builds will run on the very same machine that holds the CVS repository, so this machine also runs a CVS server.

Question #1: is there a significant performance advantage in using a "local" CVS (CVSROOT=/path/to/repository) versus a pserver one (CVSROOT=:pserver:user@host:2401/path/to/repository)

Question #2: if running local has benefits, is it possible to run local while the server is also up (which a priori shouldn't cause any more problems than two users with requests that spawn parallel instances of the server)

---

