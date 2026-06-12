---
title: "placement of main functions in client and server code in rpc different?"
date: 2014-10-31
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-31
I'm generating files for client and server code in rpcgen. Say, my idl file is called idl.x, I will then have mainly four files : idl_svc.c , idl_server.c, idl_clnt.c and idl_client.c

In the client files, the architecture is pretty clear in that, the main function is held by the file we as application developers are supposed to edit. This then calls the idl_clnt.c which creates stubs and goes to the transport layer through sockets.

In the server side however, the main file is held in the idl_svc.c which we're not supposed to edit. This file calls functions in idl_server.c which contains all the remote procedure code which we're supposed to fill in, as per the application needs. Why is that? **Isn't the step just before going to the network the one that should be the don't-edit file?**

I feel the client model makes sense, whereas the server model has left me confused.

---

