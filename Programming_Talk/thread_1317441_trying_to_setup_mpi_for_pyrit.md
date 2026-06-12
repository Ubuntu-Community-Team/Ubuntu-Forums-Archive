---
title: "trying to setup mpi for pyrit"
date: 2009-11-06
forum: Programming Talk
---

### Post by andytof47 on 2009-11-06
hi there, just trying to setup mpi for pyrit, to make things a little faster.

I follow the instructions here [https://wiki.ubuntu.com/MpichCluster]("https://wiki.ubuntu.com/MpichCluster")

and get to this command

```
sudo echo  /mirror *(rw,sync) >> /etc/exports
```

and I get this error

```
bash: syntax error near unexpected token `('

```

SoI can't follow th e tutorial to set this up. 

I posted here cause the most MPI results came up here so I figure someone must know what is wrong..

cheers):P

---

### Post by andytof47 on 2009-11-07
hey cmon ubunutu community,

be friendly :)

help a fellow user out
 :popcorn:


bump

---

### Post by mcurran on 2011-02-22
First you should try to understand what the command is actually doing; then you would easily notice that it should go like this:

echo "/mirror    *(rw,sync)" >> /etc/exports

This command appends the line "/mirror    *(rw,sync)" to the exports file in the following directory:  /etc

Any more questions?  You should also install nfs-kernel-server first, because it usually wants to overwrite the exports file, and you need it for the cluster, unless your going to use gfs (which I doubt)...  So install that, and then run the command I provided.  

Let us know how you did, or how the nodes are running w/ pyrit.  I'm thinking of setting up the same with a couple of my old PC's.  Mostly to learn.  I'll need to research on howto setup the ip configurations, and whether I'll need to make my master a dhcp server or bridge the connections somehow for my first node.  I want them to be independent from a switch or router, because, I'm only doing one or two nodes and don't want to clog up my lan bandwith.

---

