---
title: "accept/epoll problem"
date: 2009-12-05
forum: Programming Talk
---

### Post by amanda2131821 on 2009-12-05
I have this code that uses epoll and it has a problem. When I run it, it gives output: Server-socket() is OK... Server-bind() is OK... 3 4 accept: Invalid argument
  I'm running it on ubuntu linux, system updated, both as limited user and root what is wrong with the input to accept? What should I change?
     struct epoll_event ev, events[MAX_EVENTS];
   struct sockaddr_in serveraddr;
   int listen_sock, conn_sock, nfds, epollfd;
   int yes = 1;

   /* Set up listening socket, 'listen_sock' (socket(),
   bind(), listen()) */

 if((listen_sock = socket(AF_INET, SOCK_STREAM, 0)) == -1) 
 {
  perror("Server-socket() error lol!");
  //just exit lol!
  exit(1);
 }
 printf("Server-socket() is OK...\n");
 //"address already in use" error message 
 /*if(setsockopt(listen_sock, SOL_SOCKET, SO_REUSEADDR, &yes, sizeof(int)) == -1) 
 {
  perror("Server-setsockopt() error lol!");
  exit(1);
 }
 printf("Server-setsockopt() is OK...\n");*/
 // bind 
 serveraddr.sin_family = AF_INET;
 serveraddr.sin_addr.s_addr = INADDR_ANY;
 serveraddr.sin_port = htons(PORT);
 memset(&(serveraddr.sin_zero), '\0', 8);
 if(bind(listen_sock, (struct sockaddr *)&serveraddr, sizeof(serveraddr)) == -1) 
 {
  perror("Server-bind() error lol!");
  exit(1);
 }
 printf("Server-bind() is OK...\n");

 epollfd = epoll_create(MAX_EVENTS);
 if (epollfd == -1) {
    perror("epoll_create");
    exit(EXIT_FAILURE);
 }

 ev.events = EPOLLIN;
 ev.data.fd = listen_sock;
 if (epoll_ctl(epollfd, EPOLL_CTL_ADD, listen_sock, &ev) == -1) {
    perror("epoll_ctl: listen_sock");
    exit(EXIT_FAILURE);
 }

 for (;;) {
    nfds = epoll_wait(epollfd, events, MAX_EVENTS, -1);
    if (nfds == -1) {
     perror("epoll_pwait");
     exit(EXIT_FAILURE);
    }

    for (int n = 0; n < nfds; ++n) {
     if (events[n].data.fd == listen_sock) {
      struct sockaddr_in clientaddr;
      socklen_t addrlen = sizeof(clientaddr);
      cout <<listen_sock <<'\n' <<epollfd <<'\n';
      conn_sock = accept(listen_sock, (struct sockaddr *) &clientaddr, &addrlen);
      if (conn_sock == -1) {
       perror("accept");
       exit(EXIT_FAILURE);
      }
      fcntl(conn_sock, F_SETFL, fcntl(conn_sock, F_GETFD, 0)|O_NONBLOCK);
      ev.events = EPOLLIN | EPOLLET;
      ev.data.fd = conn_sock;
      if (epoll_ctl(epollfd, EPOLL_CTL_ADD, conn_sock,
         &ev) == -1) {
       perror("epoll_ctl: conn_sock");
       exit(EXIT_FAILURE);
      }
     } else {
      printf("%d\n", events[n].data.fd);
     }
    }
 }

---

