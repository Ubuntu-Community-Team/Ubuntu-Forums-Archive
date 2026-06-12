---
title: "lvalue require as left operand of assignment"
date: 2013-02-04
forum: Programming Talk
---

### Post by sanda199 on 2013-02-04
Hi everyone, I got above error in my program. My program is socket program. I am using ubuntu 11.10. 

#include <netdb.h>
#include <netinet/in.h>
#include <string.h>
#include <cstdlib>
#include <iostream>
#include <stdio.h>

#define PORT 4547

/*int parseARGS(char **args, char *line)
{
	int tmp = 0;
	args[tmp] = strtok(line, ":" );
	while ((args[++tmp] = strtok(NULL, ":" )) != NULL);
	return tmp -1;
}*/

int main(int argc, char *argv[])
{
	char *header[4096];
	int listenSOCKET, connectSOCKET;
	socklen_t clientADDRESSLENGTH;
	struct sockaddr_in clientADDRESS, serverADDRESS;
	char recvBUFF[4096];
	char *filename, *filesize;
	FILE *recvFILE;
	int received = 0;
	char tempstr[4096];
	
	int count1=1, count2=1, percent;
	
	listenSOCKET = socket(AF_INET, SOCK_STREAM, 0);
	if (listenSOCKET <0)
	{
		printf("Cannot create socket\n");
		close(listenSOCKET);
		return 1;
	}
	PORT = atoi(argv[1]);
	serverADDRESS.sin_family = AF_INET;
	serverADDRESS.sin_addr.s_addr = INADDR_ANY;
	serverADDRESS.sin_port = htons(PORT);

	if (bind(listenSOCKET, (struct sockaddr *)&serverADDRESS, sizeof(serverADDRESS))<0)
	{
		printf("Cannot bind socket\n");
		close(listenSOCKET);
		return 1;
	}
	
	listen(listenSOCKET, 5);
	clientADDRESSLENGTH = sizeof(clientADDRESS);
	connectSOCKET = accept(listenSOCKET,(struct sockaddr *)&clientADDRESS, &clientADDRESSLENGTH);
	if (connectSOCKET<0)
	{
		printf("Cannot accpet connection\n");
		close(listenSOCKET);
		return 1;
	}
	bzero(recvBUFF,4096);
	while(1)
	{
		if(recv(connectSOCKET,recvBUFF,1,0) == 0)
			printf("ERROR on receiving");
	}
	close(listenSOCKET);
	return 0;
}


if anyone know how to solve it.pls kindly tell me. thanks.

---

### Post by Bachstelze on 2013-02-05
On which line? Please paste the error message in full.

---

### Post by sanda199 on 2013-02-05
> **Bachstelze said:**
> On which line? Please paste the error message in full.



I found the error. It is because of that line. 
PORT = atoi(argv[1]);

---

### Post by r-senior on 2013-02-05
Does this mean that your problem is solved? If so, please look for the options near the top of your page that allow you to mark the thread as solved.

---

### Post by ofnuts on 2013-02-05
So, once the preprocessor has run, you get:
```

4547 = atoi(argv[1]);

```

PORT is not the name of a variable. Maybe you want:
```

#define DEFAULT_PORT 4547
int port=DEFAULT_PORT;

```

---

