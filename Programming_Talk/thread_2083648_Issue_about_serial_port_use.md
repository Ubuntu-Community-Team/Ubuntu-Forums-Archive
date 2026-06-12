---
title: "Issue about serial port use"
date: 2012-11-13
forum: Programming Talk
---

### Post by pellyhawk on 2012-11-13
Hi, I am reading some code block written in C/C++ and hope to used it in another project. But I have some difficulty in understanding it. Would you please help me?

```
typedef struct _SERIAL_PORT_STR_
{
	struct termios t, oldtermios;
	int			fd;
	UCHAR		portReadBuf[PORT_READ_BUF_SIZE];
	USHORT	read_In;
	USHORT	read_Out;
	USHORT	testCnt;
	UCHAR		aByte;
	UCHAR		recvAbyte;
	
	pthread_mutex_t mutex;
	pthread_t hReadThread;
	pthread_attr_t threadAttr;
}SERIAL_PORT;

#define SERIAL_PORT_NUM_MAX		3
static  SERIAL_PORT	SerialPort[SERIAL_PORT_NUM_MAX];
#define port	SerialPort[paraIndex]

UCHAR initPortReadThread(UCHAR portNo, int hCom)
{
	UCHAR  paraIndex = plaf_getPortIdx(portNo);
	
	port.fd = hCom;
	
	if(pthread_mutex_init(&port.mutex, NULL))
	{
		return FAILURE;
	}
	
	// initialize the thread attribute
	pthread_attr_init(&port.threadAttr);
	// Set the stack size of the thread
	pthread_attr_setstacksize(&port.threadAttr, 120*1024);
	// Create the thread
	
	/* MAX two port */
	if(pthread_create(&port.hReadThread, &port.threadAttr, PortReadThread, &paraIndex))
	{
		return FAILURE;
	}

#ifdef	_PLAF_DEBUG_
	printf("\nplaf init:::::portNo=%d, paraIndex=%d, port.fd=%d\n", portNo, paraIndex, port.fd);
#endif
	
	return SUCCESS;
}

void* PortReadThread(void *arg)
{
	char	log[64];
	UCHAR	paraIndex = *(UCHAR *)arg;
	
#ifdef	_PLAF_DEBUG_
	printf("PortReadThread start, paraIndex=%d, fd=%d", paraIndex, port.fd);
#endif
	
	while (port.fd > 0)
	{
		/*
		if ((++port.testCnt)%1000 == 0)
		{
			sprintf(log, "Port[%d] ReadThread running......", port.fd);
			plaf_writeLog(log);
		}
		*/
		
		/* Get the port mutex */
		pthread_mutex_lock(&port.mutex);
		ioctl(port.fd, CONTROL_SET_RTS, 0);
		do
		{
			port.recvAbyte = 0;
			port.recvAbyte = read(port.fd, &port.aByte, 1);
			if (port.recvAbyte == 1)
			{
				//printf("%02X ", port.aByte);
				port.portReadBuf[port.read_In] = port.aByte;
				port.read_In = (++port.read_In) % PORT_READ_BUF_SIZE;
				if (port.read_In == port.read_Out)
				{
					port.read_Out = (++port.read_Out) % PORT_READ_BUF_SIZE;
				}
				
				continue;
			}
		}while(port.recvAbyte == 1);
		
		//printf("\r\nport.read_In=%d,port.read_Out=%d\r\n ", port.read_In,port.read_Out);
		pthread_mutex_unlock(&port.mutex);
		usleep(5*1000);
	}
	pthread_mutex_destroy(&port.mutex);
	
	return SUCCESS;
}


ULONG plaf_Recveive(UCHAR portNo, UCHAR* buffer,USHORT len)
{
	ULONG bytes_read=0;
	UCHAR paraIndex = plaf_getPortIdx(portNo);
	
	if(port.read_In == port.read_Out)
	{
		return 0;
	}
	
	while(port.read_In != port.read_Out)
	{
		if (bytes_read >= len)
		{
			break;
		}
		buffer[bytes_read++] = port.portReadBuf[port.read_Out];
		port.read_Out = (++port.read_Out) % PORT_READ_BUF_SIZE;
	}
	
	return bytes_read;
}

USHORT plaf_AvailBytes(UCHAR portNo)
{
	USHORT temp_read_In = 0;
	USHORT temp_read_Out = 0;
	UCHAR  paraIndex = plaf_getPortIdx(portNo);
	
	temp_read_In = port.read_In;
	temp_read_Out = port.read_Out;
  
	if (temp_read_In == temp_read_Out)
	{
		return 0;
	}
	else if ((temp_read_In - temp_read_Out) > 0)
	{
		//printf("111recvLens=%d,read_In=%d,read_Out=%d\r\n",(temp_read_In - temp_read_Out),temp_read_In,temp_read_Out);
		return (temp_read_In - temp_read_Out);
	}
	else
	{
		//printf("222recvLens=%d,read_In=%d,read_Out=%d",((PORT_READ_BUF_SIZE - temp_read_Out)+temp_read_In),temp_read_In,temp_read_Out);
		return ((PORT_READ_BUF_SIZE - temp_read_Out)+temp_read_In);
	}
}
```

I questions are:
1. what are [COLOR="Red"]read_In[/COLOR] and [COLOR="Red"]read_Out[/COLOR], and what are their function, especially [COLOR="Red"]port.read_In == port.read_Out[/COLOR] and [COLOR="Red"]port.read_In != port.read_Out[/COLOR]. I guess they are pointers of buffer of read and write serial port respectively.

2. What does the function [COLOR="Red"]USHORT plaf_AvailBytes(UCHAR portNo) [/COLOR] do?

Many thanks.!!!

---

### Post by spjackson on 2012-11-13
It appears to me that read_In and read_Out mark the end and start of the used portion of the ring buffer portReadBuf.

(port.read_In == port.read_Out) ==> There are 0 bytes used in the buffer.
(port.read_In != port.read_Out) ==> There are > 0 bytes used in the buffer.

plaf_AvailBytes returns the number of bytes used in the buffer.

---

### Post by dwhitney67 on 2012-11-13
Not related to the original question, but the use of a local variable 'paraIndex' in the pthread_create() call, as shown below, can lead to an error:
```

if(pthread_create(&port.hReadThread, &port.threadAttr, PortReadThread, &**paraIndex**))
{
    ...
}

```
There's no guarantee that the thread will start "immediately" to digest the value stored in 'paraIndex' before this variable falls out of scope in the function that kicked off the thread.

This little program demonstrates the problem:
```

#include <pthread.h>
#include <stdio.h>
#include <inttypes.h>

void* thread(void* arg)
{
    uint8_t paraIndex = *(uint8_t*) arg;

    printf("paraIndex is %hhu\n", paraIndex);   /* prints 0, but should be 5 */

    return NULL;
}

pthread_t kick_off_thread()
{
    pthread_t tid;

    uint8_t paraIndex = 5;

    pthread_create(&tid, 0, thread, (void*) &paraIndex);

    return tid;
}

int main()
{
    pthread_t tid = kick_off_thread();
    pthread_join(tid, NULL);
    return 0;
}

```

P.S.  The program above yielded a value of 0, not the expected 5.

---

### Post by pellyhawk on 2012-11-14
> **spjackson said:**
> It appears to me that read_In and read_Out mark the end and start of the used portion of the ring buffer portReadBuf.

(port.read_In == port.read_Out) ==> There are 0 bytes used in the buffer.
(port.read_In != port.read_Out) ==> There are > 0 bytes used in the buffer.

plaf_AvailBytes returns the number of bytes used in the buffer.

Thank you!!

And I notice that read_In always points to the last byte position of portReadBuf, while the read_Out always points to the first byte position, i.e. 0. But the value of read_Out means the multiple of PORT_READ_BUF_SIZE. I do not know whether my understanding is correct.

I also found that in the whole project, read_In and read_Out is not initialized, such as give the value of "0". Then the read_In and read_Out is at random. I wonder if all linux compiler initialize variable with "0"?

Thanks

---

### Post by pellyhawk on 2012-11-14
Yeah, the problem is indeed existent. It seems I have to give a value we wanted to paraIndex in [COLOR="Red"]void* thread(void* arg)[/COLOR].
```
void* thread(void* arg)
{
    uint8_t paraIndex = *(uint8_t*) arg;
    
    [COLOR="Red"]paraIndex = 5;[/COLOR]

    printf("paraIndex is %hhu\n", paraIndex);   /* prints 0, but should be 5 */

    return NULL;
}
```

Do you have a better way to solve this bug? Thanks.

> **dwhitney67 said:**
> Not related to the original question, but the use of a local variable 'paraIndex' in the pthread_create() call, as shown below, can lead to an error:
```

if(pthread_create(&port.hReadThread, &port.threadAttr, PortReadThread, &**paraIndex**))
{
    ...
}

```
There's no guarantee that the thread will start "immediately" to digest the value stored in 'paraIndex' before this variable falls out of scope in the function that kicked off the thread.

This little program demonstrates the problem:
```

#include <pthread.h>
#include <stdio.h>
#include <inttypes.h>

void* thread(void* arg)
{
    uint8_t paraIndex = *(uint8_t*) arg;

    printf("paraIndex is %hhu\n", paraIndex);   /* prints 0, but should be 5 */

    return NULL;
}

pthread_t kick_off_thread()
{
    pthread_t tid;

    uint8_t paraIndex = 5;

    pthread_create(&tid, 0, thread, (void*) &paraIndex);

    return tid;
}

int main()
{
    pthread_t tid = kick_off_thread();
    pthread_join(tid, NULL);
    return 0;
}

```

P.S.  The program above yielded a value of 0, not the expected 5.

---

### Post by dwhitney67 on 2012-11-14
> **pellyhawk said:**
> 
Do you have a better way to solve this bug? Thanks.

In C, the only way to ensure that the data that is passed to the thread is viable, is to make sure that either the data stays in scope (declared in main() function or globally) or is allocated on the heap.


P.S.  Even the 'portNo' that is passed to the function initPortReadThread() is considered a local variable to the function.

---

### Post by pellyhawk on 2012-11-14
> **pellyhawk said:**
> Thank you!!

And I notice that read_In always points to the last byte position of portReadBuf, while the read_Out always points to the first byte position, i.e. 0. But the value of read_Out means the multiple of PORT_READ_BUF_SIZE. I do not know whether my understanding is correct.

I also found that in the whole project, read_In and read_Out is not initialized, such as give the value of "0". Then the read_In and read_Out is at random. I wonder if all linux compiler initialize variable with "0"?

Thanks
After learn what is ring buffer by google and what spjackson told me in the reply, I found that I make a mistake at my last post. But there is an exception about [COLOR="Red"](port.read_In == port.read_Out)[/COLOR]. In the function void* PortReadThread(void *arg), ```
				if (port.read_In == port.read_Out)
				{
					port.read_Out = (++port.read_Out) % PORT_READ_BUF_SIZE;
				}
```

it seems that (port.read_In == port.read_Out) does not mean there are 0 byte in the buffer. I guess it means it overwrite the byte read_Out points to, thus port.read_In also shifts. The function modified is as follow (marked in red): 

```
void* PortReadThread(void *arg)
{
	char	log[64];
	UCHAR	paraIndex = *(UCHAR *)arg;
	
#ifdef	_PLAF_DEBUG_
	printf("PortReadThread start, paraIndex=%d, fd=%d", paraIndex, port.fd);
#endif
	
	while (port.fd > 0)
	{
		/*
		if ((++port.testCnt)%1000 == 0)
		{
			sprintf(log, "Port[%d] ReadThread running......", port.fd);
			plaf_writeLog(log);
		}
		*/
		
		/* Get the port mutex */
		pthread_mutex_lock(&port.mutex);
		ioctl(port.fd, CONTROL_SET_RTS, 0);
		do
		{
			port.recvAbyte = 0;
			port.recvAbyte = read(port.fd, &port.aByte, 1);
			if (port.recvAbyte == 1)
			{
				//printf("%02X ", port.aByte);
				port.portReadBuf[port.read_In] = port.aByte;
				port.read_In = (++port.read_In) % PORT_READ_BUF_SIZE;
				if (port.read_In == port.read_Out) [COLOR="Red"]// overwrite the byte read_Out points to[/COLOR]
				{
                                    [COLOR="Red"]port.read_In = (++port.read_In) % PORT_READ_BUF_SIZE; // read_In also need a shift[/COLOR]
				    port.read_Out = (++port.read_Out) % PORT_READ_BUF_SIZE;
				}
				
				continue;
			}
		}while(port.recvAbyte == 1);
		
		//printf("\r\nport.read_In=%d,port.read_Out=%d\r\n ", port.read_In,port.read_Out);
		pthread_mutex_unlock(&port.mutex);
		usleep(5*1000);
	}
	pthread_mutex_destroy(&port.mutex);
	
	return SUCCESS;
}
```

Is it right? Thanks

P.S. That read_In and read_Out are not initialized before used is still a question. Do I need to initialize them with ```

read_In = 0;
read_Out = 0;
```

---

