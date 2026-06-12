---
title: "Problem with array of pointers to sockets.. Please help :("
date: 2008-12-03
forum: Programming Talk
---

### Post by akshata on 2008-12-03
Hi ,
       I have been trying to store an array of pointers to sockets in a global structure, to retrieve it at a later point in time. But I'm unable to do so and the pointer points to some invalid address and the kernel crashes Could someone please  help me? This program is written in the kernel for Ubuntu 8.10

The following is the Code:

struct my_sock
{
     struct socket *cli_sock;
}Sock;
Sock *s[10];

struct socket * server_skt;
int sock_init()
{
     // Server binds and listens on a particular socket
       
while(1)
{
      for(i=0;i<3;i++)
      {
      s[i]=(Sock *)kmalloc(sizeof(Sock),GFP_KERNEL);
      iError=sock_create(PF_INET,SOCK_STREAM,IP_PROTO_TCP,&(s[i]->cli_sock));
        iError=server_skt->ops->accept(server_skt,s[i]->cli_sock,"connect");

       }
       kthread_run(kconnect,(void *)&data,0); 

}
}
int kconnect(void *data)
{
      for(i=0;i<3;i++)
      {
       ilen=sizeof(struct sockaddr);
       ierror=s[i]->cli_sock->ops->getname(s[i]->cli_sock,struct sockaddr *)&cli_addr,&ilen,1);
       // Here i get the value of iError as -107 defined as ENOCONN  when i tried printing s[i]->cli_sock address it showed a different value in the main fuction and in the thread. Am I losing the pointers here?  
       }
}


can anyone please tell me where im goin wrong with the pointers?

Thanks

---

### Post by dwhitney67 on 2008-12-03
Sorry... initial response edited.

Did you copy/paste this line of code, or did you type it in by hand?
```

ierror=s[i]->cli_sock->ops->getname(s[i]->cli_sock,struct sockaddr *)&cli_addr,&ilen,1);

```
It appears to be missing an opening parenthesis before struct sockaddr.

Also, have you been able to determine if the Sock pointer values are what you expect in your thread?  Are you not able to pass the array of Sock pointers as your thread data parameter?

---

### Post by akshata on 2008-12-03
Yes, i did type it in by hand and thats the reason the opening paranthesis is missing.

How can i pass an array of socket parameters as data to my thread and retrieve it from the thread? Is this possible? I tried printing out the pointers in the main function and the thread and they are different , even though the array of pointers is declared global.

Could you please help me how i can pass the array of pointers as an argument to the threas and access them in the thread?

Thanks

---

### Post by dwhitney67 on 2008-12-03
Hypothetically, the following should work:
[php]
...

Sock* s[10];

...

int init_sock()
{
  ...

  kthread_run(kconnect, s, 0); 

  // I've never written kernel drivers to this extent.  In regular C
  // applications, when you launch a thread, the main-thread (which is
  // where we are at the moment), cannot end until the spawned thread
  // finishes.  Thus I'm not sure if you need to check to ensure the
  // thread has finished before returning from the init_sock() function.
}

int kconnect(void *data)
{
  Sock** s = (Sock**) data;

  // now, the only problem here is that your program does not know
  // how many Socks there are; sure, you as the programmer know, but
  // really it is the thread that should be able to obtain this
  // information during runtime.  An alternative would be to bundle
  // the Sock array and the number of elements in the array into a
  // structure, then pass that structure as the data to the thread.

  ...
}
[/php]

---

