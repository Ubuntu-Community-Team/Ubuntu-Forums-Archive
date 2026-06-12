---
title: "Device or Resource Busy in send() in socket programming"
date: 2013-02-21
forum: Programming Talk
---

### Post by mrjmrj on 2013-02-21
I am trying to communicate with a network interface through socket programming. In the first step I read and in the second step I write to the network interface. For both reading and writing I am using a same socket but I have two separate select() for each of them. The code is included. My problem is in writing. After 22 or 23 successful reading and writing send() returns error (Device or Resource Busy). This happens although select() does not timed out and FD_ISSET(socketD,&write_fds) returns true!!!. I am completely confused about this. If there is problem with writing (as send() states it) why select() does not notice???!!!!!. I should note that in the next round for writing select() blocks for 3-4 seconds that indicates that in this round it knows about the writing problem. This behavior continues and repeats.
Thanks in advance for help.



```
int main(void)
{
	
	/* some codes*/

	fd_set read_fds;
	fd_set write_fds;
	struct timeval timeout;

	for(;;)
	{
		/////////////////////////////////////////////////////////////
		// READING FROM SOCKET
		/////////////////////////////////////////////////////////////
		
		timeout.tv_sec = 10;
		timeout.tv_usec = 0;
		FD_ZERO(&read_fds);
		FD_SET(socketD,&read_fds);
				
		retselect=select(socketD+1, &read_fds, NULL, NULL, &timeout);

		if( retselect == 0)
		{
			...
		}

		if( retselect < 0)
		{
			....
		}


		if (FD_ISSET(socketD,&read_fds))
		{
			printf("Reading is possible\n");
			

			readSize = recv(socketD,buf,sizeof(buf),MSG_NOSIGNAL);

			
			fwrite(buf,1,readSize,fp);
			
						
		    
			if (readSize < 0) 
			{
				...
			}
			printf("Number of bytes read into the buffer: %d \n",readSize);
		}
		else
			printf("SELECT for read failed.\n");

		//FD_CLR(socketD,&read_fds);

		/////////////////////////////////////////////////////////////
		// WRITING TO SOCKET
		/////////////////////////////////////////////////////////////

		timeout.tv_sec = 10;
		timeout.tv_usec = 0;
		FD_ZERO(&write_fds);
		FD_SET(socketD,&write_fds);
		
		retselect=select(socketD+1, NULL, &write_fds, NULL, &timeout);

		if( retselect == 0)
		{
			...
		}

		if( retselect < 0)
		{
			...
		}
		
		
		if (FD_ISSET(socketD,&write_fds))
		{
			
			printf("Writing is possible\n");

				if ((readSize - WP_HEADER) == 4 && (buf[WP_HEADER + 3] == 1  || buf[WP_HEADER + 3] == 2 ))
				{
					
					
						memset(writeframe, 0, WP_HEADER + 4);
						memcpy(writeframe + WP_HEADER, sin, 4);
										}
				else
				{
					memset(writeframe, 0, WP_HEADER + 4);
					memcpy(writeframe + WP_HEADER, sio,4);
					
				}
				
				writeSize = send(socketD, writeframe, WP_HEADER + 4, 0);
				printf("Number of bytes Write into the buffer: %d \n", writeSize);
				

				if ( writeSize < 0)
				{
					perror("Write error,\n");
				}
				
				if (writeSize > 0)
				{	
					int writefilesize = fwrite(writeframe, 1, writeSize, writefp);
					printf("Buf size write to file = %d\n", writefilesize);
				}
	
		}
		else
			printf("SELECT for write failed.\n");

		//FD_CLR(socketD,&write_fds);
	}
```

---

### Post by dwhitney67 on 2013-02-21
See my response here:  [http://www.linuxquestions.org/questions/programming-9/device-or-resource-busy-in-send-in-socket-programming-4175451165/#post4896942](http://www.linuxquestions.org/questions/programming-9/device-or-resource-busy-in-send-in-socket-programming-4175451165/#post4896942)

---

