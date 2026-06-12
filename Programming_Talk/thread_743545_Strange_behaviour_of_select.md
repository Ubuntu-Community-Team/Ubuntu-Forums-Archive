---
title: "Strange behaviour of select"
date: 2008-04-02
forum: Programming Talk
---

### Post by fyplinux on 2008-04-02
I am using select in such a way:

```

.....
fd_set confds;
struct timeval contv;
int conretval;

FD_ZERO(&confds);

FD_SET(local_sock, &confds);//set the pipe of send/receive


contv.tv_sec = TIME_OUT;//timeout
contv.tv_usec = 0;

printf("select : waiting the connection to be established\n");
conretval = select(local_sock+1, NULL, &confds, NULL, &contv);//after this,the sets and timeout become undefined

printf("select returned\n");
if(conretval > 0){
	if(FD_ISSET(local_sock,&confds)){
		printf("local_sock is in set\n");
		if(write(local_sock,"hello",5) == -1){
			perror("Connect to a peer ");
			constat = 0;
		}
		//read ack
		char *hello = calloc(6,sizeof(char));
		if(read(local_sock,hello,5) == -1){
			perror("Connect to a peer ");
			constat = 0;
		}
		free(hello);
	}
	else{
		printf("Connect to %s time out\n", ipbuf);
		constat = 0;
	}
}
else{
	printf("Connect to %s time out\n", ipbuf);
	constat = 0;
}
....

```
The message sequence could be shown:
select : waiting the connection to be established
select returned
local_sock is in set

then the program is blocked for a long time(about 3 mins) to send the message.

Could you help me to find the reason?

---

### Post by bzamora on 2008-04-03
Not certain this will address your issue... but in the comm porgramming I've done in the past, sometimes data is not transmitted until a comm buffer has been filled or it times out. Consider doing a flush after your write and that may cause your data to be sent quicker.

---

### Post by supirman on 2008-04-03
The small snippet you posted isn't really enough to diagnose the issue easily..

How did you determine that the write call is blocking?  Did you put a printf between the write and read calls to see when the write call actually completes?  If you post the entire code so that the problem can be replicated, you'll likely get more help.

---

