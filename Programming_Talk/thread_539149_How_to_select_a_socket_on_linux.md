---
title: "How to select a socket on linux"
date: 2007-08-30
forum: Programming Talk
---

### Post by yinglcs2 on 2007-08-30
Hi,

I have the following code which listen on a socket for 20 sec.
it return 1 if something is available , -1 otherwise:

My question is even my program close the 'listenSocket' later on. It
shows as CLOSED_WAIT when I do a 'netstat' at the command prompt.

I am sure I close 'listenSocket' in my program. I am wonder if I am
doing the select calls  correctly and if I need to do anything to
clean things up.

Thank you for any tips.

int waitOnSocket(int listenSocket) {
fd_set read_set;
   struct timeval timeout;

   FD_ZERO( &read_set );                 /* clear the FD set */
   FD_SET( listenSocket, &read_set );    /* add the socket to the set
*/

   timeout.tv_sec  = 20;        /* set timeout to 20 s */
   timeout.tv_usec = 0;

   switch ( select( listenSocket + 1, &read_set, NULL, NULL,
&timeout ) )
   {
        case 0:
            printf ("RTSP Request wait timeout occured.\n");
            return -1;

        case 1 :
             return 1;

        default:
            printf ("some error during select\n" );
            return -1;
    }

return -1;
}

---

### Post by AZzKikR on 2007-08-31
I read a bit on the internet on CLOSE_WAIT, and it seems that the CLOSE_WAIT status doesn't have a timeout. One search result even talked about a CLOSE_WAIT of 5 days. I sthink you will have to manually close the socket in your code, but this is just an idea.

---

