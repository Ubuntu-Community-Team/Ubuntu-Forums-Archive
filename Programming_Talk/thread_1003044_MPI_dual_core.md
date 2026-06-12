---
title: "MPI dual core"
date: 2008-12-05
forum: Programming Talk
---

### Post by kjohansen on 2008-12-05
I am taking a class in parallel computing, we have access to a super computer center through ssh but it is a very busy server right now and I cant get a hold of any nodes.

I want to install MPI on my dual core so that I can test without dealing with the cluster until I have a finished product.

I installed MPI but it is only recognizing one node, does anyone have any experience with MPI and dual core processes and know how to make it recognize both cores?

thanks.

---

### Post by slavik on 2008-12-05
One thing you can do is set up a virtual machine and use that as the second node.

---

### Post by ubuser_7 on 2008-12-06
You can do something like:

```

$ echo <your_ip_address> > my_machine
$ mpirun -np 4 -machinefile my_machine <other_arguments>

```

This would make MPI run on machines listed in the my_machine file. It will start all 4 (as in above example) on the same IP address. If you setup a virtual machine, you can add it to the my_machine file too (in a new line) and the processes will be distributed. 

This is what I am currently using. Hope this works.

---

### Post by xavions on 2009-05-21
Hi,

I'd like to learn how to use MPI on my dual core laptop. Could you please give me the steps to follow before i can run mpirun?
thanks

---

