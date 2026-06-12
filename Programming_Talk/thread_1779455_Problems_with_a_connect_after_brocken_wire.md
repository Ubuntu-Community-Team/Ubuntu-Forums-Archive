---
title: "Problems with a connect after brocken wire"
date: 2011-06-10
forum: Programming Talk
---

### Post by ritchie-w on 2011-06-10
Hi,

i just have the problem, that my tcp/ip client does not reconnect to the socket server after a shut down of the server.

As well, when the server will starts after the client.

The connect command will get always the errno "101", which means ENETUNREACH, network unreachable!

Only after a restart of the client, the connect will work again.

How can I get closer to the problem? What is my problem?

Here is the code of the openSocket()
```

	if( m_SocketDesc == 0)
		{
		m_SocketDesc=socket(AF_INET, SOCK_STREAM, 0);												// get a socket descriptor
		memset(&addr, 0, sizeof(addr));																						// clear the address
		addr.sin_family = AF_INET;																									// set up IP Address
		addr.sin_addr.s_addr =inet_addr(m_ServerIPAdress);
		addr.sin_port = htons(m_IPPort);																						// Set up the Port of the comunication
		if(connect(m_SocketDesc, (struct sockaddr*)&addr, sizeof(addr))==-1) 
			{
			qDebug() << "Socket Desc.:"  << m_SocketDesc << "Error no. "  << errno;
			close(m_SocketDesc);
			
			m_SocketDesc=0;
			sleep(5);
			return		1;
			}
		}

```

And here is the code of the CloseConnection, which I will call, when I get a failure during sendto() or recv().
```

har buffer;

	if( m_SocketDesc != 0)																											// Close only if a descriptor exists
		{
//		while(read(m_SocketDesc, &buffer, 1)>0);
//		while(recv(m_SocketDesc, &buffer, 1, MSG_NOSIGNAL)>0);
		shutdown(m_SocketDesc,SHUT_RDWR );

		if( close(m_SocketDesc) == 0 )
			m_SocketDesc=0;
		}

```

[b]
Edit:  I recode both program and used different functions for the connection and now it works.
[/b]

Greetings R.

---

