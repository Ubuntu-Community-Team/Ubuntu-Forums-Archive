---
title: "Synchronise / compare directory server:/home/&lt;user&gt; with client::/home/&lt;user&gt;"
date: 2008-09-11
forum: Programming Talk
---

### Post by c.monty on 2008-09-11
hi!
I've installed a central file server with ubuntu in an heterogeneous environment with Linux and Windows clients.

/home-directory on server is shared (NFS and SAMBA).
each client can mount share /home/<user>.
there's a 1:1 relation for users on clients and server.

the problem is as follows:
in case the server is not available, linux clients will write files on the local /home/<user> directory.
these files needs to be synchronised with server when server is available again **and** should be deleted on client after successfull synchronisation.

my first thought was to use either rsync or diff.
however, I don't know how to set up file deletion.

thx for your support
:guitar:

---

